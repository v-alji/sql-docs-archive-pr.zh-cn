---
title: 备份事务日志 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- transaction log backups [SQL Server], SQL Server Management Studio
- backups [SQL Server], creating
- backing up transaction logs [SQL Server], SQL Server Management Studio
ms.assetid: 3426b5eb-6327-4c7f-88aa-37030be69fbf
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b57ca40b08718cda5095249991e0d424e6593a24
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581337"
---
# <a name="back-up-a-transaction-log-sql-server"></a><span data-ttu-id="ca6f7-102">备份事务日志 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ca6f7-102">Back Up a Transaction Log (SQL Server)</span></span>
  <span data-ttu-id="ca6f7-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]或 PowerShell 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中备份事务日志。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-103">This topic describes how to back up a transaction log in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or PowerShell.</span></span>  
  
 <span data-ttu-id="ca6f7-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="ca6f7-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="ca6f7-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="ca6f7-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="ca6f7-106">限制和局限</span><span class="sxs-lookup"><span data-stu-id="ca6f7-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="ca6f7-107">建议</span><span class="sxs-lookup"><span data-stu-id="ca6f7-107">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="ca6f7-108">安全性</span><span class="sxs-lookup"><span data-stu-id="ca6f7-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="ca6f7-109">**若要备份事务日志，请使用**</span><span class="sxs-lookup"><span data-stu-id="ca6f7-109">**To back up a transaction log, using:**</span></span>  
  
     [<span data-ttu-id="ca6f7-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ca6f7-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="ca6f7-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ca6f7-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="ca6f7-112">PowerShell</span><span class="sxs-lookup"><span data-stu-id="ca6f7-112">PowerShell</span></span>](#PowerShellProcedure)  
  
    > [!NOTE]  
    >  <span data-ttu-id="ca6f7-113"> 此外，还可以使用[维护计划向导](../maintenance-plans/use-the-maintenance-plan-wizard.md)来创建备份。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-113">Alternatively, you can use the[Maintenance Plan Wizard](../maintenance-plans/use-the-maintenance-plan-wizard.md)to create backups.</span></span>  
  
-   [<span data-ttu-id="ca6f7-114">相关任务</span><span class="sxs-lookup"><span data-stu-id="ca6f7-114">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ca6f7-115">开始之前</span><span class="sxs-lookup"><span data-stu-id="ca6f7-115">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="ca6f7-116">限制和局限</span><span class="sxs-lookup"><span data-stu-id="ca6f7-116">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="ca6f7-117">不允许在显式或隐式事务中使用 BACKUP 语句。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-117">The BACKUP statement is not allowed in an explicit or implicit transaction.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="ca6f7-118">建议</span><span class="sxs-lookup"><span data-stu-id="ca6f7-118">Recommendations</span></span>  
  
-   <span data-ttu-id="ca6f7-119">如果数据库使用完整恢复模式或大容量日志恢复模式，则必须足够频繁地备份事务日志，以保护数据和避免事务日志变满。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-119">If a database uses either the full or bulk-logged recovery model, you must back up the transaction log regularly enough to protect your data and to keep the transaction log from filling.</span></span> <span data-ttu-id="ca6f7-120">这将截断日志，并且支持将数据库还原到特定时间点。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-120">This truncates the log and supports restoring the database to a specific point in time.</span></span>  
  
-   <span data-ttu-id="ca6f7-121">默认情况下，每个成功的备份操作都会在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误日志和系统事件日志中添加一个条目。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-121">By default, every successful backup operation adds an entry in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log and in the system event log.</span></span> <span data-ttu-id="ca6f7-122">如果非常频繁地备份日志，这些成功消息会迅速累积，从而产生一个巨大的错误日志，这样会使查找其他消息变得非常困难。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-122">If back up the log very frequently, these success messages accumulate quickly, resulting in huge error logs that can make finding other messages difficult.</span></span> <span data-ttu-id="ca6f7-123">在这些情况下，如果任何脚本均不依赖于这些日志条目，则可以使用跟踪标志 3226 取消这些条目。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-123">In such cases you can suppress these log entries by using trace flag 3226 if none of your scripts depend on those entries.</span></span> <span data-ttu-id="ca6f7-124">有关详细信息，请参阅[跟踪标志 (Transact-SQL)](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-124">For more information, see [Trace Flags &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="ca6f7-125">Security</span><span class="sxs-lookup"><span data-stu-id="ca6f7-125">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ca6f7-126">权限</span><span class="sxs-lookup"><span data-stu-id="ca6f7-126">Permissions</span></span>  
 <span data-ttu-id="ca6f7-127">默认情况下，为 **sysadmin** 固定服务器角色以及 **db_owner** 和 **db_backupoperator** 固定数据库角色的成员授予 BACKUP DATABASE 和 BACKUP LOG 权限。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-127">BACKUP DATABASE and BACKUP LOG permissions default to members of the **sysadmin** fixed server role and the **db_owner** and **db_backupoperator** fixed database roles.</span></span>  
  
 <span data-ttu-id="ca6f7-128">备份设备的物理文件的所有权和权限问题可能会妨碍备份操作。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-128">Ownership and permission problems on the backup device's physical file can interfere with a backup operation.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="ca6f7-129">必须能够读取和写入设备；运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务的帐户必须具有写入权限。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-129">must be able to read and write to the device; the account under which the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service runs must have write permissions.</span></span> <span data-ttu-id="ca6f7-130">但是，用于在系统表中为备份设备添加项目的 [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql)不检查文件访问权限。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-130">However, [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql), which adds an entry for a backup device in the system tables, does not check file access permissions.</span></span> <span data-ttu-id="ca6f7-131">备份设备物理文件的这些问题可能直到为备份或还原而访问物理资源时才会出现。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-131">Such problems on the backup device's physical file may not appear until the physical resource is accessed when the backup or restore is attempted.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="ca6f7-132">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ca6f7-132">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-back-up-a-transaction-log"></a><span data-ttu-id="ca6f7-133">备份事务日志</span><span class="sxs-lookup"><span data-stu-id="ca6f7-133">To back up a transaction log</span></span>  
  
1.  <span data-ttu-id="ca6f7-134">连接到相应的 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]实例之后，在对象资源管理器中，单击服务器名称以展开服务器树。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-134">After connecting to the appropriate instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="ca6f7-135">展开 **“数据库”** ，然后根据数据库的不同，选择用户数据库，或展开 **“系统数据库”** ，再选择系统数据库。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-135">Expand **Databases**, and, depending on the database, either select a user database or expand **System Databases** and select a system database.</span></span>  
  
3.  <span data-ttu-id="ca6f7-136">右键单击数据库，指向 **“任务”** ，再单击 **“备份”** 。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-136">Right-click the database, point to **Tasks**, and then click **Back Up**.</span></span> <span data-ttu-id="ca6f7-137">将出现 **“备份数据库”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-137">The **Back Up Database** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="ca6f7-138">在 **“数据库”** 列表框中，验证数据库名称。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-138">In the **Database** list box, verify the database name.</span></span> <span data-ttu-id="ca6f7-139">您也可以从列表中选择其他数据库。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-139">You can optionally select a different database from the list.</span></span>  
  
5.  <span data-ttu-id="ca6f7-140">验证恢复模式是 **FULL** 还是 **BULK_LOGGED**。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-140">Verify that the recovery model is either **FULL** or **BULK_LOGGED**.</span></span>  
  
6.  <span data-ttu-id="ca6f7-141">在 **“备份类型”** 列表框中，选择 **“事务日志”** 。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-141">In the **Backup type** list box, select **Transaction Log**.</span></span>  
  
7.  <span data-ttu-id="ca6f7-142">还可以根据需要选择 **“仅复制备份”** 创建仅复制备份。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-142">Optionally, you can select **Copy Only Backup** to create a copy-only backup.</span></span> <span data-ttu-id="ca6f7-143">*仅复制备份*是[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]独立于常规备份序列[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的备份。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-143">A *copy-only backup* is a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup that is independent of the sequence of conventional [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backups.</span></span> <span data-ttu-id="ca6f7-144">有关详细信息，请参阅[仅复制备份 (SQL Server)](copy-only-backups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-144">For more information, see [Copy-Only Backups &#40;SQL Server&#41;](copy-only-backups-sql-server.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ca6f7-145">选择“差异”  选项时，无法创建仅复制备份。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-145">When the **Differential** option is selected, you cannot create a copy-only backup.</span></span>  
  
8.  <span data-ttu-id="ca6f7-146">可以接受 **“名称”** 文本框中建议的默认备份集名称，也可以为备份集输入其他名称。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-146">Either accept the default backup set name suggested in the **Name** text box, or enter a different name for the backup set.</span></span>  
  
9. <span data-ttu-id="ca6f7-147">或者，在 **“说明”** 文本框中，输入备份集的说明。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-147">Optionally, in the **Description** text box, enter a description of the backup set.</span></span>  
  
10. <span data-ttu-id="ca6f7-148">指定备份集的过期时间：</span><span class="sxs-lookup"><span data-stu-id="ca6f7-148">Specify when the backup set will expire:</span></span>  
  
    -   <span data-ttu-id="ca6f7-149">若要使备份集在特定天数后过期，请单击 **“之后”** （默认选项），并输入备份集从创建到过期所需的天数。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-149">To have the backup set expire after a specific number of days, click **After** (the default option), and enter the number of days after set creation that the set will expire.</span></span> <span data-ttu-id="ca6f7-150">此值范围为 0 到 99999 天；0 天表示备份集将永不过期。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-150">This value can be from 0 to 99999 days; a value of 0 days means that the backup set will never expire.</span></span>  
  
         <span data-ttu-id="ca6f7-151">默认值在 **“服务器属性”** 对话框（位于 **“数据库设置”** 页上）的 **“默认备份媒体保持期(天)”** 选项中设置。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-151">The default value is set in the **Default backup media retention (in days)** option of the **Server Properties** dialog box (**Database Settings** page).</span></span> <span data-ttu-id="ca6f7-152">若要访问此对话框，请在对象资源管理器中右键单击服务器名称，选择“属性”，再选择 **“数据库设置”** 页。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-152">To access this dialog box, right-click the server name in Object Explorer and select properties; then select the **Database Settings** page.</span></span>  
  
    -   <span data-ttu-id="ca6f7-153">若要使备份集在特定日期过期，请单击 **“在”** ，并输入备份集的过期日期。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-153">To have the backup set expire on a specific date, click **On**, and enter the date on which the set will expire.</span></span>  
  
11. <span data-ttu-id="ca6f7-154">通过单击 **“磁盘”** 、 **“URL”** 或 **“磁带”** ，选择备份目标的类型。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-154">Choose the type of backup destination by clicking **Disk**, **URL** or **Tape**.</span></span> <span data-ttu-id="ca6f7-155">若要选择包含单个介质集的多个磁盘或磁带机（最多为 64 个）的路径，请单击 **“添加”** 。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-155">To select the paths of up to 64 disk or tape drives containing a single media set, click **Add**.</span></span> <span data-ttu-id="ca6f7-156">选择的路径将显示在 **“备份到”** 列表框中。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-156">The selected paths are displayed in the **Backup to** list box.</span></span>  
  
     <span data-ttu-id="ca6f7-157">若要删除备份目标，请选择该备份目标并单击 **“删除”** 。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-157">To remove a backup destination, select it and click **Remove**.</span></span> <span data-ttu-id="ca6f7-158">若要查看备份目标的内容，请选择该备份目标并单击 **“内容”** 。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-158">To view the contents of a backup destination, select it and click **Contents**.</span></span>  
  
12. <span data-ttu-id="ca6f7-159">若要查看或选择高级选项，请在 **“选择页”** 窗格中单击 **“选项”** 。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-159">To view or select the advanced options, click **Options** in the **Select a page** pane.</span></span>  
  
13. <span data-ttu-id="ca6f7-160">可以通过单击以下选项之一来选择 **“覆盖介质”** 选项：</span><span class="sxs-lookup"><span data-stu-id="ca6f7-160">Select an **Overwrite Media** option, by clicking one of the following:</span></span>  
  
    -   <span data-ttu-id="ca6f7-161">**备份到现有介质集**</span><span class="sxs-lookup"><span data-stu-id="ca6f7-161">**Back up to the existing media set**</span></span>  
  
         <span data-ttu-id="ca6f7-162">对于此选项，请单击 **“追加到现有备份集”** 或 **“覆盖所有现有备份集”** 。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-162">For this option, click either **Append to the existing backup set** or **Overwrite all existing backup sets**.</span></span> <span data-ttu-id="ca6f7-163">有关详细信息，请参阅 [媒体集、媒体簇和备份集 (SQL Server)](media-sets-media-families-and-backup-sets-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-163">For more information, see [Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md).</span></span>  
  
         <span data-ttu-id="ca6f7-164">或者选择 **“检查介质集名称和备份集过期时间”** ，以使备份操作对介质集和备份集的过期日期和时间进行验证。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-164">Optionally, select **Check media set name and backup set expiration** to cause the backup operation to verify the date and time at which the media set and backup set expire.</span></span>  
  
         <span data-ttu-id="ca6f7-165">或者在 **“介质集名称”** 文本框中输入名称。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-165">Optionally, enter a name in the **Media set name** text box.</span></span> <span data-ttu-id="ca6f7-166">如果没有指定名称，将使用空白名称创建介质集。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-166">If no name is specified, a media set with a blank name is created.</span></span> <span data-ttu-id="ca6f7-167">如果指定了介质集名称，将检查介质（磁带或磁盘），以确定实际名称是否与此处输入的名称匹配。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-167">If you specify a media set name, the media (tape or disk) is checked to see whether the actual name matches the name you enter here.</span></span>  
  
         <span data-ttu-id="ca6f7-168">如果将介质名称保留空白，并选中该框以便与介质进行核对，则只有当介质上的介质名称也是空白时才能成功。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-168">If you leave the media name blank and check the box to check it against the media, success will equal the media name on the media also being blank.</span></span>  
  
    -   <span data-ttu-id="ca6f7-169">**备份到新介质集并清除所有现有备份集**</span><span class="sxs-lookup"><span data-stu-id="ca6f7-169">**Back up to a new media set, and erase all existing backup sets**</span></span>  
  
         <span data-ttu-id="ca6f7-170">对于该选项，请在 **“新建介质集名称”** 文本框中输入名称，并在 **“新建介质集说明”** 文本框中描述介质集（可选）。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-170">For this option, enter a name in the **New media set name** text box, and, optionally, describe the media set in the **New media set description** text box.</span></span> <span data-ttu-id="ca6f7-171">有关详细信息，请参阅 [媒体集、媒体簇和备份集 (SQL Server)](media-sets-media-families-and-backup-sets-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-171">For more information, see [Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md).</span></span>  
  
14. <span data-ttu-id="ca6f7-172">或者，在 **“可靠性”** 部分中，选中：</span><span class="sxs-lookup"><span data-stu-id="ca6f7-172">In the **Reliability** section, optionally, check:</span></span>  
  
    -   <span data-ttu-id="ca6f7-173">**完成后验证备份**。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-173">**Verify backup when finished**.</span></span>  
  
    -   <span data-ttu-id="ca6f7-174">**“写入介质前检查校验和”** 和 **“出现校验和错误时继续”** （可选）。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-174">**Perform checksum before writing to media**, and, optionally, **Continue on checksum error**.</span></span> <span data-ttu-id="ca6f7-175">有关校验和的信息，请参阅[在备份和还原期间可能的媒体错误 (SQL Server)](possible-media-errors-during-backup-and-restore-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-175">For information on checksums, see [Possible Media Errors During Backup and Restore &#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md).</span></span>  
  
15. <span data-ttu-id="ca6f7-176">在 **“事务日志”** 区域中：</span><span class="sxs-lookup"><span data-stu-id="ca6f7-176">In the **Transaction log** section:</span></span>  
  
    -   <span data-ttu-id="ca6f7-177">对于例行的日志备份，请保留默认选项 **“通过删除不活动的条目截断事务日志”** 。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-177">For routine log backups, keep the default selection, **Truncate the transaction log by removing inactive entries**.</span></span>  
  
    -   <span data-ttu-id="ca6f7-178">若要备份日志尾部（即活动的日志），请选中 **“备份日志尾部，并使数据库处于还原状态”**。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-178">To back up the tail of the log (that is, the active log), check **Back up the tail of the log, and leave database in the restoring state**.</span></span>  
  
         <span data-ttu-id="ca6f7-179">备份日志尾部失败后执行结尾日志备份，以防丢失所做的工作。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-179">A tail-log backup is taken after a failure to back up the tail of the log in order to prevent work loss.</span></span> <span data-ttu-id="ca6f7-180">在失败之后且在开始还原数据库之前，或者在故障转移到辅助数据库时，备份活动日志（结尾日志备份）。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-180">Back up the active log (a tail-log backup) both after a failure, before beginning to restore the database, or when failing over to a secondary database.</span></span> <span data-ttu-id="ca6f7-181">选择此选项等效于在 Transact-SQL BACKUP LOG 语句中指定 NORECOVERY 选项。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-181">Selecting this option is equivalent to specifying the NORECOVERY option in the BACKUP LOG statement of Transact-SQL.</span></span> <span data-ttu-id="ca6f7-182">有关结尾日志备份的详细信息，请参阅[结尾日志备份 (SQL Server) ](tail-log-backups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-182">For more information about tail-log backups, see [Tail-Log Backups &#40;SQL Server&#41;](tail-log-backups-sql-server.md).</span></span>  
  
16. <span data-ttu-id="ca6f7-183">如果备份到磁带驱动器（如同 **“常规”** 页的 **“目标”** 部分指定的一样），则 **“备份后卸载磁带”** 选项处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-183">If you are backing up to a tape drive (as specified in the **Destination** section of the **General** page), the **Unload the tape after backup** option is active.</span></span> <span data-ttu-id="ca6f7-184">单击此选项可以激活 **“卸载前倒带”** 选项。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-184">Clicking this option activates the **Rewind the tape before unloading** option.</span></span>  
  
17. [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] <span data-ttu-id="ca6f7-185">及更高版本支持 [备份压缩](backup-compression-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-185">and later supports [backup compression](backup-compression-sql-server.md).</span></span> <span data-ttu-id="ca6f7-186">默认情况下，是否压缩备份取决于 **backup-compression default** 服务器配置选项的值。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-186">By default, whether a backup is compressed depends on the value of the **backup-compression default** server configuration option.</span></span> <span data-ttu-id="ca6f7-187">但是，不管当前服务器级默认设置如何，都可以通过选中 **“压缩备份”** 来压缩备份，并且可以通过选中 **“不压缩备份”** 来防止压缩备份。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-187">However, regardless of the current server-level default, you can compress a backup by checking **Compress backup**, and you can prevent compression by checking **Do not compress backup**.</span></span>  
  
     <span data-ttu-id="ca6f7-188">**查看当前备份压缩默认值**</span><span class="sxs-lookup"><span data-stu-id="ca6f7-188">**To view the current backup compression default**</span></span>  
  
    -   [<span data-ttu-id="ca6f7-189">查看或配置 backup compression default 服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="ca6f7-189">View or Configure the backup compression default Server Configuration Option</span></span>](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)  
  
 <span data-ttu-id="ca6f7-190">**加密**</span><span class="sxs-lookup"><span data-stu-id="ca6f7-190">**Encryption**</span></span>  
  
 <span data-ttu-id="ca6f7-191">若要加密备份文件，请选中 **“加密备份”** 复选框。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-191">To encrypt the backup file check the **Encrypt backup** check box.</span></span> <span data-ttu-id="ca6f7-192">选择要用于加密备份文件的加密算法，并提供一个证书或非对称密钥。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-192">Select an encryption algorithm to use for encrypting the backup file and provide a Certificate or Asymmetric key.</span></span> <span data-ttu-id="ca6f7-193">可用于加密的算法是：</span><span class="sxs-lookup"><span data-stu-id="ca6f7-193">The available algorithms for encryption are:</span></span>  
  
-   <span data-ttu-id="ca6f7-194">AES 128</span><span class="sxs-lookup"><span data-stu-id="ca6f7-194">AES 128</span></span>  
  
-   <span data-ttu-id="ca6f7-195">AES 192</span><span class="sxs-lookup"><span data-stu-id="ca6f7-195">AES 192</span></span>  
  
-   <span data-ttu-id="ca6f7-196">AES 256</span><span class="sxs-lookup"><span data-stu-id="ca6f7-196">AES 256</span></span>  
  
-   <span data-ttu-id="ca6f7-197">三重 DES</span><span class="sxs-lookup"><span data-stu-id="ca6f7-197">Triple DES</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="ca6f7-198">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ca6f7-198">Using Transact-SQL</span></span>  
  
#### <a name="to-back-up-a-transaction-log"></a><span data-ttu-id="ca6f7-199">备份事务日志</span><span class="sxs-lookup"><span data-stu-id="ca6f7-199">To back up a transaction log</span></span>  
  
1.  <span data-ttu-id="ca6f7-200">执行 BACKUP LOG 语句以备份事务日志，同时指定下列对象：</span><span class="sxs-lookup"><span data-stu-id="ca6f7-200">Execute the BACKUP LOG statement to back up the transaction log, specifying the following:</span></span>  
  
    -   <span data-ttu-id="ca6f7-201">要备份的事务日志所属的数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-201">The name of the database to which the transaction log that you want to back up belongs.</span></span>  
  
    -   <span data-ttu-id="ca6f7-202">写入事务日志备份的备份设备。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-202">The backup device where the transaction log backup is written.</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="ca6f7-203">示例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="ca6f7-203">Example (Transact-SQL)</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="ca6f7-204">此示例使用 [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] 数据库，该数据库使用简单恢复模式。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-204">This example uses the [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] database, which uses the simple recovery model.</span></span> <span data-ttu-id="ca6f7-205">若要允许日志备份，请在完整备份数据库之前，将数据库设置为使用完整恢复模式。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-205">To permit log backups, before taking a full database backup, the database was set to use the full recovery model.</span></span> <span data-ttu-id="ca6f7-206">有关详细信息，请参阅[查看或更改数据库的恢复模式 (SQL Server)](view-or-change-the-recovery-model-of-a-database-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-206">For more information, see [View or Change the Recovery Model of a Database &#40;SQL Server&#41;](view-or-change-the-recovery-model-of-a-database-sql-server.md).</span></span>  
  
 <span data-ttu-id="ca6f7-207">以下示例将在以前创建的已命名备份设备 [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] 上创建 `MyAdvWorks_FullRM_log1`数据库的事务日志备份。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-207">This example creates a transaction log backup for the [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] database to the previously created named backup device, `MyAdvWorks_FullRM_log1`.</span></span>  
  
```sql  
BACKUP LOG AdventureWorks2012  
   TO MyAdvWorks_FullRM_log1;  
GO  
```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="ca6f7-208">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ca6f7-208">Using PowerShell</span></span>  
  
<span data-ttu-id="ca6f7-209">使用 `Backup-SqlDatabase` cmdlet 并且为 `Log` 参数的值指定 `-BackupAction`。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-209">Use the `Backup-SqlDatabase` cmdlet and specify `Log` for the value of the `-BackupAction` parameter.</span></span>  
  
<span data-ttu-id="ca6f7-210">下面的示例在服务器实例 `MyDB` 的默认备份位置创建数据库 `Computer\Instance`的日志备份。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-210">The following example creates a log backup of the `MyDB` database to the default backup location of the server instance `Computer\Instance`.</span></span>  
  
    ```powershell
    Backup-SqlDatabase -ServerInstance Computer\Instance -Database MyDB -BackupAction Log  
    ```  
  
<span data-ttu-id="ca6f7-211">若要设置并使用 SQL Server PowerShell 提供程序，请参阅[SQL Server PowerShell 提供程序](../../powershell/sql-server-powershell-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="ca6f7-211">To set up and use the SQL Server PowerShell provider, see [SQL Server PowerShell Provider](../../powershell/sql-server-powershell-provider.md).</span></span>
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="ca6f7-212">相关任务</span><span class="sxs-lookup"><span data-stu-id="ca6f7-212">Related Tasks</span></span>  
  
-   [<span data-ttu-id="ca6f7-213">还原事务日志备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ca6f7-213">Restore a Transaction Log Backup &#40;SQL Server&#41;</span></span>](restore-a-transaction-log-backup-sql-server.md)  
  
-   [<span data-ttu-id="ca6f7-214">将 SQL Server 数据库还原到某个时间点（完整恢复模式）</span><span class="sxs-lookup"><span data-stu-id="ca6f7-214">Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;</span></span>](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)  
  
-   [<span data-ttu-id="ca6f7-215">解决事务日志已满的问题（SQL Server 错误 9002）</span><span class="sxs-lookup"><span data-stu-id="ca6f7-215">Troubleshoot a Full Transaction Log &#40;SQL Server Error 9002&#41;</span></span>](../logs/troubleshoot-a-full-transaction-log-sql-server-error-9002.md)  
  
## <a name="see-also"></a><span data-ttu-id="ca6f7-216">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ca6f7-216">See Also</span></span>  
 <span data-ttu-id="ca6f7-217">[BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ca6f7-217">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="ca6f7-218">[应用事务日志备份 (SQL Server)](transaction-log-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ca6f7-218">[Apply Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span></span>  
 <span data-ttu-id="ca6f7-219">[维护计划](../maintenance-plans/maintenance-plans.md) </span><span class="sxs-lookup"><span data-stu-id="ca6f7-219">[Maintenance Plans](../maintenance-plans/maintenance-plans.md) </span></span>  
 [<span data-ttu-id="ca6f7-220">完整文件备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ca6f7-220">Full File Backups &#40;SQL Server&#41;</span></span>](full-file-backups-sql-server.md)  
