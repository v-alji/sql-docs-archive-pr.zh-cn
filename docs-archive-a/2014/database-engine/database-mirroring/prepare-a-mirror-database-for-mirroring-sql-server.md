---
title: 为镜像准备镜像数据库 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], preparing for mirroring
- logins [SQL Server], database mirroring
- mirror database [SQL Server]
ms.assetid: 8676f9d8-c451-419b-b934-786997d46c2b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: cf46b4f6fd8e7af55e1930ef6063c4754673fa79
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690126"
---
# <a name="prepare-a-mirror-database-for-mirroring-sql-server"></a><span data-ttu-id="7e48f-102">为镜像准备镜像数据库 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="7e48f-102">Prepare a Mirror Database for Mirroring (SQL Server)</span></span>
  <span data-ttu-id="7e48f-103">在数据库镜像会话开始之前，数据库所有者或系统管理员必须确保已创建镜像数据库并可进行镜像。</span><span class="sxs-lookup"><span data-stu-id="7e48f-103">Before a database mirroring session can start, the database owner or system administrator must make sure that the mirror database has been created and is ready for mirroring.</span></span> <span data-ttu-id="7e48f-104">创建新镜像数据库的最低要求是：执行主体数据库的完整备份和一个后续日志备份，并使用 WITH NORECOVERY 将这两个备份还原到镜像服务器实例上。</span><span class="sxs-lookup"><span data-stu-id="7e48f-104">Creating a new mirror database minimally requires taking a full backup of the principal database and a subsequent log backup and restoring them both onto the mirror server instance, using WITH NORECOVERY.</span></span>  
  
 <span data-ttu-id="7e48f-105">本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中准备镜像数据库。</span><span class="sxs-lookup"><span data-stu-id="7e48f-105">This topic describes how to prepare a mirror database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="7e48f-106">开始之前</span><span class="sxs-lookup"><span data-stu-id="7e48f-106">Before You Begin</span></span>  
  
###  <a name="requirements"></a><a name="Requirements"></a> <span data-ttu-id="7e48f-107">要求</span><span class="sxs-lookup"><span data-stu-id="7e48f-107">Requirements</span></span>  
  
-   <span data-ttu-id="7e48f-108">主体服务器和镜像服务器实例必须运行在相同版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]上。</span><span class="sxs-lookup"><span data-stu-id="7e48f-108">The principal and mirror server instances must be running on the same version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="7e48f-109">尽管镜像服务器可以具有更高版本的 SQL Server，但仅在仔细计划的升级过程中建议此配置。</span><span class="sxs-lookup"><span data-stu-id="7e48f-109">While it is possible for the mirror server to have a higher version of SQL Server, this configuration is only recommended during a carefully planned upgrade process.</span></span> <span data-ttu-id="7e48f-110">在此类配置中，会面临自动故障转移的风险，数据移动在其中会被自动挂起，因为数据不能移到更低版本的 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="7e48f-110">In such a configuration, you run the risk of an automatic failover, in which data movement is automatically suspended because data cannot move to a lower version of SQL Server.</span></span> <span data-ttu-id="7e48f-111">有关详细信息，请参阅 [Minimize Downtime for Mirrored Databases When Upgrading Server Instances](upgrading-mirrored-instances.md)。</span><span class="sxs-lookup"><span data-stu-id="7e48f-111">For more information, see [Minimize Downtime for Mirrored Databases When Upgrading Server Instances](upgrading-mirrored-instances.md).</span></span>  
  
-   <span data-ttu-id="7e48f-112">主体服务器和镜像服务器实例必须运行在相同版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]上。</span><span class="sxs-lookup"><span data-stu-id="7e48f-112">The principal and mirror server instances must be running on the same edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="7e48f-113">有关 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中数据库镜像支持的详细信息，请参阅 [SQL Server 2014 各个版本支持的功能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="7e48f-113">For information about support for database mirroring in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
-   <span data-ttu-id="7e48f-114">数据库必须使用完整恢复模式。</span><span class="sxs-lookup"><span data-stu-id="7e48f-114">The database must use the full recovery model.</span></span>  
  
     <span data-ttu-id="7e48f-115">有关详细信息，请参阅[查看或更改数据库的恢复模式 (SQL Server)](../../relational-databases/backup-restore/view-or-change-the-recovery-model-of-a-database-sql-server.md) 或 [sys.databases (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) 和 [ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="7e48f-115">For more information, see [View or Change the Recovery Model of a Database &#40;SQL Server&#41;](../../relational-databases/backup-restore/view-or-change-the-recovery-model-of-a-database-sql-server.md) or [sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) and [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
-   <span data-ttu-id="7e48f-116">镜像数据库的名称必须与主体数据库的名称相同。</span><span class="sxs-lookup"><span data-stu-id="7e48f-116">The name of the mirror database must be the same as the name of the principal database.</span></span>  
  
-   <span data-ttu-id="7e48f-117">为使镜像正常运行，镜像数据库必须处于 RESTORING 状态。</span><span class="sxs-lookup"><span data-stu-id="7e48f-117">The mirror database must be in the RESTORING state for mirroring to work.</span></span> <span data-ttu-id="7e48f-118">准备镜像数据库时，对于每个还原操作都必须使用 RESTORE WITH NORECOVERY。</span><span class="sxs-lookup"><span data-stu-id="7e48f-118">When preparing a mirror database, you must use RESTORE WITH NORECOVERY for every restore operation.</span></span> <span data-ttu-id="7e48f-119">至少，需要还原主体数据库的完整备份（WITH NORECOVERY），之后进行所有后续的日志备份。</span><span class="sxs-lookup"><span data-stu-id="7e48f-119">Minimally, you will need to restore WITH NORECOVERY a full backup of the principal database, followed by all subsequent log backups.</span></span>  
  
-   <span data-ttu-id="7e48f-120">计划创建镜像数据库的系统的磁盘驱动器空间必须足以容纳镜像数据库。</span><span class="sxs-lookup"><span data-stu-id="7e48f-120">The system where you plan to create the mirror database must possesses a disk drive with sufficient space to hold the mirror database.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="7e48f-121">限制和局限</span><span class="sxs-lookup"><span data-stu-id="7e48f-121">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="7e48f-122">不能镜像 **master**、 **msdb**、 **temp**或 **model** 系统数据库。</span><span class="sxs-lookup"><span data-stu-id="7e48f-122">You cannot mirror the **master**, **msdb**, **temp**, or **model** system databases.</span></span>  
  
-   <span data-ttu-id="7e48f-123">不能镜像属于[AlwaysOn 可用性组 (SQL Server) ](../availability-groups/windows/always-on-availability-groups-sql-server.md)的数据库。</span><span class="sxs-lookup"><span data-stu-id="7e48f-123">You cannot mirror a database that belongs to an [AlwaysOn Availability Groups (SQL Server)](../availability-groups/windows/always-on-availability-groups-sql-server.md).</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="7e48f-124">建议</span><span class="sxs-lookup"><span data-stu-id="7e48f-124">Recommendations</span></span>  
  
-   <span data-ttu-id="7e48f-125">使用最近的主体数据库的完整数据库备份或最近的差异数据库备份。</span><span class="sxs-lookup"><span data-stu-id="7e48f-125">Use a very recent full database backup or a recent differential database backup of the principal database.</span></span>  
  
-   <span data-ttu-id="7e48f-126">如果计划在主体数据库中非常频繁地运行日志备份作业，则可能需要禁用备份作业，直到镜像启动为止。</span><span class="sxs-lookup"><span data-stu-id="7e48f-126">If a log backup job is scheduled to run very frequently on the principal database, you might have to disable the backup job until mirroring has started.</span></span>  
  
-   <span data-ttu-id="7e48f-127">如有可能，镜像数据库的路径（包括驱动器号）应该与主体数据库的路径相同。</span><span class="sxs-lookup"><span data-stu-id="7e48f-127">If possible, the path (including the drive letter) of the mirror database should be identical to the path of the principal database.</span></span>  
  
     <span data-ttu-id="7e48f-128">如果文件路径必须互不相同（例如，如果主体数据库位于“F:”驱动器上，但镜像系统没有“F:”驱动器），则必须在 RESTORE 语句中加入 MOVE 选项。</span><span class="sxs-lookup"><span data-stu-id="7e48f-128">If the file paths must differ, for example, if the principal database is on drive 'F:' but the mirror system lacks an F: drive, you must include the MOVE option in the RESTORE STATEMENT.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="7e48f-129">在不影响会话的情况下，在镜像会话过程中添加文件要求该文件路径同时存在于两个服务器上。</span><span class="sxs-lookup"><span data-stu-id="7e48f-129">Adding a file during a mirroring session without impacting the session requires that the path of the file exists on both servers.</span></span> <span data-ttu-id="7e48f-130">因此，如果在创建镜像数据库时移动了数据库文件，则随后在镜像数据库上的添加文件操作可能会失败，并可能会导致镜像挂起。</span><span class="sxs-lookup"><span data-stu-id="7e48f-130">Therefore, if you move the database files when creating the mirror database, a later add-file operation might fail on the mirror database and cause mirroring to be suspended.</span></span> <span data-ttu-id="7e48f-131">有关处理失败的创建文件操作的详细信息，请参阅[数据库镜像配置故障排除 (SQL Server)](troubleshoot-database-mirroring-configuration-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="7e48f-131">For information about dealing with a failed create-file operation, see [Troubleshoot Database Mirroring Configuration &#40;SQL Server&#41;](troubleshoot-database-mirroring-configuration-sql-server.md).</span></span>  
  
-   <span data-ttu-id="7e48f-132">如果主体数据库具有任何全文目录，建议参阅[数据库镜像和全文目录 (SQL Server)](database-mirroring-and-full-text-catalogs-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="7e48f-132">If the principal database has any full-text catalogs, we recommend that you see [Database Mirroring and Full-Text Catalogs &#40;SQL Server&#41;](database-mirroring-and-full-text-catalogs-sql-server.md).</span></span>  
  
-   <span data-ttu-id="7e48f-133">对于生产数据库，始终备份到单独的设备。</span><span class="sxs-lookup"><span data-stu-id="7e48f-133">For a production database, always back up to a separate device.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="7e48f-134">Security</span><span class="sxs-lookup"><span data-stu-id="7e48f-134">Security</span></span>  
 <span data-ttu-id="7e48f-135">备份数据库时，TRUSTWORTHY 设置为 OFF。</span><span class="sxs-lookup"><span data-stu-id="7e48f-135">TRUSTWORTHY is set to OFF when a database is backed up.</span></span> <span data-ttu-id="7e48f-136">因此，在新的镜像数据库中，TRUSTWORTHY 始终为 OFF。</span><span class="sxs-lookup"><span data-stu-id="7e48f-136">Therefore, TRUSTWORTHY is always OFF on a new mirror database.</span></span> <span data-ttu-id="7e48f-137">如果数据库在故障转移之后需要得到信任，则必须执行其他设置步骤。</span><span class="sxs-lookup"><span data-stu-id="7e48f-137">If the database needs to be trustworthy after a failover, additional setup steps are necessary.</span></span> <span data-ttu-id="7e48f-138">有关详细信息，请参阅 [将镜像数据库设置为使用 Trustworthy 属性 (Transact-SQL)](set-up-a-mirror-database-to-use-the-trustworthy-property-transact-sql.md)中准备镜像数据库。</span><span class="sxs-lookup"><span data-stu-id="7e48f-138">For more information, see [Set Up a Mirror Database to Use the Trustworthy Property &#40;Transact-SQL&#41;](set-up-a-mirror-database-to-use-the-trustworthy-property-transact-sql.md).</span></span>  
  
 <span data-ttu-id="7e48f-139">有关启用镜像数据库主秘钥自动加密的详细信息，请参阅 [设置加密的镜像数据库](set-up-an-encrypted-mirror-database.md)。</span><span class="sxs-lookup"><span data-stu-id="7e48f-139">For information about enabling automatic decryption of the database master key of a mirror database, see [Set Up an Encrypted Mirror Database](set-up-an-encrypted-mirror-database.md).</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="7e48f-140">权限</span><span class="sxs-lookup"><span data-stu-id="7e48f-140">Permissions</span></span>  
 <span data-ttu-id="7e48f-141">数据库所有者或系统管理员。</span><span class="sxs-lookup"><span data-stu-id="7e48f-141">Database owner or system administrator.</span></span>  
  
##  <a name="to-prepare-an-existing-mirror-database-to-restart-mirroring"></a><a name="PrepareToRestartMirroring"></a> <span data-ttu-id="7e48f-142">准备现有镜像数据库以重新启动镜像</span><span class="sxs-lookup"><span data-stu-id="7e48f-142">To Prepare an Existing Mirror Database to Restart Mirroring</span></span>  
 <span data-ttu-id="7e48f-143">如果已删除镜像，并且该镜像数据库仍处于 RECOVERING 状态，则可以重新启动镜像。</span><span class="sxs-lookup"><span data-stu-id="7e48f-143">If mirroring has been removed and the mirror database is still in the RECOVERING state, you can restart mirroring.</span></span>  
  
1.  <span data-ttu-id="7e48f-144">至少进行主体数据库的一个日志备份。</span><span class="sxs-lookup"><span data-stu-id="7e48f-144">Take at least one log backup on the principal database.</span></span> <span data-ttu-id="7e48f-145">有关详细信息，请参阅 [备份事务日志 (SQL Server)](../../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md)数据库还原到一个新位置并且可以选择重命名该数据库。</span><span class="sxs-lookup"><span data-stu-id="7e48f-145">For more information, see [Back Up a Transaction Log &#40;SQL Server&#41;](../../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="7e48f-146">在镜像数据库中，使用 RESTORE WITH NORECOVERY 还原删除镜像后在主体数据库中执行的所有日志备份。</span><span class="sxs-lookup"><span data-stu-id="7e48f-146">On the mirror database, use RESTORE WITH NORECOVERY to restore all log backups taken on the principal database since mirroring was removed.</span></span> <span data-ttu-id="7e48f-147">有关详细信息，请参阅 [还原事务日志备份 (SQL Server)](../../relational-databases/backup-restore/restore-a-transaction-log-backup-sql-server.md)中准备镜像数据库。</span><span class="sxs-lookup"><span data-stu-id="7e48f-147">For more information, see [Restore a Transaction Log Backup &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-a-transaction-log-backup-sql-server.md).</span></span>  
  
##  <a name="to-prepare-a-new-mirror-database"></a><a name="CombinedProcedure"></a> <span data-ttu-id="7e48f-148">准备新的镜像数据库</span><span class="sxs-lookup"><span data-stu-id="7e48f-148">To Prepare a New Mirror Database</span></span>  
 <span data-ttu-id="7e48f-149">**准备镜像数据库**</span><span class="sxs-lookup"><span data-stu-id="7e48f-149">**To prepare a mirror database**</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7e48f-150">有关此过程的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 示例，请参阅本节后面的 [示例 (Transact-SQL)](#TsqlExample)。</span><span class="sxs-lookup"><span data-stu-id="7e48f-150">For a [!INCLUDE[tsql](../../includes/tsql-md.md)] example of this procedure, see [Example (Transact-SQL)](#TsqlExample), later in this section.</span></span>  
  
1.  <span data-ttu-id="7e48f-151">连接到主体服务器实例。</span><span class="sxs-lookup"><span data-stu-id="7e48f-151">Connect to principal server instance.</span></span>  
  
2.  <span data-ttu-id="7e48f-152">创建主体数据库的完整数据库备份或差异数据库备份。</span><span class="sxs-lookup"><span data-stu-id="7e48f-152">Create either a full database backup or a differential database backup of the principal database.</span></span>  
  
    -   [<span data-ttu-id="7e48f-153">创建完整数据库备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="7e48f-153">Create a Full Database Backup &#40;SQL Server&#41;</span></span>](../../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)  
  
    -   <span data-ttu-id="7e48f-154">[创建差异数据库备份 (SQL Server)](../../relational-databases/backup-restore/create-a-differential-database-backup-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="7e48f-154">[Create a Differential Database Backup &#40;SQL Server&#41;](../../relational-databases/backup-restore/create-a-differential-database-backup-sql-server.md).</span></span>  
  
3.  <span data-ttu-id="7e48f-155">一般您需要至少进行主体数据库的一个日志备份。</span><span class="sxs-lookup"><span data-stu-id="7e48f-155">Typically, you need to take at least one log backup on the principal database.</span></span> <span data-ttu-id="7e48f-156">但是，如果数据库刚刚创建而尚未进行日志备份，或者如果恢复模式刚刚从 SIMPLE 更改为 FULL，则不必进行日志备份。</span><span class="sxs-lookup"><span data-stu-id="7e48f-156">However, a log backup might be unnecessary, if the database has just been created and no log backup has been taken yet, or if the recovery model has just been changed from SIMPLE to FULL.</span></span>  
  
    -   [<span data-ttu-id="7e48f-157">备份事务日志 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="7e48f-157">Back Up a Transaction Log &#40;SQL Server&#41;</span></span>](../../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md)  
  
4.  <span data-ttu-id="7e48f-158">除非备份是在从两个系统均可访问的网络驱动器上，否则将数据库备份和日志备份复制到将承载镜像服务器实例的系统。</span><span class="sxs-lookup"><span data-stu-id="7e48f-158">Unless the backups are on a network drive that is accessible from both systems, copy the database and log backups to the system that will host the mirror server instance.</span></span>  
  
5.  <span data-ttu-id="7e48f-159">连接到镜像服务器实例。</span><span class="sxs-lookup"><span data-stu-id="7e48f-159">Connect to mirror server instance.</span></span>  
  
6.  <span data-ttu-id="7e48f-160">使用 RESTORE WITH NORECOVERY，通过还原完整数据库备份和最近的差异数据库备份（后者为可选项）到镜像服务器实例，来创建镜像数据库。</span><span class="sxs-lookup"><span data-stu-id="7e48f-160">Using RESTORE WITH NORECOVERY, create the mirror database by restoring the full database backup and, optionally, the most recent differential database backup, onto the mirror server instance.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7e48f-161">如果要逐个文件组地还原数据库，则要确保还原整个数据库。</span><span class="sxs-lookup"><span data-stu-id="7e48f-161">If you restore the database filegroup by filegroup, be sure to restore the whole database.</span></span>  
  
    -   [<span data-ttu-id="7e48f-162">还原数据库备份 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="7e48f-162">Restore a Database Backup &#40;SQL Server Management Studio&#41;</span></span>](../../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md)  
  
    -   <span data-ttu-id="7e48f-163">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) 和 [RESTORE 参数 (Transact-SQL)](/sql/t-sql/statements/restore-statements-arguments-transact-sql)中准备镜像数据库。</span><span class="sxs-lookup"><span data-stu-id="7e48f-163">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) and [RESTORE Arguments &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql).</span></span>  
  
7.  <span data-ttu-id="7e48f-164">使用 RESTORE WITH NORECOVERY，将所有未完成的日志备份应用到镜像数据库。</span><span class="sxs-lookup"><span data-stu-id="7e48f-164">Using RESTORE WITH NORECOVERY, apply any outstanding log backup or backups to the mirror database.</span></span>  
  
    -   [<span data-ttu-id="7e48f-165">还原事务日志备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="7e48f-165">Restore a Transaction Log Backup &#40;SQL Server&#41;</span></span>](../../relational-databases/backup-restore/restore-a-transaction-log-backup-sql-server.md)  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="7e48f-166">示例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="7e48f-166">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="7e48f-167">必须先创建镜像数据库，才能启动数据库镜像会话。</span><span class="sxs-lookup"><span data-stu-id="7e48f-167">Before you can start a database mirroring session, you must create the mirror database.</span></span> <span data-ttu-id="7e48f-168">应该在启动镜像会话之前执行此操作。</span><span class="sxs-lookup"><span data-stu-id="7e48f-168">You should do this just before starting the mirroring session.</span></span>  
  
 <span data-ttu-id="7e48f-169">此示例使用了 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 示例数据库，默认情况下，该数据库使用简单恢复模式。</span><span class="sxs-lookup"><span data-stu-id="7e48f-169">This example uses the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database, which uses the simple recovery model by default.</span></span>  
  
1.  <span data-ttu-id="7e48f-170">若要对 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 数据库使用数据库镜像，请改用完整恢复模式：</span><span class="sxs-lookup"><span data-stu-id="7e48f-170">To use database mirroring with the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database, modify it to use the full recovery model:</span></span>  
  
    ```  
    USE master;  
    GO  
    ALTER DATABASE AdventureWorks   
    SET RECOVERY FULL;  
    GO  
    ```  
  
2.  <span data-ttu-id="7e48f-171">将数据库的恢复模式从 SIMPLE 更改为 FULL 之后，创建一个完整备份，以用于创建镜像数据库。</span><span class="sxs-lookup"><span data-stu-id="7e48f-171">After modifying the recovery model of the database from SIMPLE to FULL, create a full backup, which can be used to create the mirror database.</span></span> <span data-ttu-id="7e48f-172">由于恢复模式已更改，因此指定了 WITH FORMAT 选项来创建新的介质集。</span><span class="sxs-lookup"><span data-stu-id="7e48f-172">Because the recovery model has just been changed, the WITH FORMAT option is specified to create a new media set.</span></span> <span data-ttu-id="7e48f-173">这对区分完整恢复模式下的备份与以前在简单恢复模式下创建的备份非常有用。</span><span class="sxs-lookup"><span data-stu-id="7e48f-173">This is useful to separate the backups under the full recovery model from any previous backups made under the simple recovery model.</span></span> <span data-ttu-id="7e48f-174">为了实现此示例的目的，在数据库所在的同一驱动器上创建备份文件 (`C:\AdventureWorks.bak`)。</span><span class="sxs-lookup"><span data-stu-id="7e48f-174">For the purpose of this example, the backup file (`C:\AdventureWorks.bak`) is created on the same drive as the database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7e48f-175">对于生产数据库，应始终备份到单独的设备。</span><span class="sxs-lookup"><span data-stu-id="7e48f-175">For a production database, you should always back up to a separate device.</span></span>  
  
     <span data-ttu-id="7e48f-176">在主体服务器实例 ( `PARTNERHOST1`) 上，创建主体数据库的完整备份，如下所示：</span><span class="sxs-lookup"><span data-stu-id="7e48f-176">On the principal server instance (on `PARTNERHOST1`), create a full backup of the principal database as follows:</span></span>  
  
    ```  
    BACKUP DATABASE AdventureWorks   
        TO DISK = 'C:\AdventureWorks.bak'   
        WITH FORMAT  
    GO  
    ```  
  
3.  <span data-ttu-id="7e48f-177">将完整备份复制到镜像服务器。</span><span class="sxs-lookup"><span data-stu-id="7e48f-177">Copy the full backup to the mirror server.</span></span>  
  
4.  <span data-ttu-id="7e48f-178">使用 RESTORE WITH NORECOVERY，将完整备份还原到镜像服务器实例。</span><span class="sxs-lookup"><span data-stu-id="7e48f-178">Using RESTORE WITH NORECOVERY, restore the full backup onto the mirror server instance.</span></span> <span data-ttu-id="7e48f-179">还原命令取决于主体数据库与镜像数据库的路径是否相同。</span><span class="sxs-lookup"><span data-stu-id="7e48f-179">The restore command depends on whether the paths of principal and mirror databases are identical.</span></span>  
  
    -   <span data-ttu-id="7e48f-180">**如果路径相同：**</span><span class="sxs-lookup"><span data-stu-id="7e48f-180">**If the paths are identical:**</span></span>  
  
         <span data-ttu-id="7e48f-181">在 `PARTNERHOST5`的镜像服务器实例上，还原完整备份，如下所示：</span><span class="sxs-lookup"><span data-stu-id="7e48f-181">On the mirror server instance (on `PARTNERHOST5`), restore the full backup as follows:</span></span>  
  
        ```  
        RESTORE DATABASE AdventureWorks   
            FROM DISK = 'C:\AdventureWorks.bak'   
            WITH NORECOVERY  
        GO  
        ```  
  
    -   <span data-ttu-id="7e48f-182">**如果路径不同：**</span><span class="sxs-lookup"><span data-stu-id="7e48f-182">**If the paths differ:**</span></span>  
  
         <span data-ttu-id="7e48f-183">如果镜像数据库的路径与主体数据库的路径不同（例如，它们所在的驱动器号不同），则创建镜像数据库要求还原操作包含 MOVE 子句。</span><span class="sxs-lookup"><span data-stu-id="7e48f-183">If the path of the mirror database differs from the path of the principal database (for instance, their drive letters differ), creating the mirror database requires that the restore operation include a MOVE clause.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="7e48f-184">如果主体数据库与镜像数据库的路径名称不同，则无法添加文件。</span><span class="sxs-lookup"><span data-stu-id="7e48f-184">If the path names of the principal and mirror databases differ, you cannot add a file.</span></span> <span data-ttu-id="7e48f-185">原因是在接收添加文件操作所需的日志时，镜像服务器实例尝试将新文件放置在主体数据库所在的位置。</span><span class="sxs-lookup"><span data-stu-id="7e48f-185">This is because on receiving the log for the add file operation, the mirror server instance attempts to place the new file in the location used by the principal database.</span></span>  
  
         <span data-ttu-id="7e48f-186">例如，以下命令将位于 C:\Program Files\Microsoft SQL Server\MSSQL.*n*\MSSQL\Data\ 中的主体数据库备份还原到镜像数据库所在的另一个位置 D:\Program Files\Microsoft SQL Server\MSSQL.*n*\MSSQL\Dat`a\`。</span><span class="sxs-lookup"><span data-stu-id="7e48f-186">For example, the following command restores a backup of a principal database residing in C:\Program Files\Microsoft SQL Server\MSSQL.*n*\MSSQL\Data\ to a different location, D:\Program Files\Microsoft SQL Server\MSSQL.*n*\MSSQL\Dat`a\`, where the mirror database is to reside.</span></span>  
  
        ```  
        RESTORE DATABASE AdventureWorks  
           FROM DISK='C:\AdventureWorks.bak'  
           WITH NORECOVERY,   
              MOVE 'AdventureWorks_Data' TO   
                 'D:\Program Files\Microsoft SQL Server\MSSQL.n\MSSQL\Data\AdventureWorks_Data.mdf',   
              MOVE 'AdventureWorks_Log' TO  
                 'D:\Program Files\Microsoft SQL Server\MSSQL.n\MSSQL\Data\AdventureWorks_Log.ldf';  
        GO  
        ```  
  
5.  <span data-ttu-id="7e48f-187">创建完整备份之后，必须在主体数据库中创建日志备份。</span><span class="sxs-lookup"><span data-stu-id="7e48f-187">After you create the full backup, you must create a log backup on the principal database.</span></span> <span data-ttu-id="7e48f-188">例如，下面的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句将日志备份到先前的完整备份所使用的文件中：</span><span class="sxs-lookup"><span data-stu-id="7e48f-188">For example, the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement backs up the log to the same file used by the preceding full backup:</span></span>  
  
    ```  
    BACKUP LOG AdventureWorks   
        TO DISK = 'C:\AdventureWorks.bak'   
    GO  
    ```  
  
6.  <span data-ttu-id="7e48f-189">在开始镜像之前，必须应用必要的日志备份（以及所有后续日志备份）。</span><span class="sxs-lookup"><span data-stu-id="7e48f-189">Before you can start mirroring, you must apply the required log backup (and any subsequent log backups).</span></span>  
  
     <span data-ttu-id="7e48f-190">例如，以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句还原 `C:\AdventureWorks.bak`中的第一个日志：</span><span class="sxs-lookup"><span data-stu-id="7e48f-190">For example, the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement restores the first log from `C:\AdventureWorks.bak`:</span></span>  
  
    ```  
    RESTORE LOG AdventureWorks   
        FROM DISK = 'C:\AdventureWorks.bak'   
        WITH FILE=1, NORECOVERY  
    GO  
    ```  
  
7.  <span data-ttu-id="7e48f-191">如果在开始镜像之前进行任何其他日志备份，则还必须使用 WITH NORECOVERY 按顺序将所有这些日志备份还原到镜像服务器上。</span><span class="sxs-lookup"><span data-stu-id="7e48f-191">If any additional log backups occur before you start mirroring, you must also restore all of those log backups, in sequence, to the mirror server using WITH NORECOVERY.</span></span>  
  
     <span data-ttu-id="7e48f-192">例如，以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句还原 `C:\AdventureWorks.bak`中的其他两个日志：</span><span class="sxs-lookup"><span data-stu-id="7e48f-192">For example, the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement restores two additional logs from `C:\AdventureWorks.bak`:</span></span>  
  
    ```  
    RESTORE LOG AdventureWorks   
        FROM DISK = 'C:\AdventureWorks.bak'   
        WITH FILE=2, NORECOVERY  
    GO  
    RESTORE LOG AdventureWorks   
        FROM DISK = 'C:\AdventureWorks.bak'   
        WITH FILE=3, NORECOVERY  
    GO  
    ```  
  
 <span data-ttu-id="7e48f-193">有关设置数据库镜像、显示安全设置、准备镜像数据库、设置合作伙伴以及添加见证服务器的完整示例的信息，请参阅 [设置数据库镜像 (SQL Server)](database-mirroring-sql-server.md)中准备镜像数据库。</span><span class="sxs-lookup"><span data-stu-id="7e48f-193">For a complete example of setting up database mirroring, showing security setup, preparing the mirror database, setting up the partners, and adding a witness, see [Setting Up Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-preparing-a-mirror-database"></a><a name="FollowUp"></a> <span data-ttu-id="7e48f-194">跟进：准备镜像数据库之后</span><span class="sxs-lookup"><span data-stu-id="7e48f-194">Follow Up: After Preparing a Mirror Database</span></span>  
  
1.  <span data-ttu-id="7e48f-195">如果在最近的 RESTORE LOG 操作之后已执行了任何其他日志备份，则还必须使用 RESTORE WITH NORECOVERY 手动应用其他每个日志备份。</span><span class="sxs-lookup"><span data-stu-id="7e48f-195">If any additional log backups have been taken since your most recent RESTORE LOG operation, you must manually apply every additional log backup, using RESTORE WITH NORECOVERY.</span></span>  
  
2.  <span data-ttu-id="7e48f-196">开始镜像会话。</span><span class="sxs-lookup"><span data-stu-id="7e48f-196">Start the mirroring session.</span></span> <span data-ttu-id="7e48f-197">有关详细信息，请参阅 [使用 Windows 身份验证建立数据库镜像会话 (SQL Server Management Studio)](establish-database-mirroring-session-windows-authentication.md) 在 [使用 Windows 身份验证建立数据库镜像会话 (Transact-SQL)](database-mirroring-establish-session-windows-authentication.md)中准备镜像数据库。</span><span class="sxs-lookup"><span data-stu-id="7e48f-197">For more information, see [Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;](establish-database-mirroring-session-windows-authentication.md) or [Establish a Database Mirroring Session Using Windows Authentication &#40;Transact-SQL&#41;](database-mirroring-establish-session-windows-authentication.md).</span></span>  
  
3.  <span data-ttu-id="7e48f-198">如果您在主体数据库上禁用了备份作业，则重新启用该作业。</span><span class="sxs-lookup"><span data-stu-id="7e48f-198">If you disabled the backup job on the principal database, reenable the job.</span></span>  
  
4.  <span data-ttu-id="7e48f-199">如果数据库在故障转移后需要得到信任，则必须在镜像开始后执行额外的设置步骤。</span><span class="sxs-lookup"><span data-stu-id="7e48f-199">If the database needs to be trustworthy after a failover, extra setup steps are necessary after mirroring begins.</span></span> <span data-ttu-id="7e48f-200">有关详细信息，请参阅 [将镜像数据库设置为使用 Trustworthy 属性 (Transact-SQL)](set-up-a-mirror-database-to-use-the-trustworthy-property-transact-sql.md)中准备镜像数据库。</span><span class="sxs-lookup"><span data-stu-id="7e48f-200">For more information, see [Set Up a Mirror Database to Use the Trustworthy Property &#40;Transact-SQL&#41;](set-up-a-mirror-database-to-use-the-trustworthy-property-transact-sql.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="7e48f-201">相关任务</span><span class="sxs-lookup"><span data-stu-id="7e48f-201">Related Tasks</span></span>  
  
-   [<span data-ttu-id="7e48f-202">创建完整数据库备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="7e48f-202">Create a Full Database Backup &#40;SQL Server&#41;</span></span>](../../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="7e48f-203">还原事务日志备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="7e48f-203">Restore a Transaction Log Backup &#40;SQL Server&#41;</span></span>](../../relational-databases/backup-restore/restore-a-transaction-log-backup-sql-server.md)  
  
-   [<span data-ttu-id="7e48f-204">使用 Windows 身份验证建立数据库镜像会话 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="7e48f-204">Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;</span></span>](establish-database-mirroring-session-windows-authentication.md)  
  
-   [<span data-ttu-id="7e48f-205">使用 Windows 身份验证建立数据库镜像会话 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="7e48f-205">Establish a Database Mirroring Session Using Windows Authentication &#40;Transact-SQL&#41;</span></span>](database-mirroring-establish-session-windows-authentication.md)  
  
-   [<span data-ttu-id="7e48f-206">设置加密的镜像数据库</span><span class="sxs-lookup"><span data-stu-id="7e48f-206">Set Up an Encrypted Mirror Database</span></span>](set-up-an-encrypted-mirror-database.md)  
  
-   [<span data-ttu-id="7e48f-207">将镜像数据库设置为使用 Trustworthy 属性 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="7e48f-207">Set Up a Mirror Database to Use the Trustworthy Property &#40;Transact-SQL&#41;</span></span>](set-up-a-mirror-database-to-use-the-trustworthy-property-transact-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="7e48f-208">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7e48f-208">See Also</span></span>  
 <span data-ttu-id="7e48f-209">[数据库镜像 (SQL Server)](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="7e48f-209">[Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="7e48f-210">[用于数据库镜像和 AlwaysOn 可用性组 &#40;SQL Server 的传输安全&#41;](transport-security-database-mirroring-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="7e48f-210">[Transport Security for Database Mirroring and AlwaysOn Availability Groups &#40;SQL Server&#41;](transport-security-database-mirroring-always-on-availability.md) </span></span>  
 <span data-ttu-id="7e48f-211">[设置数据库镜像 (SQL Server)](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="7e48f-211">[Setting Up Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="7e48f-212">[备份和还原全文目录和索引](../../relational-databases/indexes/indexes.md) </span><span class="sxs-lookup"><span data-stu-id="7e48f-212">[Back Up and Restore Full-Text Catalogs and Indexes](../../relational-databases/indexes/indexes.md) </span></span>  
 <span data-ttu-id="7e48f-213">[数据库镜像和全文目录 (SQL Server)](database-mirroring-and-full-text-catalogs-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="7e48f-213">[Database Mirroring and Full-Text Catalogs &#40;SQL Server&#41;](database-mirroring-and-full-text-catalogs-sql-server.md) </span></span>  
 <span data-ttu-id="7e48f-214">[数据库镜像和复制 (SQL Server)](database-mirroring-and-replication-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="7e48f-214">[Database Mirroring and Replication &#40;SQL Server&#41;](database-mirroring-and-replication-sql-server.md) </span></span>  
 <span data-ttu-id="7e48f-215">[BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="7e48f-215">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="7e48f-216">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="7e48f-216">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 [<span data-ttu-id="7e48f-217">RESTORE 参数 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="7e48f-217">RESTORE Arguments &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-arguments-transact-sql)  
  
  
