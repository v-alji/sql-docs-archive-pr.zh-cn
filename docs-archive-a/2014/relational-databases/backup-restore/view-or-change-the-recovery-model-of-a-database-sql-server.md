---
title: 查看或更改数据库的恢复模式 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- database backups [SQL Server], recovery models
- recovery [SQL Server], recovery model
- backing up databases [SQL Server], recovery models
- recovery models [SQL Server], switching
- recovery models [SQL Server], viewing
- database restores [SQL Server], recovery models
- modifying database recovery models
ms.assetid: 94918d1d-7c10-4be7-bf9f-27e00b003a0f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 889080301109938f0514bd6b81265c100237ab60
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690664"
---
# <a name="view-or-change-the-recovery-model-of-a-database-sql-server"></a><span data-ttu-id="0b09d-102">查看或更改数据库的恢复模式 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0b09d-102">View or Change the Recovery Model of a Database (SQL Server)</span></span>
  <span data-ttu-id="0b09d-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中查看或更改数据库的恢复模式。</span><span class="sxs-lookup"><span data-stu-id="0b09d-103">This topic describes how to view or change the recovery model of a database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="0b09d-104">“恢复模式”  是一种数据库属性，它控制如何记录事务，事务日志是否需要（以及允许）进行备份，以及可以使用哪些类型的还原操作。</span><span class="sxs-lookup"><span data-stu-id="0b09d-104">A *recovery model* is a database property that controls how transactions are logged, whether the transaction log requires (and allows) backing up, and what kinds of restore operations are available.</span></span> <span data-ttu-id="0b09d-105">有三种恢复模式：简单恢复模式、完整恢复模式和大容量日志恢复模式。</span><span class="sxs-lookup"><span data-stu-id="0b09d-105">Three recovery models exist: simple, full, and bulk-logged.</span></span> <span data-ttu-id="0b09d-106">通常，数据库使用完整恢复模式或简单恢复模式。</span><span class="sxs-lookup"><span data-stu-id="0b09d-106">Typically, a database uses the full recovery model or simple recovery model.</span></span> <span data-ttu-id="0b09d-107">数据库可以随时切换为其他恢复模式。</span><span class="sxs-lookup"><span data-stu-id="0b09d-107">A database can be switched to another recovery model at any time.</span></span> <span data-ttu-id="0b09d-108">**model** 数据库将设置新数据库的默认恢复模式。</span><span class="sxs-lookup"><span data-stu-id="0b09d-108">The **model** database sets the default recovery model of new databases.</span></span>  
  
 <span data-ttu-id="0b09d-109">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="0b09d-109">**In This Topic**</span></span>  
  
-   <span data-ttu-id="0b09d-110">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="0b09d-110">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="0b09d-111">建议</span><span class="sxs-lookup"><span data-stu-id="0b09d-111">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="0b09d-112">安全性</span><span class="sxs-lookup"><span data-stu-id="0b09d-112">Security</span></span>](#Security)  
  
-   <span data-ttu-id="0b09d-113">**若要查看或更改数据库的恢复模式，可使用：**</span><span class="sxs-lookup"><span data-stu-id="0b09d-113">**To view or change the recovery model of a database, using:**</span></span>  
  
     [<span data-ttu-id="0b09d-114">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="0b09d-114">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="0b09d-115">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="0b09d-115">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="0b09d-116">**后续操作建议：**  [在更改恢复模式之后](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="0b09d-116">**Follow Up Recommendations:**  [After You Change the Recovery Model](#FollowUp)</span></span>  
  
-   [<span data-ttu-id="0b09d-117">相关任务</span><span class="sxs-lookup"><span data-stu-id="0b09d-117">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="0b09d-118">开始之前</span><span class="sxs-lookup"><span data-stu-id="0b09d-118">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="0b09d-119">建议</span><span class="sxs-lookup"><span data-stu-id="0b09d-119">Recommendations</span></span>  
  
-   <span data-ttu-id="0b09d-120">在从完整恢复模式或大容量日志恢复模式切换前，请备份事务日志。</span><span class="sxs-lookup"><span data-stu-id="0b09d-120">Before switching from the full recovery or bulk-logged recovery model, back up the transaction log.</span></span>  
  
-   <span data-ttu-id="0b09d-121">时点恢复在大容量日志模式下不可能进行。</span><span class="sxs-lookup"><span data-stu-id="0b09d-121">Point-in-time recovery is not possible with bulk-logged model.</span></span> <span data-ttu-id="0b09d-122">因此，如果在可能需要事务日志还原的大容量日志恢复模式下运行事务，这些事务可能会丢失数据。</span><span class="sxs-lookup"><span data-stu-id="0b09d-122">Therefore, if you run transactions under the bulk-logged recovery model that might require a transaction log restore, these transactions could be exposed to data loss.</span></span> <span data-ttu-id="0b09d-123">若要在灾难恢复方案中最大程度地恢复数据，建议仅在符合以下条件下切换到大容量日志恢复模式：</span><span class="sxs-lookup"><span data-stu-id="0b09d-123">To maximize data recoverability in a disaster-recovery scenario, we recommend that you switch to the bulk-logged recovery model only under the following conditions:</span></span>  
  
    -   <span data-ttu-id="0b09d-124">数据库中当前不允许存在用户。</span><span class="sxs-lookup"><span data-stu-id="0b09d-124">Users are currently not allowed in the database.</span></span>  
  
    -   <span data-ttu-id="0b09d-125">在大容量处理过程中进行的所有修改均不依靠日志备份就可恢复；例如，通过重新运行大容量处理。</span><span class="sxs-lookup"><span data-stu-id="0b09d-125">All modifications made during bulk processing are recoverable without depending on taking a log backup; for example, by re-running the bulk processes.</span></span>  
  
     <span data-ttu-id="0b09d-126">如果满足这两个条件，在大容量日志恢复模式下还原备份的事务日志时将不会丢失任何数据。</span><span class="sxs-lookup"><span data-stu-id="0b09d-126">If you satisfy these two conditions, you will not be exposed to any data loss while restoring a transaction log that was backed up under the bulk-logged recovery model..</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0b09d-127">如果在大容量操作过程中切换到完整恢复模式，则大容量操作的日志记录将从最小日志记录更改为最大日志记录，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="0b09d-127">If you switch to the full recovery model during a bulk operation, the logging of the bulk operation changes from minimal logging to full logging, and vice versa.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="0b09d-128">Security</span><span class="sxs-lookup"><span data-stu-id="0b09d-128">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="0b09d-129">权限</span><span class="sxs-lookup"><span data-stu-id="0b09d-129">Permissions</span></span>  
 <span data-ttu-id="0b09d-130">需要对数据库拥有 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="0b09d-130">Requires ALTER permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="0b09d-131">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="0b09d-131">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-or-change-the-recovery-model"></a><span data-ttu-id="0b09d-132">查看或更改恢复模式</span><span class="sxs-lookup"><span data-stu-id="0b09d-132">To view or change the recovery model</span></span>  
  
1.  <span data-ttu-id="0b09d-133">连接到相应的 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]实例之后，在对象资源管理器中，单击服务器名称以展开服务器树。</span><span class="sxs-lookup"><span data-stu-id="0b09d-133">After connecting to the appropriate instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="0b09d-134">展开 **“数据库”** ，然后根据数据库的不同，选择用户数据库，或展开 **“系统数据库”** ，再选择系统数据库。</span><span class="sxs-lookup"><span data-stu-id="0b09d-134">Expand **Databases**, and, depending on the database, either select a user database or expand **System Databases** and select a system database.</span></span>  
  
3.  <span data-ttu-id="0b09d-135">右键单击该数据库，再单击“属性”  ，这将打开“数据库属性”  对话框。</span><span class="sxs-lookup"><span data-stu-id="0b09d-135">Right-click the database, and then click **Properties**, which opens the **Database Properties** dialog box.</span></span>  
  
4.  <span data-ttu-id="0b09d-136">在 **“选择页”** 窗格中，单击 **“选项”** 。</span><span class="sxs-lookup"><span data-stu-id="0b09d-136">In the **Select a page** pane, click **Options**.</span></span>  
  
5.  <span data-ttu-id="0b09d-137">当前恢复模式显示在 **“恢复模式”** 列表框中。</span><span class="sxs-lookup"><span data-stu-id="0b09d-137">The current recovery model is displayed in the **Recovery model** list box.</span></span>  
  
6.  <span data-ttu-id="0b09d-138">也可以从列表中选择不同的模式来更改恢复模式。</span><span class="sxs-lookup"><span data-stu-id="0b09d-138">Optionally, to change the recovery model select a different model list.</span></span> <span data-ttu-id="0b09d-139">可以选择“完整”  、“大容量日志”  或“简单”  。</span><span class="sxs-lookup"><span data-stu-id="0b09d-139">The choices are **Full**, **Bulk-logged**, or **Simple**.</span></span>  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="0b09d-140">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="0b09d-140">Using Transact-SQL</span></span>  
  
#### <a name="to-view-the-recovery-model"></a><span data-ttu-id="0b09d-141">查看恢复模式</span><span class="sxs-lookup"><span data-stu-id="0b09d-141">To view the recovery model</span></span>  
  
1.  <span data-ttu-id="0b09d-142">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0b09d-142">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="0b09d-143">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="0b09d-143">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="0b09d-144">将以下示例复制并粘贴到查询窗口中，然后单击“执行”  。</span><span class="sxs-lookup"><span data-stu-id="0b09d-144">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="0b09d-145">此示例说明如何对 [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) 目录视图执行查询以了解 **模型** 数据库的恢复模式。</span><span class="sxs-lookup"><span data-stu-id="0b09d-145">This example shows how to query the [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) catalog view to learn the recovery model of the **model** database.</span></span>  
  
```sql  
SELECT name, recovery_model_desc  
   FROM sys.databases  
      WHERE name = 'model' ;  
GO  
  
```  
  
#### <a name="to-change-the-recovery-model"></a><span data-ttu-id="0b09d-146">更改恢复模式</span><span class="sxs-lookup"><span data-stu-id="0b09d-146">To change the recovery model</span></span>  
  
1.  <span data-ttu-id="0b09d-147">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0b09d-147">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="0b09d-148">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="0b09d-148">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="0b09d-149">将以下示例复制并粘贴到查询窗口中，然后单击“执行”  。</span><span class="sxs-lookup"><span data-stu-id="0b09d-149">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="0b09d-150">此示例说明如何使用 `model` ALTER DATABASE `FULL` 语句的 `SET RECOVERY` 选项将 [数据库中的恢复模式更改为](/sql/t-sql/statements/alter-database-transact-sql-set-options) 。</span><span class="sxs-lookup"><span data-stu-id="0b09d-150">This example shows how to change the recovery model in the `model` database to `FULL` by using the `SET RECOVERY` option of the [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-options) statement.</span></span>  
  
```sql  
USE master ;  
ALTER DATABASE model SET RECOVERY FULL ;  
```  
  
##  <a name="follow-up-recommendations-after-you-change-the-recovery-model"></a><a name="FollowUp"></a><span data-ttu-id="0b09d-151">跟进建议：在更改恢复模式之后</span><span class="sxs-lookup"><span data-stu-id="0b09d-151">Follow Up Recommendations: After You Change the Recovery Model</span></span>  
  
-   <span data-ttu-id="0b09d-152">**在完整恢复模式和大容量日志恢复模式之间切换后**</span><span class="sxs-lookup"><span data-stu-id="0b09d-152">**After switching between the full and bulk-logged recovery models**</span></span>  
  
    -   <span data-ttu-id="0b09d-153">完成大容量操作之后，立即切换回完整恢复模式。</span><span class="sxs-lookup"><span data-stu-id="0b09d-153">After completing the bulk operations, immediately switch back to full recovery mode.</span></span>  
  
    -   <span data-ttu-id="0b09d-154">在从大容量日志恢复模式切换回完整恢复模式后，备份日志。</span><span class="sxs-lookup"><span data-stu-id="0b09d-154">After switching from the bulk-logged recovery model back to the full recovery model, back up the log.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="0b09d-155">您的备份策略保持不变：继续执行定期数据库备份、日志备份和差异备份。</span><span class="sxs-lookup"><span data-stu-id="0b09d-155">Your backup strategy remains the same: continue performing periodic database, log, and differential backups.</span></span>  
  
-   <span data-ttu-id="0b09d-156">**从简单恢复模式切换之后**</span><span class="sxs-lookup"><span data-stu-id="0b09d-156">**After switching from the simple recovery model**</span></span>  
  
    -   <span data-ttu-id="0b09d-157">切换到完整恢复模式或大容量日志恢复模式之后，立即进行完整数据库备份或差异数据库备份以启动日志链。</span><span class="sxs-lookup"><span data-stu-id="0b09d-157">Immediately after switching to the full recovery model or bulk-logged recovery model, take a full or differential database backup to start the log chain.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="0b09d-158">到完整恢复模式或大容量日志恢复模式的切换仅在第一个数据备份之后才生效。</span><span class="sxs-lookup"><span data-stu-id="0b09d-158">The switch to the full or bulk-logged recovery model takes effect only after the first data backup.</span></span>  
  
    -   <span data-ttu-id="0b09d-159">计划安排定期日志备份并相应地更新还原计划。</span><span class="sxs-lookup"><span data-stu-id="0b09d-159">Schedule regular log backups, and update your restore plan accordingly.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="0b09d-160">如果不经常备份日志，则事务日志可能会展开直到占满磁盘空间。</span><span class="sxs-lookup"><span data-stu-id="0b09d-160">If you do not back up the log frequently enough, the transaction log can expand until it runs out of disk space.</span></span>  
  
-   <span data-ttu-id="0b09d-161">**切换到简单恢复模式之后**</span><span class="sxs-lookup"><span data-stu-id="0b09d-161">**After switching to the simple recovery model**</span></span>  
  
    -   <span data-ttu-id="0b09d-162">中断用于备份事务日志的所有计划作业。</span><span class="sxs-lookup"><span data-stu-id="0b09d-162">Discontinue any scheduled jobs for backing up the transaction log.</span></span>  
  
    -   <span data-ttu-id="0b09d-163">确保定期执行数据库备份。</span><span class="sxs-lookup"><span data-stu-id="0b09d-163">Ensure periodic database backups are scheduled.</span></span> <span data-ttu-id="0b09d-164">备份数据库对于保护数据和截断事务日志的不活动部分是基本操作。</span><span class="sxs-lookup"><span data-stu-id="0b09d-164">Backing up your database is essential both to protect your data and to truncate the inactive portion of the transaction log.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="0b09d-165">相关任务</span><span class="sxs-lookup"><span data-stu-id="0b09d-165">Related Tasks</span></span>  
  
-   [<span data-ttu-id="0b09d-166">创建完整数据库备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0b09d-166">Create a Full Database Backup &#40;SQL Server&#41;</span></span>](create-a-full-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="0b09d-167">备份事务日志 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0b09d-167">Back Up a Transaction Log &#40;SQL Server&#41;</span></span>](back-up-a-transaction-log-sql-server.md)  
  
-   [<span data-ttu-id="0b09d-168">创建作业</span><span class="sxs-lookup"><span data-stu-id="0b09d-168">Create a Job</span></span>](../../ssms/agent/create-a-job.md)  
  
-   [<span data-ttu-id="0b09d-169">Disable or Enable a Job</span><span class="sxs-lookup"><span data-stu-id="0b09d-169">Disable or Enable a Job</span></span>](../../ssms/agent/disable-or-enable-a-job.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="0b09d-170">相关内容</span><span class="sxs-lookup"><span data-stu-id="0b09d-170">Related Content</span></span>  
  
-   <span data-ttu-id="0b09d-171">[数据库维护计划](../maintenance-plans/maintenance-plans.md) （ [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 联机丛书中）</span><span class="sxs-lookup"><span data-stu-id="0b09d-171">[Database Maintenance Plans](../maintenance-plans/maintenance-plans.md) (in [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] Books Online)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b09d-172">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0b09d-172">See Also</span></span>  
 <span data-ttu-id="0b09d-173">[恢复模式 (SQL Server)](recovery-models-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="0b09d-173">[Recovery Models &#40;SQL Server&#41;](recovery-models-sql-server.md) </span></span>  
 <span data-ttu-id="0b09d-174">[事务日志 (SQL Server)](../logs/the-transaction-log-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="0b09d-174">[The Transaction Log &#40;SQL Server&#41;](../logs/the-transaction-log-sql-server.md) </span></span>  
 <span data-ttu-id="0b09d-175">[ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0b09d-175">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 <span data-ttu-id="0b09d-176">[sys.databases (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0b09d-176">[sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) </span></span>  
 [<span data-ttu-id="0b09d-177">恢复模式 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0b09d-177">Recovery Models &#40;SQL Server&#41;</span></span>](recovery-models-sql-server.md)  
  
  
