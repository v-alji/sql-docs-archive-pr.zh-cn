---
title: 在数据库损坏时备份事务日志 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- databases [SQL Server], damaged
- backing up [SQL Server]. damaged database
- transaction log backups [SQL Server], damaged databases
ms.assetid: 9b8873cc-df54-4336-ab9b-8f525132c2b0
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ea712e6bc4e73119a4f07a7775f9f25e212f8534
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576846"
---
# <a name="back-up-the-transaction-log-when-the-database-is-damaged-sql-server"></a><span data-ttu-id="3c514-102">在数据库损坏时备份事务日志 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="3c514-102">Back Up the Transaction Log When the Database Is Damaged (SQL Server)</span></span>
  <span data-ttu-id="3c514-103">本主题说明当数据库损坏时如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中备份事务日志。</span><span class="sxs-lookup"><span data-stu-id="3c514-103">This topic describes how to back up a transaction log when the database is damaged in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="3c514-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="3c514-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="3c514-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="3c514-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="3c514-106">限制和局限</span><span class="sxs-lookup"><span data-stu-id="3c514-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="3c514-107">建议</span><span class="sxs-lookup"><span data-stu-id="3c514-107">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="3c514-108">安全性</span><span class="sxs-lookup"><span data-stu-id="3c514-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="3c514-109">**若要在数据库损坏时备份事务日志，可使用：**</span><span class="sxs-lookup"><span data-stu-id="3c514-109">**To back up the transaction log when the database is damaged, using:**</span></span>  
  
     [<span data-ttu-id="3c514-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="3c514-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="3c514-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="3c514-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="3c514-112">开始之前</span><span class="sxs-lookup"><span data-stu-id="3c514-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="3c514-113">限制和局限</span><span class="sxs-lookup"><span data-stu-id="3c514-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="3c514-114">不允许在显式或隐式事务中使用 BACKUP 语句。</span><span class="sxs-lookup"><span data-stu-id="3c514-114">The BACKUP statement is not allowed in an explicit or implicit transaction.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="3c514-115">建议</span><span class="sxs-lookup"><span data-stu-id="3c514-115">Recommendations</span></span>  
  
-   <span data-ttu-id="3c514-116">对于使用完整恢复模式或大容量日志恢复模式的数据库，通常需要在开始还原数据库前备份日志尾部。</span><span class="sxs-lookup"><span data-stu-id="3c514-116">For a database that uses either the full or bulk-logged recovery model, you generally need to back up the tail of the log before beginning to restore the database.</span></span> <span data-ttu-id="3c514-117">在对日志传送配置进行故障转移之前，还应当备份主数据库的日志尾部。</span><span class="sxs-lookup"><span data-stu-id="3c514-117">You also should back up the tail of the log of the primary database before failing over a log shipping configuration.</span></span> <span data-ttu-id="3c514-118">将结尾日志备份作为恢复数据库之前的最后一个日志备份还原可以防止失败后丢失工作。</span><span class="sxs-lookup"><span data-stu-id="3c514-118">Restoring the tail-log backup as the final log backup before recovering the database avoids work loss after a failure.</span></span> <span data-ttu-id="3c514-119">有关结尾日志备份的详细信息，请参阅[结尾日志备份 (SQL Server) ](tail-log-backups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="3c514-119">For more information about tail-log backups, see [Tail-Log Backups &#40;SQL Server&#41;](tail-log-backups-sql-server.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="3c514-120">Security</span><span class="sxs-lookup"><span data-stu-id="3c514-120">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="3c514-121">权限</span><span class="sxs-lookup"><span data-stu-id="3c514-121">Permissions</span></span>  
 <span data-ttu-id="3c514-122">默认情况下，为 **sysadmin** 固定服务器角色以及 **db_owner** 和 **db_backupoperator** 固定数据库角色的成员授予 BACKUP DATABASE 和 BACKUP LOG 权限。</span><span class="sxs-lookup"><span data-stu-id="3c514-122">BACKUP DATABASE and BACKUP LOG permissions default to members of the **sysadmin** fixed server role and the **db_owner** and **db_backupoperator** fixed database roles.</span></span>  
  
 <span data-ttu-id="3c514-123">备份设备的物理文件的所有权和权限问题可能会妨碍备份操作。</span><span class="sxs-lookup"><span data-stu-id="3c514-123">Ownership and permission problems on the backup device's physical file can interfere with a backup operation.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="3c514-124">必须能够读取和写入设备；运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务的帐户必须具有写入权限。</span><span class="sxs-lookup"><span data-stu-id="3c514-124">must be able to read and write to the device; the account under which the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service runs must have write permissions.</span></span> <span data-ttu-id="3c514-125">但是，用于在系统表中为备份设备添加项目的 [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql)不检查文件访问权限。</span><span class="sxs-lookup"><span data-stu-id="3c514-125">However, [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql), which adds an entry for a backup device in the system tables, does not check file access permissions.</span></span> <span data-ttu-id="3c514-126">备份设备物理文件的这些问题可能直到为备份或还原而访问物理资源时才会出现。</span><span class="sxs-lookup"><span data-stu-id="3c514-126">Such problems on the backup device's physical file may not appear until the physical resource is accessed when the backup or restore is attempted.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="3c514-127">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="3c514-127">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-back-up-the-tail-of-the-transaction-log"></a><span data-ttu-id="3c514-128">备份事务日志尾部</span><span class="sxs-lookup"><span data-stu-id="3c514-128">To back up the tail of the transaction log</span></span>  
  
1.  <span data-ttu-id="3c514-129">连接到相应的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 实例之后，在“对象资源管理器”中，单击服务器名称以展开服务器树。</span><span class="sxs-lookup"><span data-stu-id="3c514-129">After connecting to the appropriate instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="3c514-130">展开 **“数据库”** ，然后根据数据库的不同，选择用户数据库，或展开 **“系统数据库”** ，再选择系统数据库。</span><span class="sxs-lookup"><span data-stu-id="3c514-130">Expand **Databases**, and, depending on the database, either select a user database or expand **System Databases** and select a system database.</span></span>  
  
3.  <span data-ttu-id="3c514-131">右键单击数据库，指向 **“任务”** ，再单击 **“备份”** 。</span><span class="sxs-lookup"><span data-stu-id="3c514-131">Right-click the database, point to **Tasks**, and then click **Back Up**.</span></span> <span data-ttu-id="3c514-132">将出现 **“备份数据库”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="3c514-132">The **Back Up Database** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="3c514-133">在 **“数据库”** 列表框中，验证数据库名称。</span><span class="sxs-lookup"><span data-stu-id="3c514-133">In the **Database** list box, verify the database name.</span></span> <span data-ttu-id="3c514-134">您也可以从列表中选择其他数据库。</span><span class="sxs-lookup"><span data-stu-id="3c514-134">You can optionally select a different database from the list.</span></span>  
  
5.  <span data-ttu-id="3c514-135">验证恢复模式是 **FULL** 还是 **BULK_LOGGED**。</span><span class="sxs-lookup"><span data-stu-id="3c514-135">Verify that the recovery model is either **FULL** or **BULK_LOGGED**.</span></span>  
  
6.  <span data-ttu-id="3c514-136">在 **“备份类型”** 列表框中，选择 **“事务日志”** 。</span><span class="sxs-lookup"><span data-stu-id="3c514-136">In the **Backup type** list box, select **Transaction Log**.</span></span>  
  
7.  <span data-ttu-id="3c514-137">使 **“仅复制备份”** 处于取消选中状态。</span><span class="sxs-lookup"><span data-stu-id="3c514-137">Leave **Copy Only Backup** deselected.</span></span>  
  
8.  <span data-ttu-id="3c514-138">在 **“备份集”** 区域中，可以接受 **“名称”** 文本框中建议的默认备份集名称，也可以为备份集输入其他名称。</span><span class="sxs-lookup"><span data-stu-id="3c514-138">In the **Backup set** area, either accept the default backup set name suggested in the **Name** text box, or enter a different name for the backup set.</span></span>  
  
9. <span data-ttu-id="3c514-139">在 **“说明”** 文本框中，输入结尾日志备份的说明。</span><span class="sxs-lookup"><span data-stu-id="3c514-139">In the **Description** text box, enter a description for the tail-log backup.</span></span>  
  
10. <span data-ttu-id="3c514-140">指定备份集的过期时间：</span><span class="sxs-lookup"><span data-stu-id="3c514-140">Specify when the backup set will expire:</span></span>  
  
    -   <span data-ttu-id="3c514-141">若要使备份集在特定天数后过期，请单击 **“之后”** （默认选项），并输入备份集从创建到过期所需的天数。</span><span class="sxs-lookup"><span data-stu-id="3c514-141">To have the backup set expire after a specific number of days, click **After** (the default option), and enter the number of days after set creation that the set will expire.</span></span> <span data-ttu-id="3c514-142">此值范围为 0 到 99999 天；0 天表示备份集将永不过期。</span><span class="sxs-lookup"><span data-stu-id="3c514-142">This value can be from 0 to 99999 days; a value of 0 days means that the backup set will never expire.</span></span>  
  
         <span data-ttu-id="3c514-143">默认值在 **“服务器属性”** 对话框（位于 **“数据库设置”** 页上）的 **“默认备份媒体保持期(天)”** 选项中设置。</span><span class="sxs-lookup"><span data-stu-id="3c514-143">The default value is set in the **Default backup media retention (in days)** option of the **Server Properties** dialog box (**Database Settings** page).</span></span> <span data-ttu-id="3c514-144">若要访问此对话框，请在对象资源管理器中右键单击服务器名称，选择“属性”，再选择 **“数据库设置”** 页。</span><span class="sxs-lookup"><span data-stu-id="3c514-144">To access this dialog box, right-click the server name in Object Explorer and select properties; then select the **Database Settings** page.</span></span>  
  
    -   <span data-ttu-id="3c514-145">若要使备份集在特定日期过期，请单击 **“在”** ，并输入备份集的过期日期。</span><span class="sxs-lookup"><span data-stu-id="3c514-145">To have the backup set expire on a specific date, click **On**, and enter the date on which the set will expire.</span></span>  
  
11. <span data-ttu-id="3c514-146">通过单击 **“磁盘”** 或 **“磁带”** ，选择备份目标的类型。</span><span class="sxs-lookup"><span data-stu-id="3c514-146">Choose the type of backup destination by clicking **Disk** or **Tape**.</span></span> <span data-ttu-id="3c514-147">若要选择包含单个介质集的多个磁盘或磁带机（最多为 64 个）的路径，请单击 **“添加”** 。</span><span class="sxs-lookup"><span data-stu-id="3c514-147">To select the paths of up to 64 disk or tape drives containing a single media set, click **Add**.</span></span> <span data-ttu-id="3c514-148">选择的路径将显示在 **“备份到”** 列表框中。</span><span class="sxs-lookup"><span data-stu-id="3c514-148">The selected paths are displayed in the **Backup to** list box.</span></span>  
  
     <span data-ttu-id="3c514-149">若要删除备份目标，请选择该备份目标并单击 **“删除”** 。</span><span class="sxs-lookup"><span data-stu-id="3c514-149">To remove a backup destination, select it and click **Remove**.</span></span> <span data-ttu-id="3c514-150">若要查看备份目标的内容，请选择该备份目标并单击 **“内容”** 。</span><span class="sxs-lookup"><span data-stu-id="3c514-150">To view the contents of a backup destination, select it and click **Contents**.</span></span>  
  
12. <span data-ttu-id="3c514-151">在 **“选项”** 页上，可以通过单击下列选项之一来选择 **“覆盖介质”** 选项：</span><span class="sxs-lookup"><span data-stu-id="3c514-151">On the **Options** page, select an **Overwrite Media** option, by clicking one of the following:</span></span>  
  
    -   <span data-ttu-id="3c514-152">**备份到现有介质集**</span><span class="sxs-lookup"><span data-stu-id="3c514-152">**Back up to the existing media set**</span></span>  
  
         <span data-ttu-id="3c514-153">对于此选项，请单击 **“追加到现有备份集”** 或 **“覆盖所有现有备份集”** 。</span><span class="sxs-lookup"><span data-stu-id="3c514-153">For this option, click either **Append to the existing backup set** or **Overwrite all existing backup sets**.</span></span>  
  
         <span data-ttu-id="3c514-154">或者选择 **“检查介质集名称和备份集过期时间”** ，以使备份操作对介质集和备份集的过期日期和时间进行验证。</span><span class="sxs-lookup"><span data-stu-id="3c514-154">Optionally, select **Check media set name and backup set expiration** to cause the backup operation to verify the date and time at which the media set and backup set expire.</span></span>  
  
         <span data-ttu-id="3c514-155">或者在 **“介质集名称”** 文本框中输入名称。</span><span class="sxs-lookup"><span data-stu-id="3c514-155">Optionally, enter a name in the **Media set name** text box.</span></span> <span data-ttu-id="3c514-156">如果没有指定名称，将使用空白名称创建介质集。</span><span class="sxs-lookup"><span data-stu-id="3c514-156">If no name is specified, a media set with a blank name is created.</span></span> <span data-ttu-id="3c514-157">如果指定了介质集名称，将检查介质（磁带或磁盘），以确定实际名称是否与此处输入的名称匹配。</span><span class="sxs-lookup"><span data-stu-id="3c514-157">If you specify a media set name, the media (tape or disk) is checked to see whether the actual name matches the name you enter here.</span></span>  
  
         <span data-ttu-id="3c514-158">如果将介质名称保留空白，并选中该框以便与介质进行核对，则只有当介质上的介质名称也是空白时才能成功。</span><span class="sxs-lookup"><span data-stu-id="3c514-158">If you leave the media name blank and check the box to check it against the media, success will equal the media name on the media also being blank.</span></span>  
  
    -   <span data-ttu-id="3c514-159">**备份到新介质集并清除所有现有备份集**</span><span class="sxs-lookup"><span data-stu-id="3c514-159">**Back up to a new media set, and erase all existing backup sets**</span></span>  
  
         <span data-ttu-id="3c514-160">对于该选项，请在 **“新建介质集名称”** 文本框中输入名称，并在 **“新建介质集说明”** 文本框中描述介质集（可选）。</span><span class="sxs-lookup"><span data-stu-id="3c514-160">For this option, enter a name in the **New media set name** text box, and, optionally, describe the media set in the **New media set description** text box.</span></span>  
  
     <span data-ttu-id="3c514-161">有关媒体集选项的详细信息，请参阅[集、媒体簇和备份集 (SQL Server)](media-sets-media-families-and-backup-sets-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="3c514-161">For more information about media set options, see [Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md).</span></span>  
  
13. <span data-ttu-id="3c514-162">或者，在 **“可靠性”** 部分中，选中：</span><span class="sxs-lookup"><span data-stu-id="3c514-162">In the **Reliability** section, optionally, check:</span></span>  
  
    -   <span data-ttu-id="3c514-163">**完成后验证备份**。</span><span class="sxs-lookup"><span data-stu-id="3c514-163">**Verify backup when finished**.</span></span>  
  
    -   <span data-ttu-id="3c514-164">**写入介质前检查校验和**。</span><span class="sxs-lookup"><span data-stu-id="3c514-164">**Perform checksum before writing to media**.</span></span>  
  
    -   <span data-ttu-id="3c514-165">**出现校验和错误时继续**</span><span class="sxs-lookup"><span data-stu-id="3c514-165">**Continue on checksum error**</span></span>  
  
     <span data-ttu-id="3c514-166">有关校验和的信息，请参阅[在备份和还原期间可能的媒体错误 (SQL Server)](possible-media-errors-during-backup-and-restore-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="3c514-166">For information on checksums, see [Possible Media Errors During Backup and Restore &#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md).</span></span>  
  
14. <span data-ttu-id="3c514-167">在 **“事务日志”** 部分，选中 **“备份日志尾部，并使数据库处于还原状态”** 。</span><span class="sxs-lookup"><span data-stu-id="3c514-167">In the **Transaction log** section, check **Back up the tail of the log, and leave database in the restoring state**.</span></span>  
  
     <span data-ttu-id="3c514-168">这相当于指定以下 [BACKUP](/sql/t-sql/statements/backup-transact-sql) 语句：</span><span class="sxs-lookup"><span data-stu-id="3c514-168">This is equivalent to specifying the following [BACKUP](/sql/t-sql/statements/backup-transact-sql) statement:</span></span>  
  
     `BACKUP LOG <database_name> TO <backup_device> WITH NORECOVERY`  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="3c514-169">在还原时，“还原数据库”对话框将结尾日志备份的类型显示为“事务日志(仅备份)”  。</span><span class="sxs-lookup"><span data-stu-id="3c514-169">At restore time, the Restore Database dialog box displays the type of a tail-log backup as **Transaction Log (Copy Only)**.</span></span>  
  
15. <span data-ttu-id="3c514-170">如果备份到磁带驱动器（如同 **“常规”** 页的 **“目标”** 部分指定的一样），则 **“备份后卸载磁带”** 选项处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="3c514-170">If you are backing up to a tape drive (as specified in the **Destination** section of the **General** page), the **Unload the tape after backup** option is active.</span></span> <span data-ttu-id="3c514-171">单击此选项可以激活 **“卸载前倒带”** 选项。</span><span class="sxs-lookup"><span data-stu-id="3c514-171">Clicking this option activates the **Rewind the tape before unloading** option.</span></span>  
  
16. [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] <span data-ttu-id="3c514-172">及更高版本支持 [备份压缩](backup-compression-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="3c514-172">and later supports [backup compression](backup-compression-sql-server.md).</span></span> <span data-ttu-id="3c514-173">默认情况下，是否压缩备份取决于 **backup-compression default** 服务器配置选项的值。</span><span class="sxs-lookup"><span data-stu-id="3c514-173">By default, whether a backup is compressed depends on the value of the **backup-compression default** server configuration option.</span></span> <span data-ttu-id="3c514-174">但是，不管当前服务器级默认设置如何，都可以通过选中 **“压缩备份”** 来压缩备份，并且可以通过选中 **“不压缩备份”** 来防止压缩备份。</span><span class="sxs-lookup"><span data-stu-id="3c514-174">However, regardless of the current server-level default, you can compress a backup by checking **Compress backup**, and you can prevent compression by checking **Do not compress backup**.</span></span>  
  
     <span data-ttu-id="3c514-175">**查看当前备份压缩默认值**</span><span class="sxs-lookup"><span data-stu-id="3c514-175">**To view the current backup compression default**</span></span>  
  
    -   [<span data-ttu-id="3c514-176">查看或配置 backup compression default 服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="3c514-176">View or Configure the backup compression default Server Configuration Option</span></span>](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="3c514-177">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="3c514-177">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-backup-of-the-currently-active-transaction-log"></a><span data-ttu-id="3c514-178">创建当前活动的事务日志的备份</span><span class="sxs-lookup"><span data-stu-id="3c514-178">To create a backup of the currently active transaction log</span></span>  
  
1.  <span data-ttu-id="3c514-179">执行 BACKUP LOG 语句以备份当前活动的事务日志，同时指定：</span><span class="sxs-lookup"><span data-stu-id="3c514-179">Execute the BACKUP LOG statement to back up the currently active transaction log, specifying:</span></span>  
  
    -   <span data-ttu-id="3c514-180">要备份的事务日志所属的数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="3c514-180">The name of the database to which the transaction log to back up belongs.</span></span>  
  
    -   <span data-ttu-id="3c514-181">事务日志备份将写入的备份设备。</span><span class="sxs-lookup"><span data-stu-id="3c514-181">The backup device where the transaction log backup will be written.</span></span>  
  
    -   <span data-ttu-id="3c514-182">NO_TRUNCATE 子句。</span><span class="sxs-lookup"><span data-stu-id="3c514-182">The NO_TRUNCATE clause.</span></span>  
  
         <span data-ttu-id="3c514-183">只要事务日志文件是可访问的并且没有损坏，那么即使数据库不可访问，该子句也允许备份事务日志的活动部分。</span><span class="sxs-lookup"><span data-stu-id="3c514-183">This clause allows the active part of the transaction log to be backed up even if the database is inaccessible, provided that the transaction log file is accessible and undamaged.</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="3c514-184">示例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="3c514-184">Example (Transact-SQL)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3c514-185">此示例使用 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]，该对象使用简单恢复模式。</span><span class="sxs-lookup"><span data-stu-id="3c514-185">This example uses the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)], which uses the simple recovery model.</span></span> <span data-ttu-id="3c514-186">若要允许日志备份，请在完整备份数据库之前，将数据库设置为使用完整恢复模式。</span><span class="sxs-lookup"><span data-stu-id="3c514-186">To permit log backups, before taking a full database backup, the database was set to use the full recovery model.</span></span> <span data-ttu-id="3c514-187">有关详细信息，请参阅[查看或更改数据库的恢复模式 (SQL Server)](view-or-change-the-recovery-model-of-a-database-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="3c514-187">For more information, see [View or Change the Recovery Model of a Database &#40;SQL Server&#41;](view-or-change-the-recovery-model-of-a-database-sql-server.md).</span></span>  
  
 <span data-ttu-id="3c514-188">此示例在数据库损坏且不可访问时备份当前活动事务日志（如果事务日志已损坏且可访问）。</span><span class="sxs-lookup"><span data-stu-id="3c514-188">This example backs up the currently active transaction log when a database is damaged and inaccessible, if the transaction log is undamaged and accessible.</span></span>  
  
```scr  
BACKUP LOG AdventureWorks2012  
   TO MyAdvWorks_FullRM_log1  
   WITH NO_TRUNCATE;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="3c514-189">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3c514-189">See Also</span></span>  
 <span data-ttu-id="3c514-190">[还原事务日志备份 (SQL Server)](restore-a-transaction-log-backup-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="3c514-190">[Restore a Transaction Log Backup &#40;SQL Server&#41;](restore-a-transaction-log-backup-sql-server.md) </span></span>  
 <span data-ttu-id="3c514-191">[将 SQL Server 数据库还原到某个时间点（完整恢复模式）](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="3c514-191">[Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md) </span></span>  
 <span data-ttu-id="3c514-192">[备份数据库（“备份选项”页）](back-up-database-backup-options-page.md) </span><span class="sxs-lookup"><span data-stu-id="3c514-192">[Back Up Database &#40;Backup Options Page&#41;](back-up-database-backup-options-page.md) </span></span>  
 <span data-ttu-id="3c514-193">[备份数据库（“常规”页）](../../integration-services/general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="3c514-193">[Back Up Database &#40;General Page&#41;](../../integration-services/general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="3c514-194">[应用事务日志备份 (SQL Server)](transaction-log-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="3c514-194">[Apply Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span></span>  
 <span data-ttu-id="3c514-195">[BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3c514-195">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="3c514-196">[文件还原（简单恢复模式）](file-restores-simple-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="3c514-196">[File Restores &#40;Simple Recovery Model&#41;](file-restores-simple-recovery-model.md) </span></span>  
 [<span data-ttu-id="3c514-197">文件还原（完整恢复模式）</span><span class="sxs-lookup"><span data-stu-id="3c514-197">File Restores &#40;Full Recovery Model&#41;</span></span>](file-restores-full-recovery-model.md)  
  
  
