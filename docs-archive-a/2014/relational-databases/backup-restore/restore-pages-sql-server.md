---
title: 还原页 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.restorepage.general.f1
helpviewer_keywords:
- restoring pages [SQL Server]
- pages [SQL Server], restoring
- databases [SQL Server], damaged
- page restores [SQL Server]
- pages [SQL Server], damaged
- restoring [SQL Server], pages
ms.assetid: 07e40950-384e-4d84-9ac5-84da6dd27a91
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6fb008314b9cb156f1cc575bda71b6364eca6e3a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688951"
---
# <a name="restore-pages-sql-server"></a><span data-ttu-id="42131-102">还原页 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="42131-102">Restore Pages (SQL Server)</span></span>
  <span data-ttu-id="42131-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 本主题说明如何使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 [!INCLUDE[tsql](../../includes/tsql-md.md)]在  中还原页。</span><span class="sxs-lookup"><span data-stu-id="42131-103">This topic describes how to restore pages in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="42131-104">页面还原的目的是还原一个或多个损坏的页，而不还原整个数据库。</span><span class="sxs-lookup"><span data-stu-id="42131-104">The goal of a page restore is to restore one or more damaged pages without restoring the whole database.</span></span> <span data-ttu-id="42131-105">通常，要进行还原的页已经由于在访问该页时遇到错误而标记为“可疑”。</span><span class="sxs-lookup"><span data-stu-id="42131-105">Typically, pages that are candidates for restore have been marked as "suspect" because of an error that is encountered when accessing the page.</span></span> <span data-ttu-id="42131-106">可疑页在 [msdb](/sql/relational-databases/system-tables/suspect-pages-transact-sql) 数据库的 **suspect_pages** 表中进行了标识。</span><span class="sxs-lookup"><span data-stu-id="42131-106">Suspect pages are identified in the [suspect_pages](/sql/relational-databases/system-tables/suspect-pages-transact-sql) table in the **msdb** database.</span></span>  
  
 <span data-ttu-id="42131-107">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="42131-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="42131-108">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="42131-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="42131-109">何时适合页面还原？</span><span class="sxs-lookup"><span data-stu-id="42131-109">When is a Page Restore Useful?</span></span>](#WhenUseful)  
  
     [<span data-ttu-id="42131-110">限制和局限</span><span class="sxs-lookup"><span data-stu-id="42131-110">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="42131-111">建议</span><span class="sxs-lookup"><span data-stu-id="42131-111">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="42131-112">安全性</span><span class="sxs-lookup"><span data-stu-id="42131-112">Security</span></span>](#Security)  
  
-   <span data-ttu-id="42131-113">**若要还原页，请使用：**</span><span class="sxs-lookup"><span data-stu-id="42131-113">**To restore pages, using:**</span></span>  
  
     [<span data-ttu-id="42131-114">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="42131-114">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="42131-115">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="42131-115">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="42131-116">开始之前</span><span class="sxs-lookup"><span data-stu-id="42131-116">Before You Begin</span></span>  
  
###  <a name="when-is-a-page-restore-useful"></a><a name="WhenUseful"></a> <span data-ttu-id="42131-117">何时适合页面还原？</span><span class="sxs-lookup"><span data-stu-id="42131-117">When is a Page Restore Useful?</span></span>  
 <span data-ttu-id="42131-118">页面还原用于修复隔离出来的损坏页。</span><span class="sxs-lookup"><span data-stu-id="42131-118">A page restore is intended for repairing isolated damaged pages.</span></span> <span data-ttu-id="42131-119">还原和恢复少量页面的速度可能比还原一个文件更快，因此减少了还原操作中处于脱机状态的数据量。</span><span class="sxs-lookup"><span data-stu-id="42131-119">Restoring and recovering a few individual pages might be faster than a file restore, reducing the amount of data that is offline during a restore operation.</span></span> <span data-ttu-id="42131-120">然而，如果文件中要还原的不只是少量页面，则通常还原整个文件更为有效。</span><span class="sxs-lookup"><span data-stu-id="42131-120">However, if you have to restore more than a few pages in a file, it is generally more efficient to restore the whole file.</span></span> <span data-ttu-id="42131-121">例如，如果某个设备上的大量页都指出此设备有未解决的故障；不妨考虑还原该文件（可以还原到另一位置）并修复该设备。</span><span class="sxs-lookup"><span data-stu-id="42131-121">For example, if lots of pages on a device indicate a pending device failure, consider restoring the file, possibly to another location, and repairing the device.</span></span>  
  
 <span data-ttu-id="42131-122">此外，并非所有的页面错误都需要还原。</span><span class="sxs-lookup"><span data-stu-id="42131-122">Furthermore, not all page errors require a restore.</span></span> <span data-ttu-id="42131-123">缓存数据（例如辅助索引）中可能出现的问题可以通过重新计算这些数据来解决。</span><span class="sxs-lookup"><span data-stu-id="42131-123">A problem can occur in cached data, such as a secondary index, that can be resolved by recalculating the data.</span></span> <span data-ttu-id="42131-124">例如，如果数据库管理员删除一个辅助索引，然后再重新生成一个辅助索引，则损坏的数据虽然已修复，但并没有在 [suspect_pages](/sql/relational-databases/system-tables/suspect-pages-transact-sql) 表中反映出这一情况。</span><span class="sxs-lookup"><span data-stu-id="42131-124">For example, if the database administrator drops a secondary index and rebuilds it, the corrupted data, although fixed, is not indicated as such in the [suspect_pages](/sql/relational-databases/system-tables/suspect-pages-transact-sql) table.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="42131-125">限制和局限</span><span class="sxs-lookup"><span data-stu-id="42131-125">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="42131-126">页面还原适用于使用完整或大容量日志恢复模式的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库。</span><span class="sxs-lookup"><span data-stu-id="42131-126">Page restore applies to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases that are using the full or bulk-logged recovery models.</span></span> <span data-ttu-id="42131-127">只有读/写文件组支持页面还原。</span><span class="sxs-lookup"><span data-stu-id="42131-127">Page restore is supported only for read/write filegroups.</span></span>  
  
-   <span data-ttu-id="42131-128">仅可以还原数据库页。</span><span class="sxs-lookup"><span data-stu-id="42131-128">Only database pages can be restored.</span></span> <span data-ttu-id="42131-129">页面还原不能用于还原下列内容：</span><span class="sxs-lookup"><span data-stu-id="42131-129">Page restore cannot be used to restore the following:</span></span>  
  
    -   <span data-ttu-id="42131-130">事务日志</span><span class="sxs-lookup"><span data-stu-id="42131-130">Transaction log</span></span>  
  
    -   <span data-ttu-id="42131-131">分配页：全局分配映射 (GAM) 页、共享全局分配映射 (SGAM) 页和页可用空间 (PFS) 页。</span><span class="sxs-lookup"><span data-stu-id="42131-131">Allocation pages: Global Allocation Map (GAM) pages, Shared Global Allocation Map (SGAM) pages, and Page Free Space (PFS) pages.</span></span>  
  
    -   <span data-ttu-id="42131-132">所有数据文件的页 0（文件引导页）</span><span class="sxs-lookup"><span data-stu-id="42131-132">Page 0 of all data files (the file boot page)</span></span>  
  
    -   <span data-ttu-id="42131-133">页 1:9（数据库引导页）</span><span class="sxs-lookup"><span data-stu-id="42131-133">Page 1:9 (the database boot page)</span></span>  
  
    -   <span data-ttu-id="42131-134">全文目录</span><span class="sxs-lookup"><span data-stu-id="42131-134">Full-text catalog</span></span>  
  
-   <span data-ttu-id="42131-135">对于使用大容量日志恢复模式的数据库，页面还原还有下列附加条件：</span><span class="sxs-lookup"><span data-stu-id="42131-135">For a database that uses the bulk-logged recovery model, page restore has the following additional conditions:</span></span>  
  
    -   <span data-ttu-id="42131-136">对大容量日志数据而言，在文件组或页数据处于脱机状态时进行备份是有问题的，因为日志中不记录脱机数据。</span><span class="sxs-lookup"><span data-stu-id="42131-136">Backing up while filegroup or page data is offline is problematic for bulk-logged data, because the offline data is not recorded in the log.</span></span> <span data-ttu-id="42131-137">任何脱机页都可能导致无法备份日志。</span><span class="sxs-lookup"><span data-stu-id="42131-137">Any offline page can prevent backing up the log.</span></span> <span data-ttu-id="42131-138">在这种情况下，则应考虑使用 DBCC REPAIR，因为此方式导致的数据丢失少于还原到最近备份引起的数据丢失。</span><span class="sxs-lookup"><span data-stu-id="42131-138">In this cases, consider using DBCC REPAIR, because this might cause less data loss than restoring to the most recent backup.</span></span>  
  
    -   <span data-ttu-id="42131-139">如果大容量日志数据库的日志备份遇到错误页，除非指定了 WITH CONTINUE_AFTER_ERROR，否则将失败。</span><span class="sxs-lookup"><span data-stu-id="42131-139">If a log backup of a bulk-logged database encounters a bad page, it fails unless WITH CONTINUE_AFTER_ERROR is specified.</span></span>  
  
    -   <span data-ttu-id="42131-140">通常，页面还原不能与大容量日志恢复模式配合使用。</span><span class="sxs-lookup"><span data-stu-id="42131-140">Page restore generally does not work with bulk-logged recovery.</span></span>  
  
         <span data-ttu-id="42131-141">执行页面还原的最佳做法是将数据库设置为完整恢复模式，并尝试进行一次日志备份。</span><span class="sxs-lookup"><span data-stu-id="42131-141">A best practice for performing page restore is to set the database to the full recovery model, and try a log backup.</span></span> <span data-ttu-id="42131-142">如果可以进行日志备份，则可以继续进行页面还原。</span><span class="sxs-lookup"><span data-stu-id="42131-142">If the log backup works, you can continue with the page restore.</span></span> <span data-ttu-id="42131-143">如果日志备份失败，则您将不得不丢失上一个日志备份之后的工作，或必须尝试运行 DBCC（必须使用 REPAIR_ALLOW_DATA_LOSS 选项）。</span><span class="sxs-lookup"><span data-stu-id="42131-143">If the log backup fails, you either have to lose work since the previous log backup or you have to try running DBCC must be run with the REPAIR_ALLOW_DATA_LOSS option.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="42131-144">建议</span><span class="sxs-lookup"><span data-stu-id="42131-144">Recommendations</span></span>  
  
-   <span data-ttu-id="42131-145">页面还原方案：</span><span class="sxs-lookup"><span data-stu-id="42131-145">Page restore scenarios:</span></span>  
  
     <span data-ttu-id="42131-146">脱机页面还原</span><span class="sxs-lookup"><span data-stu-id="42131-146">Offline page restore</span></span>  
     <span data-ttu-id="42131-147">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的所有版本都支持在数据库脱机时还原页面。</span><span class="sxs-lookup"><span data-stu-id="42131-147">All editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] support restoring pages when the database is offline.</span></span> <span data-ttu-id="42131-148">在脱机还原页过程中，还原损坏的页时数据库处于脱机状态。</span><span class="sxs-lookup"><span data-stu-id="42131-148">In an offline page restore, the database is offline while damaged pages are restored.</span></span> <span data-ttu-id="42131-149">还原顺序结束时，数据库将联机。</span><span class="sxs-lookup"><span data-stu-id="42131-149">At the end of the restore sequence, the database comes online.</span></span>  
  
     <span data-ttu-id="42131-150">联机页面还原</span><span class="sxs-lookup"><span data-stu-id="42131-150">Online page restore</span></span>  
     [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="42131-151">Enterprise Edition 支持联机页面还原，但它们在数据库当前处于脱机状态时将使用脱机还原。</span><span class="sxs-lookup"><span data-stu-id="42131-151">Enterprise edition supports online page restores, though they use offline restore if the database is currently offline.</span></span> <span data-ttu-id="42131-152">在大多数情况下，可以在数据库（包括页面要还原到的文件组）保持联机状态时还原损坏的页。</span><span class="sxs-lookup"><span data-stu-id="42131-152">In most cases, a damaged page can be restored while the database remains online, including the filegroup to which a page is being restored.</span></span> <span data-ttu-id="42131-153">在主文件组处于联机状态时，即使有一个或多个辅助文件组处于脱机状态，页面还原也通常联机执行。</span><span class="sxs-lookup"><span data-stu-id="42131-153">When the primary filegroup is online, even if one or more of its secondary filegroups are offline, page restores are usually performed online.</span></span> <span data-ttu-id="42131-154">但有时候，损坏的页可能需要脱机还原。</span><span class="sxs-lookup"><span data-stu-id="42131-154">Occasionally, however, a damaged page can require an offline restore.</span></span> <span data-ttu-id="42131-155">例如，某些重要的页发生损坏可能会使数据库无法启动。</span><span class="sxs-lookup"><span data-stu-id="42131-155">For example, damage to certain critical pages might prevent the database from starting.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="42131-156">如果损坏的页存储了重要的数据库元数据，则在联机页面还原尝试过程中对元数据的必需的更新可能失败。</span><span class="sxs-lookup"><span data-stu-id="42131-156">If damaged pages are storing critical database metadata, required updates to metadata might fail during an online page restore attempt.</span></span> <span data-ttu-id="42131-157">在此情况下，你可以执行脱机页面还原，但首先，你必须创建一个 [结尾日志备份](tail-log-backups-sql-server.md) （通过使用 RESTORE WITH NORECOVERY 备份事务日志）。</span><span class="sxs-lookup"><span data-stu-id="42131-157">In this case, you can perform an offline page restore, but first you must create a [tail log backup](tail-log-backups-sql-server.md) (by backing up the transaction log using RESTORE WITH NORECOVERY).</span></span>  
  
-   <span data-ttu-id="42131-158">页面还原利用了改进的页级错误报告（包含页校验和）和跟踪。</span><span class="sxs-lookup"><span data-stu-id="42131-158">Page restore takes advantage of the improved page-level error reporting (including page checksums) and tracking.</span></span> <span data-ttu-id="42131-159">通过校验和或残缺写操作检测为已损坏的页（“损坏页”） 可以通过页还原操作进行还原。</span><span class="sxs-lookup"><span data-stu-id="42131-159">Pages that are detected as corrupted by check-summing or a torn write, *damaged pages*, can be restored by a page restore operation.</span></span> <span data-ttu-id="42131-160">仅还原显式指定的页。</span><span class="sxs-lookup"><span data-stu-id="42131-160">Only explicitly specified pages are restored.</span></span> <span data-ttu-id="42131-161">每个指定页都被来自指定数据备份的页的副本替换。</span><span class="sxs-lookup"><span data-stu-id="42131-161">Each specified page is replaced by the copy of that page from the specified data backup.</span></span>  
  
     <span data-ttu-id="42131-162">在您还原随后的日志备份时，它们将仅适用于包含要还原的至少一页的数据库文件。</span><span class="sxs-lookup"><span data-stu-id="42131-162">When you restore the subsequent log backups, they are applied only to database files that contain at least one page that is being recovered.</span></span> <span data-ttu-id="42131-163">必须将不中断的日志备份链应用于最后一次完整或差异还原，以便让包含该页的文件组前进到当前的日志文件。</span><span class="sxs-lookup"><span data-stu-id="42131-163">An unbroken chain of log backups must be applied to the last full or differential restore to bring the filegroup that contains the page forward to the current log file.</span></span> <span data-ttu-id="42131-164">与文件还原中一样，每次传递日志重做，前滚集都会前进一步。</span><span class="sxs-lookup"><span data-stu-id="42131-164">As in a file restore, the roll forward set is advanced with a single log redo pass.</span></span> <span data-ttu-id="42131-165">为了成功还原页，已还原的页必须恢复到与数据库一致的状态。</span><span class="sxs-lookup"><span data-stu-id="42131-165">For a page restore to succeed, the restored pages must be recovered to a state consistent with the database.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="42131-166">Security</span><span class="sxs-lookup"><span data-stu-id="42131-166">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="42131-167">权限</span><span class="sxs-lookup"><span data-stu-id="42131-167">Permissions</span></span>  
 <span data-ttu-id="42131-168">如果不存在要还原的数据库，则用户必须有 CREATE DATABASE 权限才能执行 RESTORE。</span><span class="sxs-lookup"><span data-stu-id="42131-168">If the database being restored does not exist, the user must have CREATE DATABASE permissions to be able to execute RESTORE.</span></span> <span data-ttu-id="42131-169">如果数据库存在，则 RESTORE 权限默认授予 **sysadmin** 和 **dbcreator** 固定服务器角色成员以及数据库的所有者 (**dbo**)（对于 FROM DATABASE_SNAPSHOT 选项，数据库始终存在）。</span><span class="sxs-lookup"><span data-stu-id="42131-169">If the database exists, RESTORE permissions default to members of the **sysadmin** and **dbcreator** fixed server roles and the owner (**dbo**) of the database (for the FROM DATABASE_SNAPSHOT option, the database always exists).</span></span>  
  
 <span data-ttu-id="42131-170">RESTORE 权限被授予那些成员身份信息始终可由服务器使用的角色。</span><span class="sxs-lookup"><span data-stu-id="42131-170">RESTORE permissions are given to roles in which membership information is always readily available to the server.</span></span> <span data-ttu-id="42131-171">因为只有在固定数据库可以访问且没有损坏时（在执行 RESTORE 时并不会总是这样）才能检查固定数据库角色成员身份，所以 **db_owner** 固定数据库角色成员没有 RESTORE 权限。</span><span class="sxs-lookup"><span data-stu-id="42131-171">Because fixed database role membership can be checked only when the database is accessible and undamaged, which is not always the case when RESTORE is executed, members of the **db_owner** fixed database role do not have RESTORE permissions.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="42131-172">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="42131-172">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="42131-173">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]从 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 开始， 支持页面还原。</span><span class="sxs-lookup"><span data-stu-id="42131-173">Starting in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] supports page restores.</span></span>  
  
#### <a name="to-restore-pages"></a><span data-ttu-id="42131-174">还原页</span><span class="sxs-lookup"><span data-stu-id="42131-174">To restore pages</span></span>  
  
1.  <span data-ttu-id="42131-175">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]连接到相应的 实例，在对象资源管理器中，单击服务器名称以展开服务器树。</span><span class="sxs-lookup"><span data-stu-id="42131-175">Connect to the appropriate instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="42131-176">展开 **“数据库”** 。</span><span class="sxs-lookup"><span data-stu-id="42131-176">Expand **Databases**.</span></span> <span data-ttu-id="42131-177">根据具体的数据库，选择一个用户数据库，或展开“系统数据库”并选择一个系统数据库。</span><span class="sxs-lookup"><span data-stu-id="42131-177">Depending on the database, either select a user database or expand **System Databases**, and then select a system database.</span></span>  
  
3.  <span data-ttu-id="42131-178">右键单击该数据库，指向 **“任务”** ，再指向 **“还原”** ，然后单击 **“页”** ，这将打开“还原页”对话框。</span><span class="sxs-lookup"><span data-stu-id="42131-178">Right-click the database, point to **Tasks**, point to **Restore**, and then click **Page**, which opens the **Restore Page** dialog box.</span></span>  
  
     <span data-ttu-id="42131-179">**还原**</span><span class="sxs-lookup"><span data-stu-id="42131-179">**Restore**</span></span>  
     <span data-ttu-id="42131-180">此部分执行的功能与 [还原数据库（常规页）](../../integration-services/general-page-of-integration-services-designers-options.md) 上的 **“还原到”** 的功能相同。</span><span class="sxs-lookup"><span data-stu-id="42131-180">This section performs the same function as that of **Restore to** on the [Restore Database (General Page)](../../integration-services/general-page-of-integration-services-designers-options.md).</span></span>  
  
     <span data-ttu-id="42131-181">**Database**</span><span class="sxs-lookup"><span data-stu-id="42131-181">**Database**</span></span>  
     <span data-ttu-id="42131-182">指定要还原的数据库。</span><span class="sxs-lookup"><span data-stu-id="42131-182">Specifies the database to restore.</span></span> <span data-ttu-id="42131-183">您可以输入新的数据库，也可以从下拉列表中选择现有的数据库。</span><span class="sxs-lookup"><span data-stu-id="42131-183">You can enter a new database or select an existing database from the drop-down list.</span></span> <span data-ttu-id="42131-184"> 该列表包含了服务器上除系统数据库 **master** 和 tempdb 之外的所有数据库。</span><span class="sxs-lookup"><span data-stu-id="42131-184">The list includes all databases on the server, except the system databases **master** and **tempdb**.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="42131-185">若要还原带有密码保护的备份，必须使用 [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) 语句。</span><span class="sxs-lookup"><span data-stu-id="42131-185">To restore a password-protected backup, you must use the [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) statement.</span></span>  
  
     <span data-ttu-id="42131-186">**结尾日志备份**</span><span class="sxs-lookup"><span data-stu-id="42131-186">**Tail-Log backup**</span></span>  
     <span data-ttu-id="42131-187">在“备份设备”  中输入或选择一个文件名，将在其中存储数据库的结尾日志备份。</span><span class="sxs-lookup"><span data-stu-id="42131-187">Enter or select a file name in **Backup device** where there tail-log backup will be stored for the database.</span></span>  
  
     <span data-ttu-id="42131-188">**备份集**</span><span class="sxs-lookup"><span data-stu-id="42131-188">**Backup Sets**</span></span>  
     <span data-ttu-id="42131-189">此部分显示参与还原的备份集。</span><span class="sxs-lookup"><span data-stu-id="42131-189">This section displays the backup sets involved in the restoration.</span></span>  
  
    |<span data-ttu-id="42131-190">标头</span><span class="sxs-lookup"><span data-stu-id="42131-190">Header</span></span>|<span data-ttu-id="42131-191">值</span><span class="sxs-lookup"><span data-stu-id="42131-191">Values</span></span>|  
    |------------|------------|  
    |<span data-ttu-id="42131-192">**名称**</span><span class="sxs-lookup"><span data-stu-id="42131-192">**Name**</span></span>|<span data-ttu-id="42131-193">备份集的名称。</span><span class="sxs-lookup"><span data-stu-id="42131-193">The name of the backup set.</span></span>|  
    |<span data-ttu-id="42131-194">组件</span><span class="sxs-lookup"><span data-stu-id="42131-194">**Component**</span></span>|<span data-ttu-id="42131-195">备份组件：  数据库、文件或 \<blank>（对于事务日志）。</span><span class="sxs-lookup"><span data-stu-id="42131-195">The backed-up component: **Database**, **File**, or **\<blank>** (for transaction logs).</span></span>|  
    |<span data-ttu-id="42131-196">类型</span><span class="sxs-lookup"><span data-stu-id="42131-196">**Type**</span></span>|<span data-ttu-id="42131-197">执行的备份类型：“完整”、“差异”或“事务日志”  。</span><span class="sxs-lookup"><span data-stu-id="42131-197">The type of backup performed: **Full**, **Differential**, or **Transaction Log**.</span></span>|  
    |<span data-ttu-id="42131-198">**Server**</span><span class="sxs-lookup"><span data-stu-id="42131-198">**Server**</span></span>|<span data-ttu-id="42131-199">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 执行备份操作的实例的名称。</span><span class="sxs-lookup"><span data-stu-id="42131-199">The name of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] instance that performed the backup operation.</span></span>|  
    |<span data-ttu-id="42131-200">**Database**</span><span class="sxs-lookup"><span data-stu-id="42131-200">**Database**</span></span>|<span data-ttu-id="42131-201">备份操作中涉及的数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="42131-201">The name of the database involved in the backup operation.</span></span>|  
    |<span data-ttu-id="42131-202">**位置**</span><span class="sxs-lookup"><span data-stu-id="42131-202">**Position**</span></span>|<span data-ttu-id="42131-203">备份集在卷中的位置。</span><span class="sxs-lookup"><span data-stu-id="42131-203">The position of the backup set in the volume.</span></span>|  
    |<span data-ttu-id="42131-204">**第一个 LSN**</span><span class="sxs-lookup"><span data-stu-id="42131-204">**First LSN**</span></span>|<span data-ttu-id="42131-205">备份集中第一个事务的日志序列号 (LSN)。</span><span class="sxs-lookup"><span data-stu-id="42131-205">The log sequence number (LSN) of the first transaction in the backup set.</span></span> <span data-ttu-id="42131-206">对于文件备份为空。</span><span class="sxs-lookup"><span data-stu-id="42131-206">Blank for file backups.</span></span>|  
    |<span data-ttu-id="42131-207">**最后一个 LSN**</span><span class="sxs-lookup"><span data-stu-id="42131-207">**Last LSN**</span></span>|<span data-ttu-id="42131-208">备份集中最后一个事务的日志序列号 (LSN)。</span><span class="sxs-lookup"><span data-stu-id="42131-208">The log sequence number (LSN) of the last transaction in the backup set.</span></span> <span data-ttu-id="42131-209">对于文件备份为空。</span><span class="sxs-lookup"><span data-stu-id="42131-209">Blank for file backups.</span></span>|  
    |<span data-ttu-id="42131-210">**检查点 LSN**</span><span class="sxs-lookup"><span data-stu-id="42131-210">**Checkpoint LSN**</span></span>|<span data-ttu-id="42131-211">创建备份时最新检查点的日志序列号 (LSN)。</span><span class="sxs-lookup"><span data-stu-id="42131-211">The log sequence number (LSN) of the most recent checkpoint at the time the backup was created.</span></span>|  
    |<span data-ttu-id="42131-212">**完整 LSN**</span><span class="sxs-lookup"><span data-stu-id="42131-212">**Full LSN**</span></span>|<span data-ttu-id="42131-213">最近的完整数据库备份的日志序列号 (LSN)。</span><span class="sxs-lookup"><span data-stu-id="42131-213">The log sequence number (LSN) of the most recent full database backup.</span></span>|  
    |<span data-ttu-id="42131-214">**开始日期**</span><span class="sxs-lookup"><span data-stu-id="42131-214">**Start Date**</span></span>|<span data-ttu-id="42131-215">备份操作开始的日期和时间，按客户端的区域设置显示。</span><span class="sxs-lookup"><span data-stu-id="42131-215">The date and time when the backup operation began, presented in the regional setting of the client.</span></span>|  
    |<span data-ttu-id="42131-216">**完成日期**</span><span class="sxs-lookup"><span data-stu-id="42131-216">**Finish Date**</span></span>|<span data-ttu-id="42131-217">备份操作完成的日期和时间，按客户端的区域设置显示。</span><span class="sxs-lookup"><span data-stu-id="42131-217">The date and time when the backup operation finished, presented in the regional setting of the client.</span></span>|  
    |<span data-ttu-id="42131-218">**大小**</span><span class="sxs-lookup"><span data-stu-id="42131-218">**Size**</span></span>|<span data-ttu-id="42131-219">备份集的大小（字节）。</span><span class="sxs-lookup"><span data-stu-id="42131-219">The size of the backup set in bytes.</span></span>|  
    |<span data-ttu-id="42131-220">**用户名**</span><span class="sxs-lookup"><span data-stu-id="42131-220">**User Name**</span></span>|<span data-ttu-id="42131-221">执行备份操作的用户的名称。</span><span class="sxs-lookup"><span data-stu-id="42131-221">The name of the user who performed the backup operation.</span></span>|  
    |<span data-ttu-id="42131-222">**过期日期**</span><span class="sxs-lookup"><span data-stu-id="42131-222">**Expiration**</span></span>|<span data-ttu-id="42131-223">备份集的过期日期和时间。</span><span class="sxs-lookup"><span data-stu-id="42131-223">The date and time the backup set expires.</span></span>|  
  
     <span data-ttu-id="42131-224"> 单击“验证”以检查执行页还原操作所需的备份文件的完整性。</span><span class="sxs-lookup"><span data-stu-id="42131-224">Click **Verify** to check the integrity of the backup files needed to perform the page restore operation.</span></span>  
  
4.  <span data-ttu-id="42131-225"> 若要标识已损坏的页，则在 **“数据库”** 框中选择了正确的数据库的情况下，单击“检查数据库页”。</span><span class="sxs-lookup"><span data-stu-id="42131-225">To identify corrupted pages, with the correct database selected in the **Database** box, click **Check Database Pages**.</span></span> <span data-ttu-id="42131-226">此操作将运行较长时间。</span><span class="sxs-lookup"><span data-stu-id="42131-226">This is a long running operation.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="42131-227">若要还原未损坏的特定页，请单击“添加”  ，然后输入要还原的页的“文件 ID”  和“页 ID”  。</span><span class="sxs-lookup"><span data-stu-id="42131-227">To restore specific pages that are not corrupted, click **Add** and enter the **File ID** and **Page ID** of the pages to be restored.</span></span>  
  
5.  <span data-ttu-id="42131-228">页网格用于标识要还原的页。</span><span class="sxs-lookup"><span data-stu-id="42131-228">The pages grid is used to identify the pages to be restored.</span></span> <span data-ttu-id="42131-229">最初，此网格将从 [suspect_pages](/sql/relational-databases/system-tables/suspect-pages-transact-sql) 系统表填充。</span><span class="sxs-lookup"><span data-stu-id="42131-229">Initially, this grid is populated from the [suspect_pages](/sql/relational-databases/system-tables/suspect-pages-transact-sql) system table.</span></span> <span data-ttu-id="42131-230"> 若要从该网格添加或删除页，请单击 **“添加”** 或“删除”。</span><span class="sxs-lookup"><span data-stu-id="42131-230">To add or remove pages from the grid, click **Add** or **Remove**.</span></span> <span data-ttu-id="42131-231">有关详细信息，请参阅 [管理 suspect_pages 表 (SQL Server)](manage-the-suspect-pages-table-sql-server.md)在  中还原页。</span><span class="sxs-lookup"><span data-stu-id="42131-231">For more information, see [Manage the suspect_pages Table &#40;SQL Server&#41;](manage-the-suspect-pages-table-sql-server.md).</span></span>  
  
6.  <span data-ttu-id="42131-232">**“备份集”** 网格将列出默认还原计划中的备份集。</span><span class="sxs-lookup"><span data-stu-id="42131-232">The **Backup sets** grid lists the backup sets in the default restore plan.</span></span> <span data-ttu-id="42131-233"> 或者，单击“验证”可验证备份是否可读取以及备份集是否完整而无需还原。</span><span class="sxs-lookup"><span data-stu-id="42131-233">Optionally, click **Verify** to verify that the backups are readable and that the backup sets are complete, without restoring them.</span></span> <span data-ttu-id="42131-234">有关详细信息，请参阅 [RESTORE VERIFYONLY (Transact-SQL)](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="42131-234">For more information, see [RESTORE VERIFYONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql).</span></span>  
  
     <span data-ttu-id="42131-235">**页**</span><span class="sxs-lookup"><span data-stu-id="42131-235">**Pages**</span></span>  
  
7.  <span data-ttu-id="42131-236">若要还原在页网格中列出的页，请单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="42131-236">To restore the pages listed in the pages grid, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="42131-237">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="42131-237">Using Transact-SQL</span></span>  
 <span data-ttu-id="42131-238">若要在 RESTORE DATABASE 语句中指定一页，需要知道该页所在文件的文件 ID 和该页的页 ID。</span><span class="sxs-lookup"><span data-stu-id="42131-238">To specify a page in a RESTORE DATABASE statement, you need the file ID of the file containing the page and the page ID of the page.</span></span> <span data-ttu-id="42131-239">所需语法如下：</span><span class="sxs-lookup"><span data-stu-id="42131-239">The required syntax is as follows:</span></span>  
  
 `RESTORE DATABASE <database_name>`  
  
 `PAGE = '<file: page> [ ,... n ] ' [ ,... n ]`  
  
 `FROM <backup_device> [ ,... n ]`  
  
 `WITH NORECOVERY`  
  
 <span data-ttu-id="42131-240">有关 PAGE 选项的参数的详细信息，请参阅 [RESTORE Arguments (Transact-SQL)](/sql/t-sql/statements/restore-statements-arguments-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="42131-240">For more information about the parameters of the PAGE option, see [RESTORE Arguments &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql).</span></span> <span data-ttu-id="42131-241">有关 RESTORE DATABASE 语法的详细信息，请参阅 [RESTORE (Transact-SQL)](/sql/t-sql/statements/restore-statements-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="42131-241">For more information about the RESTORE DATABASE syntax, see [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql).</span></span>  
  
#### <a name="to-restore-pages"></a><span data-ttu-id="42131-242">还原页</span><span class="sxs-lookup"><span data-stu-id="42131-242">To restore pages</span></span>  
  
1.  <span data-ttu-id="42131-243">获取要还原的损坏页的页 ID。</span><span class="sxs-lookup"><span data-stu-id="42131-243">Obtain the page IDs of the damaged pages to be restored.</span></span> <span data-ttu-id="42131-244">校验和或残缺写错误将返回页 ID，并提供指定页所需的信息。</span><span class="sxs-lookup"><span data-stu-id="42131-244">A checksum or torn write error returns page ID, providing the information required for specifying the pages.</span></span> <span data-ttu-id="42131-245">若要查找损坏页的页 ID，请使用下列任一来源。</span><span class="sxs-lookup"><span data-stu-id="42131-245">To look up page ID of a damaged page, use any of the following sources.</span></span>  
  
    |<span data-ttu-id="42131-246">页 ID 源</span><span class="sxs-lookup"><span data-stu-id="42131-246">Source of page ID</span></span>|<span data-ttu-id="42131-247">主题</span><span class="sxs-lookup"><span data-stu-id="42131-247">Topic</span></span>|  
    |-----------------------|-----------|  
    |<span data-ttu-id="42131-248">**msdb..suspect_pages**</span><span class="sxs-lookup"><span data-stu-id="42131-248">**msdb..suspect_pages**</span></span>|[<span data-ttu-id="42131-249">管理 suspect_pages 表 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="42131-249">Manage the suspect_pages Table &#40;SQL Server&#41;</span></span>](manage-the-suspect-pages-table-sql-server.md)|  
    |<span data-ttu-id="42131-250">错误日志</span><span class="sxs-lookup"><span data-stu-id="42131-250">Error log</span></span>|[<span data-ttu-id="42131-251">查看 SQL Server 错误日志 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="42131-251">View the SQL Server Error Log &#40;SQL Server Management Studio&#41;</span></span>](../../ssms/sql-server-management-studio-ssms.md)|  
    |<span data-ttu-id="42131-252">事件跟踪</span><span class="sxs-lookup"><span data-stu-id="42131-252">Event traces</span></span>|[<span data-ttu-id="42131-253">监视事件和响应事件</span><span class="sxs-lookup"><span data-stu-id="42131-253">Monitor and Respond to Events</span></span>](../../ssms/agent/monitor-and-respond-to-events.md)|  
    |<span data-ttu-id="42131-254">DBCC</span><span class="sxs-lookup"><span data-stu-id="42131-254">DBCC</span></span>|[<span data-ttu-id="42131-255">DBCC (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="42131-255">DBCC &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-transact-sql)|  
    |<span data-ttu-id="42131-256">WMI 提供程序</span><span class="sxs-lookup"><span data-stu-id="42131-256">WMI provider</span></span>|[<span data-ttu-id="42131-257">WMI Provider for Server Events 的概念</span><span class="sxs-lookup"><span data-stu-id="42131-257">WMI Provider for Server Events Concepts</span></span>](../wmi-provider-server-events/wmi-provider-for-server-events-concepts.md)|  
  
2.  <span data-ttu-id="42131-258">从包含页的完整数据库备份、文件备份或文件组备份开始进行页面还原。</span><span class="sxs-lookup"><span data-stu-id="42131-258">Start a page restore with a full database, file, or filegroup backup that contains the page.</span></span> <span data-ttu-id="42131-259">在 RESTORE DATABASE 语句中，使用 PAGE 子句列出所有要还原的页的页 ID。</span><span class="sxs-lookup"><span data-stu-id="42131-259">In the RESTORE DATABASE statement, use the PAGE clause to list the page IDs of all of the pages to be restored.</span></span>  
  
3.  <span data-ttu-id="42131-260">应用最近的差异。</span><span class="sxs-lookup"><span data-stu-id="42131-260">Apply the most recent differentials .</span></span>  
  
4.  <span data-ttu-id="42131-261">应用后续日志备份。</span><span class="sxs-lookup"><span data-stu-id="42131-261">Apply the subsequent log backups.</span></span>  
  
5.  <span data-ttu-id="42131-262">创建新的数据库日志备份，使其包含已还原页的最终 LSN，即最后还原的页脱机的时间点。</span><span class="sxs-lookup"><span data-stu-id="42131-262">Create a new log backup of the database that includes the final LSN of the restored pages, that is, the point at which the last restored page is taken offline.</span></span> <span data-ttu-id="42131-263">设置为顺序中首先还原的最终 LSN 是重做目标 LSN。</span><span class="sxs-lookup"><span data-stu-id="42131-263">The final LSN, which is set as part of the first restore in the sequence, is the redo target LSN.</span></span> <span data-ttu-id="42131-264">包含该页的文件的联机前滚可以在重做目标 LSN 处停止。</span><span class="sxs-lookup"><span data-stu-id="42131-264">Online roll forward of the file containing the page is able to stop at the redo target LSN.</span></span> <span data-ttu-id="42131-265">若要了解文件的当前重做目标 LSN，请查看 **sys.master_files** 的 **redo_target_lsn** 列。</span><span class="sxs-lookup"><span data-stu-id="42131-265">To learn the current redo target LSN of a file, see the **redo_target_lsn** column of **sys.master_files**.</span></span> <span data-ttu-id="42131-266">有关详细信息，请参阅 [sys.master_files (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="42131-266">For more information, see [sys.master_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql).</span></span>  
  
6.  <span data-ttu-id="42131-267">还原新的日志备份。</span><span class="sxs-lookup"><span data-stu-id="42131-267">Restore the new log backup.</span></span> <span data-ttu-id="42131-268">应用这个新的日志备份后，就完成了页面还原，可以开始使用页了。</span><span class="sxs-lookup"><span data-stu-id="42131-268">After this new log backup is applied, the page restore is completed and the pages are now usable.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="42131-269">此顺序与文件还原顺序类似。</span><span class="sxs-lookup"><span data-stu-id="42131-269">This sequence is analogous to a file restore sequence.</span></span> <span data-ttu-id="42131-270">事实上，页面还原和文件还原都可以在相同的顺序中执行。</span><span class="sxs-lookup"><span data-stu-id="42131-270">In fact, page restore and file restores can both be performed as part of the same sequence.</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="42131-271">示例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="42131-271">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="42131-272">以下示例使用 `B` 还原文件 `NORECOVERY`的四个损坏页。</span><span class="sxs-lookup"><span data-stu-id="42131-272">The following example restores four damaged pages of file `B` with `NORECOVERY`.</span></span> <span data-ttu-id="42131-273">随后，将使用 `NORECOVERY`应用两个日志备份，然后是结尾日志备份（使用 `RECOVERY`还原）。</span><span class="sxs-lookup"><span data-stu-id="42131-273">Next, two log backups are applied with `NORECOVERY`, followed with the tail-log backup, which is restored with `RECOVERY`.</span></span> <span data-ttu-id="42131-274">此示例执行联机还原。</span><span class="sxs-lookup"><span data-stu-id="42131-274">This example performs an online restore.</span></span> <span data-ttu-id="42131-275">此示例中，文件 `B` 的文件 ID 为 `1`，损坏的页的页 ID 分别为 `57`、 `202`、 `916`和 `1016`。</span><span class="sxs-lookup"><span data-stu-id="42131-275">In the example, the file ID of file `B` is `1`, and the page IDs of the damaged pages are `57`, `202`, `916`, and `1016`.</span></span>  
  
```sql  
RESTORE DATABASE <database> PAGE='1:57, 1:202, 1:916, 1:1016'  
   FROM <file_backup_of_file_B>   
   WITH NORECOVERY;  
RESTORE LOG <database> FROM <log_backup>   
   WITH NORECOVERY;  
RESTORE LOG <database> FROM <log_backup>   
   WITH NORECOVERY;   
BACKUP LOG <database> TO <new_log_backup>;   
RESTORE LOG <database> FROM <new_log_backup> WITH RECOVERY;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="42131-276">另请参阅</span><span class="sxs-lookup"><span data-stu-id="42131-276">See Also</span></span>  
 <span data-ttu-id="42131-277">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="42131-277">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 <span data-ttu-id="42131-278">[应用事务日志备份 (SQL Server)](transaction-log-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="42131-278">[Apply Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span></span>  
 <span data-ttu-id="42131-279">[管理 suspect_pages 表 (SQL Server)](manage-the-suspect-pages-table-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="42131-279">[Manage the suspect_pages Table &#40;SQL Server&#41;](manage-the-suspect-pages-table-sql-server.md) </span></span>  
 [<span data-ttu-id="42131-280">SQL Server 数据库的备份和还原</span><span class="sxs-lookup"><span data-stu-id="42131-280">Back Up and Restore of SQL Server Databases</span></span>](back-up-and-restore-of-sql-server-databases.md)  
  
  
