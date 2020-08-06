---
title: 将 SQL Server 数据库还原到某个时点（完整恢复模式）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- STOPAT clause [RESTORE LOG statement]
- point in time recovery [SQL Server]
- restoring databases [SQL Server], point in time
ms.assetid: 3a5daefd-08a8-4565-b54f-28ad01a47d32
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 0c71ff6e75cbbf27042c1eac70b1f97076290865
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589162"
---
# <a name="restore-a-sql-server-database-to-a-point-in-time-full-recovery-model"></a><span data-ttu-id="837b8-102">将 SQL Server 数据库还原到某个时点（完整恢复模式）</span><span class="sxs-lookup"><span data-stu-id="837b8-102">Restore a SQL Server Database to a Point in Time (Full Recovery Model)</span></span>
  <span data-ttu-id="837b8-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 将数据库还原到 [!INCLUDE[tsql](../../includes/tsql-md.md)]中的某个时间点。</span><span class="sxs-lookup"><span data-stu-id="837b8-103">This topic describes how to restore a database to a point in time in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="837b8-104">本主题仅与使用完整恢复模式或大容量日志恢复模式的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库有关。</span><span class="sxs-lookup"><span data-stu-id="837b8-104">This topic is relevant only for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases that use the full or bulk-logged recovery models.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="837b8-105">在大容量日志恢复模式下，如果日志备份包含大容量更改，则不能使用时点恢复方式恢复到该备份内的某个点。</span><span class="sxs-lookup"><span data-stu-id="837b8-105">Under the bulk-logged recovery model, if a log backup contains bulk-logged changes, point-in-time recovery is not possible to a point within that backup.</span></span> <span data-ttu-id="837b8-106">必须将数据库恢复到事务日志备份的结尾。</span><span class="sxs-lookup"><span data-stu-id="837b8-106">The database must be recovered to the end of the transaction log backup.</span></span>  
  
-   <span data-ttu-id="837b8-107">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="837b8-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="837b8-108">建议</span><span class="sxs-lookup"><span data-stu-id="837b8-108">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="837b8-109">安全性</span><span class="sxs-lookup"><span data-stu-id="837b8-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="837b8-110">**如何将 SQL Server 数据库还原到某个时间点，使用：**</span><span class="sxs-lookup"><span data-stu-id="837b8-110">**To restore a SQL Server database to a point in time, using:**</span></span>  
  
     [<span data-ttu-id="837b8-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="837b8-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="837b8-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="837b8-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="837b8-113">开始之前</span><span class="sxs-lookup"><span data-stu-id="837b8-113">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="837b8-114">建议</span><span class="sxs-lookup"><span data-stu-id="837b8-114">Recommendations</span></span>  
  
-   <span data-ttu-id="837b8-115">使用 STANDBY 查找未知的时间点。</span><span class="sxs-lookup"><span data-stu-id="837b8-115">Use STANDBY to find unknown point in time.</span></span>  
  
-   <span data-ttu-id="837b8-116">在还原顺序中尽早指定时间点</span><span class="sxs-lookup"><span data-stu-id="837b8-116">Specify the point in time early in a restore sequence</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="837b8-117">Security</span><span class="sxs-lookup"><span data-stu-id="837b8-117">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="837b8-118">权限</span><span class="sxs-lookup"><span data-stu-id="837b8-118">Permissions</span></span>  
 <span data-ttu-id="837b8-119">如果不存在要还原的数据库，则用户必须有 CREATE DATABASE 权限才能执行 RESTORE。</span><span class="sxs-lookup"><span data-stu-id="837b8-119">If the database being restored does not exist, the user must have CREATE DATABASE permissions to be able to execute RESTORE.</span></span> <span data-ttu-id="837b8-120">如果数据库存在，则 RESTORE 权限默认授予 **sysadmin** 和 **dbcreator** 固定服务器角色成员以及数据库的所有者 (**dbo**)（对于 FROM DATABASE_SNAPSHOT 选项，数据库始终存在）。</span><span class="sxs-lookup"><span data-stu-id="837b8-120">If the database exists, RESTORE permissions default to members of the **sysadmin** and **dbcreator** fixed server roles and the owner (**dbo**) of the database (for the FROM DATABASE_SNAPSHOT option, the database always exists).</span></span>  
  
 <span data-ttu-id="837b8-121">RESTORE 权限被授予那些成员身份信息始终可由服务器使用的角色。</span><span class="sxs-lookup"><span data-stu-id="837b8-121">RESTORE permissions are given to roles in which membership information is always readily available to the server.</span></span> <span data-ttu-id="837b8-122">因为只有在固定数据库可以访问且没有损坏时（在执行 RESTORE 时并不会总是这样）才能检查固定数据库角色成员身份，所以 **db_owner** 固定数据库角色成员没有 RESTORE 权限。</span><span class="sxs-lookup"><span data-stu-id="837b8-122">Because fixed database role membership can be checked only when the database is accessible and undamaged, which is not always the case when RESTORE is executed, members of the **db_owner** fixed database role do not have RESTORE permissions.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="837b8-123">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="837b8-123">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="837b8-124">**将数据库还原到时间点**</span><span class="sxs-lookup"><span data-stu-id="837b8-124">**To restore a database to a point in time**</span></span>  
  
1.  <span data-ttu-id="837b8-125">在“对象资源管理器”中，连接到相应的 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]实例，然后展开服务器树。</span><span class="sxs-lookup"><span data-stu-id="837b8-125">In Object Explorer, connect to the appropriate instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="837b8-126">展开 **“数据库”** 。</span><span class="sxs-lookup"><span data-stu-id="837b8-126">Expand **Databases**.</span></span> <span data-ttu-id="837b8-127"> 根据具体的数据库，选择一个用户数据库，或展开“系统数据库”并选择一个系统数据库。</span><span class="sxs-lookup"><span data-stu-id="837b8-127">Depending on the database, either select a user database or expand **System Databases**, and then select a system database.</span></span>  
  
3.  <span data-ttu-id="837b8-128">右键单击数据库，指向“任务”  ，再指向“还原”  ，然后单击“数据库”  。</span><span class="sxs-lookup"><span data-stu-id="837b8-128">Right-click the database, point to **Tasks**, point to **Restore**, and then click **Database**.</span></span>  
  
4.  <span data-ttu-id="837b8-129">在 **“常规”** 页上，使用 **“源”** 部分指定要还原的备份集的源和位置。</span><span class="sxs-lookup"><span data-stu-id="837b8-129">On the **General** page, use the **Source** section to specify the source and location of the backup sets to restore.</span></span> <span data-ttu-id="837b8-130">选择以下选项之一：</span><span class="sxs-lookup"><span data-stu-id="837b8-130">Select one of the following options:</span></span>  
  
    -   <span data-ttu-id="837b8-131">**Database**</span><span class="sxs-lookup"><span data-stu-id="837b8-131">**Database**</span></span>  
  
         <span data-ttu-id="837b8-132">从下拉列表中选择要还原的数据库。</span><span class="sxs-lookup"><span data-stu-id="837b8-132">Select the database to restore from the drop-down list.</span></span> <span data-ttu-id="837b8-133">此列表仅包含已根据 **msdb** 备份历史记录进行备份的数据库。</span><span class="sxs-lookup"><span data-stu-id="837b8-133">The list contains only databases that have been backed up according to the **msdb** backup history.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="837b8-134">如果备份是从另一台服务器执行的，则目标服务器不具有指定数据库的备份历史记录信息。</span><span class="sxs-lookup"><span data-stu-id="837b8-134">If the backup is taken from a different server, the destination server will not have the backup history information for the specified database.</span></span> <span data-ttu-id="837b8-135">这种情况下，请选择 **“设备”** 以手动指定要还原的文件或设备。</span><span class="sxs-lookup"><span data-stu-id="837b8-135">In this case, select **Device** to manually specify the file or device to restore.</span></span>  
  
    -   <span data-ttu-id="837b8-136">**设备**</span><span class="sxs-lookup"><span data-stu-id="837b8-136">**Device**</span></span>  
  
         <span data-ttu-id="837b8-137">单击“浏览”按钮 ( **...** ) 以打开“选择备份设备”  对话框。</span><span class="sxs-lookup"><span data-stu-id="837b8-137">Click the browse (**...**) button to open the **Select backup devices** dialog box.</span></span> <span data-ttu-id="837b8-138">在 **“备份介质类型”** 框中，从列出的设备类型中选择一种。</span><span class="sxs-lookup"><span data-stu-id="837b8-138">In the **Backup media type** box, select one of the listed device types.</span></span> <span data-ttu-id="837b8-139">若要为 **“备份介质”** 框选择一个或多个设备，请单击 **“添加”** 。</span><span class="sxs-lookup"><span data-stu-id="837b8-139">To select one or more devices for the **Backup media** box, click **Add**.</span></span>  
  
         <span data-ttu-id="837b8-140">将所需设备添加到 **“备份介质”** 列表框后，单击 **“确定”** 返回到 **“常规”** 页。</span><span class="sxs-lookup"><span data-stu-id="837b8-140">After you add the devices you want to the **Backup media** list box, click **OK** to return to the **General** page.</span></span>  
  
         <span data-ttu-id="837b8-141">在 **“源: 设备: 数据库”** 列表框中，选择应还原的数据库名称。</span><span class="sxs-lookup"><span data-stu-id="837b8-141">In the **Source: Device: Database** list box, select the name of the database which should be restored.</span></span>  
  
         <span data-ttu-id="837b8-142">**注意** ：此列表仅在选择了 **“设备”** 时才可用。</span><span class="sxs-lookup"><span data-stu-id="837b8-142">**Note** This list is only available when **Device** is selected.</span></span> <span data-ttu-id="837b8-143">只有在所选设备上具有备份的数据库才可用。</span><span class="sxs-lookup"><span data-stu-id="837b8-143">Only databases that have backups on the selected device will be available.</span></span>  
  
5.  <span data-ttu-id="837b8-144">在 **“目标”** 部分中， **“数据库”** 框自动填充要还原的数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="837b8-144">In the **Destination** section, the **Database** box is automatically populated with the name of the database to be restored.</span></span> <span data-ttu-id="837b8-145">若要更改数据库名称，请在 **“数据库”** 框中输入新名称。</span><span class="sxs-lookup"><span data-stu-id="837b8-145">To change the name of the database, enter the new name in the **Database** box.</span></span>  
  
6.  <span data-ttu-id="837b8-146">单击 **“时间线”** 以访问 **“备份时间线”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="837b8-146">Click **Timeline** to access the **Backup Timeline** dialog box.</span></span>  
  
7.  <span data-ttu-id="837b8-147">在 **“还原到”** 部分中，单击 **“具体日期和时间”** 。</span><span class="sxs-lookup"><span data-stu-id="837b8-147">In the **Restore to** section, click **Specific date and time**.</span></span>  
  
8.  <span data-ttu-id="837b8-148">使用 **“日期”** 和 **“时间”** 框或滑动条来指定应停止还原的具体日期和时间。</span><span class="sxs-lookup"><span data-stu-id="837b8-148">Use either the **Date** and **Time** boxes or the slider bar to specify a specific date and time to where the restore should stop.</span></span> [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
    > [!NOTE]  
    >  <span data-ttu-id="837b8-149">使用“时间线间隔”  框更改时间线上显示的时间量。</span><span class="sxs-lookup"><span data-stu-id="837b8-149">Use the **Timeline Interval** box to change the amount of time displayed on the timeline.</span></span>  
  
9. <span data-ttu-id="837b8-150">指定具体时点后，数据库恢复顾问确保只有需要还原到该时点的那些备份在 **“要还原的备份集”** 网格的 **“还原”** 列中处于选中状态。</span><span class="sxs-lookup"><span data-stu-id="837b8-150">After you have specified a specific point in time, the Database Recovery Advisor ensures that only backups that are required for restoring to that point in time are selected in the **Restore** column of the **Backup sets to restore** grid.</span></span> <span data-ttu-id="837b8-151">这些选定的备份构成了为您的时点还原建议的还原计划。</span><span class="sxs-lookup"><span data-stu-id="837b8-151">These selected backups make up the recommended restore plan for your point-in-time restore.</span></span> <span data-ttu-id="837b8-152">应当仅使用选定的备份进行时点还原操作。</span><span class="sxs-lookup"><span data-stu-id="837b8-152">You should use only the selected backups for your point-in-time restore operation.</span></span>  
  
     <span data-ttu-id="837b8-153">有关“用于还原的备份集”  网格中的列的信息，请参阅[还原数据库（“常规”页）](../../integration-services/general-page-of-integration-services-designers-options.md)。</span><span class="sxs-lookup"><span data-stu-id="837b8-153">For information about the columns in the **Backup sets to restore** grid, see [Restore Database &#40;General Page&#41;](../../integration-services/general-page-of-integration-services-designers-options.md).</span></span> <span data-ttu-id="837b8-154">有关数据库恢复顾问的信息，请参阅[还原和恢复概述 (SQL Server)](restore-and-recovery-overview-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="837b8-154">For information about the Database Recovery Advisor, see [Restore and Recovery Overview &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md).</span></span>  
  
10. <span data-ttu-id="837b8-155">在 **“选项”** 页的 **“还原选项”** 面板中，可以根据您的实际情况选择下列任意选项：</span><span class="sxs-lookup"><span data-stu-id="837b8-155">On the **Options** page, in the **Restore options** panel, you can select any of the following options, if appropriate for your situation:</span></span>  
  
    -   <span data-ttu-id="837b8-156">**覆盖现有数据库(WITH REPLACE)**</span><span class="sxs-lookup"><span data-stu-id="837b8-156">**Overwrite the existing database (WITH REPLACE)**</span></span>  
  
    -   <span data-ttu-id="837b8-157">**保留复制设置(WITH KEEP_REPLICATION)**</span><span class="sxs-lookup"><span data-stu-id="837b8-157">**Preserve the replication settings (WITH KEEP_REPLICATION)**</span></span>  
  
    -   <span data-ttu-id="837b8-158">**限制对还原数据库的访问(WITH RESTRICTED_USER)**</span><span class="sxs-lookup"><span data-stu-id="837b8-158">**Restrict access to the restored database (WITH RESTRICTED_USER)**</span></span>  
  
     <span data-ttu-id="837b8-159">有关这些选项的详细信息，请参阅[还原数据库（“选项”页）](restore-database-options-page.md)。</span><span class="sxs-lookup"><span data-stu-id="837b8-159">For more information about these options, see [Restore Database &#40;Options Page&#41;](restore-database-options-page.md).</span></span>  
  
11. <span data-ttu-id="837b8-160">为 **“恢复状态”** 框选择一个选项。</span><span class="sxs-lookup"><span data-stu-id="837b8-160">Select an option for the **Recovery state** box.</span></span> <span data-ttu-id="837b8-161">此框确定还原操作之后的数据库状态。</span><span class="sxs-lookup"><span data-stu-id="837b8-161">This box determines the state of the database after the restore operation.</span></span>  
  
    -   <span data-ttu-id="837b8-162">**RESTORE WITH RECOVERY** 是默认行为，它通过回滚未提交的事务，使数据库处于可以使用的状态。</span><span class="sxs-lookup"><span data-stu-id="837b8-162">**RESTORE WITH RECOVERY** is the default behavior which leaves the database ready for use by rolling back the uncommitted transactions.</span></span> <span data-ttu-id="837b8-163">无法还原其他事务日志。</span><span class="sxs-lookup"><span data-stu-id="837b8-163">Additional transaction logs cannot be restored.</span></span> <span data-ttu-id="837b8-164">如果您要立即还原所有必要的备份，则选择此选项。</span><span class="sxs-lookup"><span data-stu-id="837b8-164">Select this option if you are restoring all of the necessary backups now.</span></span>  
  
    -   <span data-ttu-id="837b8-165">**RESTORE WITH NORECOVERY** 不对数据库执行任何操作，不回滚未提交的事务。</span><span class="sxs-lookup"><span data-stu-id="837b8-165">**RESTORE WITH NORECOVERY** which leaves the database non-operational, and does not roll back the uncommitted transactions.</span></span> <span data-ttu-id="837b8-166">可以还原其他事务日志。</span><span class="sxs-lookup"><span data-stu-id="837b8-166">Additional transaction logs can be restored.</span></span> <span data-ttu-id="837b8-167">除非恢复数据库，否则无法使用数据库。</span><span class="sxs-lookup"><span data-stu-id="837b8-167">The database cannot be used until it is recovered.</span></span>  
  
    -   <span data-ttu-id="837b8-168">**RESTORE WITH STANDBY** 使数据库处于只读模式。</span><span class="sxs-lookup"><span data-stu-id="837b8-168">**RESTORE WITH STANDBY** which leaves the database in read-only mode.</span></span> <span data-ttu-id="837b8-169">它撤消未提交的事务，但将撤消操作保存在备用文件中，以便能够还原恢复结果。</span><span class="sxs-lookup"><span data-stu-id="837b8-169">It undoes uncommitted transactions, but saves the undo actions in a standby file so that recovery effects can be reverted.</span></span>  
  
     <span data-ttu-id="837b8-170">有关这些选项的说明，请参阅[还原数据库（“选项”页）](restore-database-options-page.md)。</span><span class="sxs-lookup"><span data-stu-id="837b8-170">For descriptions of the options, see [Restore Database &#40;Options Page&#41;](restore-database-options-page.md).</span></span>  
  
12. <span data-ttu-id="837b8-171">如果对于选择的时间点是必需的，则选择“还原前进行结尾日志备份”  。</span><span class="sxs-lookup"><span data-stu-id="837b8-171">**Take tail-log backup before restore** will be selected if it is necessary for the point in time that you have selected.</span></span> <span data-ttu-id="837b8-172">无需修改此设置，但可以选择备份日志尾部（即使不需要）。</span><span class="sxs-lookup"><span data-stu-id="837b8-172">You do not need to modify this setting, but you can choose to backup the tail of the log even if it is not required.</span></span>  
  
13. <span data-ttu-id="837b8-173">如果存在与数据库的活动连接，则还原操作可能会失败。</span><span class="sxs-lookup"><span data-stu-id="837b8-173">Restore operations may fail if there are active connections to the database.</span></span> <span data-ttu-id="837b8-174">选中 **“关闭现有连接”** 以确保关闭 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 和数据库之间的所有活动连接。</span><span class="sxs-lookup"><span data-stu-id="837b8-174">Check the **Close existing connections option** to ensure that all active connections between [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] and the database are closed.</span></span> <span data-ttu-id="837b8-175">此复选框可在执行还原操作之前将数据库设置为单用户模式，并在该操作完成后将数据库设置为多用户模式。</span><span class="sxs-lookup"><span data-stu-id="837b8-175">This check box sets the database to single user mode before performing the restore operations, and sets the database to multi-user mode when complete.</span></span>  
  
14. <span data-ttu-id="837b8-176">如果要在每个还原操作之间进行提示，请选择 **“还原每个备份之前进行提示”** 。</span><span class="sxs-lookup"><span data-stu-id="837b8-176">Select **Prompt before restoring each backup** if you wish to be prompted between each restore operation.</span></span> <span data-ttu-id="837b8-177">除非数据库过大并且您要监视还原操作的状态，否则通常没有必要选中该选项。</span><span class="sxs-lookup"><span data-stu-id="837b8-177">This is not usually necessary unless the database is large and you wish to monitor the status of the restore operation.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="837b8-178">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="837b8-178">Using Transact-SQL</span></span>  
 <span data-ttu-id="837b8-179">**开始之前**</span><span class="sxs-lookup"><span data-stu-id="837b8-179">**Before you begin**</span></span>  
  
 <span data-ttu-id="837b8-180">始终从日志备份还原到指定时间。</span><span class="sxs-lookup"><span data-stu-id="837b8-180">A specified time is always restored from a log backup.</span></span> <span data-ttu-id="837b8-181">在还原序列的每个 RESTORE LOG 语句中，必须在相同的 STOPAT 子句中指定目标时间或事务。</span><span class="sxs-lookup"><span data-stu-id="837b8-181">In every RESTORE LOG statement of the restore sequence, you must specify your target time or transaction in an identical STOPAT clause.</span></span> <span data-ttu-id="837b8-182">作为时点还原的先决条件，必须首先还原其端点早于目标还原时间的完整数据库备份。</span><span class="sxs-lookup"><span data-stu-id="837b8-182">As a prerequisite to a point-in-time restore, you must first restore a full database backup whose end point is earlier than your target restore time.</span></span> <span data-ttu-id="837b8-183">只要您之后还原每个随后日志备份（到达和包括包含目标时间点的日志备份），该完整数据库备份就可以早于最近的完整数据库备份。</span><span class="sxs-lookup"><span data-stu-id="837b8-183">That full database backup can be older than the most recent full database backup as long as you then restore every subsequent log backup, up to and including the log backup that contains your target point in time.</span></span>  
  
 <span data-ttu-id="837b8-184">如果数据备份太临近指定的目标时间，而需帮助识别要还原哪个数据库备份，则可以在 RESTORE DATABASE 语句中可选地指定 WITH STOPAT 子句以引发错误。</span><span class="sxs-lookup"><span data-stu-id="837b8-184">To help you identify which database backup to restore, you can optionally specify your WITH STOPAT clause in your RESTORE DATABASE statement to raise an error if a data backup is too recent for the specified target time.</span></span> <span data-ttu-id="837b8-185">始终会还原完整数据备份，即使该数据备份包含目标时间也同样如此。</span><span class="sxs-lookup"><span data-stu-id="837b8-185">The complete data backup is always restored, even if it contains the target time.</span></span>  
  
 <span data-ttu-id="837b8-186">**基本 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语法**</span><span class="sxs-lookup"><span data-stu-id="837b8-186">**Basic [!INCLUDE[tsql](../../includes/tsql-md.md)] syntax**</span></span>  
  
 <span data-ttu-id="837b8-187">还原日志*database_name*的 <backup_device> 与 STOPAT \*\* = *`time`* 、\*\* RECOVERY .。。</span><span class="sxs-lookup"><span data-stu-id="837b8-187">RESTORE LOG *database_name* FROM <backup_device> WITH STOPAT **=*`time`*,** RECOVERY...</span></span>  
  
 <span data-ttu-id="837b8-188">恢复点是在 time 指定的值或之前发生的最新的事务提交 `datetime` 。 *time*</span><span class="sxs-lookup"><span data-stu-id="837b8-188">The recovery point is the latest transaction commit that occurred at or before the `datetime` value that is specified by *time*.</span></span>  
  
 <span data-ttu-id="837b8-189">要只还原在特定时间点之前所做的修改，请为还原的每个备份指定 WITH STOPAT  **time=**  。</span><span class="sxs-lookup"><span data-stu-id="837b8-189">To restore only the modifications that were made before a specific point in time, specify WITH STOPAT **=** *time* for each backup you restore.</span></span> <span data-ttu-id="837b8-190">这样确保了不会超出目标时间。</span><span class="sxs-lookup"><span data-stu-id="837b8-190">This makes sure that you do not go past the target time.</span></span>  
  
 <span data-ttu-id="837b8-191">**将数据库还原到时间点**</span><span class="sxs-lookup"><span data-stu-id="837b8-191">**To restore a database to a point in time**</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="837b8-192">有关此过程的示例，请参阅本节后面的 [示例 (Transact-SQL)](#TsqlExample)。</span><span class="sxs-lookup"><span data-stu-id="837b8-192">For an example of this procedure, see [Example (Transact-SQL)](#TsqlExample), later in this section.</span></span>  
  
1.  <span data-ttu-id="837b8-193">连接到您要还原数据库的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="837b8-193">Connect to server instance on which you want to restore the database.</span></span>  
  
2.  <span data-ttu-id="837b8-194">执行使用 NORECOVERY 选项的 RESTORE DATABASE 语句。</span><span class="sxs-lookup"><span data-stu-id="837b8-194">Execute the RESTORE DATABASE statement using the NORECOVERY option.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="837b8-195">如果部分还原顺序不包括任何 [FILESTREAM](../blob/filestream-sql-server.md) 文件组，则不支持时间点还原。</span><span class="sxs-lookup"><span data-stu-id="837b8-195">If a partial restore sequence excludes any [FILESTREAM](../blob/filestream-sql-server.md) filegroup, point-in-time restore is not supported.</span></span> <span data-ttu-id="837b8-196">可以强制该还原顺序以继续执行操作。</span><span class="sxs-lookup"><span data-stu-id="837b8-196">You can force the restore sequence to continue.</span></span> <span data-ttu-id="837b8-197">但在 RESTORE 语句中省略的 FILESTREAM 文件组将永远无法还原。</span><span class="sxs-lookup"><span data-stu-id="837b8-197">However the FILESTREAM filegroups that are omitted from your RESTORE statement can never be restored.</span></span> <span data-ttu-id="837b8-198">若要强制执行时点还原，请指定 CONTINUE_AFTER_ERROR 选项以及 STOPAT、STOPATMARK 或 STOPBEFOREMARK 选项，还必须在随后的 RESTORE LOG 语句中指定后面的三个选项。</span><span class="sxs-lookup"><span data-stu-id="837b8-198">To force a point-in-time restore, specify the CONTINUE_AFTER_ERROR option together with the STOPAT, STOPATMARK, or STOPBEFOREMARK option, which you must also specify in your subsequent RESTORE LOG statements.</span></span> <span data-ttu-id="837b8-199">如果指定 CONTINUE_AFTER_ERROR，则部分还原顺序将成功，但 FILESTREAM 文件组将不可恢复。</span><span class="sxs-lookup"><span data-stu-id="837b8-199">If you specify CONTINUE_AFTER_ERROR, the partial restore sequence succeeds and the FILESTREAM filegroup becomes unrecoverable.</span></span>  
  
3.  <span data-ttu-id="837b8-200">还原上次差异数据库备份（如果有），而不恢复数据库 (RESTORE DATABASE *database_name* FROM *backup_device* WITH NORECOVERY)。</span><span class="sxs-lookup"><span data-stu-id="837b8-200">Restore the last differential database backup, if any,  without recovering the database (RESTORE DATABASE *database_name* FROM *backup_device* WITH NORECOVERY).</span></span>  
  
4.  <span data-ttu-id="837b8-201">按照创建事务日志备份的相同顺序应用每个事务日志备份，同时指定要停止还原日志的时间 (RESTORE DATABASE *database_name*从 <backup_device>，使用 STOPAT\*\* = *`time`* ，\*\* 恢复) 。</span><span class="sxs-lookup"><span data-stu-id="837b8-201">Apply each transaction log backup in the same sequence in which they were created, specifying the time at which you intend to stop restoring log (RESTORE DATABASE *database_name* FROM <backup_device> WITH STOPAT**=*`time`*,** RECOVERY).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="837b8-202">RECOVERY 和 STOPAT 选项。</span><span class="sxs-lookup"><span data-stu-id="837b8-202">The RECOVERY and STOPAT options.</span></span> <span data-ttu-id="837b8-203">如果事务日志备份不包含要求的时间（例如，如果指定的时间超出了事务日志所包含的时间范围），则会生成警告，并且不会恢复数据库。</span><span class="sxs-lookup"><span data-stu-id="837b8-203">If the transaction log backup does not contain the requested time (for example, if the time specified is beyond the end of the time covered by the transaction log), a warning is generated and the database remains unrecovered.</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="837b8-204">示例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="837b8-204">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="837b8-205">下面的示例将数据库还原到它在 `12:00 AM` 的 `April 15, 2020` 的状态，并显示涉及多个日志备份的还原操作。</span><span class="sxs-lookup"><span data-stu-id="837b8-205">The following example restores a database to its state as of `12:00 AM` on `April 15, 2020` and shows a restore operation that involves multiple log backups.</span></span> <span data-ttu-id="837b8-206">在备份设备上，要还原的完整数据库备份 `AdventureWorksBackups`是设备上的第三个备份集 (`FILE = 3`)，第一个日志备份是第四个备份集 (`FILE = 4`)，第二个日志备份是第五个备份集 (`FILE = 5`)。</span><span class="sxs-lookup"><span data-stu-id="837b8-206">On the backup device, `AdventureWorksBackups`, the full database backup to be restored is the third backup set on the device (`FILE = 3`), the first log backup is the fourth backup set (`FILE = 4`), and the second log backup is the fifth backup set (`FILE = 5`).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="837b8-207">[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 数据库使用简单恢复模式。</span><span class="sxs-lookup"><span data-stu-id="837b8-207">The [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database uses the simple recovery model.</span></span> <span data-ttu-id="837b8-208">若要允许日志备份，请在完整备份数据库之前，使用 `ALTER DATABASE AdventureWorks SET RECOVERY FULL`将数据库设置为使用完整恢复模式。</span><span class="sxs-lookup"><span data-stu-id="837b8-208">To permit log backups, before taking a full database backup, the database was set to use the full recovery model, using `ALTER DATABASE AdventureWorks SET RECOVERY FULL`.</span></span>  
  
```  
RESTORE DATABASE AdventureWorks  
   FROM AdventureWorksBackups  
   WITH FILE=3, NORECOVERY;  
  
RESTORE LOG AdventureWorks  
   FROM AdventureWorksBackups  
   WITH FILE=4, NORECOVERY, STOPAT = 'Apr 15, 2020 12:00 AM';  
  
RESTORE LOG AdventureWorks  
   FROM AdventureWorksBackups  
   WITH FILE=5, NORECOVERY, STOPAT = 'Apr 15, 2020 12:00 AM';  
RESTORE DATABASE AdventureWorks WITH RECOVERY;   
GO  
  
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="837b8-209">相关任务</span><span class="sxs-lookup"><span data-stu-id="837b8-209">Related Tasks</span></span>  
  
-   [<span data-ttu-id="837b8-210">还原数据库备份 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="837b8-210">Restore a Database Backup &#40;SQL Server Management Studio&#41;</span></span>](restore-a-database-backup-using-ssms.md)  
  
-   [<span data-ttu-id="837b8-211">备份事务日志 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="837b8-211">Back Up a Transaction Log &#40;SQL Server&#41;</span></span>](back-up-a-transaction-log-sql-server.md)  
  
-   [<span data-ttu-id="837b8-212">在完整恢复模式下将数据库还原到故障点 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="837b8-212">Restore a Database to the Point of Failure Under the Full Recovery Model &#40;Transact-SQL&#41;</span></span>](restore-database-to-point-of-failure-full-recovery.md)  
  
-   [<span data-ttu-id="837b8-213">将数据库还原到标记的事务 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="837b8-213">Restore a Database to a Marked Transaction &#40;SQL Server Management Studio&#41;</span></span>](restore-a-database-to-a-marked-transaction-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="837b8-214">恢复到日志序列号 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="837b8-214">Recover to a Log Sequence Number &#40;SQL Server&#41;</span></span>](recover-to-a-log-sequence-number-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="837b8-215">另请参阅</span><span class="sxs-lookup"><span data-stu-id="837b8-215">See Also</span></span>  
 <span data-ttu-id="837b8-216">[backupset (Transact-SQL)](/sql/relational-databases/system-tables/backupset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="837b8-216">[backupset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql) </span></span>  
 <span data-ttu-id="837b8-217">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="837b8-217">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 [<span data-ttu-id="837b8-218">RESTORE HEADERONLY (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="837b8-218">RESTORE HEADERONLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-headeronly-transact-sql)  
  
  
