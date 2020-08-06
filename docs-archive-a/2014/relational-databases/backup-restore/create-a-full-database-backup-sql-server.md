---
title: 创建完整数据库备份 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- backing up databases [SQL Server], full backups
- backing up databases [SQL Server], SQL Server Management Studio
- backups [SQL Server], creating
- database backups [SQL Server], SQL Server Management Studio
ms.assetid: 586561fc-dfbb-4842-84f8-204a9100a534
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f406464680a1669133dc87bdfb231c644d33fbdb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693386"
---
# <a name="create-a-full-database-backup-sql-server"></a><span data-ttu-id="817b7-102">创建完整数据库备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="817b7-102">Create a Full Database Backup (SQL Server)</span></span>
  <span data-ttu-id="817b7-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]或 PowerShell 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中创建完整数据库备份。</span><span class="sxs-lookup"><span data-stu-id="817b7-103">This topic describes how to create a full database backup in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or PowerShell.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="817b7-104">有关 SQL Server 备份到 Azure Blob 存储服务的信息，请参阅[SQL Server 通过 Azure Blob 存储服务进行备份和还原](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)。</span><span class="sxs-lookup"><span data-stu-id="817b7-104">For information on SQL Server backup to the Azure Blob storage service, see, [SQL Server Backup and Restore with Azure Blob Storage Service](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md).</span></span>  
  
 <span data-ttu-id="817b7-105">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="817b7-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="817b7-106">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="817b7-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="817b7-107">限制和局限</span><span class="sxs-lookup"><span data-stu-id="817b7-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="817b7-108">建议</span><span class="sxs-lookup"><span data-stu-id="817b7-108">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="817b7-109">安全性</span><span class="sxs-lookup"><span data-stu-id="817b7-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="817b7-110">**若要创建完整数据库备份，请使用：**</span><span class="sxs-lookup"><span data-stu-id="817b7-110">**To create a full database backup, using:**</span></span>  
  
     [<span data-ttu-id="817b7-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="817b7-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="817b7-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="817b7-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="817b7-113">PowerShell</span><span class="sxs-lookup"><span data-stu-id="817b7-113">PowerShell</span></span>](#PowerShellProcedure)  
  
-   [<span data-ttu-id="817b7-114">相关任务</span><span class="sxs-lookup"><span data-stu-id="817b7-114">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="817b7-115">开始之前</span><span class="sxs-lookup"><span data-stu-id="817b7-115">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="817b7-116">限制和局限</span><span class="sxs-lookup"><span data-stu-id="817b7-116">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="817b7-117">不允许在显式或隐式事务中使用 BACKUP 语句。</span><span class="sxs-lookup"><span data-stu-id="817b7-117">The BACKUP statement is not allowed in an explicit or implicit transaction.</span></span>  
  
-   <span data-ttu-id="817b7-118">无法在早期版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中还原较新版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]创建的备份。</span><span class="sxs-lookup"><span data-stu-id="817b7-118">Backups that are created by more recent version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cannot be restored in earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="817b7-119">有关详细信息，请参阅 [备份概述 (SQL Server)](backup-overview-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="817b7-119">For more information, see [Backup Overview &#40;SQL Server&#41;](backup-overview-sql-server.md).</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="817b7-120">建议</span><span class="sxs-lookup"><span data-stu-id="817b7-120">Recommendations</span></span>  
  
-   <span data-ttu-id="817b7-121">随着数据库不断增大，完整备份需花费更多时间才能完成，并且需要更多的存储空间。</span><span class="sxs-lookup"><span data-stu-id="817b7-121">As a database increases in size full database backups take more time to finish and require more storage space.</span></span> <span data-ttu-id="817b7-122">因此，对于大型数据库而言，您可以用一系列“差异数据库备份”  来补充完整数据库备份。</span><span class="sxs-lookup"><span data-stu-id="817b7-122">Therefore, for a large database, you might want to supplement a full database backup with a series of *differential database backups*.</span></span> <span data-ttu-id="817b7-123">有关详细信息，请参阅 [差异备份 (SQL Server)](differential-backups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="817b7-123">For more information, see [Differential Backups &#40;SQL Server&#41;](differential-backups-sql-server.md).</span></span>  
  
-   <span data-ttu-id="817b7-124">你可以使用 [sp_spaceused](/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql) 系统存储过程估计完整数据库备份的大小。</span><span class="sxs-lookup"><span data-stu-id="817b7-124">You can estimate the size of a full database backup by using the [sp_spaceused](/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql) system stored procedure.</span></span>  
  
-   <span data-ttu-id="817b7-125">默认情况下，每个成功的备份操作都会在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误日志和系统事件日志中添加一个条目。</span><span class="sxs-lookup"><span data-stu-id="817b7-125">By default, every successful backup operation adds an entry in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log and in the system event log.</span></span> <span data-ttu-id="817b7-126">如果非常频繁地备份日志，这些成功消息会迅速累积，从而产生一个巨大的错误日志，这样会使查找其他消息变得非常困难。</span><span class="sxs-lookup"><span data-stu-id="817b7-126">If back up the log very frequently, these success messages accumulate quickly, resulting in huge error logs that can make finding other messages difficult.</span></span> <span data-ttu-id="817b7-127">在这些情况下，如果任何脚本均不依赖于这些日志条目，则可以使用跟踪标志 3226 取消这些条目。</span><span class="sxs-lookup"><span data-stu-id="817b7-127">In such cases you can suppress these log entries by using trace flag 3226 if none of your scripts depend on those entries.</span></span> <span data-ttu-id="817b7-128">有关详细信息，请参阅[跟踪标志 (Transact-SQL)](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="817b7-128">For more information, see [Trace Flags &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="817b7-129">Security</span><span class="sxs-lookup"><span data-stu-id="817b7-129">Security</span></span>  
 <span data-ttu-id="817b7-130">针对数据库备份，TRUSTWORTHY 设置为 OFF。</span><span class="sxs-lookup"><span data-stu-id="817b7-130">TRUSTWORTHY is set to OFF on a database backup.</span></span> <span data-ttu-id="817b7-131">有关如何将 TRUSTWORTHY 设置为 ON 的详细信息，请参阅 [ALTER DATABASE SET 选项 (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql-set-options)。</span><span class="sxs-lookup"><span data-stu-id="817b7-131">For information about how to set TRUSTWORTHY to ON, see [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options).</span></span>  
  
 <span data-ttu-id="817b7-132">从 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 开始，`PASSWORD` 和 `MEDIAPASSWORD` 选项不可再用于创建备份；</span><span class="sxs-lookup"><span data-stu-id="817b7-132">Beginning with [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] the `PASSWORD` and `MEDIAPASSWORD` options are discontinued for creating backups.</span></span> <span data-ttu-id="817b7-133">不过，您仍可以还原使用密码创建的备份。</span><span class="sxs-lookup"><span data-stu-id="817b7-133">You can still restore backups created with passwords.</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="817b7-134">权限</span><span class="sxs-lookup"><span data-stu-id="817b7-134">Permissions</span></span>  
 <span data-ttu-id="817b7-135">默认情况下，为 **sysadmin** 固定服务器角色以及 **db_owner** 和 **db_backupoperator** 固定数据库角色的成员授予 BACKUP DATABASE 和 BACKUP LOG 权限。</span><span class="sxs-lookup"><span data-stu-id="817b7-135">BACKUP DATABASE and BACKUP LOG permissions default to members of the **sysadmin** fixed server role and the **db_owner** and **db_backupoperator** fixed database roles.</span></span>  
  
 <span data-ttu-id="817b7-136">备份设备的物理文件的所有权和权限问题可能会妨碍备份操作。</span><span class="sxs-lookup"><span data-stu-id="817b7-136">Ownership and permission problems on the backup device's physical file can interfere with a backup operation.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="817b7-137">必须能够读取和写入设备；运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务的帐户必须具有写入权限。</span><span class="sxs-lookup"><span data-stu-id="817b7-137">must be able to read and write to the device; the account under which the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service runs must have write permissions.</span></span> <span data-ttu-id="817b7-138">但是，用于在系统表中为备份设备添加项目的 [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql)不检查文件访问权限。</span><span class="sxs-lookup"><span data-stu-id="817b7-138">However, [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql), which adds an entry for a backup device in the system tables, does not check file access permissions.</span></span> <span data-ttu-id="817b7-139">备份设备物理文件的这些问题可能直到为备份或还原而访问物理资源时才会出现。</span><span class="sxs-lookup"><span data-stu-id="817b7-139">Such problems on the backup device's physical file may not appear until the physical resource is accessed when the backup or restore is attempted.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="817b7-140">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="817b7-140">Using SQL Server Management Studio</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="817b7-141">使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 指定备份任务时，可以通过单击“脚本”\*\*\*\* 按钮并选择脚本目标生成相应的 [!INCLUDE[tsql](../../includes/tsql-md.md)] [BACKUP](/sql/t-sql/statements/backup-transact-sql) 脚本。</span><span class="sxs-lookup"><span data-stu-id="817b7-141">When you specify a back up task by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], you can generate the corresponding [!INCLUDE[tsql](../../includes/tsql-md.md)] [BACKUP](/sql/t-sql/statements/backup-transact-sql) script by clicking the **Script** button and selecting a script destination.</span></span>  
  
#### <a name="to-back-up-a-database"></a><span data-ttu-id="817b7-142">备份数据库</span><span class="sxs-lookup"><span data-stu-id="817b7-142">To back up a database</span></span>  
  
1.  <span data-ttu-id="817b7-143">连接到相应的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 实例之后，在“对象资源管理器”中，单击服务器名称以展开服务器树。</span><span class="sxs-lookup"><span data-stu-id="817b7-143">After connecting to the appropriate instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="817b7-144">展开 **“数据库”** ，然后根据数据库的不同，选择用户数据库，或展开 **“系统数据库”** ，再选择系统数据库。</span><span class="sxs-lookup"><span data-stu-id="817b7-144">Expand **Databases**, and depending on the database, either select a user database or expand **System Databases** and select a system database.</span></span>  
  
3.  <span data-ttu-id="817b7-145">右键单击数据库，指向 **“任务”** ，再单击 **“备份”** 。</span><span class="sxs-lookup"><span data-stu-id="817b7-145">Right-click the database, point to **Tasks**, and then click **Back Up**.</span></span> <span data-ttu-id="817b7-146">将出现 **“备份数据库”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="817b7-146">The **Back Up Database** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="817b7-147">在 `Database` 列表框中，验证数据库名称。</span><span class="sxs-lookup"><span data-stu-id="817b7-147">In the `Database` list box, verify the database name.</span></span> <span data-ttu-id="817b7-148">您也可以从列表中选择其他数据库。</span><span class="sxs-lookup"><span data-stu-id="817b7-148">You can optionally select a different database from the list.</span></span>  
  
5.  <span data-ttu-id="817b7-149">可以对任意恢复模式（**FULL**、**BULK_LOGGED** 或 **SIMPLE**）执行数据库备份。</span><span class="sxs-lookup"><span data-stu-id="817b7-149">You can perform a database backup for any recovery model (**FULL**, **BULK_LOGGED**, or **SIMPLE**).</span></span>  
  
6.  <span data-ttu-id="817b7-150">在 **“备份类型”** 列表框中，选择 **“完整”**。</span><span class="sxs-lookup"><span data-stu-id="817b7-150">In the **Backup type** list box, select **Full**.</span></span>  
  
     <span data-ttu-id="817b7-151">请注意，创建了完整数据库备份后，可以创建差异数据库备份；有关详细信息，请参阅 [创建差异数据库备份 (SQL Server)](create-a-differential-database-backup-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="817b7-151">Note that after creating a full database backup, you can create a differential database backup; for more information, see [Create a Differential Database Backup &#40;SQL Server&#41;](create-a-differential-database-backup-sql-server.md).</span></span>  
  
7.  <span data-ttu-id="817b7-152">还可以根据需要选择 **“仅复制备份”** 创建仅复制备份。</span><span class="sxs-lookup"><span data-stu-id="817b7-152">Optionally, you can select **Copy Only Backup** to create a copy-only backup.</span></span> <span data-ttu-id="817b7-153">*仅复制备份*是[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]独立于常规备份序列[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的备份。</span><span class="sxs-lookup"><span data-stu-id="817b7-153">A *copy-only backup* is a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup that is independent of the sequence of conventional [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backups.</span></span> <span data-ttu-id="817b7-154">有关详细信息，请参阅[仅复制备份 (SQL Server)](copy-only-backups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="817b7-154">For more information, see [Copy-Only Backups &#40;SQL Server&#41;](copy-only-backups-sql-server.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="817b7-155">选择“差异”  选项时，无法创建仅复制备份。</span><span class="sxs-lookup"><span data-stu-id="817b7-155">When the **Differential** option is selected, you cannot create a copy-only backup.</span></span>  
  
8.  <span data-ttu-id="817b7-156">对于 "**备份组件**"，单击 `Database` 。</span><span class="sxs-lookup"><span data-stu-id="817b7-156">For **Backup component**, click `Database`.</span></span>  
  
9. <span data-ttu-id="817b7-157">可以接受 **“名称”** 文本框中建议的默认备份集名称，也可以为备份集输入其他名称。</span><span class="sxs-lookup"><span data-stu-id="817b7-157">Either accept the default backup set name suggested in the **Name** text box, or enter a different name for the backup set.</span></span>  
  
10. <span data-ttu-id="817b7-158">或者，在 **“说明”** 文本框中，输入备份集的说明。</span><span class="sxs-lookup"><span data-stu-id="817b7-158">Optionally, in the **Description** text box, enter a description of the backup set.</span></span>  
  
11. <span data-ttu-id="817b7-159">通过单击 **“磁盘”**、 **“类型”** 或 **“URL”**，选择备份目标的类型。</span><span class="sxs-lookup"><span data-stu-id="817b7-159">Choose the type of backup destination by clicking **Disk**, **Tape** or **URL**.</span></span> <span data-ttu-id="817b7-160">若要选择包含单个介质集的多个磁盘或磁带机（最多为 64 个）的路径，请单击 **“添加”** 。</span><span class="sxs-lookup"><span data-stu-id="817b7-160">To select the paths of up to 64 disk or tape drives containing a single media set, click **Add**.</span></span> <span data-ttu-id="817b7-161">选择的路径将显示在 **“备份到”** 列表框中。</span><span class="sxs-lookup"><span data-stu-id="817b7-161">The selected paths are displayed in the **Backup to** list box.</span></span>  
  
     <span data-ttu-id="817b7-162">若要删除备份目标，请选择该备份目标并单击 **“删除”** 。</span><span class="sxs-lookup"><span data-stu-id="817b7-162">To remove a backup destination, select it and click **Remove**.</span></span> <span data-ttu-id="817b7-163">若要查看备份目标的内容，请选择该备份目标并单击 **“内容”** 。</span><span class="sxs-lookup"><span data-stu-id="817b7-163">To view the contents of a backup destination, select it and click **Contents**.</span></span>  
  
12. <span data-ttu-id="817b7-164">若要查看或选择介质选项，请在 **“选择页”** 窗格中单击 **“介质选项”** 。</span><span class="sxs-lookup"><span data-stu-id="817b7-164">To view or select the media options, click **Media Options** in the **Select a page** pane.</span></span>  
  
13. <span data-ttu-id="817b7-165">可以通过单击以下选项之一来选择 **“覆盖介质”** 选项：</span><span class="sxs-lookup"><span data-stu-id="817b7-165">Select an **Overwrite Media** option, by clicking one of the following:</span></span>  
  
    -   <span data-ttu-id="817b7-166">**备份到现有介质集**</span><span class="sxs-lookup"><span data-stu-id="817b7-166">**Back up to the existing media set**</span></span>  
  
         <span data-ttu-id="817b7-167">对于此选项，请单击 **“追加到现有备份集”** 或 **“覆盖所有现有备份集”** 。</span><span class="sxs-lookup"><span data-stu-id="817b7-167">For this option, click either **Append to the existing backup set** or **Overwrite all existing backup sets**.</span></span> <span data-ttu-id="817b7-168">有关详细信息，请参阅 [媒体集、媒体簇和备份集 (SQL Server)](media-sets-media-families-and-backup-sets-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="817b7-168">For more information, see [Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md).</span></span>  
  
         <span data-ttu-id="817b7-169">或者选择 **“检查介质集名称和备份集过期时间”** ，以使备份操作对介质集和备份集的过期日期和时间进行验证。</span><span class="sxs-lookup"><span data-stu-id="817b7-169">Optionally, select **Check media set name and backup set expiration** to cause the backup operation to verify the date and time at which the media set and backup set expire.</span></span>  
  
         <span data-ttu-id="817b7-170">或者在 **“介质集名称”** 文本框中输入名称。</span><span class="sxs-lookup"><span data-stu-id="817b7-170">Optionally, enter a name in the **Media set name** text box.</span></span> <span data-ttu-id="817b7-171">如果没有指定名称，将使用空白名称创建介质集。</span><span class="sxs-lookup"><span data-stu-id="817b7-171">If no name is specified, a media set with a blank name is created.</span></span> <span data-ttu-id="817b7-172">如果指定了介质集名称，将检查介质（磁带或磁盘），以确定实际名称是否与此处输入的名称匹配。</span><span class="sxs-lookup"><span data-stu-id="817b7-172">If you specify a media set name, the media (tape or disk) is checked to see whether the actual name matches the name you enter here.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="817b7-173">如果在 **“常规”** 页中选择了 **“URL”** 作为备份目标，则禁用此选项。</span><span class="sxs-lookup"><span data-stu-id="817b7-173">This option is disabled if you selected **URL** as the backup destination in the **General** page.</span></span> <span data-ttu-id="817b7-174">有关详细信息，请参阅[备份数据库（媒体选项页）](back-up-database-media-options-page.md)。</span><span class="sxs-lookup"><span data-stu-id="817b7-174">For more information, see [Back Up Database &#40;Media Options Page&#41;](back-up-database-media-options-page.md)</span></span>  
        >   
        >  <span data-ttu-id="817b7-175">如果要使用加密，则请勿选择此选项。</span><span class="sxs-lookup"><span data-stu-id="817b7-175">If you plan to use encryption, do not select this option.</span></span> <span data-ttu-id="817b7-176">如果选择此选项，则将禁用 **“备份选项”** 页中的加密选项。</span><span class="sxs-lookup"><span data-stu-id="817b7-176">If you select this option, the encryption options in the **Backup Options** page will be disabled.</span></span> <span data-ttu-id="817b7-177">追加到现有备份集时不支持加密。</span><span class="sxs-lookup"><span data-stu-id="817b7-177">Encryption is not supported when appending to the existing backup set.</span></span>  
  
    -   <span data-ttu-id="817b7-178">**备份到新介质集并清除所有现有备份集**</span><span class="sxs-lookup"><span data-stu-id="817b7-178">**Back up to a new media set, and erase all existing backup sets**</span></span>  
  
         <span data-ttu-id="817b7-179">对于该选项，请在 **“新建介质集名称”** 文本框中输入名称，并在 **“新建介质集说明”** 文本框中描述介质集（可选）。</span><span class="sxs-lookup"><span data-stu-id="817b7-179">For this option, enter a name in the **New media set name** text box, and, optionally, describe the media set in the **New media set description** text box.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="817b7-180">如果在 **“常规”** 页中选择了 **“URL”** ，则禁用此选项。</span><span class="sxs-lookup"><span data-stu-id="817b7-180">This option is disabled if you selected **URL** in the **General** page.</span></span> <span data-ttu-id="817b7-181">备份到 Azure 存储时不支持这些操作。</span><span class="sxs-lookup"><span data-stu-id="817b7-181">These actions are not supported when backing up to Azure storage.</span></span>  
  
14. <span data-ttu-id="817b7-182">在 "**可靠性**" 部分中，可以选择检查：</span><span class="sxs-lookup"><span data-stu-id="817b7-182">In the **Reliability** section, optionally check:</span></span>  
  
    -   <span data-ttu-id="817b7-183">**完成后验证备份**。</span><span class="sxs-lookup"><span data-stu-id="817b7-183">**Verify backup when finished**.</span></span>  
  
    -   <span data-ttu-id="817b7-184">**“写入介质前检查校验和”** 和 **“出现校验和错误时继续”** （可选）。</span><span class="sxs-lookup"><span data-stu-id="817b7-184">**Perform checksum before writing to media**, and, optionally, **Continue on checksum error**.</span></span> <span data-ttu-id="817b7-185">有关校验和的信息，请参阅[在备份和还原期间可能的媒体错误 (SQL Server)](possible-media-errors-during-backup-and-restore-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="817b7-185">For information on checksums, see [Possible Media Errors During Backup and Restore &#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md).</span></span>  
  
15. <span data-ttu-id="817b7-186">如果备份到磁带驱动器（如同 **“常规”** 页的 **“目标”** 部分指定的一样），则 **“备份后卸载磁带”** 选项处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="817b7-186">If you are backing up to a tape drive (as specified in the **Destination** section of the **General** page), the **Unload the tape after backup** option is active.</span></span> <span data-ttu-id="817b7-187">单击此选项可以激活 **“卸载前倒带”** 选项。</span><span class="sxs-lookup"><span data-stu-id="817b7-187">Clicking this option activates the **Rewind the tape before unloading** option.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="817b7-188">除非备份的是事务日志（如同“常规”  页的“备份类型”  部分中指定的一样），否则“事务日志”  部分中的选项处于不活动状态。</span><span class="sxs-lookup"><span data-stu-id="817b7-188">The options in the **Transaction log** section are inactive unless you are backing up a transaction log (as specified in the **Backup type** section of the **General** page).</span></span>  
  
16. <span data-ttu-id="817b7-189">若要查看或选择备份选项，请在 **“选择页”** 窗格中单击 **“备份选项”** 。</span><span class="sxs-lookup"><span data-stu-id="817b7-189">To view or select the backup options, click **Backup Options** in the **Select a page** pane.</span></span>  
  
17. <span data-ttu-id="817b7-190">指定备份集何时过期以及何时可以覆盖备份集而不用显式跳过过期数据验证：</span><span class="sxs-lookup"><span data-stu-id="817b7-190">Specify when the backup set will expire and can be overwritten without explicitly skipping verification of the expiration data:</span></span>  
  
    -   <span data-ttu-id="817b7-191">若要使备份集在特定天数后过期，请单击 **“之后”** （默认选项），并输入备份集从创建到过期所需的天数。</span><span class="sxs-lookup"><span data-stu-id="817b7-191">To have the backup set expire after a specific number of days, click **After** (the default option), and enter the number of days after set creation that the set will expire.</span></span> <span data-ttu-id="817b7-192">此值范围为 0 到 99999 天；0 天表示备份集将永不过期。</span><span class="sxs-lookup"><span data-stu-id="817b7-192">This value can be from 0 to 99999 days; a value of 0 days means that the backup set will never expire.</span></span>  
  
         <span data-ttu-id="817b7-193">默认值在 "服务器属性" 对话框的 "**服务器属性**" (对话框的 "\*\*默认备份介质保持期 (天) \*\* " 选项中设置) 的 "数据库设置" 页。</span><span class="sxs-lookup"><span data-stu-id="817b7-193">The default value is set in the **Default backup media retention (in days)** option of the **Server Properties** dialog box (Database Settings Page).</span></span> <span data-ttu-id="817b7-194">若要访问它，请在对象资源管理器中右键单击服务器名称，选择属性，再选择“数据库设置”  页。</span><span class="sxs-lookup"><span data-stu-id="817b7-194">To access this, right-click the server name in Object Explorer and select properties; then select the **Database Settings** page.</span></span>  
  
    -   <span data-ttu-id="817b7-195">若要使备份集在特定日期过期，请单击 **“在”** ，并输入备份集的过期日期。</span><span class="sxs-lookup"><span data-stu-id="817b7-195">To have the backup set expire on a specific date, click **On**, and enter the date on which the set will expire.</span></span>  
  
         <span data-ttu-id="817b7-196">有关备份过期日期的详细信息，请参阅 [BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="817b7-196">For more information about backup expiration dates, see [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql).</span></span>  
  
18. [!INCLUDE[ssEnterpriseEd10](../../../includes/ssenterpriseed10-md.md)] <span data-ttu-id="817b7-197">及更高版本支持 [备份压缩](backup-compression-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="817b7-197">and later supports [backup compression](backup-compression-sql-server.md).</span></span> <span data-ttu-id="817b7-198">默认情况下，是否压缩备份取决于 **backup-compression default** 服务器配置选项的值。</span><span class="sxs-lookup"><span data-stu-id="817b7-198">By default, whether a backup is compressed depends on the value of the **backup-compression default** server configuration option.</span></span> <span data-ttu-id="817b7-199">但是，不管当前服务器级默认设置如何，都可以通过选中 **“压缩备份”** 来压缩备份，并且可以通过选中 **“不压缩备份”** 来防止压缩备份。</span><span class="sxs-lookup"><span data-stu-id="817b7-199">However, regardless of the current server-level default, you can compress a backup by checking **Compress backup**, and you can prevent compression by checking **Do not compress backup**.</span></span>  
  
     <span data-ttu-id="817b7-200">**查看或更改当前备份压缩默认值**</span><span class="sxs-lookup"><span data-stu-id="817b7-200">**To view or change the current backup compression default**</span></span>  
  
    -   [<span data-ttu-id="817b7-201">查看或配置 backup compression default 服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="817b7-201">View or Configure the backup compression default Server Configuration Option</span></span>](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)  
  
19. <span data-ttu-id="817b7-202">指定是否要对备份使用加密。</span><span class="sxs-lookup"><span data-stu-id="817b7-202">Specify whether to use encryption for the backup.</span></span> <span data-ttu-id="817b7-203">选择要用于加密步骤的加密算法，然后从现有证书或非对称密钥的列表中提供一个证书或非对称密钥。</span><span class="sxs-lookup"><span data-stu-id="817b7-203">Select an encryption algorithm to use for the encryption step, and provide a Certificate or Asymmetric key from a list of existing certificates or asymmetric keys.</span></span> <span data-ttu-id="817b7-204">SQL Server 2014 或更高版本中支持加密。</span><span class="sxs-lookup"><span data-stu-id="817b7-204">Encryption is supported in SQL Server 2014 or later.</span></span> <span data-ttu-id="817b7-205">有关加密选项的详细信息，请参阅 [备份数据库（“备份选项”页）](back-up-database-backup-options-page.md)。</span><span class="sxs-lookup"><span data-stu-id="817b7-205">For more details on the Encryption options, see [Back Up Database &#40;Backup Options Page&#41;](back-up-database-backup-options-page.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="817b7-206">此外，还可以使用维护计划向导来创建数据库备份。</span><span class="sxs-lookup"><span data-stu-id="817b7-206">Alternatively, you can use the Maintenance Plan Wizard to create database backups.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="817b7-207">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="817b7-207">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-full-database-backup"></a><span data-ttu-id="817b7-208">创建完整数据库备份</span><span class="sxs-lookup"><span data-stu-id="817b7-208">To create a full database backup</span></span>  
  
1.  <span data-ttu-id="817b7-209">执行 BACKUP DATABASE 语句可以创建完整数据库备份，同时指定：</span><span class="sxs-lookup"><span data-stu-id="817b7-209">Execute the BACKUP DATABASE statement to create the full database backup, specifying:</span></span>  
  
    -   <span data-ttu-id="817b7-210">要备份的数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="817b7-210">The name of the database to back up.</span></span>  
  
    -   <span data-ttu-id="817b7-211">写入完整数据库备份的备份设备。</span><span class="sxs-lookup"><span data-stu-id="817b7-211">The backup device where the full database backup is written.</span></span>  
  
     <span data-ttu-id="817b7-212">完整数据库备份的基本 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语法如下：</span><span class="sxs-lookup"><span data-stu-id="817b7-212">The basic [!INCLUDE[tsql](../../includes/tsql-md.md)] syntax for a full database backup is:</span></span>  
  
     <span data-ttu-id="817b7-213">BACKUP DATABASE *database*</span><span class="sxs-lookup"><span data-stu-id="817b7-213">BACKUP DATABASE *database*</span></span>  
  
     <span data-ttu-id="817b7-214">TO backup_device  [ **,** ...*n* ]</span><span class="sxs-lookup"><span data-stu-id="817b7-214">TO *backup_device* [ **,**...*n* ]</span></span>  
  
     <span data-ttu-id="817b7-215">[ WITH with_options  [ **,** ...*o* ] ] ;</span><span class="sxs-lookup"><span data-stu-id="817b7-215">[ WITH *with_options* [ **,**...*o* ] ] ;</span></span>  
  
    |<span data-ttu-id="817b7-216">选项</span><span class="sxs-lookup"><span data-stu-id="817b7-216">Option</span></span>|<span data-ttu-id="817b7-217">说明</span><span class="sxs-lookup"><span data-stu-id="817b7-217">Description</span></span>|  
    |------------|-----------------|  
    |<span data-ttu-id="817b7-218">*database*</span><span class="sxs-lookup"><span data-stu-id="817b7-218">*database*</span></span>|<span data-ttu-id="817b7-219">要备份的数据库。</span><span class="sxs-lookup"><span data-stu-id="817b7-219">Is the database that is to be backed up.</span></span>|  
    |<span data-ttu-id="817b7-220">*backup_device* [ **,** ...*n* ]</span><span class="sxs-lookup"><span data-stu-id="817b7-220">*backup_device* [ **,**...*n* ]</span></span>|<span data-ttu-id="817b7-221">指定一个列表，它包含 1 至 64 个用于备份操作的备份设备。</span><span class="sxs-lookup"><span data-stu-id="817b7-221">Specifies a list of from 1 to 64 backup devices to use for the backup operation.</span></span> <span data-ttu-id="817b7-222">您可以指定物理备份设备，也可以指定对应的逻辑备份设备（如果已定义）。</span><span class="sxs-lookup"><span data-stu-id="817b7-222">You can specify a physical backup device, or you can specify a corresponding logical backup device, if already defined.</span></span> <span data-ttu-id="817b7-223">若要指定物理备份设备，请使用 DISK 或 TAPE 选项：</span><span class="sxs-lookup"><span data-stu-id="817b7-223">To specify a physical backup device, use the DISK or TAPE option:</span></span><br /><br /> <span data-ttu-id="817b7-224">{ DISK &#124; TAPE } **=** _physical_backup_device_name_</span><span class="sxs-lookup"><span data-stu-id="817b7-224">{ DISK &#124; TAPE } **=**_physical_backup_device_name_</span></span><br /><br /> <span data-ttu-id="817b7-225">有关详细信息，请参阅 [备份设备 (SQL Server)](backup-devices-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="817b7-225">For more information, see [Backup Devices &#40;SQL Server&#41;](backup-devices-sql-server.md).</span></span>|  
    |<span data-ttu-id="817b7-226">WITH with_options  [ **,** ...*o* ]</span><span class="sxs-lookup"><span data-stu-id="817b7-226">WITH *with_options* [ **,**...*o* ]</span></span>|<span data-ttu-id="817b7-227">您也可以指定一个或多个附加选项 *o*。</span><span class="sxs-lookup"><span data-stu-id="817b7-227">Optionally, specifies one or more additional options, *o*.</span></span> <span data-ttu-id="817b7-228">有关某些基本 WITH 选项的信息，请参阅步骤 2。</span><span class="sxs-lookup"><span data-stu-id="817b7-228">For information about some of the basic with options, see step 2.</span></span>|  
  
2.  <span data-ttu-id="817b7-229">（可选）指定一个或多个 WITH 选项。</span><span class="sxs-lookup"><span data-stu-id="817b7-229">Optionally, specify one or more WITH options.</span></span> <span data-ttu-id="817b7-230">下面描述了几个基本 WITH 选项。</span><span class="sxs-lookup"><span data-stu-id="817b7-230">A few basic WITH options are described here.</span></span> <span data-ttu-id="817b7-231">有关所有 WITH 选项的详细信息，请参阅 BACKUP &#40;Transact-SQL&#41;  。</span><span class="sxs-lookup"><span data-stu-id="817b7-231">For information about all the WITH options, see [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql).</span></span>  
  
    -   <span data-ttu-id="817b7-232">基本备份集 WITH 选项：</span><span class="sxs-lookup"><span data-stu-id="817b7-232">Basic backup set WITH options:</span></span>  
  
         <span data-ttu-id="817b7-233">{ COMPRESSION | NO_COMPRESSION }</span><span class="sxs-lookup"><span data-stu-id="817b7-233">{ COMPRESSION | NO_COMPRESSION }</span></span>  
         <span data-ttu-id="817b7-234">在 [!INCLUDE[ssEnterpriseEd10](../../../includes/ssenterpriseed10-md.md)] 及更高版本中，指定是否为此备份执行 [备份压缩](backup-compression-sql-server.md) ，该设置将替代服务器级默认设置。</span><span class="sxs-lookup"><span data-stu-id="817b7-234">In [!INCLUDE[ssEnterpriseEd10](../../../includes/ssenterpriseed10-md.md)] and later only, specifies whether [backup compression](backup-compression-sql-server.md) is performed on this backup, overriding the server-level default.</span></span>  
  
         <span data-ttu-id="817b7-235">ENCRYPTION (ALGORITHM,  SERVER CERTIFICATE |ASYMMETRIC KEY)</span><span class="sxs-lookup"><span data-stu-id="817b7-235">ENCRYPTION (ALGORITHM,  SERVER CERTIFICATE |ASYMMETRIC KEY)</span></span>  
         <span data-ttu-id="817b7-236">仅在 SQL Server 2014 或更高版本中，指定要使用的加密算法以及要用于保护加密的证书或非对称密钥。</span><span class="sxs-lookup"><span data-stu-id="817b7-236">In SQL Server 2014 or later only, specify the encryption algorithm to use, and the Certificate or Asymmetric key to use to secure the encryption.</span></span>  
  
         <span data-ttu-id="817b7-237">说明 **=** { **" *`text`* "**  |  **@** _text_variable_ }</span><span class="sxs-lookup"><span data-stu-id="817b7-237">DESCRIPTION **=** { **'*`text`*'** | **@**_text_variable_ }</span></span>  
         <span data-ttu-id="817b7-238">指定说明备份集的自由格式文本。</span><span class="sxs-lookup"><span data-stu-id="817b7-238">Specifies the free-form text that describes the backup set.</span></span> <span data-ttu-id="817b7-239">该字符串最长可达 255 个字符。</span><span class="sxs-lookup"><span data-stu-id="817b7-239">The string can have a maximum of 255 characters.</span></span>  
  
         <span data-ttu-id="817b7-240">名称 **=** { *backup_set_name*  |  **@** _backup_set_name_var_ }</span><span class="sxs-lookup"><span data-stu-id="817b7-240">NAME **=** { *backup_set_name* | **@**_backup_set_name_var_ }</span></span>  
         <span data-ttu-id="817b7-241">指定备份集的名称。</span><span class="sxs-lookup"><span data-stu-id="817b7-241">Specifies the name of the backup set.</span></span> <span data-ttu-id="817b7-242">名称最长可达 128 个字符。</span><span class="sxs-lookup"><span data-stu-id="817b7-242">Names can have a maximum of 128 characters.</span></span> <span data-ttu-id="817b7-243">如果未指定 NAME，它将为空。</span><span class="sxs-lookup"><span data-stu-id="817b7-243">If NAME is not specified, it is blank.</span></span>  
  
    -   <span data-ttu-id="817b7-244">基本备份集 WITH 选项：</span><span class="sxs-lookup"><span data-stu-id="817b7-244">Basic backup set WITH options:</span></span>  
  
         <span data-ttu-id="817b7-245">默认情况下，BACKUP 将备份追加到现有介质集中，并保留现有备份集。</span><span class="sxs-lookup"><span data-stu-id="817b7-245">By default, BACKUP appends the backup to an existing media set, preserving existing backup sets.</span></span> <span data-ttu-id="817b7-246">若要显式指定此设置，请使用 NOINIT 选项。</span><span class="sxs-lookup"><span data-stu-id="817b7-246">To explicitly specify this, use the NOINIT option.</span></span> <span data-ttu-id="817b7-247">有关附加到现有备份集的信息，请参阅 [媒体集、媒体簇和备份集 (SQL Server)](media-sets-media-families-and-backup-sets-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="817b7-247">For information about appending to existing backup sets, see [Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md).</span></span>  
  
         <span data-ttu-id="817b7-248">或者，若要将备份介质格式化，可以使用 FORMAT 选项：</span><span class="sxs-lookup"><span data-stu-id="817b7-248">Alternatively, to format the backup media, use the FORMAT option:</span></span>  
  
         <span data-ttu-id="817b7-249">FORMAT [ **，** MEDIANAME **=** { *media_name*  |  **@** _media_name_variable_ }] [ **，** MEDIADESCRIPTION **=** { *text*  |  **@** _text_variable_ }]</span><span class="sxs-lookup"><span data-stu-id="817b7-249">FORMAT [ **,** MEDIANAME**=** { *media_name* | **@**_media_name_variable_ } ] [ **,** MEDIADESCRIPTION **=** { *text* | **@**_text_variable_ } ]</span></span>  
         <span data-ttu-id="817b7-250">当您第一次使用介质或者希望覆盖所有现有数据时可以使用 FORMAT 子句。</span><span class="sxs-lookup"><span data-stu-id="817b7-250">Use the FORMAT clause when you are using media for the first time or you want to overwrite all existing data.</span></span> <span data-ttu-id="817b7-251">根据需要，可以为新介质指定介质名称和说明。</span><span class="sxs-lookup"><span data-stu-id="817b7-251">Optionally, assign the new media a media name and description.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="817b7-252">当使用 BACKUP 语句的 FORMAT 子句时要十分小心，因为它会破坏以前存储在备份介质中的所有备份。</span><span class="sxs-lookup"><span data-stu-id="817b7-252">Use extreme caution when you are using the FORMAT clause of the BACKUP statement because this destroys any backups that were previously stored on the backup media.</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="817b7-253">示例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="817b7-253">Examples (Transact-SQL)</span></span>  
  
#### <a name="a-backing-up-to-a-disk-device"></a><span data-ttu-id="817b7-254">A.</span><span class="sxs-lookup"><span data-stu-id="817b7-254">A.</span></span> <span data-ttu-id="817b7-255">备份到磁盘设备</span><span class="sxs-lookup"><span data-stu-id="817b7-255">Backing up to a disk device</span></span>  
 <span data-ttu-id="817b7-256">下面的示例通过使用 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 创建新的介质集，将整个 `FORMAT` 数据库备份到磁盘。</span><span class="sxs-lookup"><span data-stu-id="817b7-256">The following example backs up the complete [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database to disk, by using `FORMAT` to create a new media set.</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
BACKUP DATABASE AdventureWorks2012  
TO DISK = 'Z:\SQLServerBackups\AdventureWorks2012.Bak'  
   WITH FORMAT,  
      MEDIANAME = 'Z_SQLServerBackups',  
      NAME = 'Full Backup of AdventureWorks2012';  
GO  
```  
  
#### <a name="b-backing-up-to-a-tape-device"></a><span data-ttu-id="817b7-257">B.</span><span class="sxs-lookup"><span data-stu-id="817b7-257">B.</span></span> <span data-ttu-id="817b7-258">备份到磁带设备</span><span class="sxs-lookup"><span data-stu-id="817b7-258">Backing up to a tape device</span></span>  
 <span data-ttu-id="817b7-259">下面的示例将完整的 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]数据库备份到磁带上，并将该备份追加到以前的备份中。</span><span class="sxs-lookup"><span data-stu-id="817b7-259">The following example backs up the complete [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]database to tape, appending the backup to the previous backups.</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
BACKUP DATABASE AdventureWorks2012  
   TO TAPE = '\\.\Tape0'  
   WITH NOINIT,  
      NAME = 'Full Backup of AdventureWorks2012';  
GO  
```  
  
#### <a name="c-backing-up-to-a-logical-tape-device"></a><span data-ttu-id="817b7-260">C.</span><span class="sxs-lookup"><span data-stu-id="817b7-260">C.</span></span> <span data-ttu-id="817b7-261">备份到逻辑磁带设备</span><span class="sxs-lookup"><span data-stu-id="817b7-261">Backing up to a logical tape device</span></span>  
 <span data-ttu-id="817b7-262">下例为某个磁带驱动器创建一个逻辑备份设备，</span><span class="sxs-lookup"><span data-stu-id="817b7-262">The following example creates a logical backup device for a tape drive.</span></span> <span data-ttu-id="817b7-263">然后将完整的 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 数据库备份到该设备上。</span><span class="sxs-lookup"><span data-stu-id="817b7-263">The example then backs up the complete [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database to that device.</span></span>  
  
```sql  
-- Create a logical backup device,   
-- AdventureWorks2012_Bak_Tape, for tape device \\.\tape0.  
USE master;  
GO  
EXEC sp_addumpdevice 'tape', 'AdventureWorks2012_Bak_Tape', '\\.\tape0'; USE AdventureWorks2012;  
GO  
BACKUP DATABASE AdventureWorks2012  
   TO AdventureWorks2012_Bak_Tape  
   WITH FORMAT,  
      MEDIANAME = 'AdventureWorks2012_Bak_Tape',  
      MEDIADESCRIPTION = '\\.\tape0',   
      NAME = 'Full Backup of AdventureWorks2012';  
GO  
```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="817b7-264">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="817b7-264">Using PowerShell</span></span>  
  
1.  <span data-ttu-id="817b7-265">使用 `Backup-SqlDatabase` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="817b7-265">Use the `Backup-SqlDatabase` cmdlet.</span></span> <span data-ttu-id="817b7-266">若要显式指示这是完整数据库备份，请指定 **-BackupAction**参数及其默认值 `Database` 。</span><span class="sxs-lookup"><span data-stu-id="817b7-266">To explicitly indicate that this is a full database backup, specify the **-BackupAction**  parameter with its default value, `Database`.</span></span> <span data-ttu-id="817b7-267">对于完整数据库备份而言，此参数是可选的。</span><span class="sxs-lookup"><span data-stu-id="817b7-267">This parameter is optional for full database backups.</span></span>  
  
     <span data-ttu-id="817b7-268">下面的示例在服务器实例 `MyDB` 的默认备份位置创建数据库 `Computer\Instance`的完整数据库备份。</span><span class="sxs-lookup"><span data-stu-id="817b7-268">The following example creates a full database backup of the `MyDB` database to the default backup location of the server instance `Computer\Instance`.</span></span> <span data-ttu-id="817b7-269">此示例也可以指定 `-BackupAction Database`。</span><span class="sxs-lookup"><span data-stu-id="817b7-269">Optionally, this example specifies `-BackupAction Database`.</span></span>  
  
    ```powershell
    Backup-SqlDatabase -ServerInstance Computer\Instance -Database MyDB -BackupAction Database  
    ```  
  
 <span data-ttu-id="817b7-270">**设置和使用 SQL Server PowerShell 提供程序**</span><span class="sxs-lookup"><span data-stu-id="817b7-270">**To set up and use the SQL Server PowerShell provider**</span></span>  
  
-   [<span data-ttu-id="817b7-271">SQL Server PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="817b7-271">SQL Server PowerShell Provider</span></span>](../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="817b7-272">相关任务</span><span class="sxs-lookup"><span data-stu-id="817b7-272">Related Tasks</span></span>  
  
-   [<span data-ttu-id="817b7-273">备份数据库 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="817b7-273">Back Up a Database (SQL Server)</span></span>](create-a-full-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="817b7-274">创建差异数据库备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="817b7-274">Create a Differential Database Backup &#40;SQL Server&#41;</span></span>](create-a-differential-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="817b7-275">还原数据库备份 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="817b7-275">Restore a Database Backup &#40;SQL Server Management Studio&#41;</span></span>](restore-a-database-backup-using-ssms.md)  
  
-   [<span data-ttu-id="817b7-276">在简单恢复模式下还原数据库备份 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="817b7-276">Restore a Database Backup Under the Simple Recovery Model &#40;Transact-SQL&#41;</span></span>](restore-a-database-backup-under-the-simple-recovery-model-transact-sql.md)  
  
-   [<span data-ttu-id="817b7-277">在完整恢复模式下将数据库还原到故障点 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="817b7-277">Restore a Database to the Point of Failure Under the Full Recovery Model &#40;Transact-SQL&#41;</span></span>](restore-database-to-point-of-failure-full-recovery.md)  
  
-   [<span data-ttu-id="817b7-278">将数据库还原到新位置 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="817b7-278">Restore a Database to a New Location &#40;SQL Server&#41;</span></span>](restore-a-database-to-a-new-location-sql-server.md)  
  
-   [<span data-ttu-id="817b7-279">使用维护计划向导</span><span class="sxs-lookup"><span data-stu-id="817b7-279">Use the Maintenance Plan Wizard</span></span>](../maintenance-plans/use-the-maintenance-plan-wizard.md)  
  
## <a name="see-also"></a><span data-ttu-id="817b7-280">另请参阅</span><span class="sxs-lookup"><span data-stu-id="817b7-280">See Also</span></span>  
 <span data-ttu-id="817b7-281">[备份概述 (SQL Server)](backup-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="817b7-281">[Backup Overview &#40;SQL Server&#41;](backup-overview-sql-server.md) </span></span>  
 <span data-ttu-id="817b7-282">[事务日志备份 (SQL Server)](transaction-log-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="817b7-282">[Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span></span>  
 <span data-ttu-id="817b7-283">[媒体集、媒体簇和备份集 (SQL Server)](media-sets-media-families-and-backup-sets-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="817b7-283">[Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md) </span></span>  
 <span data-ttu-id="817b7-284">[sp_addumpdevice (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="817b7-284">[sp_addumpdevice &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql) </span></span>  
 <span data-ttu-id="817b7-285">[BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="817b7-285">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="817b7-286">[备份数据库（“常规”页）](../../integration-services/general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="817b7-286">[Back Up Database &#40;General Page&#41;](../../integration-services/general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="817b7-287">[备份数据库（“备份选项”页）](back-up-database-backup-options-page.md) </span><span class="sxs-lookup"><span data-stu-id="817b7-287">[Back Up Database &#40;Backup Options Page&#41;](back-up-database-backup-options-page.md) </span></span>  
 <span data-ttu-id="817b7-288">[差异备份 (SQL Server)](differential-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="817b7-288">[Differential Backups &#40;SQL Server&#41;](differential-backups-sql-server.md) </span></span>  
 [<span data-ttu-id="817b7-289">完整数据库备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="817b7-289">Full Database Backups &#40;SQL Server&#41;</span></span>](full-database-backups-sql-server.md)  
