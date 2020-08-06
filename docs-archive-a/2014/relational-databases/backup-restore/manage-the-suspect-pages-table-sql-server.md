---
title: 管理 suspect_pages 表 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- 824 (Database Engine error)
- restoring pages [SQL Server]
- pages [SQL Server], suspect
- pages [SQL Server], restoring
- suspect_pages system table
- suspect pages [SQL Server]
- restoring [SQL Server], pages
ms.assetid: f394d4bc-1518-4e61-97fc-bf184d972e2b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: dd7aea63ae85a16e23ff532c7e18ace3c376a707
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591408"
---
# <a name="manage-the-suspect_pages-table-sql-server"></a><span data-ttu-id="8281c-102">管理 suspect_pages 表 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="8281c-102">Manage the suspect_pages Table (SQL Server)</span></span>
  <span data-ttu-id="8281c-103">本主题介绍如何使用 **或** 来在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中管理 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] suspect_pages [!INCLUDE[tsql](../../includes/tsql-md.md)]表。</span><span class="sxs-lookup"><span data-stu-id="8281c-103">This topic describes how to manage the **suspect_pages** table in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="8281c-104">**suspect_pages** 表可用来维护有关可疑页的信息，并且还有助于确定有无必要进行还原。</span><span class="sxs-lookup"><span data-stu-id="8281c-104">The **suspect_pages** table is used for maintaining information about suspect pages, and is relevant in helping to decide whether a restore is necessary.</span></span> <span data-ttu-id="8281c-105">[suspect_pages](/sql/relational-databases/system-tables/suspect-pages-transact-sql) 表位于 [msdb 数据库](../databases/msdb-database.md)中。</span><span class="sxs-lookup"><span data-stu-id="8281c-105">The [suspect_pages](/sql/relational-databases/system-tables/suspect-pages-transact-sql) table resides in the [msdb database](../databases/msdb-database.md).</span></span>  
  
 <span data-ttu-id="8281c-106">如果 [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)] 在试图读取某个数据页时遇到下列错误之一，该页面将被视为“可疑”：</span><span class="sxs-lookup"><span data-stu-id="8281c-106">A page is considered "suspect" when the [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)] encounters one of the following errors when it tries to read a data page:</span></span>  
  
-   <span data-ttu-id="8281c-107">由操作系统发出 (CRC) 导致循环冗余检查导致的[823 错误](../errors-events/mssqlserver-823-database-engine-error.md)，如磁盘错误 (特定硬件错误) </span><span class="sxs-lookup"><span data-stu-id="8281c-107">An [823 error](../errors-events/mssqlserver-823-database-engine-error.md) that was caused by a cyclic redundancy check (CRC) issued by the operating system, such as a disk error (certain hardware errors)</span></span>  
  
-   <span data-ttu-id="8281c-108">[824 错误](../errors-events/mssqlserver-824-database-engine-error.md)，如页撕裂 (任何逻辑错误) </span><span class="sxs-lookup"><span data-stu-id="8281c-108">An [824 error](../errors-events/mssqlserver-824-database-engine-error.md), such as a torn page (any logical error)</span></span>  
  
 <span data-ttu-id="8281c-109">每个可疑页的页 ID 将记录在 **suspect_pages** 表中。</span><span class="sxs-lookup"><span data-stu-id="8281c-109">The page ID of every suspect page is recorded in the **suspect_pages** table.</span></span> <span data-ttu-id="8281c-110">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 将记录在常规处理过程中发现的所有可疑页，例如在下列情况下：</span><span class="sxs-lookup"><span data-stu-id="8281c-110">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] records any suspect pages encountered during regular processing, such as the following:</span></span>  
  
-   <span data-ttu-id="8281c-111">查询必须读取页。</span><span class="sxs-lookup"><span data-stu-id="8281c-111">A query has to read a page.</span></span>  
  
-   <span data-ttu-id="8281c-112">在运行 DBCC CHECKDB 的过程中。</span><span class="sxs-lookup"><span data-stu-id="8281c-112">During a DBCC CHECKDB operation.</span></span>  
  
-   <span data-ttu-id="8281c-113">在备份操作的过程中。</span><span class="sxs-lookup"><span data-stu-id="8281c-113">During a backup operation.</span></span>  
  
 <span data-ttu-id="8281c-114">当执行还原操作、DBCC 修复操作或删除数据库操作时， **suspect_pages** 表也会根据需要进行更新。</span><span class="sxs-lookup"><span data-stu-id="8281c-114">The **suspect_pages** table is also updated as necessary during a restore operation, a DBCC repair operation, or a drop database operation.</span></span>  
  
 <span data-ttu-id="8281c-115">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="8281c-115">**In This Topic**</span></span>  
  
-   <span data-ttu-id="8281c-116">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="8281c-116">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="8281c-117">建议</span><span class="sxs-lookup"><span data-stu-id="8281c-117">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="8281c-118">安全性</span><span class="sxs-lookup"><span data-stu-id="8281c-118">Security</span></span>](#Security)  
  
-   <span data-ttu-id="8281c-119">**若要管理 suspect_pages 表，可使用：**</span><span class="sxs-lookup"><span data-stu-id="8281c-119">**To manage the suspect_pages table, using:**</span></span>  
  
     [<span data-ttu-id="8281c-120">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="8281c-120">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="8281c-121">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="8281c-121">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="8281c-122">开始之前</span><span class="sxs-lookup"><span data-stu-id="8281c-122">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="8281c-123">建议</span><span class="sxs-lookup"><span data-stu-id="8281c-123">Recommendations</span></span>  
  
-   <span data-ttu-id="8281c-124">**suspect_pages 表中记录的错误**</span><span class="sxs-lookup"><span data-stu-id="8281c-124">**Errors Recorded in suspect_pages Table**</span></span>  
  
     <span data-ttu-id="8281c-125">在 **suspect_pages** 表中，由于出现 824 错误而失败的每页占一行，最多为 1,000 行。</span><span class="sxs-lookup"><span data-stu-id="8281c-125">The **suspect_pages** table contains one row per page that failed with an 824 error, up to a limit of 1,000 rows.</span></span> <span data-ttu-id="8281c-126">下表显示了记录在 **suspect_pages** 表的 **event_type** 列中的错误。</span><span class="sxs-lookup"><span data-stu-id="8281c-126">The following table shows errors logged in the **event_type** column of the **suspect_pages** table.</span></span>  
  
    |<span data-ttu-id="8281c-127">错误说明</span><span class="sxs-lookup"><span data-stu-id="8281c-127">Error description</span></span>|<span data-ttu-id="8281c-128">**event_type** 值</span><span class="sxs-lookup"><span data-stu-id="8281c-128">**event_type** value</span></span>|  
    |-----------------------|---------------------------|  
    |<span data-ttu-id="8281c-129">由操作系统 CRC 错误造成的 823 错误，或者校验和错误或页撕裂以外的 824 错误（例如，页 ID 错误）</span><span class="sxs-lookup"><span data-stu-id="8281c-129">823 error caused by an operating system CRC error  or 824 error other than a bad checksum or a torn page (for example, a bad page ID)</span></span>|<span data-ttu-id="8281c-130">1</span><span class="sxs-lookup"><span data-stu-id="8281c-130">1</span></span>|  
    |<span data-ttu-id="8281c-131">错误的校验和</span><span class="sxs-lookup"><span data-stu-id="8281c-131">Bad checksum</span></span>|<span data-ttu-id="8281c-132">2</span><span class="sxs-lookup"><span data-stu-id="8281c-132">2</span></span>|  
    |<span data-ttu-id="8281c-133">残缺页</span><span class="sxs-lookup"><span data-stu-id="8281c-133">Torn page</span></span>|<span data-ttu-id="8281c-134">3</span><span class="sxs-lookup"><span data-stu-id="8281c-134">3</span></span>|  
    |<span data-ttu-id="8281c-135">已还原（页在标记为错误后已还原）</span><span class="sxs-lookup"><span data-stu-id="8281c-135">Restored (The page was restored after it was marked bad)</span></span>|<span data-ttu-id="8281c-136">4</span><span class="sxs-lookup"><span data-stu-id="8281c-136">4</span></span>|  
    |<span data-ttu-id="8281c-137">已修复（DBCC、AlwaysOn 或镜像修复了页面）</span><span class="sxs-lookup"><span data-stu-id="8281c-137">Repaired (DBCC, AlwaysOn, or mirroring repaired the page)</span></span>|<span data-ttu-id="8281c-138">5</span><span class="sxs-lookup"><span data-stu-id="8281c-138">5</span></span>|  
    |<span data-ttu-id="8281c-139">已由 DBCC 释放</span><span class="sxs-lookup"><span data-stu-id="8281c-139">Deallocated by DBCC</span></span>|<span data-ttu-id="8281c-140">7</span><span class="sxs-lookup"><span data-stu-id="8281c-140">7</span></span>|  
  
     <span data-ttu-id="8281c-141">暂时性的错误也会记录在 **suspect_pages** 表中。</span><span class="sxs-lookup"><span data-stu-id="8281c-141">The **suspect_pages** table also records transient errors.</span></span> <span data-ttu-id="8281c-142">暂时性错误的来源包含 I/O 错误（例如电缆断开连接）或暂时未通过重复校验和测试的页。</span><span class="sxs-lookup"><span data-stu-id="8281c-142">Sources of transient errors include an I/O error (for example, a cable was disconnected) or a page that temporarily fails a repeated checksum test.</span></span>  
  
-   <span data-ttu-id="8281c-143">**数据库引擎如何更新 suspect_pages 表**</span><span class="sxs-lookup"><span data-stu-id="8281c-143">**How the Database Engine Updates the suspect_pages Table**</span></span>  
  
     <span data-ttu-id="8281c-144">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 对 **suspect_pages** 表执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="8281c-144">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] takes the following actions on the **suspect_pages** table:</span></span>  
  
    -   <span data-ttu-id="8281c-145">如果表未满，则每出现一个 824 错误，该表都会更新以指明出现了错误，且错误计数器也将相应递增。</span><span class="sxs-lookup"><span data-stu-id="8281c-145">If the table is not full, it is updated for every 824 error, to indicate that an error has occurred, and the error counter is incremented.</span></span> <span data-ttu-id="8281c-146">如果通过修复、还原或释放操作修复后的页仍有错误，则其 **number_of_errors** 计数将会递增，其 **last_update** 列也会更新</span><span class="sxs-lookup"><span data-stu-id="8281c-146">If a page has an error after it is fixed by being repaired, restored, or deallocated, its **number_of_errors** count is incremented and its **last_update** column is updated</span></span>  
  
    -   <span data-ttu-id="8281c-147">列出的页通过还原或修复操作修复之后，该操作将更新 **suspect_pages** 行，以指示此页已修复 (**event_type** = 5) 或已还原 (**event_type** = 4)。</span><span class="sxs-lookup"><span data-stu-id="8281c-147">After a listed page is fixed by a restore or a repair operation, the operation updates the **suspect_pages** row to indicate that the page is repaired (**event_type** = 5) or restored (**event_type** = 4).</span></span>  
  
    -   <span data-ttu-id="8281c-148">如果运行 DBCC 检查，则该检查会将所有未出错页标记为已修复 (**event_type** = 5) 或已释放 (**event_type** = 7)。</span><span class="sxs-lookup"><span data-stu-id="8281c-148">If a DBCC check is run, the check marks any error-free pages as repaired (**event_type** = 5) or deallocated (**event_type** = 7).</span></span>  
  
-   <span data-ttu-id="8281c-149">**自动更新 suspect_pages 表**</span><span class="sxs-lookup"><span data-stu-id="8281c-149">**Automatic Updates to the suspect_pages Table**</span></span>  
  
     <span data-ttu-id="8281c-150">尝试读取数据文件中的某一页由于以下原因之一失败后，数据库镜像伙伴或 AlwaysOn 可用性副本将更新 **suspect_pages** 表。</span><span class="sxs-lookup"><span data-stu-id="8281c-150">A database mirroring partner or AlwaysOn availability replica updates the **suspect_pages** table after an attempt to read a page from a data file fails for one of the following reasons.</span></span>  
  
    -   <span data-ttu-id="8281c-151">由操作系统 CRC 错误导致的 823 错误。</span><span class="sxs-lookup"><span data-stu-id="8281c-151">An 823 error that is caused by an operating system CRC error.</span></span>  
  
    -   <span data-ttu-id="8281c-152">824 错误（像页撕裂这样的逻辑损坏）。</span><span class="sxs-lookup"><span data-stu-id="8281c-152">An 824 error (logical corruption such as a torn page).</span></span>  
  
     <span data-ttu-id="8281c-153">以下操作还自动更新 **suspect_pages** 表中的行。</span><span class="sxs-lookup"><span data-stu-id="8281c-153">The following actions also automatically update rows in the **suspect_pages** table.</span></span>  
  
    -   <span data-ttu-id="8281c-154">DBCC CHECKDB REPAIR_ALLOW_DATA_LOSS 更新 **suspect_pages** 表，以指示已释放或已修复的各页。</span><span class="sxs-lookup"><span data-stu-id="8281c-154">DBCC CHECKDB REPAIR_ALLOW_DATA_LOSS updates the **suspect_pages** table to indicate each page that it has deallocated or repaired.</span></span>  
  
    -   <span data-ttu-id="8281c-155">完整还原、文件还原或页面还原将页面项标记为已还原。</span><span class="sxs-lookup"><span data-stu-id="8281c-155">A full, file, or page RESTORE marks the page entries as restored.</span></span>  
  
     <span data-ttu-id="8281c-156">以下操作将自动从 **suspect_pages** 表中删除行。</span><span class="sxs-lookup"><span data-stu-id="8281c-156">The following actions automatically delete rows from the **suspect_pages** table.</span></span>  
  
    -   <span data-ttu-id="8281c-157">ALTER DATABASE REMOVE FILE</span><span class="sxs-lookup"><span data-stu-id="8281c-157">ALTER DATABASE REMOVE FILE</span></span>  
  
    -   <span data-ttu-id="8281c-158">DROP DATABASE</span><span class="sxs-lookup"><span data-stu-id="8281c-158">DROP DATABASE</span></span>  
  
-   <span data-ttu-id="8281c-159">**数据库管理员的维护角色**</span><span class="sxs-lookup"><span data-stu-id="8281c-159">**Maintenance Role of the Database Administrator**</span></span>  
  
     <span data-ttu-id="8281c-160">数据库管理员负责管理表（主要通过删除旧的行实现）。</span><span class="sxs-lookup"><span data-stu-id="8281c-160">Database administrators are responsible for managing the table, primarily by deleting old rows.</span></span> <span data-ttu-id="8281c-161">**suspect_pages** 表有大小限制，如果此表已满，则不会记录新的错误。</span><span class="sxs-lookup"><span data-stu-id="8281c-161">The **suspect_pages** table is limited in size, and if it fills, new errors are not logged.</span></span> <span data-ttu-id="8281c-162">若要防止此表填满，数据库管理员或系统管理员必须通过删除行来手动清除此表中的旧条目。</span><span class="sxs-lookup"><span data-stu-id="8281c-162">To prevent this table from filling up, the database administrator or system administrator must manually clear out old entries from this table by deleting rows.</span></span> <span data-ttu-id="8281c-163">因此，我们建议你定期删除或归档具有已还原或已修复的 **event_type** 的行或者具有旧的 **last_update** 值的行。</span><span class="sxs-lookup"><span data-stu-id="8281c-163">Therefore, we recommend that you periodically delete or archive rows that have an **event_type** of restored or repaired, or rows that have an old **last_update** value.</span></span>  
  
     <span data-ttu-id="8281c-164">若要监视对 suspect_pages 表执行的操作，可使用 [Database Suspect Data Page 事件类](../event-classes/database-suspect-data-page-event-class.md)。</span><span class="sxs-lookup"><span data-stu-id="8281c-164">To monitor the activity on the suspect_pages table, you can use the [Database Suspect Data Page Event Class](../event-classes/database-suspect-data-page-event-class.md).</span></span> <span data-ttu-id="8281c-165">有时，行会因暂时性错误而添加到 **suspect_pages** 表。</span><span class="sxs-lookup"><span data-stu-id="8281c-165">Rows are sometimes added to the **suspect_pages** table because of transient errors.</span></span> <span data-ttu-id="8281c-166">如果正在向该表添加很多行，则 I/O 子系统可能出了问题。</span><span class="sxs-lookup"><span data-stu-id="8281c-166">If many rows are being added to the table, however, a problem probably exists with the I/O subsystem.</span></span> <span data-ttu-id="8281c-167">如果您注意到正向该表添加的行数突然增加，我们建议您检查一下 I/O 子系统是不是出现了问题。</span><span class="sxs-lookup"><span data-stu-id="8281c-167">If you notice a sudden increase in the number of rows being added to the table, we recommend that you investigate possible problems in your I/O subsystem.</span></span>  
  
     <span data-ttu-id="8281c-168">数据库管理员还可以插入或更新记录。</span><span class="sxs-lookup"><span data-stu-id="8281c-168">A database administrator can also insert or update records.</span></span> <span data-ttu-id="8281c-169">例如，如果数据库管理员知道某个特定的可疑页实际上没问题但想要暂时保留记录，更新行可能就很有用。</span><span class="sxs-lookup"><span data-stu-id="8281c-169">For example, updating a row might useful when the database administrator knows that a particular suspect page is actually intact, but wants to preserve the record for a while.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="8281c-170">Security</span><span class="sxs-lookup"><span data-stu-id="8281c-170">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="8281c-171">权限</span><span class="sxs-lookup"><span data-stu-id="8281c-171">Permissions</span></span>  
 <span data-ttu-id="8281c-172">任何拥有 **msdb** 访问权限的人员都可以读取 **suspect_pages** 表中的数据。</span><span class="sxs-lookup"><span data-stu-id="8281c-172">Anyone with access to **msdb** can read the data in the **suspect_pages** table.</span></span> <span data-ttu-id="8281c-173">任何拥有 suspect_pages 表的 UPDATE 权限的人员都可以更新它的记录。</span><span class="sxs-lookup"><span data-stu-id="8281c-173">Anyone with UPDATE permission on the suspect_pages table can update its records.</span></span> <span data-ttu-id="8281c-174">**msdb** 上的 **db_owner** 固定数据库角色或 **sysadmin** 固定服务器角色的成员都可以插入、更新和删除记录。</span><span class="sxs-lookup"><span data-stu-id="8281c-174">Members the **db_owner** fixed database role on **msdb** or the **sysadmin** fixed server role can insert, update, and delete records.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="8281c-175">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="8281c-175">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-manage-the-suspect_pages-table"></a><span data-ttu-id="8281c-176">管理 suspect_pages 表</span><span class="sxs-lookup"><span data-stu-id="8281c-176">To manage the suspect_pages table</span></span>  
  
1.  <span data-ttu-id="8281c-177">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)]的实例，再依次展开该实例、 **“数据库”** 。</span><span class="sxs-lookup"><span data-stu-id="8281c-177">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)], expand that instance, and then expand **Databases**.</span></span>  
  
2.  <span data-ttu-id="8281c-178">依次展开“系统数据库”  、“msdb”  、“表”  和“系统表”  。</span><span class="sxs-lookup"><span data-stu-id="8281c-178">Expand **System Databases**, expand **msdb**, expand **Tables**, and then expand **System Tables**.</span></span>  
  
3.  <span data-ttu-id="8281c-179">展开“dbo.suspect_pages”  ，然后右键单击“编辑前 200 行”  。</span><span class="sxs-lookup"><span data-stu-id="8281c-179">Expand **dbo.suspect_pages** and right-click **Edit Top 200 Rows**.</span></span>  
  
4.  <span data-ttu-id="8281c-180">在查询窗口中，编辑、更新或删除所需的行。</span><span class="sxs-lookup"><span data-stu-id="8281c-180">In the query window, edit, update, or delete the rows that you want.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="8281c-181">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="8281c-181">Using Transact-SQL</span></span>  
  
#### <a name="to-manage-the-suspect_pages-table"></a><span data-ttu-id="8281c-182">管理 suspect_pages 表</span><span class="sxs-lookup"><span data-stu-id="8281c-182">To manage the suspect_pages table</span></span>  
  
1.  <span data-ttu-id="8281c-183">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8281c-183">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="8281c-184">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="8281c-184">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="8281c-185">将以下示例复制并粘贴到查询窗口中，然后单击 **“执行”** 。</span><span class="sxs-lookup"><span data-stu-id="8281c-185">Copy and paste the following examples into the query window and click **Execute**.</span></span> <span data-ttu-id="8281c-186">此示例将删除 `suspect_pages` 表中的一些行。</span><span class="sxs-lookup"><span data-stu-id="8281c-186">This example deletes some of the rows from the `suspect_pages` table.</span></span>  
  
```  
-- Delete restored, repaired, or deallocated pages.  
DELETE FROM msdb..suspect_pages  
   WHERE (event_type = 4 OR event_type = 5 OR event_type = 7);  
GO  
  
```  
  
 <span data-ttu-id="8281c-187">此示例将返回 `suspect_pages` 表中的错误网页。</span><span class="sxs-lookup"><span data-stu-id="8281c-187">This example returns the bad pages in the `suspect_pages` table.</span></span>  
  
```  
-- Select nonspecific 824, bad checksum, and torn page errors.  
SELECT * FROM msdb..suspect_pages  
   WHERE (event_type = 1 OR event_type = 2 OR event_type = 3);  
GO  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="8281c-188">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8281c-188">See Also</span></span>  
 <span data-ttu-id="8281c-189">[DROP DATABASE (Transact SQL)](/sql/t-sql/statements/drop-database-audit-specification-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8281c-189">[DROP DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-database-audit-specification-transact-sql) </span></span>  
 <span data-ttu-id="8281c-190">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8281c-190">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 <span data-ttu-id="8281c-191">[BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8281c-191">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="8281c-192">[DBCC (Transact-SQL)](/sql/t-sql/database-console-commands/dbcc-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8281c-192">[DBCC &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-transact-sql) </span></span>  
 <span data-ttu-id="8281c-193">[还原页 (SQL Server)](restore-pages-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="8281c-193">[Restore Pages &#40;SQL Server&#41;](restore-pages-sql-server.md) </span></span>  
 <span data-ttu-id="8281c-194">[suspect_pages &#40;Transact-sql&#41;](/sql/relational-databases/system-tables/suspect-pages-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8281c-194">[suspect_pages &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/suspect-pages-transact-sql) </span></span>  
 <span data-ttu-id="8281c-195">[MSSQLSERVER_823](../errors-events/mssqlserver-823-database-engine-error.md) </span><span class="sxs-lookup"><span data-stu-id="8281c-195">[MSSQLSERVER_823](../errors-events/mssqlserver-823-database-engine-error.md) </span></span>  
 [<span data-ttu-id="8281c-196">MSSQLSERVER_824</span><span class="sxs-lookup"><span data-stu-id="8281c-196">MSSQLSERVER_824</span></span>](../errors-events/mssqlserver-824-database-engine-error.md)  
  
  
