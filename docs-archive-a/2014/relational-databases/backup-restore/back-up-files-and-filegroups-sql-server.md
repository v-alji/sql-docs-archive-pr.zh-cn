---
title: 备份文件和文件组 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- backing up filegroups [SQL Server]
- file backups [SQL Server], how-to topics
- backing up files [SQL Server]
- backups [SQL Server], creating
- filegroups [SQL Server], backing up
ms.assetid: a0d3a567-7d8b-4cfe-a505-d197b9a51f70
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7affc90b064febaa70e0a67108074f412b4bbf00
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577743"
---
# <a name="back-up-files-and-filegroups-sql-server"></a><span data-ttu-id="e1938-102">备份文件和文件组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="e1938-102">Back Up Files and Filegroups (SQL Server)</span></span>
  <span data-ttu-id="e1938-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]或 PowerShell 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中备份文件和文件组。</span><span class="sxs-lookup"><span data-stu-id="e1938-103">This topic describes how to back up files and filegroups in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or PowerShell.</span></span> <span data-ttu-id="e1938-104">当数据库大小和性能要求使完整数据库备份显得不切实际，则可以创建文件备份。</span><span class="sxs-lookup"><span data-stu-id="e1938-104">When the database size and performance requirements make a full database backup impractical, you can create a file backup instead.</span></span> <span data-ttu-id="e1938-105">文件备份  包含一个或多个文件（或文件组）中的所有数据。</span><span class="sxs-lookup"><span data-stu-id="e1938-105">A *file backup* contains all the data in one or more files (or filegroups).</span></span> <span data-ttu-id="e1938-106">有关文件备份的详细信息，请参阅 [完整文件备份 (SQL Server)](full-file-backups-sql-server.md) 和 [差异备份 (SQL Server)](differential-backups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="e1938-106">For more information about file backups, see [Full File Backups &#40;SQL Server&#41;](full-file-backups-sql-server.md) and [Differential Backups &#40;SQL Server&#41;](differential-backups-sql-server.md).</span></span>  
  
 <span data-ttu-id="e1938-107">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="e1938-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="e1938-108">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="e1938-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="e1938-109">限制和局限</span><span class="sxs-lookup"><span data-stu-id="e1938-109">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="e1938-110">建议</span><span class="sxs-lookup"><span data-stu-id="e1938-110">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="e1938-111">安全性</span><span class="sxs-lookup"><span data-stu-id="e1938-111">Security</span></span>](#Security)  
  
-   <span data-ttu-id="e1938-112">**若要备份文件和文件组，可使用：**</span><span class="sxs-lookup"><span data-stu-id="e1938-112">**To back up files and filegroups, using:**</span></span>  
  
     [<span data-ttu-id="e1938-113">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e1938-113">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="e1938-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e1938-114">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="e1938-115">PowerShell</span><span class="sxs-lookup"><span data-stu-id="e1938-115">PowerShell</span></span>](#PowerShellProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="e1938-116">开始之前</span><span class="sxs-lookup"><span data-stu-id="e1938-116">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="e1938-117">限制和局限</span><span class="sxs-lookup"><span data-stu-id="e1938-117">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="e1938-118">不允许在显式或隐式事务中使用 BACKUP 语句。</span><span class="sxs-lookup"><span data-stu-id="e1938-118">The BACKUP statement is not allowed in an explicit or implicit transaction.</span></span>  
  
-   <span data-ttu-id="e1938-119">在简单恢复模式下，必须一起备份所有读/写文件。</span><span class="sxs-lookup"><span data-stu-id="e1938-119">Under the simple recovery model, read/write files must all be backed up together.</span></span> <span data-ttu-id="e1938-120">这有助于确保将数据库还原到一致的时点。</span><span class="sxs-lookup"><span data-stu-id="e1938-120">This helps make sure that the database can be restored to a consistent point in time.</span></span> <span data-ttu-id="e1938-121">请使用 READ_WRITE_FILEGROUPS 选项，而不是逐个指定每个读/写文件或文件组。</span><span class="sxs-lookup"><span data-stu-id="e1938-121">Instead of individually specifying each read/write file or filegroup, use the READ_WRITE_FILEGROUPS option.</span></span> <span data-ttu-id="e1938-122">此选项用于备份数据库中的所有读/写文件组。</span><span class="sxs-lookup"><span data-stu-id="e1938-122">This option backs up all the read/write filegroups in the database.</span></span> <span data-ttu-id="e1938-123">通过指定 READ_WRITE_FILEGROUPS 创建的备份称为*部分备份*。</span><span class="sxs-lookup"><span data-stu-id="e1938-123">A backup that is created by specifying READ_WRITE_FILEGROUPS is known as a *partial backup*.</span></span> <span data-ttu-id="e1938-124">有关详细信息，请参阅[部分备份 (SQL Server)](partial-backups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="e1938-124">For more information, see [Partial Backups &#40;SQL Server&#41;](partial-backups-sql-server.md).</span></span>  
  
-   <span data-ttu-id="e1938-125">有关限制的详细信息，请参阅 [备份概述 (SQL Server)](backup-overview-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="e1938-125">For more information about limitations and restrictions, see [Backup Overview &#40;SQL Server&#41;](backup-overview-sql-server.md).</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="e1938-126">建议</span><span class="sxs-lookup"><span data-stu-id="e1938-126">Recommendations</span></span>  
  
-   <span data-ttu-id="e1938-127">默认情况下，每个成功的备份操作都会在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误日志和系统事件日志中添加一个条目。</span><span class="sxs-lookup"><span data-stu-id="e1938-127">By default, every successful backup operation adds an entry in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log and in the system event log.</span></span> <span data-ttu-id="e1938-128">如果非常频繁地备份日志，这些成功消息会迅速累积，从而产生一个巨大的错误日志，这样会使查找其他消息变得非常困难。</span><span class="sxs-lookup"><span data-stu-id="e1938-128">If you back up the log very frequently, these success messages accumulate quickly, resulting in huge error logs that can make finding other messages difficult.</span></span> <span data-ttu-id="e1938-129">在这些情况下，如果任何脚本均不依赖于这些日志条目，则可以使用跟踪标志 3226 取消这些条目。</span><span class="sxs-lookup"><span data-stu-id="e1938-129">In such cases you can suppress these log entries by using trace flag 3226 if none of your scripts depend on those entries.</span></span> <span data-ttu-id="e1938-130">有关详细信息，请参阅[跟踪标志 (Transact-SQL)](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="e1938-130">For more information, see [Trace Flags &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="e1938-131">Security</span><span class="sxs-lookup"><span data-stu-id="e1938-131">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="e1938-132">权限</span><span class="sxs-lookup"><span data-stu-id="e1938-132">Permissions</span></span>  
 <span data-ttu-id="e1938-133">默认情况下，为 **sysadmin** 固定服务器角色以及 **db_owner** 和 **db_backupoperator** 固定数据库角色的成员授予 BACKUP DATABASE 和 BACKUP LOG 权限。</span><span class="sxs-lookup"><span data-stu-id="e1938-133">BACKUP DATABASE and BACKUP LOG permissions default to members of the **sysadmin** fixed server role and the **db_owner** and **db_backupoperator** fixed database roles.</span></span>  
  
 <span data-ttu-id="e1938-134">备份设备的物理文件的所有权和权限问题可能会妨碍备份操作。</span><span class="sxs-lookup"><span data-stu-id="e1938-134">Ownership and permission problems on the backup device's physical file can interfere with a backup operation.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="e1938-135">必须能够读取和写入设备；运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务的帐户必须具有写入权限。</span><span class="sxs-lookup"><span data-stu-id="e1938-135">must be able to read and write to the device; the account under which the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service runs must have write permissions.</span></span> <span data-ttu-id="e1938-136">但是，用于在系统表中为备份设备添加项目的 [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql)不检查文件访问权限。</span><span class="sxs-lookup"><span data-stu-id="e1938-136">However, [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql), which adds an entry for a backup device in the system tables, does not check file access permissions.</span></span> <span data-ttu-id="e1938-137">备份设备物理文件的这些问题可能直到为备份或还原而访问物理资源时才会出现。</span><span class="sxs-lookup"><span data-stu-id="e1938-137">Such problems on the backup device's physical file may not appear until the physical resource is accessed when the backup or restore is attempted.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="e1938-138">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e1938-138">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-back-up-database-files-and-filegroups"></a><span data-ttu-id="e1938-139">备份数据库文件和文件组</span><span class="sxs-lookup"><span data-stu-id="e1938-139">To back up database files and filegroups</span></span>  
  
1.  <span data-ttu-id="e1938-140">连接到相应的 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]实例之后，在对象资源管理器中，单击服务器名称以展开服务器树。</span><span class="sxs-lookup"><span data-stu-id="e1938-140">After connecting to the appropriate instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="e1938-141">展开 **“数据库”** ，然后根据数据库的不同，选择用户数据库，或展开 **“系统数据库”** ，再选择系统数据库。</span><span class="sxs-lookup"><span data-stu-id="e1938-141">Expand **Databases**, and, depending on the database, either select a user database or expand **System Databases** and select a system database.</span></span>  
  
3.  <span data-ttu-id="e1938-142">右键单击数据库，指向 **“任务”** ，再单击 **“备份”** 。</span><span class="sxs-lookup"><span data-stu-id="e1938-142">Right-click the database, point to **Tasks**, and then click **Back Up**.</span></span> <span data-ttu-id="e1938-143">将出现 **“备份数据库”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="e1938-143">The **Back Up Database** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="e1938-144">在 **“数据库”** 列表中，验证数据库名称。</span><span class="sxs-lookup"><span data-stu-id="e1938-144">In the **Database** list, verify the database name.</span></span> <span data-ttu-id="e1938-145">您也可以从列表中选择其他数据库。</span><span class="sxs-lookup"><span data-stu-id="e1938-145">You can optionally select a different database from the list.</span></span>  
  
5.  <span data-ttu-id="e1938-146">在 **“备份类型”** 列表中，选择 **“完整”** 或 **“差异”** 。</span><span class="sxs-lookup"><span data-stu-id="e1938-146">In the **Backup type** list, select **Full** or **Differential**.</span></span>  
  
6.  <span data-ttu-id="e1938-147">对于 **“备份组件”** 选项，单击 **“文件和文件组”** 。</span><span class="sxs-lookup"><span data-stu-id="e1938-147">For the **Backup component** option, click **File and Filegroups**.</span></span>  
  
7.  <span data-ttu-id="e1938-148">在 **“选择文件和文件组”** 对话框中，选择要备份的文件和文件组。</span><span class="sxs-lookup"><span data-stu-id="e1938-148">In the **Select Files and Filegroups** dialog box, select the files and filegroups you want to back up.</span></span> <span data-ttu-id="e1938-149">可以选择一个或多个单个文件，也可以复选文件组的框，从而自动选择该文件组中的所有文件。</span><span class="sxs-lookup"><span data-stu-id="e1938-149">You can select one or more individual files or check the box for a filegroup to automatically select all the files in that filegroup.</span></span>  
  
8.  <span data-ttu-id="e1938-150">可以接受 **“名称”** 文本框中建议的默认备份集名称，也可以为备份集输入其他名称。</span><span class="sxs-lookup"><span data-stu-id="e1938-150">Either accept the default backup set name suggested in the **Name** text box, or enter a different name for the backup set.</span></span>  
  
9. <span data-ttu-id="e1938-151">或者，在 **“说明”** 文本框中，输入备份集的说明。</span><span class="sxs-lookup"><span data-stu-id="e1938-151">Optionally, in the **Description** text box, enter a description of the backup set.</span></span>  
  
10. <span data-ttu-id="e1938-152">指定备份集的过期时间：</span><span class="sxs-lookup"><span data-stu-id="e1938-152">Specify when the backup set will expire:</span></span>  
  
    -   <span data-ttu-id="e1938-153">若要让备份集在特定天数之后过期，请单击“之后”\*\*\*\*（默认选项）。</span><span class="sxs-lookup"><span data-stu-id="e1938-153">To have the backup set expire after a specific number of days, click **After** (the default option).</span></span> <span data-ttu-id="e1938-154">然后，输入备份集自创建后到过期日之间的天数。</span><span class="sxs-lookup"><span data-stu-id="e1938-154">Then, enter the number of days after set creation that the set will expire.</span></span> <span data-ttu-id="e1938-155">此值范围为 0 到 99999 天；0 天表示备份集将永不过期。</span><span class="sxs-lookup"><span data-stu-id="e1938-155">This value can be from 0 to 99999 days; a value of 0 days means that the backup set will never expire.</span></span>  
  
         <span data-ttu-id="e1938-156">默认值在 **“服务器属性”** 对话框（位于 **“数据库设置”** 页上）的 **“默认备份媒体保持期(天)”** 选项中设置。</span><span class="sxs-lookup"><span data-stu-id="e1938-156">The default value is set in the **Default backup media retention (in days)** option of the **Server Properties** dialog box (**Database Settings** page).</span></span> <span data-ttu-id="e1938-157">若要访问此选项，请在对象资源管理器中右键单击服务器名称，并选择“属性”，然后选择“数据库设置”  页。</span><span class="sxs-lookup"><span data-stu-id="e1938-157">To access this option, right-click the server name in Object Explorer and select properties; then select the **Database Settings** page.</span></span>  
  
    -   <span data-ttu-id="e1938-158">若要使备份集在特定日期过期，请单击 **“在”** ，并输入备份集的过期日期。</span><span class="sxs-lookup"><span data-stu-id="e1938-158">To have the backup set expire on a specific date, click **On**, and enter the date on which the set will expire.</span></span>  
  
11. <span data-ttu-id="e1938-159">通过单击 **“磁盘”** 或 **“磁带”** ，选择备份目标的类型。</span><span class="sxs-lookup"><span data-stu-id="e1938-159">Choose the type of backup destination by clicking **Disk** or **Tape**.</span></span> <span data-ttu-id="e1938-160">若要选择包含单个介质集的多个磁盘驱动器或磁带机（最多为 64 个）的路径，请单击 **“添加”** 。</span><span class="sxs-lookup"><span data-stu-id="e1938-160">To select the paths of up to 64 disk or tape drives that contain a single media set, click **Add**.</span></span> <span data-ttu-id="e1938-161">所选路径将显示在 **“备份到”** 列表中。</span><span class="sxs-lookup"><span data-stu-id="e1938-161">The selected paths are displayed in the **Backup to** list.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e1938-162">若要删除备份目标，请选择该备份目标并单击 **“删除”** 。</span><span class="sxs-lookup"><span data-stu-id="e1938-162">To remove a backup destination, select it and click **Remove**.</span></span> <span data-ttu-id="e1938-163">若要查看备份目标的内容，请选择该备份目标并单击 **“内容”** 。</span><span class="sxs-lookup"><span data-stu-id="e1938-163">To view the contents of a backup destination, select it and click **Contents**.</span></span>  
  
12. <span data-ttu-id="e1938-164">若要查看或选择高级选项，请在 **“选择页”** 窗格中单击 **“选项”** 。</span><span class="sxs-lookup"><span data-stu-id="e1938-164">To view or select the advanced options, click **Options** in the **Select a page** pane.</span></span>  
  
13. <span data-ttu-id="e1938-165">可以通过单击以下选项之一来选择 **“覆盖介质”** 选项：</span><span class="sxs-lookup"><span data-stu-id="e1938-165">Select an **Overwrite Media** option, by clicking one of the following:</span></span>  
  
    -   <span data-ttu-id="e1938-166">**备份到现有介质集**</span><span class="sxs-lookup"><span data-stu-id="e1938-166">**Back up to the existing media set**</span></span>  
  
         <span data-ttu-id="e1938-167">对于此选项，请单击 **“追加到现有备份集”** 或 **“覆盖所有现有备份集”** 。</span><span class="sxs-lookup"><span data-stu-id="e1938-167">For this option, click either **Append to the existing backup set** or **Overwrite all existing backup sets**.</span></span> <span data-ttu-id="e1938-168">有关备份到现有媒体集的信息，请参阅[媒体集、媒体簇和备份集 (SQL Server)](media-sets-media-families-and-backup-sets-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="e1938-168">For information about backing up to an existing media set, see [Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md).</span></span>  
  
         <span data-ttu-id="e1938-169">或者选择 **“检查介质集名称和备份集过期时间”** ，以使备份操作对介质集和备份集的过期日期和时间进行验证。</span><span class="sxs-lookup"><span data-stu-id="e1938-169">Optionally, select **Check media set name and backup set expiration** to cause the backup operation to verify the date and time at which the media set and backup set expire.</span></span>  
  
         <span data-ttu-id="e1938-170">或者在 **“介质集名称”** 文本框中输入名称。</span><span class="sxs-lookup"><span data-stu-id="e1938-170">Optionally, enter a name in the **Media set name** text box.</span></span> <span data-ttu-id="e1938-171">如果没有指定名称，将使用空白名称创建介质集。</span><span class="sxs-lookup"><span data-stu-id="e1938-171">If no name is specified, a media set with a blank name is created.</span></span> <span data-ttu-id="e1938-172">如果指定了介质集名称，将检查介质（磁带或磁盘），以确定实际名称是否与此处输入的名称匹配。</span><span class="sxs-lookup"><span data-stu-id="e1938-172">If you specify a media set name, the media (tape or disk) is checked to see whether the actual name matches the name that you enter here.</span></span>  
  
         <span data-ttu-id="e1938-173">如果将介质名称保留空白，并选中该框以便与介质进行核对，则只有当介质上的介质名称也是空白时才能成功。</span><span class="sxs-lookup"><span data-stu-id="e1938-173">If you leave the media name blank and check the box to check it against the media, success will equal the media name on the media also being blank.</span></span>  
  
    -   <span data-ttu-id="e1938-174">**备份到新介质集并清除所有现有备份集**</span><span class="sxs-lookup"><span data-stu-id="e1938-174">**Back up to a new media set, and erase all existing backup sets**</span></span>  
  
         <span data-ttu-id="e1938-175">对于该选项，请在 **“新建介质集名称”** 文本框中输入名称，并在 **“新建介质集说明”** 文本框中描述介质集（可选）。</span><span class="sxs-lookup"><span data-stu-id="e1938-175">For this option, enter a name in the **New media set name** text box, and, optionally, describe the media set in the **New media set description** text box.</span></span> <span data-ttu-id="e1938-176">有关创建新媒体集的详细信息，请参阅[媒体集、媒体簇和备份集 (SQL Server)](media-sets-media-families-and-backup-sets-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="e1938-176">For more information about creating a new media set, see [Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md).</span></span>  
  
14. <span data-ttu-id="e1938-177">在 "**可靠性**" 部分中，可以选择检查：</span><span class="sxs-lookup"><span data-stu-id="e1938-177">In the **Reliability** section, optionally check:</span></span>  
  
    -   <span data-ttu-id="e1938-178">**完成后验证备份**。</span><span class="sxs-lookup"><span data-stu-id="e1938-178">**Verify backup when finished**.</span></span>  
  
    -   <span data-ttu-id="e1938-179">**“写入介质前检查校验和”** 和 **“出现校验和错误时继续”** （可选）。</span><span class="sxs-lookup"><span data-stu-id="e1938-179">**Perform checksum before writing to media**, and, optionally, **Continue on checksum error**.</span></span> <span data-ttu-id="e1938-180">有关校验和的详细信息，请参阅[在备份和还原期间可能的媒体错误 (SQL Server)](possible-media-errors-during-backup-and-restore-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="e1938-180">For more information about checksums, see [Possible Media Errors During Backup and Restore &#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md).</span></span>  
  
15. <span data-ttu-id="e1938-181">如果备份到磁带驱动器（如同 **“常规”** 页的 **“目标”** 部分指定的一样），则 **“备份后卸载磁带”** 选项处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="e1938-181">If you are backing up to a tape drive (as specified in the **Destination** section of the **General** page), the **Unload the tape after backup** option is active.</span></span> <span data-ttu-id="e1938-182">单击此选项可以启用 **“卸载前倒带”** 选项。</span><span class="sxs-lookup"><span data-stu-id="e1938-182">Clicking this option enables the **Rewind the tape before unloading** option.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e1938-183">除非备份的是事务日志（如同“常规”  页的“备份类型”  部分中指定的一样），否则“事务日志”  部分中的选项处于不活动状态。</span><span class="sxs-lookup"><span data-stu-id="e1938-183">The options in the **Transaction log** section are inactive unless you are backing up a transaction log (as specified in the **Backup type** section of the **General** page).</span></span>  
  
16. [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] <span data-ttu-id="e1938-184">及更高版本支持 [备份压缩](backup-compression-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="e1938-184">and later versions support [backup compression](backup-compression-sql-server.md).</span></span> <span data-ttu-id="e1938-185">默认情况下，是否压缩备份取决于 **backup-compression default** 服务器配置选项的值。</span><span class="sxs-lookup"><span data-stu-id="e1938-185">By default, whether a backup is compressed depends on the value of the **backup-compression default** server configuration option.</span></span> <span data-ttu-id="e1938-186">但是，不管当前服务器级默认设置如何，都可以通过选中 **“压缩备份”** 来压缩备份，并且可以通过选中 **“不压缩备份”** 来防止压缩备份。</span><span class="sxs-lookup"><span data-stu-id="e1938-186">However, regardless of the current server-level default, you can compress a backup by checking **Compress backup**, and you can prevent compression by checking **Do not compress backup**.</span></span>  
  
     <span data-ttu-id="e1938-187">**查看当前备份压缩默认值**</span><span class="sxs-lookup"><span data-stu-id="e1938-187">**To view the current backup compression default**</span></span>  
  
    -   [<span data-ttu-id="e1938-188">查看或配置 backup compression default 服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="e1938-188">View or Configure the backup compression default Server Configuration Option</span></span>](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="e1938-189">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e1938-189">Using Transact-SQL</span></span>  
  
#### <a name="to-back-up-files-and-filegroups"></a><span data-ttu-id="e1938-190">备份文件和文件组</span><span class="sxs-lookup"><span data-stu-id="e1938-190">To back up files and filegroups</span></span>  
  
1.  <span data-ttu-id="e1938-191">若要创建文件或文件组备份，请使用 [BACKUP DATABASE <file_or_filegroup>](/sql/t-sql/statements/backup-transact-sql) 语句。</span><span class="sxs-lookup"><span data-stu-id="e1938-191">To create a file or filegroup backup, use a [BACKUP DATABASE <file_or_filegroup>](/sql/t-sql/statements/backup-transact-sql) statement.</span></span> <span data-ttu-id="e1938-192">此语句至少必须指定以下各项：</span><span class="sxs-lookup"><span data-stu-id="e1938-192">Minimally, this statement must specify the following:</span></span>  
  
    -   <span data-ttu-id="e1938-193">数据库名称。</span><span class="sxs-lookup"><span data-stu-id="e1938-193">The database name.</span></span>  
  
    -   <span data-ttu-id="e1938-194">FILE 或 FILEGROUP 子句（为每个文件或文件组分别指定）。</span><span class="sxs-lookup"><span data-stu-id="e1938-194">A FILE or FILEGROUP clause for each file or filegroup, respectively.</span></span>  
  
    -   <span data-ttu-id="e1938-195">将写入完整备份的备份设备。</span><span class="sxs-lookup"><span data-stu-id="e1938-195">The backup device on which the full backup will be written.</span></span>  
  
     <span data-ttu-id="e1938-196">用于文件备份的基本 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语法如下：</span><span class="sxs-lookup"><span data-stu-id="e1938-196">The basic [!INCLUDE[tsql](../../includes/tsql-md.md)] syntax for a file backup is:</span></span>  
  
     <span data-ttu-id="e1938-197">BACKUP DATABASE *database*</span><span class="sxs-lookup"><span data-stu-id="e1938-197">BACKUP DATABASE *database*</span></span>  
  
     <span data-ttu-id="e1938-198">{ FILE **=** logical_file_name  | FILEGROUP **=** logical_filegroup_name  } [ **,** ...f  ]</span><span class="sxs-lookup"><span data-stu-id="e1938-198">{ FILE **=**_logical_file_name_ | FILEGROUP **=**_logical_filegroup_name_ } [ **,**...*f* ]</span></span>  
  
     <span data-ttu-id="e1938-199">TO backup_device  [ **,** ...*n* ]</span><span class="sxs-lookup"><span data-stu-id="e1938-199">TO *backup_device* [ **,**...*n* ]</span></span>  
  
     <span data-ttu-id="e1938-200">[ WITH with_options  [ **,** ...*o* ] ] ;</span><span class="sxs-lookup"><span data-stu-id="e1938-200">[ WITH *with_options* [ **,**...*o* ] ] ;</span></span>  
  
    |<span data-ttu-id="e1938-201">选项</span><span class="sxs-lookup"><span data-stu-id="e1938-201">Option</span></span>|<span data-ttu-id="e1938-202">说明</span><span class="sxs-lookup"><span data-stu-id="e1938-202">Description</span></span>|  
    |------------|-----------------|  
    |<span data-ttu-id="e1938-203">*database*</span><span class="sxs-lookup"><span data-stu-id="e1938-203">*database*</span></span>|<span data-ttu-id="e1938-204">备份事务日志、部分数据库或完整的数据库时所用的源数据库。</span><span class="sxs-lookup"><span data-stu-id="e1938-204">Is the database from which the transaction log, partial database, or complete database is backed up.</span></span>|  
    |<span data-ttu-id="e1938-205">FILE **=** logical_file_name </span><span class="sxs-lookup"><span data-stu-id="e1938-205">FILE **=**_logical_file_name_</span></span>|<span data-ttu-id="e1938-206">指定要包含在文件备份中的文件的逻辑名称。</span><span class="sxs-lookup"><span data-stu-id="e1938-206">Specifies the logical name of a file to include in the file backup.</span></span>|  
    |<span data-ttu-id="e1938-207">FILEGROUP **=** logical_filegroup_name </span><span class="sxs-lookup"><span data-stu-id="e1938-207">FILEGROUP **=**_logical_filegroup_name_</span></span>|<span data-ttu-id="e1938-208">指定要包含在文件备份中的文件组的逻辑名称。</span><span class="sxs-lookup"><span data-stu-id="e1938-208">Specifies the logical name of a filegroup to include in the file backup.</span></span> <span data-ttu-id="e1938-209">在简单恢复模式下，只允许对只读文件组执行文件组备份。</span><span class="sxs-lookup"><span data-stu-id="e1938-209">Under the simple recovery model, a filegroup backup is allowed only for a read-only filegroup.</span></span>|  
    |<span data-ttu-id="e1938-210">[ **,** ...*f* ]</span><span class="sxs-lookup"><span data-stu-id="e1938-210">[ **,**...*f* ]</span></span>|<span data-ttu-id="e1938-211">表示可以指定多个文件和文件组的占位符。</span><span class="sxs-lookup"><span data-stu-id="e1938-211">Is a placeholder that indicates that multiple files and filegroups may be specified.</span></span> <span data-ttu-id="e1938-212">不限制文件或文件组的数量。</span><span class="sxs-lookup"><span data-stu-id="e1938-212">The number of files or filegroups is unlimited.</span></span>|  
    |<span data-ttu-id="e1938-213">*backup_device* [ **,** ...*n* ]</span><span class="sxs-lookup"><span data-stu-id="e1938-213">*backup_device* [ **,**...*n* ]</span></span>|<span data-ttu-id="e1938-214">指定一个列表，它包含 1 至 64 个用于备份操作的备份设备。</span><span class="sxs-lookup"><span data-stu-id="e1938-214">Specifies a list of from 1 to 64 backup devices to use for the backup operation.</span></span> <span data-ttu-id="e1938-215">您可以指定物理备份设备，也可以指定对应的逻辑备份设备（如果已定义）。</span><span class="sxs-lookup"><span data-stu-id="e1938-215">You can specify a physical backup device, or you can specify a corresponding logical backup device, if already defined.</span></span> <span data-ttu-id="e1938-216">若要指定物理备份设备，请使用 DISK 或 TAPE 选项：</span><span class="sxs-lookup"><span data-stu-id="e1938-216">To specify a physical backup device, use the DISK or TAPE option:</span></span><br /><br /> <span data-ttu-id="e1938-217">{ DISK &#124; TAPE } **=** _physical_backup_device_name_</span><span class="sxs-lookup"><span data-stu-id="e1938-217">{ DISK &#124; TAPE } **=**_physical_backup_device_name_</span></span><br /><br /> <span data-ttu-id="e1938-218">有关详细信息，请参阅 [备份设备 (SQL Server)](backup-devices-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="e1938-218">For more information, see [Backup Devices &#40;SQL Server&#41;](backup-devices-sql-server.md).</span></span>|  
    |<span data-ttu-id="e1938-219">WITH with_options  [ **,** ...*o* ]</span><span class="sxs-lookup"><span data-stu-id="e1938-219">WITH *with_options* [ **,**...*o* ]</span></span>|<span data-ttu-id="e1938-220">您也可以指定一个或多个附加选项，如 DIFFERENTIAL。</span><span class="sxs-lookup"><span data-stu-id="e1938-220">Optionally, specifies one or more additional options, such as DIFFERENTIAL.</span></span><br /><br /> <span data-ttu-id="e1938-221">注意：差异文件备份需要以完整文件备份为基础。</span><span class="sxs-lookup"><span data-stu-id="e1938-221">Note: A differential file backup requires a full file backup as a base.</span></span> <span data-ttu-id="e1938-222">有关详细信息，请参阅[创建差异数据库备份 (SQL Server)](create-a-differential-database-backup-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="e1938-222">For more information, see [Create a Differential Database Backup &#40;SQL Server&#41;](create-a-differential-database-backup-sql-server.md).</span></span>|  
  
2.  <span data-ttu-id="e1938-223">在完整恢复模式下，还必须备份事务日志。</span><span class="sxs-lookup"><span data-stu-id="e1938-223">Under the full recovery model, you must also back up the transaction log.</span></span> <span data-ttu-id="e1938-224">若要使用一整套文件的完整备份来还原数据库，您还必须拥有足够的日志备份，以便涵盖从第一个文件备份开始的所有文件备份。</span><span class="sxs-lookup"><span data-stu-id="e1938-224">To use a complete set of full file backups to restore a database, you must also have enough log backups to span all the file backups, from the start of the first file backup.</span></span> <span data-ttu-id="e1938-225">有关详细信息，请参阅 [备份事务日志 (SQL Server)](back-up-a-transaction-log-sql-server.md)数据库还原到一个新位置并且可以选择重命名该数据库。</span><span class="sxs-lookup"><span data-stu-id="e1938-225">For more information, see [Back Up a Transaction Log &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md).</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="e1938-226">示例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="e1938-226">Examples (Transact-SQL)</span></span>  
 <span data-ttu-id="e1938-227">下面的示例备份了 `Sales` 数据库的辅助文件组的一个或多个文件。</span><span class="sxs-lookup"><span data-stu-id="e1938-227">The following examples back up one or more files of the secondary filegroups of the `Sales` database.</span></span> <span data-ttu-id="e1938-228">此数据库使用完整恢复模式并且包含以下辅助文件组：</span><span class="sxs-lookup"><span data-stu-id="e1938-228">This database uses the full recovery model and contains the following secondary filegroups:</span></span>  
  
-   <span data-ttu-id="e1938-229">名为 `SalesGroup1` 的文件组，它包含文件 `SGrp1Fi1` 和 `SGrp1Fi2`。</span><span class="sxs-lookup"><span data-stu-id="e1938-229">A filegroup named `SalesGroup1` that has the files `SGrp1Fi1` and `SGrp1Fi2`.</span></span>  
  
-   <span data-ttu-id="e1938-230">名为 `SalesGroup2` 的文件组，它包含文件 `SGrp2Fi1` 和 `SGrp2Fi2`。</span><span class="sxs-lookup"><span data-stu-id="e1938-230">A filegroup named `SalesGroup2` that has the files `SGrp2Fi1` and `SGrp2Fi2`.</span></span>  
  
#### <a name="a-creating-a-file-backup-of-two-files"></a><span data-ttu-id="e1938-231">A.</span><span class="sxs-lookup"><span data-stu-id="e1938-231">A.</span></span> <span data-ttu-id="e1938-232">为两个文件创建文件备份</span><span class="sxs-lookup"><span data-stu-id="e1938-232">Creating a file backup of two files</span></span>  
 <span data-ttu-id="e1938-233">下面的示例仅为 `SGrp1Fi2` 文件组的 `SalesGroup1` 文件和 `SGrp2Fi2` 文件组的 `SalesGroup2` 文件创建差异文件备份。</span><span class="sxs-lookup"><span data-stu-id="e1938-233">The following example creates a differential file backup of only the `SGrp1Fi2` file of the `SalesGroup1` and the `SGrp2Fi2` file of the `SalesGroup2` filegroup.</span></span>  
  
```sql  
--Backup the files in the SalesGroup1 secondary filegroup.  
BACKUP DATABASE Sales  
   FILE = 'SGrp1Fi2',   
   FILE = 'SGrp2Fi2'   
   TO DISK = 'G:\SQL Server Backups\Sales\SalesGroup1.bck';  
GO  
```  
  
#### <a name="b-creating-a-full-file-backup-of-the-secondary-filegroups"></a><span data-ttu-id="e1938-234">B.</span><span class="sxs-lookup"><span data-stu-id="e1938-234">B.</span></span> <span data-ttu-id="e1938-235">创建辅助文件组的完整文件备份</span><span class="sxs-lookup"><span data-stu-id="e1938-235">Creating a full file backup of the secondary filegroups</span></span>  
 <span data-ttu-id="e1938-236">下面的示例将对两个辅助文件组中的各个文件创建完整文件备份。</span><span class="sxs-lookup"><span data-stu-id="e1938-236">The following example creates a full file backup of every file in both of the secondary filegroups.</span></span>  
  
```sql  
--Back up the files in SalesGroup1.  
BACKUP DATABASE Sales  
   FILEGROUP = 'SalesGroup1',  
   FILEGROUP = 'SalesGroup2'  
   TO DISK = 'C:\MySQLServer\Backups\Sales\SalesFiles.bck';  
GO  
```  
  
#### <a name="c-creating-a-differential-file-backup-of-the-secondary-filegroups"></a><span data-ttu-id="e1938-237">C.</span><span class="sxs-lookup"><span data-stu-id="e1938-237">C.</span></span> <span data-ttu-id="e1938-238">创建辅助文件组的差异文件备份</span><span class="sxs-lookup"><span data-stu-id="e1938-238">Creating a differential file backup of the secondary filegroups</span></span>  
 <span data-ttu-id="e1938-239">下面的示例将对两个辅助文件组中的各个文件创建差异文件备份。</span><span class="sxs-lookup"><span data-stu-id="e1938-239">The following example creates a differential file backup of every file in both of the secondary filegroups.</span></span>  
  
```sql  
--Back up the files in SalesGroup1.  
BACKUP DATABASE Sales  
   FILEGROUP = 'SalesGroup1',  
   FILEGROUP = 'SalesGroup2'  
   TO DISK = 'C:\MySQLServer\Backups\Sales\SalesFiles.bck'  
   WITH   
      DIFFERENTIAL;  
GO  
```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="e1938-240">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="e1938-240">Using PowerShell</span></span>  
  
<span data-ttu-id="e1938-241">使用 `Backup-SqlDatabase` cmdlet 并且为 `Files` 参数的值指定 `-BackupAction`。</span><span class="sxs-lookup"><span data-stu-id="e1938-241">Use the `Backup-SqlDatabase` cmdlet and specify `Files` for the value of the `-BackupAction` parameter.</span></span> <span data-ttu-id="e1938-242">此外，还指定下列参数之一：</span><span class="sxs-lookup"><span data-stu-id="e1938-242">Also, specify one of the following parameters:</span></span>  
  
    -   <span data-ttu-id="e1938-243">若要备份某个特定文件，请指定 `-DatabaseFile` *string*参数，其中*string*是要备份的一个或多个数据库文件。</span><span class="sxs-lookup"><span data-stu-id="e1938-243">To back up a specific file, specify the `-DatabaseFile`*String* parameter, where *String* is one or more database files to be backed up.</span></span>  
  
    -   <span data-ttu-id="e1938-244">若要备份给定文件组中的所有文件，请指定 `-DatabaseFileGroup` *string*参数，其中*string*是要备份的一个或多个数据库文件组。</span><span class="sxs-lookup"><span data-stu-id="e1938-244">To back up all the files in a given filegroup, specify the `-DatabaseFileGroup`*String* parameter, where *String* is one or more database filegroups to be backed up.</span></span>  
  
     <span data-ttu-id="e1938-245">下面的示例在 `MyDB` 数据库中创建辅助文件组“FileGroup1”和“FileGroup2”中的每个文件的完整文件备份。</span><span class="sxs-lookup"><span data-stu-id="e1938-245">The following example creates a full file backup of every file in the secondary filegroups 'FileGroup1' and 'FileGroup2' in the `MyDB` database.</span></span> <span data-ttu-id="e1938-246">将在服务器实例 `Computer\Instance`的默认备份位置上创建备份。</span><span class="sxs-lookup"><span data-stu-id="e1938-246">The backups are created on the default backup location of the server instance `Computer\Instance`.</span></span>  
  
    ```powershell
    Backup-SqlDatabase -ServerInstance Computer\Instance -Database MyDB -BackupAction Files -DatabaseFileGroup "FileGroup1","FileGroup2"  
    ```  
  
<span data-ttu-id="e1938-247">若要设置并使用 SQL Server PowerShell 提供程序，请参阅[SQL Server PowerShell 提供程序](../../powershell/sql-server-powershell-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="e1938-247">To set up and use the SQL Server PowerShell provider, see [SQL Server PowerShell Provider](../../powershell/sql-server-powershell-provider.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e1938-248">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e1938-248">See Also</span></span>  
 <span data-ttu-id="e1938-249">[备份概述 (SQL Server)](backup-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="e1938-249">[Backup Overview &#40;SQL Server&#41;](backup-overview-sql-server.md) </span></span>  
 <span data-ttu-id="e1938-250">[BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e1938-250">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="e1938-251">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e1938-251">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 <span data-ttu-id="e1938-252">[备份历史记录和标头信息 (SQL Server)](backup-history-and-header-information-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="e1938-252">[Backup History and Header Information &#40;SQL Server&#41;](backup-history-and-header-information-sql-server.md) </span></span>  
 <span data-ttu-id="e1938-253">[备份数据库（“常规”页）](../../integration-services/general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="e1938-253">[Back Up Database &#40;General Page&#41;](../../integration-services/general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="e1938-254">[备份数据库（“备份选项”页）](back-up-database-backup-options-page.md) </span><span class="sxs-lookup"><span data-stu-id="e1938-254">[Back Up Database &#40;Backup Options Page&#41;](back-up-database-backup-options-page.md) </span></span>  
 <span data-ttu-id="e1938-255">[完整文件备份 (SQL Server)](full-file-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="e1938-255">[Full File Backups &#40;SQL Server&#41;](full-file-backups-sql-server.md) </span></span>  
 <span data-ttu-id="e1938-256">[差异备份 (SQL Server)](differential-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="e1938-256">[Differential Backups &#40;SQL Server&#41;](differential-backups-sql-server.md) </span></span>  
 <span data-ttu-id="e1938-257">[文件还原（完整恢复模式）](file-restores-full-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="e1938-257">[File Restores &#40;Full Recovery Model&#41;](file-restores-full-recovery-model.md) </span></span>  
 [<span data-ttu-id="e1938-258">文件还原（简单恢复模式）</span><span class="sxs-lookup"><span data-stu-id="e1938-258">File Restores &#40;Simple Recovery Model&#41;</span></span>](file-restores-simple-recovery-model.md)  
  
  
