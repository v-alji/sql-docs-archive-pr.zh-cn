---
title: 为可用性组手动准备辅助数据库 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.configsecondarydbs.f1
- sql12.swb.availabilitygroup.preparedbs.f1
helpviewer_keywords:
- secondary databases [SQL Server], in availability group
- secondary databases [SQL Server]
- Availability Groups [SQL Server], configuring
- Availability Groups [SQL Server], databases
ms.assetid: 9f2feb3c-ea9b-4992-8202-2aeed4f9a6dd
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3da3f7332bdabce65785b2844157dd4639389254
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580382"
---
# <a name="manually-prepare-a-secondary-database-for-an-availability-group-sql-server"></a><span data-ttu-id="db173-102">为可用性组手动准备辅助数据库 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="db173-102">Manually Prepare a Secondary Database for an Availability Group (SQL Server)</span></span>
  <span data-ttu-id="db173-103">本主题介绍如何通过使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 、 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]或 PowerShell 在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中为 AlwaysOn 可用性组准备辅助数据库。</span><span class="sxs-lookup"><span data-stu-id="db173-103">This topic describes how to prepare a secondary database for an AlwaysOn availability group in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell.</span></span> <span data-ttu-id="db173-104">准备辅助数据库需要两个步骤：(1) 使用 RESTORE WITH NORECOVERY 将主数据库的最近数据库备份和后续的日志备份还原到承载辅助副本的每个服务器实例；(2) 将还原的数据库联接到可用性组。</span><span class="sxs-lookup"><span data-stu-id="db173-104">Preparing a secondary database requires two steps: (1) restoring a recent database backup of the primary database and subsequent log backups onto each server instance that hosts the secondary replica, using RESTORE WITH NORECOVERY, and (2) joining the restored database to the availability group.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="db173-105">如果您具有现有的日志传送配置，则可能能够将日志传送主数据库与其一个或多个辅助数据库一起转换为 AlwaysOn 主数据库和一个或多个 AlwaysOn 辅助数据库。</span><span class="sxs-lookup"><span data-stu-id="db173-105">If you have an existing log shipping configuration, you might be able to convert the log shipping primary database along with one or more of its secondary databases to an AlwaysOn primary database and one or more AlwaysOn secondary databases.</span></span> <span data-ttu-id="db173-106">有关详细信息，请参阅[从日志传送迁移到 AlwaysOn 可用性组 &#40;SQL Server&#41;的先决条件](prereqs-migrating-log-shipping-to-always-on-availability-groups.md)。</span><span class="sxs-lookup"><span data-stu-id="db173-106">For more information, see [Prerequisites for Migrating from Log Shipping to AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-migrating-log-shipping-to-always-on-availability-groups.md).</span></span>  
  
-   <span data-ttu-id="db173-107">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="db173-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="db173-108">先决条件和限制</span><span class="sxs-lookup"><span data-stu-id="db173-108">Prerequisites and Restrictions</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="db173-109">建议</span><span class="sxs-lookup"><span data-stu-id="db173-109">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="db173-110">安全性</span><span class="sxs-lookup"><span data-stu-id="db173-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="db173-111">**若要准备辅助数据库，请使用：**</span><span class="sxs-lookup"><span data-stu-id="db173-111">**To prepare a secondary database, using:**</span></span>  
  
     [<span data-ttu-id="db173-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="db173-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="db173-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="db173-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="db173-114">PowerShell</span><span class="sxs-lookup"><span data-stu-id="db173-114">PowerShell</span></span>](#PowerShellProcedure)  
  
-   [<span data-ttu-id="db173-115">相关备份和还原任务</span><span class="sxs-lookup"><span data-stu-id="db173-115">Related Backup and Restore Tasks</span></span>](#RelatedTasks)  
  
-   <span data-ttu-id="db173-116">**跟进：** [准备辅助数据库之后](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="db173-116">**Follow Up:** [After Preparing a Secondary Database](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="db173-117">开始之前</span><span class="sxs-lookup"><span data-stu-id="db173-117">Before You Begin</span></span>  
  
###  <a name="prerequisites-and-restrictions"></a><a name="Prerequisites"></a> <span data-ttu-id="db173-118">先决条件和限制</span><span class="sxs-lookup"><span data-stu-id="db173-118">Prerequisites and Restrictions</span></span>  
  
-   <span data-ttu-id="db173-119">确保计划放置数据库的系统的磁盘驱动器空间足以存储辅助数据库。</span><span class="sxs-lookup"><span data-stu-id="db173-119">Make sure that the system where you plan to place database possesses a disk drive with sufficient space for the secondary databases.</span></span>  
  
-   <span data-ttu-id="db173-120">辅助数据库的名称必须与主数据库的名称相同。</span><span class="sxs-lookup"><span data-stu-id="db173-120">The name of the secondary database must be the same as the name of the primary database.</span></span>  
  
-   <span data-ttu-id="db173-121">使用 RESTORE WITH NORECOVERY 执行每个还原操作。</span><span class="sxs-lookup"><span data-stu-id="db173-121">Use RESTORE WITH NORECOVERY for every restore operation.</span></span>  
  
-   <span data-ttu-id="db173-122">如果辅助数据库需要位于与主数据库不同的文件路径中（包括驱动器号），还原命令还必须对每个数据库文件使用 WITH MOVE 选项，将这些文件指定到辅助数据库的路径。</span><span class="sxs-lookup"><span data-stu-id="db173-122">If the secondary database needs to reside on a different file path (including the drive letter) than the primary database, the restore command must also use the WITH MOVE option for each of the database files to specify them to the path of the secondary database.</span></span>  
  
-   <span data-ttu-id="db173-123">如果要逐个文件组地还原数据库，则要确保还原整个数据库。</span><span class="sxs-lookup"><span data-stu-id="db173-123">If you restore the database filegroup by filegroup, be sure to restore the whole database.</span></span>  
  
-   <span data-ttu-id="db173-124">还原数据库后，必须还原 (WITH NORECOVERY) 自上次还原的数据备份之后创建的各个日志备份。</span><span class="sxs-lookup"><span data-stu-id="db173-124">After restoring the database, you must restore (WITH NORECOVERY) every log backup created since the last restored data backup.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="db173-125">建议</span><span class="sxs-lookup"><span data-stu-id="db173-125">Recommendations</span></span>  
  
-   <span data-ttu-id="db173-126">在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]独立实例上，我们建议，如有可能，给定辅助数据库的文件路径（包括驱动器号）应该与相应的主数据库的路径相同。</span><span class="sxs-lookup"><span data-stu-id="db173-126">On stand-alone instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], we recommend that, if possible, the file path (including the drive letter) of a given secondary database be identical to the path of the corresponding primary database.</span></span> <span data-ttu-id="db173-127">这是因为，如果在创建辅助数据库时移动了数据库文件，则随后在辅助数据库上执行的添加文件操作可能会失败，并导致该辅助数据库挂起。</span><span class="sxs-lookup"><span data-stu-id="db173-127">This is because if you move the database files when creating a secondary database, a later add-file operation might fail on the secondary database and cause the secondary database to be suspended.</span></span>  
  
-   <span data-ttu-id="db173-128">准备辅助数据库之前，我们强烈建议您挂起针对可用性组中数据库的计划日志备份，直到完成辅助副本的初始化。</span><span class="sxs-lookup"><span data-stu-id="db173-128">Before preparing your secondary databases, we strongly recommend that you suspend scheduled log backups on the databases in the availability group until the initialization of secondary replicas has completed.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="db173-129">Security</span><span class="sxs-lookup"><span data-stu-id="db173-129">Security</span></span>  
 <span data-ttu-id="db173-130">备份数据库时，"[可信数据库" 属性](../../../relational-databases/security/trustworthy-database-property.md)设置为 "关闭"。</span><span class="sxs-lookup"><span data-stu-id="db173-130">When a database is backed up, the [TRUSTWORTHY database property](../../../relational-databases/security/trustworthy-database-property.md) is set to OFF.</span></span> <span data-ttu-id="db173-131">因此，在新还原的数据库中，TRUSTWORTHY 始终为 OFF。</span><span class="sxs-lookup"><span data-stu-id="db173-131">Therefore, TRUSTWORTHY is always OFF on a newly restored database.</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="db173-132">权限</span><span class="sxs-lookup"><span data-stu-id="db173-132">Permissions</span></span>  
 <span data-ttu-id="db173-133">默认情况下，为 **sysadmin** 固定服务器角色以及 **db_owner** 和 **db_backupoperator** 固定数据库角色的成员授予 BACKUP DATABASE 和 BACKUP LOG 权限。</span><span class="sxs-lookup"><span data-stu-id="db173-133">BACKUP DATABASE and BACKUP LOG permissions default to members of the **sysadmin** fixed server role and the **db_owner** and **db_backupoperator** fixed database roles.</span></span> <span data-ttu-id="db173-134">有关详细信息，请参阅 [BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="db173-134">For more information, see [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql).</span></span>  
  
 <span data-ttu-id="db173-135">如果服务器实例上不存在要还原的数据库，则 RESTORE 语句要求 CREATE DATABASE 权限。</span><span class="sxs-lookup"><span data-stu-id="db173-135">When the database being restored does not exist on the server instance, the RESTORE statement requires CREATE DATABASE permissions.</span></span> <span data-ttu-id="db173-136">有关详细信息，请参阅 [RESTORE (Transact-SQL)](/sql/t-sql/statements/restore-statements-transact-sql)备份。</span><span class="sxs-lookup"><span data-stu-id="db173-136">For more information, see [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="db173-137">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="db173-137">Using SQL Server Management Studio</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="db173-138"> 如果备份和还原文件路径在承载主副本的服务器实例和承载辅助副本的每个实例之间完全相同，则应该能够通过使用 [新建可用性组向导](use-the-availability-group-wizard-sql-server-management-studio.md)、 [将副本添加到可用性组向导](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)或 [将数据库添加到可用性组向导](availability-group-add-database-to-group-wizard.md)创建辅助数据库。</span><span class="sxs-lookup"><span data-stu-id="db173-138">If the backup and restore file paths are identical between the server instance that hosts the primary replica and every instance that hosts a secondary replica, you should be able create secondary databases by using [New Availability Group Wizard](use-the-availability-group-wizard-sql-server-management-studio.md), [Add Replica to Availability Group Wizard](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md), or [Add Database to Availability Group Wizard](availability-group-add-database-to-group-wizard.md).</span></span>  
  
 <span data-ttu-id="db173-139">**准备辅助数据库**</span><span class="sxs-lookup"><span data-stu-id="db173-139">**To prepare a secondary database**</span></span>  
  
1.  <span data-ttu-id="db173-140">除非您已经有了主数据库的最近数据库备份，否则需要创建新的完全或差异数据库备份。</span><span class="sxs-lookup"><span data-stu-id="db173-140">Unless you already have a recent database backup of the primary database, create a new full or differential database backup.</span></span> <span data-ttu-id="db173-141">最好将此备份和任何后续的日志备份放到推荐的网络共享上。</span><span class="sxs-lookup"><span data-stu-id="db173-141">As a best practice, place this backup and any subsequent log backups onto the recommended network share.</span></span>  
  
2.  <span data-ttu-id="db173-142">至少为主数据库创建一个新日志备份。</span><span class="sxs-lookup"><span data-stu-id="db173-142">Create at least one new log backup of the primary database.</span></span>  
  
3.  <span data-ttu-id="db173-143">在承载辅助副本的服务器实例上，依次还原主数据库的完整数据库备份（还可以选择还原差异备份）以及所有后续的日志备份。</span><span class="sxs-lookup"><span data-stu-id="db173-143">On the server instance that hosts the secondary replica, restore the full database backup of the primary database (and optionally a differential backup) followed by any subsequent log backups.</span></span>  
  
     <span data-ttu-id="db173-144">在 "**还原 DATABASEOptions** " 页上，选择 "\*\*使数据库保持不可操作状态，不回滚未提交的事务"。可以还原其他事务日志。 (RESTORE WITH NORECOVERY) \*\*。</span><span class="sxs-lookup"><span data-stu-id="db173-144">On the **RESTORE DATABASEOptions** page, select **Leave the database non-operational, and do not roll back the uncommitted transactions. Additional transaction logs can be restored. (RESTORE WITH NORECOVERY)**.</span></span>  
  
     <span data-ttu-id="db173-145">如果主数据库与辅助数据库的文件路径不同，例如，如果主数据库位于驱动器“F:”，但承载辅助副本的服务器实例缺少 F: 驱动器，请在 WITH 语句中包括 MOVE 选项。</span><span class="sxs-lookup"><span data-stu-id="db173-145">If the file paths of the primary database and the secondary database differ, for example, if the primary database is on drive 'F:' but the server instance that hosts the secondary replica lacks an F: drive, include the MOVE option in your WITH clause.</span></span>  
  
4.  <span data-ttu-id="db173-146">若要完成辅助数据库的配置，您需要将辅助数据库联接到可用性组。</span><span class="sxs-lookup"><span data-stu-id="db173-146">To complete configuration of the secondary database, you need to join the secondary database to the availability group.</span></span> <span data-ttu-id="db173-147">有关详细信息，请参阅[将辅助数据库联接到可用性组 (SQL Server)](join-a-secondary-database-to-an-availability-group-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="db173-147">For more information, [Join a Secondary Database to an Availability Group &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="db173-148"> 有关如何执行这些备份和还原操作的信息，请参阅本节后面的 [相关备份和还原任务](#RelatedTasks)。</span><span class="sxs-lookup"><span data-stu-id="db173-148">For information about how to perform these backup and restore operations, see [Related Backup and Restore Tasks](#RelatedTasks), later in this section.</span></span>  
  
###  <a name="related-backup-and-restore-tasks"></a><a name="RelatedTasks"></a><span data-ttu-id="db173-149">相关备份和还原任务</span><span class="sxs-lookup"><span data-stu-id="db173-149">Related Backup and Restore Tasks</span></span>  
 <span data-ttu-id="db173-150">**创建数据库备份**</span><span class="sxs-lookup"><span data-stu-id="db173-150">**To create a database backup**</span></span>  
  
-   [<span data-ttu-id="db173-151">创建完整数据库备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="db173-151">Create a Full Database Backup &#40;SQL Server&#41;</span></span>](../../../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="db173-152">创建差异数据库备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="db173-152">Create a Differential Database Backup &#40;SQL Server&#41;</span></span>](../../../relational-databases/backup-restore/create-a-differential-database-backup-sql-server.md)  
  
 <span data-ttu-id="db173-153">**创建日志备份**</span><span class="sxs-lookup"><span data-stu-id="db173-153">**To create a log backup**</span></span>  
  
-   [<span data-ttu-id="db173-154">备份事务日志 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="db173-154">Back Up a Transaction Log &#40;SQL Server&#41;</span></span>](../../../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md)  
  
 <span data-ttu-id="db173-155">**还原备份**</span><span class="sxs-lookup"><span data-stu-id="db173-155">**To restore backups**</span></span>  
  
-   [<span data-ttu-id="db173-156">还原数据库备份 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="db173-156">Restore a Database Backup &#40;SQL Server Management Studio&#41;</span></span>](../../../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md)  
  
-   [<span data-ttu-id="db173-157">还原差异数据库备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="db173-157">Restore a Differential Database Backup &#40;SQL Server&#41;</span></span>](../../../relational-databases/backup-restore/restore-a-differential-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="db173-158">还原事务日志备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="db173-158">Restore a Transaction Log Backup &#40;SQL Server&#41;</span></span>](../../../relational-databases/backup-restore/restore-a-transaction-log-backup-sql-server.md)  
  
-   [<span data-ttu-id="db173-159">将数据库还原到新位置 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="db173-159">Restore a Database to a New Location &#40;SQL Server&#41;</span></span>](../../../relational-databases/backup-restore/restore-a-database-to-a-new-location-sql-server.md)  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="db173-160">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="db173-160">Using Transact-SQL</span></span>  
 <span data-ttu-id="db173-161">**准备辅助数据库**</span><span class="sxs-lookup"><span data-stu-id="db173-161">**To prepare a secondary database**</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="db173-162">有关此过程的示例，请参阅本主题前面的 [示例 (Transact-SQL)](#ExampleTsql)。</span><span class="sxs-lookup"><span data-stu-id="db173-162">For an example of this procedure, see [Example (Transact-SQL)](#ExampleTsql), earlier in this topic.</span></span>  
  
1.  <span data-ttu-id="db173-163">除非您已经有了主数据库的最近完整备份，否则请连接到承载主副本的服务器实例并创建完整数据库备份。</span><span class="sxs-lookup"><span data-stu-id="db173-163">Unless you have a recent full backup of the primary database, connect to the server instance that hosts the primary replica and create a full database backup.</span></span> <span data-ttu-id="db173-164">最好将此备份和任何后续的日志备份放到推荐的网络共享上。</span><span class="sxs-lookup"><span data-stu-id="db173-164">As a best practice, place this backup and any subsequent log backups onto the recommended network share.</span></span>  
  
2.  <span data-ttu-id="db173-165">在承载辅助副本的服务器实例上，依次还原主数据库的完整数据库备份（还可以选择还原差异备份）以及所有后续的日志备份。</span><span class="sxs-lookup"><span data-stu-id="db173-165">On the server instance that hosts the secondary replica, restore the full database backup of the primary database (and optionally a differential backup) followed by all subsequent log backups.</span></span> <span data-ttu-id="db173-166">使用 WITH NORECOVERY 执行每个还原操作。</span><span class="sxs-lookup"><span data-stu-id="db173-166">Use WITH NORECOVERY for every restore operation.</span></span>  
  
     <span data-ttu-id="db173-167">如果主数据库与辅助数据库的文件路径不同，例如，如果主数据库位于驱动器“F:”，但承载辅助副本的服务器实例缺少 F: 驱动器，请在 WITH 语句中包括 MOVE 选项。</span><span class="sxs-lookup"><span data-stu-id="db173-167">If the file paths of the primary database and the secondary database differ, for example, if the primary database is on drive 'F:' but the server instance that hosts the secondary replica lacks an F: drive, include the MOVE option in your WITH clause.</span></span>  
  
3.  <span data-ttu-id="db173-168">在执行完必要的日志备份之后，如果对主数据库进行了任何日志备份，还必须将这些备份复制到承载辅助副本的服务器实例上并将每个日志备份都应用到辅助数据库，以最早的备份开始进行，并始终使用 RESTORE WITH NORECOVERY。</span><span class="sxs-lookup"><span data-stu-id="db173-168">If any log backups have been taken on the primary database since the required log backup, you must also copy these to the server instance that hosts the secondary replica and apply each of those log backups to the secondary database, starting with the earliest and always using RESTORE WITH NORECOVERY.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="db173-169">如果主数据库刚刚创建，则不会存在日志备份；或者如果恢复模式刚刚从“简单”更改为“完整”，则尚未进行任何日志备份。</span><span class="sxs-lookup"><span data-stu-id="db173-169">A log backup would not exist if the primary database has just been created and no log backup has been taken yet or if the recovery model has just been changed from simple to full.</span></span>  
  
4.  <span data-ttu-id="db173-170">若要完成辅助数据库的配置，您需要将辅助数据库联接到可用性组。</span><span class="sxs-lookup"><span data-stu-id="db173-170">To complete configuration of the secondary database, you need to join the secondary database to the availability group.</span></span> <span data-ttu-id="db173-171">有关详细信息，请参阅[将辅助数据库联接到可用性组 (SQL Server)](join-a-secondary-database-to-an-availability-group-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="db173-171">For more information, [Join a Secondary Database to an Availability Group &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="db173-172"> 有关如何执行这些备份和还原操作的信息，请参阅本主题后面的 [相关备份和还原任务](#RelatedTasks)。</span><span class="sxs-lookup"><span data-stu-id="db173-172">For information about how to perform these backup and restore operations, see [Related Backup and Restore Tasks](#RelatedTasks), later in this topic.</span></span>  
  
###  <a name="transact-sql-example"></a><a name="ExampleTsql"></a><span data-ttu-id="db173-173">Transact-sql 示例</span><span class="sxs-lookup"><span data-stu-id="db173-173">Transact-SQL Example</span></span>  
 <span data-ttu-id="db173-174">下面的示例准备一个辅助数据库。</span><span class="sxs-lookup"><span data-stu-id="db173-174">The following example prepares a secondary database.</span></span> <span data-ttu-id="db173-175">此示例使用了 [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] 示例数据库，默认情况下，该数据库使用简单恢复模式。</span><span class="sxs-lookup"><span data-stu-id="db173-175">This example uses the [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] sample database, which uses the simple recovery model by default.</span></span>  
  
1.  <span data-ttu-id="db173-176">若要使用 [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] 数据库，请改用完整恢复模式：</span><span class="sxs-lookup"><span data-stu-id="db173-176">To use the [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] database, modify it to use the full recovery model:</span></span>  
  
    ```sql
    USE master;  
    GO  
    ALTER DATABASE MyDB1   
    SET RECOVERY FULL;  
    GO  
    ```  
  
2.  <span data-ttu-id="db173-177">将数据库的恢复模式从 SIMPLE 更改为 FULL 之后，创建一个完整备份，以用于创建辅助数据库。</span><span class="sxs-lookup"><span data-stu-id="db173-177">After modifying the recovery model of the database from SIMPLE to FULL, create a full backup, which can be used to create the secondary database.</span></span> <span data-ttu-id="db173-178">由于恢复模式已更改，因此指定了 WITH FORMAT 选项来创建新的介质集。</span><span class="sxs-lookup"><span data-stu-id="db173-178">Because the recovery model has just been changed, the WITH FORMAT option is specified to create a new media set.</span></span> <span data-ttu-id="db173-179">这对区分完整恢复模式下的备份与以前在简单恢复模式下创建的备份非常有用。</span><span class="sxs-lookup"><span data-stu-id="db173-179">This is useful to separate the backups under the full recovery model from any previous backups made under the simple recovery model.</span></span> <span data-ttu-id="db173-180">为了实现此示例的目的，在数据库所在的驱动器上创建备份文件 (C:\\[!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)].bak)。</span><span class="sxs-lookup"><span data-stu-id="db173-180">For the purpose of this example, the backup file (C:\\[!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)].bak) is created on the same drive as the database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="db173-181">对于生产数据库，应始终备份到单独的设备。</span><span class="sxs-lookup"><span data-stu-id="db173-181">For a production database, you should always back up to a separate device.</span></span>  
  
     <span data-ttu-id="db173-182">在承载主副本的服务器实例 (`INSTANCE01`) 上，按如下方式创建主数据库的完整备份：</span><span class="sxs-lookup"><span data-stu-id="db173-182">On the server instance that hosts the primary replica (`INSTANCE01`), create a full backup of the primary database as follows:</span></span>  
  
    ```sql
    BACKUP DATABASE MyDB1   
        TO DISK = 'C:\MyDB1.bak'   
        WITH FORMAT  
    GO  
    ```  
  
3.  <span data-ttu-id="db173-183">将完整备份复制到承载辅助副本的服务器实例上。</span><span class="sxs-lookup"><span data-stu-id="db173-183">Copy the full backup to the server instance that hosts the secondary replica.</span></span>  
  
4.  <span data-ttu-id="db173-184">使用 RESTORE WITH NORECOVERY 在承载辅助副本的服务器实例上还原完整备份。</span><span class="sxs-lookup"><span data-stu-id="db173-184">Restore the full backup, using RESTORE WITH NORECOVERY, onto the server instance that hosts the secondary replica.</span></span> <span data-ttu-id="db173-185">还原命令取决于主数据库与辅助数据库的路径是否相同。</span><span class="sxs-lookup"><span data-stu-id="db173-185">The restore command depends on whether the paths of primary and secondary databases are identical.</span></span>  
  
    -   <span data-ttu-id="db173-186">**如果路径相同：**</span><span class="sxs-lookup"><span data-stu-id="db173-186">**If the paths are identical:**</span></span>  
  
         <span data-ttu-id="db173-187">在承载辅助副本的计算机上，按如下方式还原完整备份：</span><span class="sxs-lookup"><span data-stu-id="db173-187">On the computer that hosts the secondary replica, restore the full backup as follows:</span></span>  
  
        ```sql
        RESTORE DATABASE MyDB1   
            FROM DISK = 'C:\MyDB1.bak'   
            WITH NORECOVERY  
        GO  
        ```  
  
    -   <span data-ttu-id="db173-188">**如果路径不同：**</span><span class="sxs-lookup"><span data-stu-id="db173-188">**If the paths differ:**</span></span>  
  
         <span data-ttu-id="db173-189">如果辅助数据库的路径与主数据库的路径不同（例如，它们所在的驱动器号不同），则创建辅助数据库要求还原操作包含 MOVE 子句。</span><span class="sxs-lookup"><span data-stu-id="db173-189">If the path of the secondary database differs from the path of the primary database (for instance, their drive letters differ), creating the secondary database requires that the restore operation include a MOVE clause.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="db173-190">如果主数据库与辅助数据库的路径名称不同，则无法添加文件。</span><span class="sxs-lookup"><span data-stu-id="db173-190">If the path names of the primary and secondary databases differ, you cannot add a file.</span></span> <span data-ttu-id="db173-191">原因是在接收添加文件操作所需的日志时，承载辅助副本的服务器实例会尝试将新文件放在主数据库所用的路径中。</span><span class="sxs-lookup"><span data-stu-id="db173-191">This is because on receiving the log for the add file operation, the server instance of the secondary replica attempts to place the new file in the same path as used by the primary database.</span></span>  
  
         <span data-ttu-id="db173-192">例如，下面的命令可还原主数据库的备份，主数据库位于 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]默认实例的数据目录 C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA 中。</span><span class="sxs-lookup"><span data-stu-id="db173-192">For example, the following command restores a backup of a primary database that resides in the data directory of the default instance of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA.</span></span> <span data-ttu-id="db173-193">还原数据库操作必须将数据库移到 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 名为 (*AlwaysOn1*) 的远程实例的数据目录中，该实例在另一个群集节点上托管辅助副本。</span><span class="sxs-lookup"><span data-stu-id="db173-193">The restore database operation must move the database to the data directory of a remote instance of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] named  (*AlwaysOn1*), which hosts the secondary replica on another cluster node.</span></span> <span data-ttu-id="db173-194">在该处，数据和日志文件还原到*C:\Program FILES\MICROSOFT SQL Server\MSSQL12。ALWAYSON1\MSSQL\DATA*目录。</span><span class="sxs-lookup"><span data-stu-id="db173-194">There, the data and log files are restored to the *C:\Program Files\Microsoft SQL Server\MSSQL12.ALWAYSON1\MSSQL\DATA* directory .</span></span> <span data-ttu-id="db173-195">该还原操作使用 WITH NORECOVERY 令辅助数据库保持还原状态。</span><span class="sxs-lookup"><span data-stu-id="db173-195">The restore operation uses WITH NORECOVERY, to leave the secondary database in the restoring database.</span></span>  
  
        ```sql
        RESTORE DATABASE MyDB1  
          FROM DISK='C:\MyDB1.bak'  
         WITH NORECOVERY,   
            MOVE 'MyDB1_Data' TO   
             'C:\Program Files\Microsoft SQL Server\MSSQL12.ALWAYSON1\MSSQL\DATA\MyDB1_Data.mdf',   
            MOVE 'MyDB1_Log' TO  
             'C:\Program Files\Microsoft SQL Server\MSSQL12.ALWAYSON1\MSSQL\DATA\MyDB1_Data.ldf';  
        GO  
        ```  
  
5.  <span data-ttu-id="db173-196">还原完整备份之后，必须在主数据库中创建日志备份。</span><span class="sxs-lookup"><span data-stu-id="db173-196">After you restore the full backup, you must create a log backup on the primary database.</span></span> <span data-ttu-id="db173-197">例如，以下 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 语句将日志备份到名为 *E:\MyDB1_log.bak*的备份文件：</span><span class="sxs-lookup"><span data-stu-id="db173-197">For example, the following [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement backs up the log to the a backup file named *E:\MyDB1_log.bak*:</span></span>  
  
    ```sql
    BACKUP LOG MyDB1   
      TO DISK = 'E:\MyDB1_log.bak'   
    GO  
    ```  
  
6.  <span data-ttu-id="db173-198">在将数据库联接到辅助副本之前，必须应用必要的日志备份（以及所有后续日志备份）。</span><span class="sxs-lookup"><span data-stu-id="db173-198">Before you can join the database to the secondary replica, you must apply the required log backup (and any subsequent log backups).</span></span>  
  
     <span data-ttu-id="db173-199">例如，以下 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 语句还原 *C:\MyDB1.bak*中的第一个日志：</span><span class="sxs-lookup"><span data-stu-id="db173-199">For example, the following [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement restores the first log from *C:\MyDB1.bak*:</span></span>  
  
    ```sql
    RESTORE LOG MyDB1   
      FROM DISK = 'E:\MyDB1_log.bak'   
        WITH FILE=1, NORECOVERY  
    GO  
    ```  
  
7.  <span data-ttu-id="db173-200">如果在数据库联接到辅助副本之前进行了任何其他日志备份，则还必须使用 RESTORE WITH NORECOVERY 按顺序将所有这些日志备份还原到承载辅助副本的服务器实例上。</span><span class="sxs-lookup"><span data-stu-id="db173-200">If any additional log backups occur before the database joins the secondary replica, you must also restore all of those log backups, in sequence, to the server instance that hosts the secondary replica using RESTORE WITH NORECOVERY.</span></span>  
  
     <span data-ttu-id="db173-201">例如，以下 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 语句还原 *E:\MyDB1_log.bak*中的其他两个日志：</span><span class="sxs-lookup"><span data-stu-id="db173-201">For example, the following [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement restores two additional logs from *E:\MyDB1_log.bak*:</span></span>  
  
    ```sql
    RESTORE LOG MyDB1   
      FROM DISK = 'E:\MyDB1_log.bak'   
        WITH FILE=2, NORECOVERY  
    GO  
    RESTORE LOG MyDB1   
      FROM DISK = 'E:\MyDB1_log.bak'   
        WITH FILE=3, NORECOVERY  
    GO  
    ```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="db173-202">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="db173-202">Using PowerShell</span></span>  
 <span data-ttu-id="db173-203">**准备辅助数据库**</span><span class="sxs-lookup"><span data-stu-id="db173-203">**To prepare a secondary database**</span></span>  
  
1.  <span data-ttu-id="db173-204">如果您需要创建主数据库的最近备份，请将目录 (`cd`) 改为承载主副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="db173-204">If you need to create a recent backup of the primary database, change directory (`cd`) to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="db173-205">使用 `Backup-SqlDatabase` cmdlet 创建每个备份。</span><span class="sxs-lookup"><span data-stu-id="db173-205">Use the `Backup-SqlDatabase` cmdlet to create each of the backups.</span></span>  
  
3.  <span data-ttu-id="db173-206">切换目录 (`cd`) 到承载辅助副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="db173-206">Change directory (`cd`) to the server instance that hosts the secondary replica.</span></span>  
  
4.  <span data-ttu-id="db173-207">若要还原数据库以及每个主数据库的日志备份，请使用 `restore-SqlDatabase` cmdlet 并指定 `NoRecovery` 还原参数。</span><span class="sxs-lookup"><span data-stu-id="db173-207">To restore the database and log backups of each primary database, use the `restore-SqlDatabase` cmdlet, specifying the `NoRecovery` restore parameter.</span></span> <span data-ttu-id="db173-208">如果文件路径在承载主副本和目标辅助副本的计算机之间存在差异，还要使用 `RelocateFile` 还原参数。</span><span class="sxs-lookup"><span data-stu-id="db173-208">If the file paths differ between the computers that host the primary replica and the target secondary replica, also use the `RelocateFile` restore parameter.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="db173-209">若要查看 cmdlet 的语法，请在 `Get-Help` PowerShell 环境中使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cmdlet。</span><span class="sxs-lookup"><span data-stu-id="db173-209">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="db173-210">有关详细信息，请参阅 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="db173-210">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
5.  <span data-ttu-id="db173-211">若要完成辅助数据库的配置，您需要将其联接到可用性组。</span><span class="sxs-lookup"><span data-stu-id="db173-211">To complete configuration of the secondary database, you need to join it to the availability group.</span></span> <span data-ttu-id="db173-212">有关详细信息，请参阅[将辅助数据库联接到可用性组 (SQL Server)](join-a-secondary-database-to-an-availability-group-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="db173-212">For more information, [Join a Secondary Database to an Availability Group &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md).</span></span>  
  
 <span data-ttu-id="db173-213">**设置和使用 SQL Server PowerShell 提供程序**</span><span class="sxs-lookup"><span data-stu-id="db173-213">**To set up and use the SQL Server PowerShell provider**</span></span>  
  
-   [<span data-ttu-id="db173-214">SQL Server PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="db173-214">SQL Server PowerShell Provider</span></span>](../../../powershell/sql-server-powershell-provider.md)  
  
###  <a name="sample-backup-and-restore-script-and-command"></a><a name="ExamplePSscript"></a><span data-ttu-id="db173-215">备份和还原脚本和命令示例</span><span class="sxs-lookup"><span data-stu-id="db173-215">Sample Backup and Restore Script and Command</span></span>  
 <span data-ttu-id="db173-216">下面的 PowerShell 命令将完整的数据库备份和事务日志备份到网络共享，并自该共享位置还原这些备份。</span><span class="sxs-lookup"><span data-stu-id="db173-216">The following PowerShell commands back up a full database backup and transaction log to a network share and restore those backups from that share.</span></span> <span data-ttu-id="db173-217">此示例假定数据库还原到的文件路径与数据库备份到的文件路径相同。</span><span class="sxs-lookup"><span data-stu-id="db173-217">This example assumes that the file path to which the database is restored is the same as the file path on which the database was backed up.</span></span>  
  
```powershell
# Create database backup  
Backup-SqlDatabase -Database "MyDB1" -BackupFile "\\share\backups\MyDB1.bak" -ServerInstance "SourceMachine\Instance"  
# Create log backup  
Backup-SqlDatabase -Database "MyDB1" -BackupAction "Log" -BackupFile "\\share\backups\MyDB1.trn" -ServerInstance "SourceMachine\Instance"  
# Restore database backup
Restore-SqlDatabase -Database "MyDB1" -BackupFile "\\share\backups\MyDB1.bak" -NoRecovery -ServerInstance "DestinationMachine\Instance"  
# Restore log backup
Restore-SqlDatabase -Database "MyDB1" -BackupFile "\\share\backups\MyDB1.trn" -RestoreAction "Log" -NoRecovery -ServerInstance "DestinationMachine\Instance"
```  
  
##  <a name="follow-up-after-preparing-a-secondary-database"></a><a name="FollowUp"></a> <span data-ttu-id="db173-218">跟进：准备辅助数据库之后</span><span class="sxs-lookup"><span data-stu-id="db173-218">Follow Up: After Preparing a Secondary Database</span></span>  
 <span data-ttu-id="db173-219">若要完成辅助数据库的配置，您需要将新还原的数据库联接到可用性组。</span><span class="sxs-lookup"><span data-stu-id="db173-219">To complete configuration of the secondary database, join the newly restored database to the availability group.</span></span> <span data-ttu-id="db173-220">有关详细信息，请参阅 [将辅助数据库联接到可用性组 (SQL Server)](join-a-secondary-database-to-an-availability-group-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="db173-220">For more information, see [Join a Secondary Database to an Availability Group &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db173-221">另请参阅</span><span class="sxs-lookup"><span data-stu-id="db173-221">See Also</span></span>  
 <span data-ttu-id="db173-222">[AlwaysOn 可用性组 &#40;SQL Server 概述&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="db173-222">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="db173-223">[BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="db173-223">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="db173-224">[RESTORE 参数 (Transact-SQL)](/sql/t-sql/statements/restore-statements-arguments-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="db173-224">[RESTORE Arguments &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql) </span></span>  
 <span data-ttu-id="db173-225">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="db173-225">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 [<span data-ttu-id="db173-226">排除失败的添加文件操作 &#40;AlwaysOn 可用性组&#41;</span><span class="sxs-lookup"><span data-stu-id="db173-226">Troubleshoot a Failed Add-File Operation &#40;AlwaysOn Availability Groups&#41;</span></span>](troubleshoot-a-failed-add-file-operation-always-on-availability-groups.md)  
