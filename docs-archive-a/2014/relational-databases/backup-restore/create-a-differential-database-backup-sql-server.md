---
title: 创建差异数据库备份 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- full differential backups [SQL Server]
- database backups [SQL Server], full differential backups
- backing up databases [SQL Server], full differential backups
- backups [SQL Server], creating
ms.assetid: 70f49794-b217-4519-9f2a-76ed61fa9f99
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2c3fb53d90ce633498bc518282d1ff03ce0b926e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591409"
---
# <a name="create-a-differential-database-backup-sql-server"></a><span data-ttu-id="a72b3-102">创建差异数据库备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="a72b3-102">Create a Differential Database Backup (SQL Server)</span></span>
  <span data-ttu-id="a72b3-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中创建差异数据库备份。</span><span class="sxs-lookup"><span data-stu-id="a72b3-103">This topic describes how to create a differential database backup in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="a72b3-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="a72b3-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="a72b3-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="a72b3-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="a72b3-106">限制和局限</span><span class="sxs-lookup"><span data-stu-id="a72b3-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="a72b3-107">先决条件</span><span class="sxs-lookup"><span data-stu-id="a72b3-107">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="a72b3-108">建议</span><span class="sxs-lookup"><span data-stu-id="a72b3-108">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="a72b3-109">安全性</span><span class="sxs-lookup"><span data-stu-id="a72b3-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="a72b3-110">**若要创建差异数据库备份，请使用：**</span><span class="sxs-lookup"><span data-stu-id="a72b3-110">**To create a differential database backup, using:**</span></span>  
  
     [<span data-ttu-id="a72b3-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a72b3-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="a72b3-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a72b3-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="a72b3-113">开始之前</span><span class="sxs-lookup"><span data-stu-id="a72b3-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="a72b3-114">限制和局限</span><span class="sxs-lookup"><span data-stu-id="a72b3-114">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="a72b3-115">不允许在显式或隐式事务中使用 BACKUP 语句。</span><span class="sxs-lookup"><span data-stu-id="a72b3-115">The BACKUP statement is not allowed in an explicit or implicit transaction.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="a72b3-116">先决条件</span><span class="sxs-lookup"><span data-stu-id="a72b3-116">Prerequisites</span></span>  
  
-   <span data-ttu-id="a72b3-117">创建差异数据库备份需要有以前的完整数据库备份。</span><span class="sxs-lookup"><span data-stu-id="a72b3-117">Creating a differential database backup requires that a previous full database backup exist.</span></span> <span data-ttu-id="a72b3-118">如果选定的数据库从未进行过备份，则请在创建任何差异备份之前，先执行完整数据库备份。</span><span class="sxs-lookup"><span data-stu-id="a72b3-118">If the selected database has never been backed up, run a full database backup before creating any differential backups.</span></span> <span data-ttu-id="a72b3-119">有关详细信息，请参阅 [创建完整数据库备份 (SQL Server)](create-a-full-database-backup-sql-server.md)中创建差异数据库备份。</span><span class="sxs-lookup"><span data-stu-id="a72b3-119">For more information, see [Create a Full Database Backup &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md).</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="a72b3-120">建议</span><span class="sxs-lookup"><span data-stu-id="a72b3-120">Recommendations</span></span>  
  
-   <span data-ttu-id="a72b3-121">当差异备份的大小增大时，还原差异备份会显著延长还原数据库所需的时间。</span><span class="sxs-lookup"><span data-stu-id="a72b3-121">As the differential backups increase in size, restoring a differential backup can significantly increase the time that is required to restore a database.</span></span> <span data-ttu-id="a72b3-122">因此，建议按设定的间隔执行新的完整备份，以便为数据建立新的差异基准。</span><span class="sxs-lookup"><span data-stu-id="a72b3-122">Therefore, we recommend that you take a new full backup at set intervals to establish a new differential base for the data.</span></span> <span data-ttu-id="a72b3-123">例如，您可以每周执行一次整个数据库的完整备份（即完整数据库备份），然后在该周内执行一系列常规的差异数据库备份。</span><span class="sxs-lookup"><span data-stu-id="a72b3-123">For example, you might take a weekly full backup of the whole database (that is, a full database backup) followed by a regular series of differential database backups during the week.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="a72b3-124">Security</span><span class="sxs-lookup"><span data-stu-id="a72b3-124">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="a72b3-125">权限</span><span class="sxs-lookup"><span data-stu-id="a72b3-125">Permissions</span></span>  
 <span data-ttu-id="a72b3-126">默认情况下，为 **sysadmin** 固定服务器角色以及 **db_owner** 和 **db_backupoperator** 固定数据库角色的成员授予 BACKUP DATABASE 和 BACKUP LOG 权限。</span><span class="sxs-lookup"><span data-stu-id="a72b3-126">BACKUP DATABASE and BACKUP LOG permissions default to members of the **sysadmin** fixed server role and the **db_owner** and **db_backupoperator** fixed database roles.</span></span>  
  
 <span data-ttu-id="a72b3-127">备份设备的物理文件的所有权和权限问题可能会妨碍备份操作。</span><span class="sxs-lookup"><span data-stu-id="a72b3-127">Ownership and permission problems on the backup device's physical file can interfere with a backup operation.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="a72b3-128">必须能够读取和写入设备；运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务的帐户必须具有写入权限。</span><span class="sxs-lookup"><span data-stu-id="a72b3-128">must be able to read and write to the device; the account under which the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service runs must have write permissions.</span></span> <span data-ttu-id="a72b3-129">但是，用于在系统表中为备份设备添加项目的 [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql)不检查文件访问权限。</span><span class="sxs-lookup"><span data-stu-id="a72b3-129">However, [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql), which adds an entry for a backup device in the system tables, does not check file access permissions.</span></span> <span data-ttu-id="a72b3-130">备份设备物理文件的这些问题可能直到为备份或还原而访问物理资源时才会出现。</span><span class="sxs-lookup"><span data-stu-id="a72b3-130">Such problems on the backup device's physical file may not appear until the physical resource is accessed when the backup or restore is attempted.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="a72b3-131">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a72b3-131">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-differential-database-backup"></a><span data-ttu-id="a72b3-132">创建差异数据库备份</span><span class="sxs-lookup"><span data-stu-id="a72b3-132">To create a differential database backup</span></span>  
  
1.  <span data-ttu-id="a72b3-133">连接到相应的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 实例之后，在“对象资源管理器”中，单击服务器名称以展开服务器树。</span><span class="sxs-lookup"><span data-stu-id="a72b3-133">After connecting to the appropriate instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="a72b3-134">展开 **“数据库”** ，然后根据数据库的不同，选择用户数据库，或展开 **“系统数据库”** ，再选择系统数据库。</span><span class="sxs-lookup"><span data-stu-id="a72b3-134">Expand **Databases**, and depending on the database, either select a user database or expand **System Databases** and select a system database.</span></span>  
  
3.  <span data-ttu-id="a72b3-135">右键单击数据库，指向 **“任务”** ，再单击 **“备份”** 。</span><span class="sxs-lookup"><span data-stu-id="a72b3-135">Right-click the database, point to **Tasks**, and then click **Back Up**.</span></span> <span data-ttu-id="a72b3-136">将出现 **“备份数据库”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="a72b3-136">The **Back Up Database** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="a72b3-137">在 **“数据库”** 列表框中，验证数据库名称。</span><span class="sxs-lookup"><span data-stu-id="a72b3-137">In the **Database** list box, verify the database name.</span></span> <span data-ttu-id="a72b3-138">您也可以从列表中选择其他数据库。</span><span class="sxs-lookup"><span data-stu-id="a72b3-138">You can optionally select a different database from the list.</span></span>  
  
     <span data-ttu-id="a72b3-139">可以执行任意恢复模式（完整、大容量日志或简单）的差异备份。</span><span class="sxs-lookup"><span data-stu-id="a72b3-139">You can perform a differential backup for any recovery model (full, bulk-logged, or simple).</span></span>  
  
5.  <span data-ttu-id="a72b3-140">在 **“备份类型”** 列表框中，选择 **“差异”** 。</span><span class="sxs-lookup"><span data-stu-id="a72b3-140">In the **Backup type** list box, select **Differential**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="a72b3-141"> 选择了 **“差异”** 后，请验证是否清除了 **“仅复制备份”** 复选框。</span><span class="sxs-lookup"><span data-stu-id="a72b3-141">When **Differential** is selected, verify that the **Copy Only Backup** check box is cleared.</span></span>  
  
6.  <span data-ttu-id="a72b3-142">对于 **“备份组件”** ，请单击 **“数据库”** 。</span><span class="sxs-lookup"><span data-stu-id="a72b3-142">For **Backup component**, click **Database**.</span></span>  
  
7.  <span data-ttu-id="a72b3-143">可以接受 **“名称”** 文本框中建议的默认备份集名称，也可以为备份集输入其他名称。</span><span class="sxs-lookup"><span data-stu-id="a72b3-143">Either accept the default backup set name suggested in the **Name** text box, or enter a different name for the backup set.</span></span>  
  
8.  <span data-ttu-id="a72b3-144">或者，在 **“说明”** 文本框中，输入备份集的说明。</span><span class="sxs-lookup"><span data-stu-id="a72b3-144">Optionally, in the **Description** text box, enter a description of the backup set.</span></span>  
  
9. <span data-ttu-id="a72b3-145">指定备份集的过期时间：</span><span class="sxs-lookup"><span data-stu-id="a72b3-145">Specify when the backup set will expire:</span></span>  
  
    -   <span data-ttu-id="a72b3-146">若要使备份集在特定天数后过期，请单击 **“之后”** （默认选项），并输入备份集从创建到过期所需的天数。</span><span class="sxs-lookup"><span data-stu-id="a72b3-146">To have the backup set expire after a specific number of days, click **After** (the default option), and enter the number of days after set creation that the set will expire.</span></span> <span data-ttu-id="a72b3-147">此值范围为 0 到 99999 天；0 天表示备份集将永不过期。</span><span class="sxs-lookup"><span data-stu-id="a72b3-147">This value can be from 0 to 99999 days; a value of 0 days means that the backup set will never expire.</span></span>  
  
         <span data-ttu-id="a72b3-148">默认值在 **“服务器属性”** 对话框（位于 **“数据库设置”** 页上）的 **“默认备份媒体保持期(天)”** 选项中设置。</span><span class="sxs-lookup"><span data-stu-id="a72b3-148">The default value is set in the **Default backup media retention (in days)** option of the **Server Properties** dialog box (**Database Settings** page).</span></span> <span data-ttu-id="a72b3-149">若要访问它，请在对象资源管理器中右键单击服务器名称，选择属性，再选择“数据库设置”  页。</span><span class="sxs-lookup"><span data-stu-id="a72b3-149">To access this, right-click the server name in Object Explorer and select properties; then select the **Database Settings** page.</span></span>  
  
    -   <span data-ttu-id="a72b3-150">若要使备份集在特定日期过期，请单击 **“在”** ，并输入备份集的过期日期。</span><span class="sxs-lookup"><span data-stu-id="a72b3-150">To have the backup set expire on a specific date, click **On**, and enter the date on which the set will expire.</span></span>  
  
10. <span data-ttu-id="a72b3-151">通过单击 **“磁盘”** 或 **“磁带”** ，选择备份目标的类型。</span><span class="sxs-lookup"><span data-stu-id="a72b3-151">Choose the type of backup destination by clicking **Disk** or **Tape**.</span></span> <span data-ttu-id="a72b3-152">若要选择包含单个介质集的多个磁盘或磁带机（最多为 64 个）的路径，请单击 **“添加”** 。</span><span class="sxs-lookup"><span data-stu-id="a72b3-152">To select the path of up to 64 disk or tape drives containing a single media set, click **Add**.</span></span> <span data-ttu-id="a72b3-153">选择的路径将显示在 **“备份到”** 列表框中。</span><span class="sxs-lookup"><span data-stu-id="a72b3-153">The selected paths are displayed in the **Backup to** list box.</span></span>  
  
     <span data-ttu-id="a72b3-154">若要删除备份目标，请选择该备份目标并单击 **“删除”** 。</span><span class="sxs-lookup"><span data-stu-id="a72b3-154">To remove a backup destination, select it and click **Remove**.</span></span> <span data-ttu-id="a72b3-155">若要查看备份目标的内容，请选择该备份目标并单击 **“内容”** 。</span><span class="sxs-lookup"><span data-stu-id="a72b3-155">To view the contents of a backup destination, select it and click **Contents**.</span></span>  
  
11. <span data-ttu-id="a72b3-156">若要查看或选择高级选项，请在 **“选择页”** 窗格中单击 **“选项”** 。</span><span class="sxs-lookup"><span data-stu-id="a72b3-156">To view or select the advanced options, click **Options** in the **Select a page** pane.</span></span>  
  
12. <span data-ttu-id="a72b3-157">可以通过单击以下选项之一来选择 **“覆盖介质”** 选项：</span><span class="sxs-lookup"><span data-stu-id="a72b3-157">Select an **Overwrite Media** option, by clicking one of the following:</span></span>  
  
    -   <span data-ttu-id="a72b3-158">**备份到现有介质集**</span><span class="sxs-lookup"><span data-stu-id="a72b3-158">**Back up to the existing media set**</span></span>  
  
         <span data-ttu-id="a72b3-159">对于此选项，请单击 **“追加到现有备份集”** 或 **“覆盖所有现有备份集”** 。</span><span class="sxs-lookup"><span data-stu-id="a72b3-159">For this option, click either **Append to the existing backup set** or **Overwrite all existing backup sets**.</span></span> <span data-ttu-id="a72b3-160">或者，选中 **“检查介质集名称和备份集过期时间”** 复选框，并在 **“介质集名称”** 文本框中输入名称（可选）。</span><span class="sxs-lookup"><span data-stu-id="a72b3-160">Optionally, check the **Check media set name and backup set expiration** check box and, optionally, enter a name in the **Media set name** text box.</span></span> <span data-ttu-id="a72b3-161">如果没有指定名称，将使用空白名称创建介质集。</span><span class="sxs-lookup"><span data-stu-id="a72b3-161">If no name is specified, a media set with a blank name is created.</span></span> <span data-ttu-id="a72b3-162">如果指定了某个介质集名称，将检查该介质（磁带或磁盘）的实际名称是否与在此输入的名称相符。</span><span class="sxs-lookup"><span data-stu-id="a72b3-162">If you specify a media set name, the media (tape or disk) is checked to see if the actual name matches the name you enter here.</span></span>  
  
         <span data-ttu-id="a72b3-163">如果将介质名称保留空白，并选中该框以便与介质进行核对，则只有当介质上的介质名称也是空白时才能成功。</span><span class="sxs-lookup"><span data-stu-id="a72b3-163">If you leave the media name blank and check the box to check it against the media, success will equal the media name on the media also being blank.</span></span>  
  
    -   <span data-ttu-id="a72b3-164">**备份到新介质集并清除所有现有备份集**</span><span class="sxs-lookup"><span data-stu-id="a72b3-164">**Back up to a new media set, and erase all existing backup sets**</span></span>  
  
         <span data-ttu-id="a72b3-165">对于该选项，请在 **“新建介质集名称”** 文本框中输入名称，并在 **“新建介质集说明”** 文本框中描述介质集（可选）。</span><span class="sxs-lookup"><span data-stu-id="a72b3-165">For this option, enter a name in the **New media set name** text box, and, optionally, describe the media set in the **New media set description** text box.</span></span>  
  
13. <span data-ttu-id="a72b3-166">或者，在 **“可靠性”** 部分中，选中：</span><span class="sxs-lookup"><span data-stu-id="a72b3-166">In the **Reliability** section, optionally, check:</span></span>  
  
    -   <span data-ttu-id="a72b3-167">**完成后验证备份**。</span><span class="sxs-lookup"><span data-stu-id="a72b3-167">**Verify backup when finished**.</span></span>  
  
    -   <span data-ttu-id="a72b3-168">**“写入介质前检查校验和”** 和 **“出现校验和错误时继续”** （可选）。</span><span class="sxs-lookup"><span data-stu-id="a72b3-168">**Perform checksum before writing to media**, and, optionally, **Continue on checksum error**.</span></span> <span data-ttu-id="a72b3-169">有关校验和的信息，请参阅[在备份和还原期间可能的媒体错误 (SQL Server)](possible-media-errors-during-backup-and-restore-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="a72b3-169">For information about checksums, see [Possible Media Errors During Backup and Restore &#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md).</span></span>  
  
14. <span data-ttu-id="a72b3-170">如果备份到磁带驱动器（如同 **“常规”** 页的 **“目标”** 部分指定的一样），则 **“备份后卸载磁带”** 选项处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="a72b3-170">If you are backing up to a tape drive (as specified in the **Destination** section of the **General** page), the **Unload the tape after backup** option is active.</span></span> <span data-ttu-id="a72b3-171">单击此选项可以激活 **“卸载前倒带”** 选项。</span><span class="sxs-lookup"><span data-stu-id="a72b3-171">Clicking this option activates the **Rewind the tape before unloading** option.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a72b3-172">除非备份的是事务日志（如同“常规”  页的“备份类型”  部分中指定的一样），否则“事务日志”  部分中的选项处于不活动状态。</span><span class="sxs-lookup"><span data-stu-id="a72b3-172">The options in the **Transaction log** section are inactive unless you are backing up a transaction log (as specified in the **Backup type** section of the **General** page).</span></span>  
  
15. [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] <span data-ttu-id="a72b3-173">及更高版本支持 [备份压缩](backup-compression-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="a72b3-173">and later supports [backup compression](backup-compression-sql-server.md).</span></span> <span data-ttu-id="a72b3-174">默认情况下，是否压缩备份取决于 **backup-compression default** 服务器配置选项的值。</span><span class="sxs-lookup"><span data-stu-id="a72b3-174">By default, whether a backup is compressed depends on the value of the **backup-compression default** server configuration option.</span></span> <span data-ttu-id="a72b3-175">但是，不管当前服务器级默认设置如何，都可以通过选中 **“压缩备份”** 来压缩备份，并且可以通过选中 **“不压缩备份”** 来防止压缩备份。</span><span class="sxs-lookup"><span data-stu-id="a72b3-175">However, regardless of the current server-level default, you can compress a backup by checking **Compress backup**, and you can prevent compression by checking **Do not compress backup**.</span></span>  
  
     <span data-ttu-id="a72b3-176">**查看当前备份压缩默认值**</span><span class="sxs-lookup"><span data-stu-id="a72b3-176">**To view the current backup compression default**</span></span>  
  
    -   [<span data-ttu-id="a72b3-177">查看或配置 backup compression default 服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="a72b3-177">View or Configure the backup compression default Server Configuration Option</span></span>](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)  
  
    > [!NOTE]  
    >  <span data-ttu-id="a72b3-178">另外，可以使用维护计划向导创建差异数据库备份。</span><span class="sxs-lookup"><span data-stu-id="a72b3-178">Alternatively, you can use the Maintenance Plan Wizard to create differential database backups.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="a72b3-179">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a72b3-179">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-differential-database-backup"></a><span data-ttu-id="a72b3-180">创建差异数据库备份</span><span class="sxs-lookup"><span data-stu-id="a72b3-180">To create a differential database backup</span></span>  
  
1.  <span data-ttu-id="a72b3-181">执行 BACKUP DATABASE 语句可以创建差异数据库备份，同时指定：</span><span class="sxs-lookup"><span data-stu-id="a72b3-181">Execute the BACKUP DATABASE statement to create the differential database backup, specifying:</span></span>  
  
    -   <span data-ttu-id="a72b3-182">要备份的数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="a72b3-182">The name of the database to back up.</span></span>  
  
    -   <span data-ttu-id="a72b3-183">写入完整数据库备份的备份设备。</span><span class="sxs-lookup"><span data-stu-id="a72b3-183">The backup device where the full database backup is written.</span></span>  
  
    -   <span data-ttu-id="a72b3-184">DIFFERENTIAL 子句，用于指定仅备份自上次创建完整数据库备份之后已更改的数据库部分。</span><span class="sxs-lookup"><span data-stu-id="a72b3-184">The DIFFERENTIAL clause, to specify that only the parts of the database that have changed after the last full database backup was created are backed up.</span></span>  
  
     <span data-ttu-id="a72b3-185">要求语法为：</span><span class="sxs-lookup"><span data-stu-id="a72b3-185">The required syntax is:</span></span>  
  
     <span data-ttu-id="a72b3-186">BACKUP DATABASE *database_name* TO <backup_device> WITH DIFFERENTIAL</span><span class="sxs-lookup"><span data-stu-id="a72b3-186">BACKUP DATABASE *database_name* TO <backup_device> WITH DIFFERENTIAL</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="a72b3-187">示例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="a72b3-187">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="a72b3-188">以下示例为 `MyAdvWorks` 数据库创建完整数据库备份和差异数据库备份。</span><span class="sxs-lookup"><span data-stu-id="a72b3-188">This example creates a full and a differential database backup for the `MyAdvWorks` database.</span></span>  
  
```sql  
-- Create a full database backup first.  
BACKUP DATABASE MyAdvWorks   
   TO MyAdvWorks_1   
   WITH INIT;  
GO  
-- Time elapses.  
-- Create a differential database backup, appending the backup  
-- to the backup device containing the full database backup.  
BACKUP DATABASE MyAdvWorks  
   TO MyAdvWorks_1  
   WITH DIFFERENTIAL;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="a72b3-189">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a72b3-189">See Also</span></span>  
 <span data-ttu-id="a72b3-190">[差异备份 (SQL Server)](differential-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a72b3-190">[Differential Backups &#40;SQL Server&#41;](differential-backups-sql-server.md) </span></span>  
 <span data-ttu-id="a72b3-191">[创建完整数据库备份 (SQL Server)](create-a-full-database-backup-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a72b3-191">[Create a Full Database Backup &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md) </span></span>  
 <span data-ttu-id="a72b3-192">[备份文件和文件组 (SQL Server)](back-up-files-and-filegroups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a72b3-192">[Back Up Files and Filegroups &#40;SQL Server&#41;](back-up-files-and-filegroups-sql-server.md) </span></span>  
 <span data-ttu-id="a72b3-193">[还原差异数据库备份 (SQL Server)](restore-a-differential-database-backup-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a72b3-193">[Restore a Differential Database Backup &#40;SQL Server&#41;](restore-a-differential-database-backup-sql-server.md) </span></span>  
 <span data-ttu-id="a72b3-194">[还原事务日志备份 (SQL Server)](restore-a-transaction-log-backup-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a72b3-194">[Restore a Transaction Log Backup &#40;SQL Server&#41;](restore-a-transaction-log-backup-sql-server.md) </span></span>  
 <span data-ttu-id="a72b3-195">[维护计划](../maintenance-plans/maintenance-plans.md) </span><span class="sxs-lookup"><span data-stu-id="a72b3-195">[Maintenance Plans](../maintenance-plans/maintenance-plans.md) </span></span>  
 [<span data-ttu-id="a72b3-196">完整文件备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="a72b3-196">Full File Backups &#40;SQL Server&#41;</span></span>](full-file-backups-sql-server.md)  
  
  
