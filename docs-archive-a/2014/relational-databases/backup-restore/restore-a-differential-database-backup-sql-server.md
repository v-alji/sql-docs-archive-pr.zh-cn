---
title: 还原差异数据库备份 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- full differential backups [SQL Server]
- restoring databases [SQL Server], full differential backups
- database backups [SQL Server], full differential backups
- database restores [SQL Server], full differential backups
- backing up databases [SQL Server], full differential backups
ms.assetid: 0dd971a4-ee38-4dd3-9f30-ef77fc58dd11
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a8eab18d84efc1a990715e0d5488085252f93a7e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589163"
---
# <a name="restore-a-differential-database-backup-sql-server"></a><span data-ttu-id="ec858-102">还原差异数据库备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ec858-102">Restore a Differential Database Backup (SQL Server)</span></span>
  <span data-ttu-id="ec858-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中还原差异数据库备份。</span><span class="sxs-lookup"><span data-stu-id="ec858-103">This topic describes how to restore a differential database backup in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="ec858-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="ec858-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="ec858-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="ec858-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="ec858-106">限制和局限</span><span class="sxs-lookup"><span data-stu-id="ec858-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="ec858-107">先决条件</span><span class="sxs-lookup"><span data-stu-id="ec858-107">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="ec858-108">安全性</span><span class="sxs-lookup"><span data-stu-id="ec858-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="ec858-109">**若要还原差异数据库备份，请使用：**</span><span class="sxs-lookup"><span data-stu-id="ec858-109">**To restore a differential database backup, using:**</span></span>  
  
     [<span data-ttu-id="ec858-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ec858-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="ec858-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ec858-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   [<span data-ttu-id="ec858-112">相关任务</span><span class="sxs-lookup"><span data-stu-id="ec858-112">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ec858-113">开始之前</span><span class="sxs-lookup"><span data-stu-id="ec858-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="ec858-114">限制和局限</span><span class="sxs-lookup"><span data-stu-id="ec858-114">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="ec858-115">不允许在显式或隐式事务中使用 RESTORE。</span><span class="sxs-lookup"><span data-stu-id="ec858-115">RESTORE is not allowed in an explicit or implicit transaction.</span></span>  
  
-   <span data-ttu-id="ec858-116">无法在早期版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中还原较新版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]创建的备份。</span><span class="sxs-lookup"><span data-stu-id="ec858-116">Backups that are created by more recent version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cannot be restored in earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="ec858-117">在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中，可以从使用 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 或更高版本创建的数据库备份来还原用户数据库。</span><span class="sxs-lookup"><span data-stu-id="ec858-117">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], you can restore a user database from a database backup that was created by using [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] or a later version.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="ec858-118">先决条件</span><span class="sxs-lookup"><span data-stu-id="ec858-118">Prerequisites</span></span>  
  
-   <span data-ttu-id="ec858-119">在完整恢复模式或大容量日志恢复模式下，必须先备份活动事务日志（称为日志尾部），然后才能还原数据库。</span><span class="sxs-lookup"><span data-stu-id="ec858-119">Under the full or bulk-logged recovery model, before you can restore a database, you must back up the active transaction log (known as the tail of the log).</span></span> <span data-ttu-id="ec858-120">有关详细信息，请参阅 [备份事务日志 (SQL Server)](back-up-a-transaction-log-sql-server.md)数据库还原到一个新位置并且可以选择重命名该数据库。</span><span class="sxs-lookup"><span data-stu-id="ec858-120">For more information, see [Back Up a Transaction Log &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="ec858-121">Security</span><span class="sxs-lookup"><span data-stu-id="ec858-121">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ec858-122">权限</span><span class="sxs-lookup"><span data-stu-id="ec858-122">Permissions</span></span>  
 <span data-ttu-id="ec858-123">如果不存在要还原的数据库，则用户必须有 CREATE DATABASE 权限才能执行 RESTORE。</span><span class="sxs-lookup"><span data-stu-id="ec858-123">If the database being restored does not exist, the user must have CREATE DATABASE permissions to be able to execute RESTORE.</span></span> <span data-ttu-id="ec858-124">如果数据库存在，则 RESTORE 权限默认授予 **sysadmin** 和 **dbcreator** 固定服务器角色成员以及数据库的所有者 (**dbo**)（对于 FROM DATABASE_SNAPSHOT 选项，数据库始终存在）。</span><span class="sxs-lookup"><span data-stu-id="ec858-124">If the database exists, RESTORE permissions default to members of the **sysadmin** and **dbcreator** fixed server roles and the owner (**dbo**) of the database (for the FROM DATABASE_SNAPSHOT option, the database always exists).</span></span>  
  
 <span data-ttu-id="ec858-125">RESTORE 权限被授予那些成员身份信息始终可由服务器使用的角色。</span><span class="sxs-lookup"><span data-stu-id="ec858-125">RESTORE permissions are given to roles in which membership information is always readily available to the server.</span></span> <span data-ttu-id="ec858-126">因为只有在固定数据库可以访问且没有损坏时（在执行 RESTORE 时并不会总是这样）才能检查固定数据库角色成员身份，所以 **db_owner** 固定数据库角色成员没有 RESTORE 权限。</span><span class="sxs-lookup"><span data-stu-id="ec858-126">Because fixed database role membership can be checked only when the database is accessible and undamaged, which is not always the case when RESTORE is executed, members of the **db_owner** fixed database role do not have RESTORE permissions.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="ec858-127">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ec858-127">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-restore-a-differential-database-backup"></a><span data-ttu-id="ec858-128">还原差异数据库备份</span><span class="sxs-lookup"><span data-stu-id="ec858-128">To restore a differential database backup</span></span>  
  
1.  <span data-ttu-id="ec858-129">连接到相应的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 实例之后，在“对象资源管理器”中，单击服务器名称以展开服务器树。</span><span class="sxs-lookup"><span data-stu-id="ec858-129">After you connect to the appropriate instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="ec858-130">展开 **“数据库”** 。</span><span class="sxs-lookup"><span data-stu-id="ec858-130">Expand **Databases**.</span></span> <span data-ttu-id="ec858-131"> 根据具体的数据库，选择一个用户数据库，或展开“系统数据库”并选择一个系统数据库。</span><span class="sxs-lookup"><span data-stu-id="ec858-131">Depending on the database, either select a user database or expand **System Databases**, and then select a system database.</span></span>  
  
3.  <span data-ttu-id="ec858-132">右键单击数据库，指向“任务”  ，再指向“还原”  ，然后单击“数据库”  。</span><span class="sxs-lookup"><span data-stu-id="ec858-132">Right-click the database, point to **Tasks**, point to **Restore**, and then click **Database**.</span></span>  
  
4.  <span data-ttu-id="ec858-133">在 **“常规”** 页上，使用 **“源”** 部分指定要还原的备份集的源和位置。</span><span class="sxs-lookup"><span data-stu-id="ec858-133">On the **General** page, use the **Source** section to specify the source and location of the backup sets to restore.</span></span> <span data-ttu-id="ec858-134">选择以下选项之一：</span><span class="sxs-lookup"><span data-stu-id="ec858-134">Select one of the following options:</span></span>  
  
    -   <span data-ttu-id="ec858-135">**Database**</span><span class="sxs-lookup"><span data-stu-id="ec858-135">**Database**</span></span>  
  
         <span data-ttu-id="ec858-136">从下拉列表中选择要还原的数据库。</span><span class="sxs-lookup"><span data-stu-id="ec858-136">Select the database to restore from the drop-down list.</span></span> <span data-ttu-id="ec858-137">此列表仅包含已根据 **msdb** 备份历史记录进行备份的数据库。</span><span class="sxs-lookup"><span data-stu-id="ec858-137">The list contains only databases that have been backed up according to the **msdb** backup history.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ec858-138">如果备份是从另一台服务器执行的，则目标服务器不具有指定数据库的备份历史记录信息。</span><span class="sxs-lookup"><span data-stu-id="ec858-138">If the backup is taken from a different server, the destination server will not have the backup history information for the specified database.</span></span> <span data-ttu-id="ec858-139">这种情况下，请选择 **“设备”** 以手动指定要还原的文件或设备。</span><span class="sxs-lookup"><span data-stu-id="ec858-139">In this case, select **Device** to manually specify the file or device to restore.</span></span>  
  
    -   <span data-ttu-id="ec858-140">**设备**</span><span class="sxs-lookup"><span data-stu-id="ec858-140">**Device**</span></span>  
  
         <span data-ttu-id="ec858-141">单击“浏览”按钮 ( **...** ) 以打开“选择备份设备”  对话框。</span><span class="sxs-lookup"><span data-stu-id="ec858-141">Click the browse (**...**) button to open the **Select backup devices** dialog box.</span></span> <span data-ttu-id="ec858-142">在 **“备份介质类型”** 框中，从列出的设备类型中选择一种。</span><span class="sxs-lookup"><span data-stu-id="ec858-142">In the **Backup media type** box, select one of the listed device types.</span></span> <span data-ttu-id="ec858-143">若要为 **“备份介质”** 框选择一个或多个设备，请单击 **“添加”** 。</span><span class="sxs-lookup"><span data-stu-id="ec858-143">To select one or more devices for the **Backup media** box, click **Add**.</span></span>  
  
         <span data-ttu-id="ec858-144">将所需设备添加到 **“备份介质”** 列表框后，单击 **“确定”** 返回到 **“常规”** 页。</span><span class="sxs-lookup"><span data-stu-id="ec858-144">After you add the devices you want to the **Backup media** list box, click **OK** to return to the **General** page.</span></span>  
  
         <span data-ttu-id="ec858-145">在“源:设备:数据库”列表框中，选择应还原的数据库名称 **。**</span><span class="sxs-lookup"><span data-stu-id="ec858-145">In the **Source: Device: Database** list box, select the name of the database which should be restored.</span></span>  
  
         <span data-ttu-id="ec858-146">**注意** ：此列表仅在选择了 **“设备”** 时才可用。</span><span class="sxs-lookup"><span data-stu-id="ec858-146">**Note** This list is only available when **Device** is selected.</span></span> <span data-ttu-id="ec858-147">只有在所选设备上具有备份的数据库才可用。</span><span class="sxs-lookup"><span data-stu-id="ec858-147">Only databases that have backups on the selected device will be available.</span></span>  
  
5.  <span data-ttu-id="ec858-148">在 **“目标”** 部分中， **“数据库”** 框自动填充要还原的数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="ec858-148">In the **Destination** section, the **Database** box is automatically populated with the name of the database to be restored.</span></span> <span data-ttu-id="ec858-149">若要更改数据库名称，请在 **“数据库”** 框中输入新名称。</span><span class="sxs-lookup"><span data-stu-id="ec858-149">To change the name of the database, enter the new name in the **Database** box.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ec858-150">若要在特定的时间点停止还原，请单击 **“时间线”** 以访问 **“备份时间线”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="ec858-150">To stop the restore at a specific point in time, click **Timeline** to access the **Backup Timeline** dialog box.</span></span> <span data-ttu-id="ec858-151">有关在特定时间点停止数据库还原的帮助，请参阅[将 SQL Server 数据库还原到某个时点（完整恢复模式）](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)。</span><span class="sxs-lookup"><span data-stu-id="ec858-151">For help with stopping a database restore at a specific point in time, see [Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md).</span></span>  
  
6.  <span data-ttu-id="ec858-152">在 **“要还原的备份集”** 网格中，选择要通过差异备份还原的备份。</span><span class="sxs-lookup"><span data-stu-id="ec858-152">In the **Backup sets to restore** grid, select the backups through the differential backup that you wish to restore.</span></span>  
  
     <span data-ttu-id="ec858-153">有关“用于还原的备份集”  网格中的列的信息，请参阅[还原数据库（“常规”页）](../../integration-services/general-page-of-integration-services-designers-options.md)。</span><span class="sxs-lookup"><span data-stu-id="ec858-153">For information about the columns in the **Backup sets to restore** grid, see [Restore Database &#40;General Page&#41;](../../integration-services/general-page-of-integration-services-designers-options.md).</span></span>  
  
7.  <span data-ttu-id="ec858-154">在 **“选项”** 页的 **“还原选项”** 面板中，可以根据您的实际情况选择下列任意选项：</span><span class="sxs-lookup"><span data-stu-id="ec858-154">On the **Options** page, in the **Restore options** panel, you can select any of the following options, if appropriate for your situation:</span></span>  
  
    -   <span data-ttu-id="ec858-155">**覆盖现有数据库(WITH REPLACE)**</span><span class="sxs-lookup"><span data-stu-id="ec858-155">**Overwrite the existing database (WITH REPLACE)**</span></span>  
  
    -   <span data-ttu-id="ec858-156">**保留复制设置(WITH KEEP_REPLICATION)**</span><span class="sxs-lookup"><span data-stu-id="ec858-156">**Preserve the replication settings (WITH KEEP_REPLICATION)**</span></span>  
  
    -   <span data-ttu-id="ec858-157">**还原每个备份之前进行提示**</span><span class="sxs-lookup"><span data-stu-id="ec858-157">**Prompt before restoring each backup**</span></span>  
  
    -   <span data-ttu-id="ec858-158">**限制对还原数据库的访问(WITH RESTRICTED_USER)**</span><span class="sxs-lookup"><span data-stu-id="ec858-158">**Restrict access to the restored database (WITH RESTRICTED_USER)**</span></span>  
  
     <span data-ttu-id="ec858-159">有关这些选项的详细信息，请参阅[还原数据库（“选项”页）](restore-database-options-page.md)。</span><span class="sxs-lookup"><span data-stu-id="ec858-159">For more information about these options, see [Restore Database &#40;Options Page&#41;](restore-database-options-page.md).</span></span>  
  
8.  <span data-ttu-id="ec858-160">为 **“恢复状态”** 框选择一个选项。</span><span class="sxs-lookup"><span data-stu-id="ec858-160">Select an option for the **Recovery state** box.</span></span> <span data-ttu-id="ec858-161">此框确定还原操作之后的数据库状态。</span><span class="sxs-lookup"><span data-stu-id="ec858-161">This box determines the state of the database after the restore operation.</span></span>  
  
    -   <span data-ttu-id="ec858-162">**RESTORE WITH RECOVERY** 是默认行为，它通过回滚未提交的事务，使数据库处于可以使用的状态。</span><span class="sxs-lookup"><span data-stu-id="ec858-162">**RESTORE WITH RECOVERY** is the default behavior which leaves the database ready for use by rolling back the uncommitted transactions.</span></span> <span data-ttu-id="ec858-163">无法还原其他事务日志。</span><span class="sxs-lookup"><span data-stu-id="ec858-163">Additional transaction logs cannot be restored.</span></span> <span data-ttu-id="ec858-164">如果您要立即还原所有必要的备份，则选择此选项。</span><span class="sxs-lookup"><span data-stu-id="ec858-164">Select this option if you are restoring all of the necessary backups now.</span></span>  
  
    -   <span data-ttu-id="ec858-165">**RESTORE WITH NORECOVERY** 不对数据库执行任何操作，不回滚未提交的事务。</span><span class="sxs-lookup"><span data-stu-id="ec858-165">**RESTORE WITH NORECOVERY** which leaves the database non-operational, and does not roll back the uncommitted transactions.</span></span> <span data-ttu-id="ec858-166">可以还原其他事务日志。</span><span class="sxs-lookup"><span data-stu-id="ec858-166">Additional transaction logs can be restored.</span></span> <span data-ttu-id="ec858-167">除非恢复数据库，否则无法使用数据库。</span><span class="sxs-lookup"><span data-stu-id="ec858-167">The database cannot be used until it is recovered.</span></span>  
  
    -   <span data-ttu-id="ec858-168">**RESTORE WITH STANDBY** 使数据库处于只读模式。</span><span class="sxs-lookup"><span data-stu-id="ec858-168">**RESTORE WITH STANDBY** which leaves the database in read-only mode.</span></span> <span data-ttu-id="ec858-169">它撤消未提交的事务，但将撤消操作保存在备用文件中，以便能够还原恢复结果。</span><span class="sxs-lookup"><span data-stu-id="ec858-169">It undoes uncommitted transactions, but saves the undo actions in a standby file so that recovery effects can be reverted.</span></span>  
  
     <span data-ttu-id="ec858-170">有关这些选项的说明，请参阅[还原数据库（“选项”页）](restore-database-options-page.md)。</span><span class="sxs-lookup"><span data-stu-id="ec858-170">For descriptions of the options, see [Restore Database &#40;Options Page&#41;](restore-database-options-page.md).</span></span>  
  
9. <span data-ttu-id="ec858-171">如果存在与数据库的活动连接，则还原操作将失败。</span><span class="sxs-lookup"><span data-stu-id="ec858-171">Restore operations will fail if there are active connections to the database.</span></span> <span data-ttu-id="ec858-172">选中 **“关闭现有连接”** 以确保关闭 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 和数据库之间的所有活动连接。</span><span class="sxs-lookup"><span data-stu-id="ec858-172">Check the **Close existing connections option** to ensure that all active connections between [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] and the database are closed.</span></span>  
  
10. <span data-ttu-id="ec858-173">如果要在每个还原操作之间进行提示，请选择 **“还原每个备份之前进行提示”** 。</span><span class="sxs-lookup"><span data-stu-id="ec858-173">Select **Prompt before restoring each backup** if you wish to be prompted between each restore operation.</span></span> <span data-ttu-id="ec858-174">除非数据库过大并且您要监视还原操作的状态，否则通常没有必要选中该选项。</span><span class="sxs-lookup"><span data-stu-id="ec858-174">This is not usually necessary unless the database is large and you wish to monitor the status of the restore operation.</span></span>  
  
11. <span data-ttu-id="ec858-175">可以使用 **“文件”** 页将数据库还原到一个新位置。</span><span class="sxs-lookup"><span data-stu-id="ec858-175">Optionally, use the **Files** page to restore the database to a new location.</span></span> <span data-ttu-id="ec858-176">有关移动数据库的帮助，请参阅[将数据库还原到新位置 (SQL Server)](restore-a-database-to-a-new-location-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="ec858-176">For help with moving a database, see [Restore a Database to a New Location &#40;SQL Server&#41;](restore-a-database-to-a-new-location-sql-server.md).</span></span>  
  
12. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="ec858-177">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ec858-177">Using Transact-SQL</span></span>  
  
#### <a name="to-restore-a-differential-database-backup"></a><span data-ttu-id="ec858-178">还原差异数据库备份</span><span class="sxs-lookup"><span data-stu-id="ec858-178">To restore a differential database backup</span></span>  
  
1.  <span data-ttu-id="ec858-179">执行 RESTORE DATABASE 语句并指定 NORECOVERY 子句，以还原在差异数据库备份之前执行的完整数据库备份。</span><span class="sxs-lookup"><span data-stu-id="ec858-179">Execute the RESTORE DATABASE statement, specifying the NORECOVERY clause, to restore the full database backup that comes before the differential database backup.</span></span> <span data-ttu-id="ec858-180">有关详细信息，请参阅[操作说明：还原完整备份](restore-a-database-backup-under-the-simple-recovery-model-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="ec858-180">For more information, see [How to: Restore a Full Backup](restore-a-database-backup-under-the-simple-recovery-model-transact-sql.md).</span></span>  
  
2.  <span data-ttu-id="ec858-181">执行 RESTORE DATABASE 语句以还原差异数据库备份，同时指定：</span><span class="sxs-lookup"><span data-stu-id="ec858-181">Execute the RESTORE DATABASE statement to restore the differential database backup, specifying:</span></span>  
  
    -   <span data-ttu-id="ec858-182">要应用差异数据库备份的数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="ec858-182">The name of the database to which the differential database backup is applied.</span></span>  
  
    -   <span data-ttu-id="ec858-183">从其中还原差异数据库备份的备份设备。</span><span class="sxs-lookup"><span data-stu-id="ec858-183">The backup device where the differential database backup is restored from.</span></span>  
  
    -   <span data-ttu-id="ec858-184">NORECOVERY 子句，前提是在还原差异数据库备份之后，还要应用事务日志备份。</span><span class="sxs-lookup"><span data-stu-id="ec858-184">The NORECOVERY clause if you have transaction log backups to apply after the differential database backup is restored.</span></span> <span data-ttu-id="ec858-185">否则应指定 RECOVERY 子句。</span><span class="sxs-lookup"><span data-stu-id="ec858-185">Otherwise, specify the RECOVERY clause.</span></span>  
  
3.  <span data-ttu-id="ec858-186">通过完整恢复模式或大容量日志恢复模式，还原差异数据库备份可将数据库还原到差异数据库备份完成的点。</span><span class="sxs-lookup"><span data-stu-id="ec858-186">With the full or bulk-logged recovery model, restoring a differential database backup restores the database to the point at which the differential database backup was completed.</span></span> <span data-ttu-id="ec858-187">若要恢复到故障点，在创建完最后一个差异数据库备份之后，必须应用所有已创建的事务日志备份。</span><span class="sxs-lookup"><span data-stu-id="ec858-187">To recover to the point of failure, you must apply all transaction log backups created after the last differential database backup was created.</span></span> <span data-ttu-id="ec858-188">有关详细信息，请参阅[应用事务日志备份 (SQL Server)](transaction-log-backups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="ec858-188">For more information, see [Apply Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md).</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="ec858-189">示例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="ec858-189">Examples (Transact-SQL)</span></span>  
  
#### <a name="a-restoring-a-differential-database-backup"></a><span data-ttu-id="ec858-190">A.</span><span class="sxs-lookup"><span data-stu-id="ec858-190">A.</span></span> <span data-ttu-id="ec858-191">还原差异数据库备份</span><span class="sxs-lookup"><span data-stu-id="ec858-191">Restoring a differential database backup</span></span>  
 <span data-ttu-id="ec858-192">以下示例将还原 `MyAdvWorks` 数据库及其差异数据库备份。</span><span class="sxs-lookup"><span data-stu-id="ec858-192">This example restores a database and differential database backup of the `MyAdvWorks` database.</span></span>  
  
```sql  
-- Assume the database is lost, and restore full database,   
-- specifying the original full database backup and NORECOVERY,   
-- which allows subsequent restore operations to proceed.  
RESTORE DATABASE MyAdvWorks  
   FROM MyAdvWorks_1  
   WITH NORECOVERY;  
GO  
-- Now restore the differential database backup, the second backup on   
-- the MyAdvWorks_1 backup device.  
RESTORE DATABASE MyAdvWorks  
   FROM MyAdvWorks_1  
   WITH FILE = 2,  
   RECOVERY;  
GO  
```  
  
#### <a name="b-restoring-a-database-differential-database-and-transaction-log-backup"></a><span data-ttu-id="ec858-193">B.</span><span class="sxs-lookup"><span data-stu-id="ec858-193">B.</span></span> <span data-ttu-id="ec858-194">还原数据库、差异数据库以及事务日志备份</span><span class="sxs-lookup"><span data-stu-id="ec858-194">Restoring a database, differential database, and transaction log backup</span></span>  
 <span data-ttu-id="ec858-195">以下示例将还原 `MyAdvWorks` 数据库及其差异数据库和事务日志备份。</span><span class="sxs-lookup"><span data-stu-id="ec858-195">This example restores a database, differential database, and transaction log backup of the `MyAdvWorks` database.</span></span>  
  
```sql  
-- Assume the database is lost at this point. Now restore the full   
-- database. Specify the original full database backup and NORECOVERY.  
-- NORECOVERY allows subsequent restore operations to proceed.  
RESTORE DATABASE MyAdvWorks  
   FROM MyAdvWorks_1  
   WITH NORECOVERY;  
GO  
-- Now restore the differential database backup, the second backup on   
-- the MyAdvWorks_1 backup device.  
RESTORE DATABASE MyAdvWorks  
   FROM MyAdvWorks_1  
   WITH FILE = 2,  
   NORECOVERY;  
GO  
-- Now restore each transaction log backup created after  
-- the differential database backup.  
RESTORE LOG MyAdvWorks  
   FROM MyAdvWorks_log1  
   WITH NORECOVERY;  
GO  
RESTORE LOG MyAdvWorks  
   FROM MyAdvWorks_log2  
   WITH RECOVERY;  
GO  
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="ec858-196">相关任务</span><span class="sxs-lookup"><span data-stu-id="ec858-196">Related Tasks</span></span>  
  
-   [<span data-ttu-id="ec858-197">创建差异数据库备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ec858-197">Create a Differential Database Backup &#40;SQL Server&#41;</span></span>](create-a-differential-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="ec858-198">还原事务日志备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ec858-198">Restore a Transaction Log Backup &#40;SQL Server&#41;</span></span>](restore-a-transaction-log-backup-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="ec858-199">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ec858-199">See Also</span></span>  
 <span data-ttu-id="ec858-200">[差异备份 (SQL Server)](differential-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ec858-200">[Differential Backups &#40;SQL Server&#41;](differential-backups-sql-server.md) </span></span>  
 [<span data-ttu-id="ec858-201">RESTORE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ec858-201">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
