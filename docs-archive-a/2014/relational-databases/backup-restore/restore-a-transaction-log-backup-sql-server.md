---
title: 还原事务日志备份 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.restoretlog.options.f1
- sql12.swb.restoretlog.general.f1
helpviewer_keywords:
- restore log
- backing up transaction logs [SQL Server], restoring
- transaction log backups [SQL Server], restoring
- restoring transaction logs [SQL Server], restoring backups
- transaction log restores [SQL Server], SQL Server Management Studio
ms.assetid: 1de2b888-78a6-4fb2-a647-ba4bf097caf3
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 68fe4bbc199d6555bd490d25f92491100b8bbfcf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589160"
---
# <a name="restore-a-transaction-log-backup-sql-server"></a><span data-ttu-id="f1cef-102">还原事务日志备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f1cef-102">Restore a Transaction Log Backup (SQL Server)</span></span>
  <span data-ttu-id="f1cef-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中还原事务日志备份。</span><span class="sxs-lookup"><span data-stu-id="f1cef-103">This topic describes how to restore a transaction log backup in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="f1cef-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="f1cef-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="f1cef-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="f1cef-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="f1cef-106">先决条件</span><span class="sxs-lookup"><span data-stu-id="f1cef-106">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="f1cef-107">安全性</span><span class="sxs-lookup"><span data-stu-id="f1cef-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="f1cef-108">**若要还原事务日志备份，请使用：**</span><span class="sxs-lookup"><span data-stu-id="f1cef-108">**To restore a transaction log backup, using:**</span></span>  
  
     [<span data-ttu-id="f1cef-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f1cef-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="f1cef-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f1cef-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   [<span data-ttu-id="f1cef-111">相关任务</span><span class="sxs-lookup"><span data-stu-id="f1cef-111">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="f1cef-112">开始之前</span><span class="sxs-lookup"><span data-stu-id="f1cef-112">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="f1cef-113">先决条件</span><span class="sxs-lookup"><span data-stu-id="f1cef-113">Prerequisites</span></span>  
  
-   <span data-ttu-id="f1cef-114">备份必须按照其创建顺序进行还原。</span><span class="sxs-lookup"><span data-stu-id="f1cef-114">Backups must be restored in the order in which they were created.</span></span> <span data-ttu-id="f1cef-115">在还原特定的事务日志备份之前，必须先还原下列以前备份，而不回滚未提交的事务，即 WITH NORECOVERY：</span><span class="sxs-lookup"><span data-stu-id="f1cef-115">Before you can restore a particular transaction log backup, you must first restore the following previous backups without rolling back uncommitted transactions, that is WITH NORECOVERY:</span></span>  
  
    -   <span data-ttu-id="f1cef-116">在特定事务日志备份之前执行的完整数据库备份和上次差异备份（如果有）。</span><span class="sxs-lookup"><span data-stu-id="f1cef-116">The full database backup and the last differential backup, if any, taken before the particular transaction log backup.</span></span> <span data-ttu-id="f1cef-117">创建最新的完整数据库备份或差异数据库备份之前，数据库必须使用完整恢复模式或大容量日志恢复模式。</span><span class="sxs-lookup"><span data-stu-id="f1cef-117">Before the most recent full or differential database backup was created, the database must have been using the full recovery model or bulk-logged recovery model.</span></span>  
  
    -   <span data-ttu-id="f1cef-118">在完整数据库备份之后执行的所有事务日志备份或在特定事务日志备份之前执行的差异备份（如果您还原了差异备份）。</span><span class="sxs-lookup"><span data-stu-id="f1cef-118">All transaction log backups taken after the full database backup or the differential backup (if you restore one) and before the particular transaction log backup.</span></span> <span data-ttu-id="f1cef-119">必须按照创建日志备份的顺序应用它们，并且日志链没有间隔。</span><span class="sxs-lookup"><span data-stu-id="f1cef-119">Log backups must be applied in the sequence in which they were created, without any gaps in the log chain.</span></span>  
  
         <span data-ttu-id="f1cef-120">有关事务日志备份的详细信息，请参阅[事务日志备份 (SQL Server)](transaction-log-backups-sql-server.md) 和[应用事务日志备份 (SQL Server)](apply-transaction-log-backups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="f1cef-120">For more information about transaction log backups, see [Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) and [Apply Transaction Log Backups &#40;SQL Server&#41;](apply-transaction-log-backups-sql-server.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="f1cef-121">Security</span><span class="sxs-lookup"><span data-stu-id="f1cef-121">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="f1cef-122">权限</span><span class="sxs-lookup"><span data-stu-id="f1cef-122">Permissions</span></span>  
 <span data-ttu-id="f1cef-123">RESTORE 权限被授予那些成员身份信息始终可由服务器使用的角色。</span><span class="sxs-lookup"><span data-stu-id="f1cef-123">RESTORE permissions are given to roles in which membership information is always readily available to the server.</span></span> <span data-ttu-id="f1cef-124">因为只有在固定数据库可以访问且没有损坏时（在执行 RESTORE 时并不会总是这样）才能检查固定数据库角色成员身份，所以 **db_owner** 固定数据库角色成员没有 RESTORE 权限。</span><span class="sxs-lookup"><span data-stu-id="f1cef-124">Because fixed database role membership can be checked only when the database is accessible and undamaged, which is not always the case when RESTORE is executed, members of the **db_owner** fixed database role do not have RESTORE permissions.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="f1cef-125">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f1cef-125">Using SQL Server Management Studio</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="f1cef-126">一般的还原过程需要在“还原数据库”对话框中同时选择日志备份以及数据和差异备份。</span><span class="sxs-lookup"><span data-stu-id="f1cef-126">The normal process of a restore is to select the log backups in the **Restore Database** dialog box along with the data and differential backups.</span></span>  
  
#### <a name="to-restore-a-transaction-log-backup"></a><span data-ttu-id="f1cef-127">还原事务日志备份</span><span class="sxs-lookup"><span data-stu-id="f1cef-127">To restore a transaction log backup</span></span>  
  
1.  <span data-ttu-id="f1cef-128">连接到相应的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 实例之后，在“对象资源管理器”中，单击服务器名称以展开服务器树。</span><span class="sxs-lookup"><span data-stu-id="f1cef-128">After connecting to the appropriate instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="f1cef-129">展开 **“数据库”** ，然后根据数据库的不同，选择用户数据库，或展开 **“系统数据库”** ，再选择系统数据库。</span><span class="sxs-lookup"><span data-stu-id="f1cef-129">Expand **Databases**, and, depending on the database, either select a user database or expand **System Databases** and select a system database.</span></span>  
  
3.  <span data-ttu-id="f1cef-130">右键单击该数据库，指向“任务”，再指向“还原”，然后单击“事务日志”，这将打开“还原事务日志”对话框。</span><span class="sxs-lookup"><span data-stu-id="f1cef-130">Right-click the database, point to **Tasks**, point to **Restore**, and then click **Transaction Log**, which opens the **Restore Transaction Log** dialog box.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f1cef-131">如果 **“事务日志”** 灰显，您可能需要首先还原完整备份或差异备份。</span><span class="sxs-lookup"><span data-stu-id="f1cef-131">If **Transaction Log** is grayed out, you may need to restore a full or differential backup first.</span></span> <span data-ttu-id="f1cef-132">使用 **“数据库”** 备份对话框。</span><span class="sxs-lookup"><span data-stu-id="f1cef-132">Use the **Database** backup dialog box.</span></span>  
  
4.  <span data-ttu-id="f1cef-133">在 **“常规”** 页上的 **“数据库”** 列表框中，选择数据库名称。</span><span class="sxs-lookup"><span data-stu-id="f1cef-133">On the **General** page, in the **Database** list box, select the name of a database.</span></span> <span data-ttu-id="f1cef-134">仅列出处于还原状态的数据库。</span><span class="sxs-lookup"><span data-stu-id="f1cef-134">Only databases in the restoring state are listed.</span></span>  
  
5.  <span data-ttu-id="f1cef-135">若要指定要还原的备份集的源和位置，请单击以下选项之一：</span><span class="sxs-lookup"><span data-stu-id="f1cef-135">To specify the source and location of the backup sets to restore, click one of the following options:</span></span>  
  
    -   <span data-ttu-id="f1cef-136">**从数据库以前的备份**</span><span class="sxs-lookup"><span data-stu-id="f1cef-136">**From previous backups of database**</span></span>  
  
         <span data-ttu-id="f1cef-137">从下拉列表中选择要还原的数据库。</span><span class="sxs-lookup"><span data-stu-id="f1cef-137">Select the database to restore from the drop-down list.</span></span> <span data-ttu-id="f1cef-138">此列表仅包含已根据 **msdb** 备份历史记录进行备份的数据库。</span><span class="sxs-lookup"><span data-stu-id="f1cef-138">The list contains only databases that have been backed up according to the **msdb** backup history.</span></span>  
  
    -   <span data-ttu-id="f1cef-139">**从文件或磁带**</span><span class="sxs-lookup"><span data-stu-id="f1cef-139">**From file or tape**</span></span>  
  
         <span data-ttu-id="f1cef-140">单击“浏览”按钮 ( **...** ) 以打开“选择备份设备”对话框。</span><span class="sxs-lookup"><span data-stu-id="f1cef-140">Click the browse (**...**) button to open the **Select backup devices** dialog box.</span></span> <span data-ttu-id="f1cef-141">在 **“备份介质类型”** 框中，从列出的设备类型中选择一种。</span><span class="sxs-lookup"><span data-stu-id="f1cef-141">In the **Backup media type** box, select one of the listed device types.</span></span> <span data-ttu-id="f1cef-142">若要为 **“备份介质”** 框选择一个或多个设备，请单击 **“添加”** 。</span><span class="sxs-lookup"><span data-stu-id="f1cef-142">To select one or more devices for the **Backup media** box, click **Add**.</span></span>  
  
         <span data-ttu-id="f1cef-143">将所需设备添加到 **“备份介质”** 列表框后，单击 **“确定”** 返回到 **“常规”** 页。</span><span class="sxs-lookup"><span data-stu-id="f1cef-143">After you add the devices you want to the **Backup media** list box, click **OK** to return to the **General** page.</span></span>  
  
6.  <span data-ttu-id="f1cef-144">在 **“选择要还原的事务日志备份”** 网格中，选择要还原的备份。</span><span class="sxs-lookup"><span data-stu-id="f1cef-144">In the **Select the transaction log backups to restore** grid, select the backups to restore.</span></span> <span data-ttu-id="f1cef-145">此网格列出了选定数据库可以使用的事务日志备份。</span><span class="sxs-lookup"><span data-stu-id="f1cef-145">This grid lists the transaction log backups available for the selected database.</span></span> <span data-ttu-id="f1cef-146">只有在日志备份的 **“第一个 LSN”** 大于数据库的 **“最后一个 LSN”** 时，此日志备份才可用。</span><span class="sxs-lookup"><span data-stu-id="f1cef-146">A log backup is available only if its **First LSN** greater than the **Last LSN** of the database.</span></span> <span data-ttu-id="f1cef-147">日志备份按照它们所包含的日志序列号 (LSN) 的顺序排列，并且也必须按照这种顺序还原。</span><span class="sxs-lookup"><span data-stu-id="f1cef-147">Log backups are listed in the order of the log sequence numbers (LSN) they contain, and they must be restored in this order.</span></span>  
  
     <span data-ttu-id="f1cef-148">下表列出了网格的列标题并对列值进行了说明。</span><span class="sxs-lookup"><span data-stu-id="f1cef-148">The following table lists the column headers of the grid and describes their values.</span></span>  
  
    |<span data-ttu-id="f1cef-149">标头</span><span class="sxs-lookup"><span data-stu-id="f1cef-149">Header</span></span>|<span data-ttu-id="f1cef-150">值</span><span class="sxs-lookup"><span data-stu-id="f1cef-150">Value</span></span>|  
    |------------|-----------|  
    |<span data-ttu-id="f1cef-151">**还原**</span><span class="sxs-lookup"><span data-stu-id="f1cef-151">**Restore**</span></span>|<span data-ttu-id="f1cef-152">如果复选框处于选中状态，则指示要还原相应的备份集。</span><span class="sxs-lookup"><span data-stu-id="f1cef-152">Selected check boxes indicate the backup sets to be restored.</span></span>|  
    |<span data-ttu-id="f1cef-153">**名称**</span><span class="sxs-lookup"><span data-stu-id="f1cef-153">**Name**</span></span>|<span data-ttu-id="f1cef-154">备份集的名称。</span><span class="sxs-lookup"><span data-stu-id="f1cef-154">Name of the backup set.</span></span>|  
    |<span data-ttu-id="f1cef-155">组件</span><span class="sxs-lookup"><span data-stu-id="f1cef-155">**Component**</span></span>|<span data-ttu-id="f1cef-156">备份组件：数据库、文件或 \<blank>（对于事务日志） 。</span><span class="sxs-lookup"><span data-stu-id="f1cef-156">Backed-up component: **Database**, **File**, or \<blank> (for transaction logs).</span></span>|  
    |<span data-ttu-id="f1cef-157">**Database**</span><span class="sxs-lookup"><span data-stu-id="f1cef-157">**Database**</span></span>|<span data-ttu-id="f1cef-158">备份操作中涉及的数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="f1cef-158">Name of the database involved in the backup operation.</span></span>|  
    |<span data-ttu-id="f1cef-159">**开始日期**</span><span class="sxs-lookup"><span data-stu-id="f1cef-159">**Start Date**</span></span>|<span data-ttu-id="f1cef-160">备份操作开始的日期和时间（按客户端的区域设置显示）。</span><span class="sxs-lookup"><span data-stu-id="f1cef-160">Date and time when the backup operation began, presented in the regional setting of the client.</span></span>|  
    |<span data-ttu-id="f1cef-161">**完成日期**</span><span class="sxs-lookup"><span data-stu-id="f1cef-161">**Finish Date**</span></span>|<span data-ttu-id="f1cef-162">备份操作完成的日期和时间（按客户端的区域设置显示）。</span><span class="sxs-lookup"><span data-stu-id="f1cef-162">Date and time when the backup operation finished, presented in the regional setting of the client.</span></span>|  
    |<span data-ttu-id="f1cef-163">**第一个 LSN**</span><span class="sxs-lookup"><span data-stu-id="f1cef-163">**First LSN**</span></span>|<span data-ttu-id="f1cef-164">备份集中第一个事务的日志序列号。</span><span class="sxs-lookup"><span data-stu-id="f1cef-164">Log sequence number of the first transaction in the backup set.</span></span> <span data-ttu-id="f1cef-165">对于文件备份为空。</span><span class="sxs-lookup"><span data-stu-id="f1cef-165">Blank for file backups.</span></span>|  
    |<span data-ttu-id="f1cef-166">**最后一个 LSN**</span><span class="sxs-lookup"><span data-stu-id="f1cef-166">**Last LSN**</span></span>|<span data-ttu-id="f1cef-167">备份集中最后一个事务的日志序列号。</span><span class="sxs-lookup"><span data-stu-id="f1cef-167">Log sequence number of the last transaction in the backup set.</span></span> <span data-ttu-id="f1cef-168">对于文件备份为空。</span><span class="sxs-lookup"><span data-stu-id="f1cef-168">Blank for file backups.</span></span>|  
    |<span data-ttu-id="f1cef-169">**检查点 LSN**</span><span class="sxs-lookup"><span data-stu-id="f1cef-169">**Checkpoint LSN**</span></span>|<span data-ttu-id="f1cef-170">创建备份时最后一个检查点的日志序号。</span><span class="sxs-lookup"><span data-stu-id="f1cef-170">Log sequence number of the most recent checkpoint at the time the backup was created.</span></span>|  
    |<span data-ttu-id="f1cef-171">**完整 LSN**</span><span class="sxs-lookup"><span data-stu-id="f1cef-171">**Full LSN**</span></span>|<span data-ttu-id="f1cef-172">最近的数据库完整备份的日志序列号。</span><span class="sxs-lookup"><span data-stu-id="f1cef-172">Log sequence number of the most recent full database backup.</span></span>|  
    |<span data-ttu-id="f1cef-173">**Server**</span><span class="sxs-lookup"><span data-stu-id="f1cef-173">**Server**</span></span>|<span data-ttu-id="f1cef-174">执行备份操作的数据库引擎实例的名称。</span><span class="sxs-lookup"><span data-stu-id="f1cef-174">Name of the Database Engine instance that performed the backup operation.</span></span>|  
    |<span data-ttu-id="f1cef-175">**用户名**</span><span class="sxs-lookup"><span data-stu-id="f1cef-175">**User Name**</span></span>|<span data-ttu-id="f1cef-176">执行备份操作的用户的名称。</span><span class="sxs-lookup"><span data-stu-id="f1cef-176">Name of the user who performed the backup operation.</span></span>|  
    |<span data-ttu-id="f1cef-177">**大小**</span><span class="sxs-lookup"><span data-stu-id="f1cef-177">**Size**</span></span>|<span data-ttu-id="f1cef-178">备份集的大小（字节）。</span><span class="sxs-lookup"><span data-stu-id="f1cef-178">Size of the backup set in bytes.</span></span>|  
    |<span data-ttu-id="f1cef-179">**位置**</span><span class="sxs-lookup"><span data-stu-id="f1cef-179">**Position**</span></span>|<span data-ttu-id="f1cef-180">备份集在卷中的位置。</span><span class="sxs-lookup"><span data-stu-id="f1cef-180">Position of the backup set in the volume.</span></span>|  
    |<span data-ttu-id="f1cef-181">**过期日期**</span><span class="sxs-lookup"><span data-stu-id="f1cef-181">**Expiration**</span></span>|<span data-ttu-id="f1cef-182">备份集过期的日期和时间。</span><span class="sxs-lookup"><span data-stu-id="f1cef-182">Date and time the backup set expires.</span></span>|  
  
7.  <span data-ttu-id="f1cef-183">选择以下方案之一：</span><span class="sxs-lookup"><span data-stu-id="f1cef-183">Select one of the following:</span></span>  
  
    -   <span data-ttu-id="f1cef-184">**时间点**</span><span class="sxs-lookup"><span data-stu-id="f1cef-184">**Point in time**</span></span>  
  
         <span data-ttu-id="f1cef-185">保留默认值（“最近状态”）；或者通过单击“浏览”按钮，打开“时间点还原”对话框，从中选择特定的日期和时间。</span><span class="sxs-lookup"><span data-stu-id="f1cef-185">Either retain the default (**Most recent possible**) or select a specific date and time by clicking the browse button, which opens the **Point in Time Restore** dialog box.</span></span>  
  
    -   <span data-ttu-id="f1cef-186">**标记的事务**</span><span class="sxs-lookup"><span data-stu-id="f1cef-186">**Marked transaction**</span></span>  
  
         <span data-ttu-id="f1cef-187">将数据库还原为以前标记的事务。</span><span class="sxs-lookup"><span data-stu-id="f1cef-187">Restore the database to a previously marked transaction.</span></span> <span data-ttu-id="f1cef-188">选择此选项会启动 **“选择标记的事务”** 对话框，从而显示一个网格，列出选定事务日志备份中可以使用的标记的事务。</span><span class="sxs-lookup"><span data-stu-id="f1cef-188">Selecting this option launches the **Select Marked Transaction** dialog box, which displays a grid listing the marked transactions available in the selected transaction log backups.</span></span>  
  
         <span data-ttu-id="f1cef-189">默认情况下，将一直还原到（但不包含）标记的事务为止。</span><span class="sxs-lookup"><span data-stu-id="f1cef-189">By default, the restore is up to, but excluding, the marked transaction.</span></span> <span data-ttu-id="f1cef-190">若要同时还原标记的事务，请选择 **“包含标记的事务”** 。</span><span class="sxs-lookup"><span data-stu-id="f1cef-190">To restore the marked transaction also, select **Include marked transaction**.</span></span>  
  
         <span data-ttu-id="f1cef-191">下表列出了网格的列标题并对列值进行了说明。</span><span class="sxs-lookup"><span data-stu-id="f1cef-191">The following table lists the column headers of the grid and describes their values.</span></span>  
  
        |<span data-ttu-id="f1cef-192">标头</span><span class="sxs-lookup"><span data-stu-id="f1cef-192">Header</span></span>|<span data-ttu-id="f1cef-193">值</span><span class="sxs-lookup"><span data-stu-id="f1cef-193">Value</span></span>|  
        |------------|-----------|  
        |\<blank>|<span data-ttu-id="f1cef-194">显示一个用于选择标记的复选框。</span><span class="sxs-lookup"><span data-stu-id="f1cef-194">Displays a checkbox for selecting the mark.</span></span>|  
        |<span data-ttu-id="f1cef-195">**事务标记**</span><span class="sxs-lookup"><span data-stu-id="f1cef-195">**Transaction Mark**</span></span>|<span data-ttu-id="f1cef-196">提交事务时，用户为标记的事务指定的名称。</span><span class="sxs-lookup"><span data-stu-id="f1cef-196">Name of the marked transaction specified by the user when the transaction was committed.</span></span>|  
        |<span data-ttu-id="f1cef-197">**Date**</span><span class="sxs-lookup"><span data-stu-id="f1cef-197">**Date**</span></span>|<span data-ttu-id="f1cef-198">事务的提交日期及时间。</span><span class="sxs-lookup"><span data-stu-id="f1cef-198">Date and time of the transaction when it was committed.</span></span> <span data-ttu-id="f1cef-199">事务日期和时间显示为 **msdbgmarkhistory** 表中所记录的日期和时间，而非客户端计算机的日期和时间。</span><span class="sxs-lookup"><span data-stu-id="f1cef-199">Transaction date and time are displayed as recorded in the **msdbgmarkhistory** table, not in the client computer's date and time.</span></span>|  
        |<span data-ttu-id="f1cef-200">**说明**</span><span class="sxs-lookup"><span data-stu-id="f1cef-200">**Description**</span></span>|<span data-ttu-id="f1cef-201">提交事务时，用户为标记的事务指定的说明（如果有的话）。</span><span class="sxs-lookup"><span data-stu-id="f1cef-201">Description of marked transaction specified by the user when the transaction was committed (if any).</span></span>|  
        |<span data-ttu-id="f1cef-202">**LSN**</span><span class="sxs-lookup"><span data-stu-id="f1cef-202">**LSN**</span></span>|<span data-ttu-id="f1cef-203">所标记事务的日志序列号。</span><span class="sxs-lookup"><span data-stu-id="f1cef-203">Log sequence number of the marked transaction.</span></span>|  
        |<span data-ttu-id="f1cef-204">**Database**</span><span class="sxs-lookup"><span data-stu-id="f1cef-204">**Database**</span></span>|<span data-ttu-id="f1cef-205">提交标记的事务时所在数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="f1cef-205">Name of the database where the marked transaction was committed.</span></span>|  
        |<span data-ttu-id="f1cef-206">**用户名**</span><span class="sxs-lookup"><span data-stu-id="f1cef-206">**User Name**</span></span>|<span data-ttu-id="f1cef-207">提交标记事务的数据库用户的名称。</span><span class="sxs-lookup"><span data-stu-id="f1cef-207">Name of the database user who committed the marked transaction.</span></span>|  
  
8.  <span data-ttu-id="f1cef-208">若要查看或选择高级选项，请在 **“选择页”** 窗格中单击 **“选项”** 。</span><span class="sxs-lookup"><span data-stu-id="f1cef-208">To view or select the advanced options, click **Options** in the **Select a page** pane.</span></span>  
  
9. <span data-ttu-id="f1cef-209">在 **“还原选项”** 部分中，选项有：</span><span class="sxs-lookup"><span data-stu-id="f1cef-209">In the **Restore options** section, the choices are:</span></span>  
  
    -   <span data-ttu-id="f1cef-210">**保留复制设置(WITH KEEP_REPLICATION)**</span><span class="sxs-lookup"><span data-stu-id="f1cef-210">**Preserve the replication settings (WITH KEEP_REPLICATION)**</span></span>  
  
         <span data-ttu-id="f1cef-211">将已发布的数据库还原到创建该数据库的服务器之外的服务器时，保留复制设置。</span><span class="sxs-lookup"><span data-stu-id="f1cef-211">Preserves the replication settings when restoring a published database to a server other than the server where the database was created.</span></span>  
  
         <span data-ttu-id="f1cef-212">此选项仅在以下情况下可用 **： "回滚未提交的事务，使数据库保持**可用状态 ..." 选项 (稍后所述) ，这等效于使用选项还原备份。 `RECOVERY`</span><span class="sxs-lookup"><span data-stu-id="f1cef-212">This option is available only with the **Leave the database ready for use by rolling back the uncommitted transactions...** option (described later), which is equivalent to restoring a backup with the `RECOVERY` option.</span></span>  
  
         <span data-ttu-id="f1cef-213">选中此选项等效于 `KEEP_REPLICATION` 在语句中使用选项 [!INCLUDE[tsql](../../includes/tsql-md.md)] `RESTORE` 。</span><span class="sxs-lookup"><span data-stu-id="f1cef-213">Checking this option is equivalent to using the `KEEP_REPLICATION` option in a [!INCLUDE[tsql](../../includes/tsql-md.md)]`RESTORE` statement.</span></span>  
  
    -   <span data-ttu-id="f1cef-214">**还原每个备份之前进行提示**</span><span class="sxs-lookup"><span data-stu-id="f1cef-214">**Prompt before restoring each backup**</span></span>  
  
         <span data-ttu-id="f1cef-215">如果选中此选项，则在第一个备份集之后还原每个备份集之前，将显示“继续还原”对话框，询问你是否要继续此还原顺序。</span><span class="sxs-lookup"><span data-stu-id="f1cef-215">Before restoring each backup set (after the first), this option brings up the **Continue with Restore** dialog box, which asks you to indicate whether you want to continue the restore sequence.</span></span> <span data-ttu-id="f1cef-216">此对话框显示下一个介质集（如果可用）的名称、备份集的名称以及备份集的说明。</span><span class="sxs-lookup"><span data-stu-id="f1cef-216">This dialog displays the name of the next media set (if available), the backup set name, and backup set description.</span></span>  
  
         <span data-ttu-id="f1cef-217">如果对于不同介质集必须更换磁带，则此选项特别有用。</span><span class="sxs-lookup"><span data-stu-id="f1cef-217">This option is particularly useful when you must swap tapes for different media sets.</span></span> <span data-ttu-id="f1cef-218">例如，如果服务器只有一个磁带设备，则可以使用此选项。</span><span class="sxs-lookup"><span data-stu-id="f1cef-218">For example, you can use it when the server has only one tape device.</span></span> <span data-ttu-id="f1cef-219">待您做好继续操作的准备后，再单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="f1cef-219">Wait until you are ready to proceed before clicking **OK**.</span></span>  
  
         <span data-ttu-id="f1cef-220">单击 **“否”** 将使数据库保持还原状态。</span><span class="sxs-lookup"><span data-stu-id="f1cef-220">Clicking **No** leaves the database in the restoring state.</span></span> <span data-ttu-id="f1cef-221">完成上次还原之后，您可以在方便时继续按顺序还原。</span><span class="sxs-lookup"><span data-stu-id="f1cef-221">At your convenience, you can continue the restore sequence after the last restore that completed.</span></span> <span data-ttu-id="f1cef-222">如果下一个备份是数据备份或差异备份，请再次使用 **“还原数据库”** 任务。</span><span class="sxs-lookup"><span data-stu-id="f1cef-222">If the next backup is a data or differential backup, use the **Restore Database** task again.</span></span> <span data-ttu-id="f1cef-223">如果下一个备份是日志备份，请使用 **“还原事务日志”** 任务。</span><span class="sxs-lookup"><span data-stu-id="f1cef-223">If the next backup is a log backup, use the **Restore Transaction Log** task.</span></span>  
  
    -   <span data-ttu-id="f1cef-224">**限制对还原数据库的访问(WITH RESTRICTED_USER)**</span><span class="sxs-lookup"><span data-stu-id="f1cef-224">**Restrict access to the restored database (WITH RESTRICTED_USER)**</span></span>  
  
         <span data-ttu-id="f1cef-225">使还原的数据库仅供 **db_owner**、 **dbcreator**或 **sysadmin**的成员使用。</span><span class="sxs-lookup"><span data-stu-id="f1cef-225">Makes the restored database available only to the members of **db_owner**, **dbcreator**, or **sysadmin**.</span></span>  
  
         <span data-ttu-id="f1cef-226">选中此选项是 `RESTRICTED_USER` 在语句中使用选项的同义词 [!INCLUDE[tsql](../../includes/tsql-md.md)] `RESTORE` 。</span><span class="sxs-lookup"><span data-stu-id="f1cef-226">Checking this option is synonymous to using the `RESTRICTED_USER` option in a [!INCLUDE[tsql](../../includes/tsql-md.md)]`RESTORE` statement.</span></span>  
  
10. <span data-ttu-id="f1cef-227">对于 **“恢复状态”** 选项，请指定还原操作之后的数据库状态。</span><span class="sxs-lookup"><span data-stu-id="f1cef-227">For the **Recovery state** options, specify the state of the database after the restore operation.</span></span>  
  
    -   <span data-ttu-id="f1cef-228">**回退未提交的事务，使数据库处于可以使用的状态。无法还原其他事务日志。(RESTORE WITH RECOVERY)**</span><span class="sxs-lookup"><span data-stu-id="f1cef-228">**Leave the database ready for use by rolling back uncommitted transactions. Additional transaction logs cannot be restored. (RESTORE WITH RECOVERY)**</span></span>  
  
         <span data-ttu-id="f1cef-229">恢复数据库。</span><span class="sxs-lookup"><span data-stu-id="f1cef-229">Recovers the database.</span></span> <span data-ttu-id="f1cef-230">此选项等效于 `RECOVERY` 语句中的选项 [!INCLUDE[tsql](../../includes/tsql-md.md)] `RESTORE` 。</span><span class="sxs-lookup"><span data-stu-id="f1cef-230">This option is equivalent to the `RECOVERY` option in a [!INCLUDE[tsql](../../includes/tsql-md.md)]`RESTORE` statement.</span></span>  
  
         <span data-ttu-id="f1cef-231">请仅在没有要还原的日志文件时选择此选项。</span><span class="sxs-lookup"><span data-stu-id="f1cef-231">Choose this option only if you have no log files you want to restore.</span></span>  
  
    -   <span data-ttu-id="f1cef-232">**不对数据库执行任何操作，不回退未提交的事务。可以还原其他事务日志。(RESTORE WITH NORECOVERY)**</span><span class="sxs-lookup"><span data-stu-id="f1cef-232">**Leave the database non-operational, and do not roll back uncommitted transactions. Additional transaction logs can be restored. (RESTORE WITH NORECOVERY)**</span></span>  
  
         <span data-ttu-id="f1cef-233">使数据库处于未恢复的 `RESTORING` 状态。</span><span class="sxs-lookup"><span data-stu-id="f1cef-233">Leaves the database unrecovered, in the `RESTORING` state.</span></span> <span data-ttu-id="f1cef-234">此选项等效于 `NORECOVERY` 在语句中使用选项 [!INCLUDE[tsql](../../includes/tsql-md.md)] `RESTORE` 。</span><span class="sxs-lookup"><span data-stu-id="f1cef-234">This option is equivalent to using the `NORECOVERY` option in a [!INCLUDE[tsql](../../includes/tsql-md.md)]`RESTORE` statement.</span></span>  
  
         <span data-ttu-id="f1cef-235">如果选择此选项， **“保留复制设置”** 选项将不可用。</span><span class="sxs-lookup"><span data-stu-id="f1cef-235">When you choose this option, the **Preserve replication settings** option is unavailable.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="f1cef-236">对于镜像或辅助数据库，应始终选择此选项。</span><span class="sxs-lookup"><span data-stu-id="f1cef-236">For a mirror or secondary database, always select this option.</span></span>  
  
    -   <span data-ttu-id="f1cef-237">**使数据库处于只读模式。撤消未提交的事务，但将撤消操作保存在文件中，以便可使恢复效果逆转。(RESTORE WITH STANDBY)**</span><span class="sxs-lookup"><span data-stu-id="f1cef-237">**Leave the database in read-only mode. Undo uncommitted transactions, but save the undo actions in a file so that recovery effects can be reversed. (RESTORE WITH STANDBY)**</span></span>  
  
         <span data-ttu-id="f1cef-238">使数据库处于备用状态。</span><span class="sxs-lookup"><span data-stu-id="f1cef-238">Leaves the database in a standby state.</span></span> <span data-ttu-id="f1cef-239">此选项等效于 `STANDBY` 在语句中使用选项 [!INCLUDE[tsql](../../includes/tsql-md.md)] `RESTORE` 。</span><span class="sxs-lookup"><span data-stu-id="f1cef-239">This option is equivalent to using the `STANDBY` option in a [!INCLUDE[tsql](../../includes/tsql-md.md)]`RESTORE` statement.</span></span>  
  
         <span data-ttu-id="f1cef-240">选择此选项需要您指定一个备用文件。</span><span class="sxs-lookup"><span data-stu-id="f1cef-240">Choosing this option requires that you specify a standby file.</span></span>  
  
11. <span data-ttu-id="f1cef-241">可选选项。如果选中此选项，请在 **“备用文件”** 文本框中指定备用文件的名称。</span><span class="sxs-lookup"><span data-stu-id="f1cef-241">Optionally, specify a standby file name in the **Standby file** text box.</span></span> <span data-ttu-id="f1cef-242">如果您使数据库处于只读模式，则必须选中此选项。</span><span class="sxs-lookup"><span data-stu-id="f1cef-242">This option is required if you leave the database in read-only mode.</span></span> <span data-ttu-id="f1cef-243">您可以浏览到该备用文件，也可以在文本框中键入其路径名。</span><span class="sxs-lookup"><span data-stu-id="f1cef-243">You can browse for the standby file or type its pathname in the text box.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="f1cef-244">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f1cef-244">Using Transact-SQL</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f1cef-245">我们建议您在每个 RESTORE 语句中显式指定 WITH NORECOVERY 或 WITH RECOVERY 以消除混淆。</span><span class="sxs-lookup"><span data-stu-id="f1cef-245">We recommend that you always explicitly specify either WITH NORECOVERY or WITH RECOVERY in every RESTORE statement to eliminate ambiguity.</span></span> <span data-ttu-id="f1cef-246">在编写脚本时，这样做尤其重要。</span><span class="sxs-lookup"><span data-stu-id="f1cef-246">This is particularly important when writing scripts.</span></span>  
  
#### <a name="to-restore-a-transaction-log-backup"></a><span data-ttu-id="f1cef-247">还原事务日志备份</span><span class="sxs-lookup"><span data-stu-id="f1cef-247">To restore a transaction log backup</span></span>  
  
1.  <span data-ttu-id="f1cef-248">执行 RESTORE LOG 语句应用事务日志备份，同时指定：</span><span class="sxs-lookup"><span data-stu-id="f1cef-248">Execute the RESTORE LOG statement to apply the transaction log backup, specifying:</span></span>  
  
    -   <span data-ttu-id="f1cef-249">事务日志将应用到的数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="f1cef-249">The name of the database to which the transaction log will be applied.</span></span>  
  
    -   <span data-ttu-id="f1cef-250">将从其中还原事务日志备份的备份设备。</span><span class="sxs-lookup"><span data-stu-id="f1cef-250">The backup device where the transaction log backup will be restored from.</span></span>  
  
    -   <span data-ttu-id="f1cef-251">NORECOVERY 子句。</span><span class="sxs-lookup"><span data-stu-id="f1cef-251">The NORECOVERY clause.</span></span>  
  
     <span data-ttu-id="f1cef-252">此语句的基本语法如下：</span><span class="sxs-lookup"><span data-stu-id="f1cef-252">The basic syntax for this statement is as follows:</span></span>  
  
     <span data-ttu-id="f1cef-253">RESTORE LOG *database_name* FROM <backup_device> WITH NORECOVERY。</span><span class="sxs-lookup"><span data-stu-id="f1cef-253">RESTORE LOG *database_name* FROM <backup_device> WITH NORECOVERY.</span></span>  
  
     <span data-ttu-id="f1cef-254">其中，*database_name* 是数据库的名称，<backup_device> 是包含正在还原的日志备份的设备的名称。</span><span class="sxs-lookup"><span data-stu-id="f1cef-254">Where *database_name* is the name of database and <backup_device>is the name of the device that contains the log backup being restored.</span></span>  
  
2.  <span data-ttu-id="f1cef-255">对必须应用的每个事务日志备份重复步骤 1。</span><span class="sxs-lookup"><span data-stu-id="f1cef-255">Repeat step 1 for each transaction log backup you have to apply.</span></span>  
  
3.  <span data-ttu-id="f1cef-256">按照还原顺序还原了最后一个备份之后，可使用以下语句之一恢复数据库：</span><span class="sxs-lookup"><span data-stu-id="f1cef-256">After restoring the last backup in your restore sequence, to recover the database use one of the following statements:</span></span>  
  
    -   <span data-ttu-id="f1cef-257">作为上一个 RESTORE LOG 语句的一部分恢复数据库：</span><span class="sxs-lookup"><span data-stu-id="f1cef-257">Recover the database as part of the last RESTORE LOG statement:</span></span>  
  
        ```  
        RESTORE LOG <database_name> FROM <backup_device> WITH RECOVERY;  
        GO  
        ```  
  
    -   <span data-ttu-id="f1cef-258">等待使用单独的 RESTORE DATABASE 语句恢复数据库：</span><span class="sxs-lookup"><span data-stu-id="f1cef-258">Wait to recover the database by using a separate RESTORE DATABASE statement:</span></span>  
  
        ```  
        RESTORE LOG <database_name> FROM <backup_device> WITH NORECOVERY;   
        RESTORE DATABASE <database_name> WITH RECOVERY;  
        GO  
        ```  
  
         <span data-ttu-id="f1cef-259">通过等待恢复数据库，可以确认已还原所有必需的日志备份。</span><span class="sxs-lookup"><span data-stu-id="f1cef-259">Waiting to recover the database gives you the opportunity to verify that you have restored all of the necessary log backups.</span></span> <span data-ttu-id="f1cef-260">执行时点还原时最好使用该方法。</span><span class="sxs-lookup"><span data-stu-id="f1cef-260">This approach is often advisable when you are performing a point-in-time restore.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="f1cef-261">如果要创建镜像数据库，则省略恢复步骤。</span><span class="sxs-lookup"><span data-stu-id="f1cef-261">If you are creating a mirror database, omit the recovery step.</span></span> <span data-ttu-id="f1cef-262">镜像数据库必须仍处于 RESTORING 状态。</span><span class="sxs-lookup"><span data-stu-id="f1cef-262">A mirror database must remain in the RESTORING state.</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="f1cef-263">示例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="f1cef-263">Examples (Transact-SQL)</span></span>  
 <span data-ttu-id="f1cef-264">默认情况下， [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 数据库使用简单恢复模式。</span><span class="sxs-lookup"><span data-stu-id="f1cef-264">By default, the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database uses the simple recovery model.</span></span> <span data-ttu-id="f1cef-265">以下示例要求修改数据库以使用完整恢复模式，如下所示：</span><span class="sxs-lookup"><span data-stu-id="f1cef-265">The following examples require modifying the database to use the full recovery model, as follows:</span></span>  
  
```sql  
ALTER DATABASE AdventureWorks2012 SET RECOVERY FULL;  
```  
  
#### <a name="a-applying-a-single-transaction-log-backup"></a><span data-ttu-id="f1cef-266">A.</span><span class="sxs-lookup"><span data-stu-id="f1cef-266">A.</span></span> <span data-ttu-id="f1cef-267">应用单个事务日志备份</span><span class="sxs-lookup"><span data-stu-id="f1cef-267">Applying a single transaction log backup</span></span>  
 <span data-ttu-id="f1cef-268">以下示例开始时使用名为 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 备份设备上的完整数据库备份来还原 `AdventureWorks2012_1`数据库。</span><span class="sxs-lookup"><span data-stu-id="f1cef-268">The following example starts by restoring the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database by using a full database backup that resides on a backup device named `AdventureWorks2012_1`.</span></span> <span data-ttu-id="f1cef-269">然后该示例应用名为 `AdventureWorks2012_log`备份设备上的第一个事务日志备份。</span><span class="sxs-lookup"><span data-stu-id="f1cef-269">The example then applies the first transaction log backup that resides on a backup device named `AdventureWorks2012_log`.</span></span> <span data-ttu-id="f1cef-270">最后，该示例恢复数据库。</span><span class="sxs-lookup"><span data-stu-id="f1cef-270">Finally, the example recovers the database.</span></span>  
  
```sql  
RESTORE DATABASE AdventureWorks2012  
   FROM AdventureWorks2012_1  
   WITH NORECOVERY;  
GO  
RESTORE LOG AdventureWorks2012  
   FROM AdventureWorks2012_log  
   WITH FILE = 1,  
   WITH NORECOVERY;  
GO  
RESTORE DATABASE AdventureWorks2012  
   WITH RECOVERY;  
GO  
```  
  
#### <a name="b-applying-multiple-transaction-log-backups"></a><span data-ttu-id="f1cef-271">B.</span><span class="sxs-lookup"><span data-stu-id="f1cef-271">B.</span></span> <span data-ttu-id="f1cef-272">应用多个事务日志备份</span><span class="sxs-lookup"><span data-stu-id="f1cef-272">Applying multiple transaction log backups</span></span>  
 <span data-ttu-id="f1cef-273">以下示例开始时使用名为 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 备份设备上的完整数据库备份来还原 `AdventureWorks2012_1`数据库。</span><span class="sxs-lookup"><span data-stu-id="f1cef-273">The following example starts by restoring the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database by using a full database backup that resides on a backup device named `AdventureWorks2012_1`.</span></span> <span data-ttu-id="f1cef-274">然后该示例逐一使用名为 `AdventureWorks2012_log`备份设备上的前三个事务日志备份。</span><span class="sxs-lookup"><span data-stu-id="f1cef-274">The example then applies, one by one, the first three transaction log backups that reside on a backup device named `AdventureWorks2012_log`.</span></span> <span data-ttu-id="f1cef-275">最后，该示例恢复数据库。</span><span class="sxs-lookup"><span data-stu-id="f1cef-275">Finally, the example recovers the database.</span></span>  
  
```sql  
RESTORE DATABASE AdventureWorks2012  
   FROM AdventureWorks2012_1  
   WITH NORECOVERY;  
GO  
RESTORE LOG AdventureWorks2012  
   FROM AdventureWorks2012_log  
   WITH FILE = 1,  
   NORECOVERY;  
GO  
RESTORE LOG AdventureWorks2012  
   FROM AdventureWorks2012_log  
   WITH FILE = 2,  
   WITH NORECOVERY;  
GO  
RESTORE LOG AdventureWorks2012  
   FROM AdventureWorks2012_log  
   WITH FILE = 3,  
   WITH NORECOVERY;  
GO  
RESTORE DATABASE AdventureWorks2012  
   WITH RECOVERY;  
GO  
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="f1cef-276">相关任务</span><span class="sxs-lookup"><span data-stu-id="f1cef-276">Related Tasks</span></span>  
  
-   [<span data-ttu-id="f1cef-277">备份事务日志 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f1cef-277">Back Up a Transaction Log &#40;SQL Server&#41;</span></span>](back-up-a-transaction-log-sql-server.md)  
  
-   [<span data-ttu-id="f1cef-278">还原数据库备份 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="f1cef-278">Restore a Database Backup &#40;SQL Server Management Studio&#41;</span></span>](restore-a-database-backup-using-ssms.md)  
  
-   [<span data-ttu-id="f1cef-279">在完整恢复模式下将数据库还原到故障点 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="f1cef-279">Restore a Database to the Point of Failure Under the Full Recovery Model &#40;Transact-SQL&#41;</span></span>](restore-database-to-point-of-failure-full-recovery.md)  
  
-   [<span data-ttu-id="f1cef-280">将 SQL Server 数据库还原到某个时间点（完整恢复模式）</span><span class="sxs-lookup"><span data-stu-id="f1cef-280">Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;</span></span>](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)  
  
-   [<span data-ttu-id="f1cef-281">将数据库还原到标记的事务 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="f1cef-281">Restore a Database to a Marked Transaction &#40;SQL Server Management Studio&#41;</span></span>](restore-a-database-to-a-marked-transaction-sql-server-management-studio.md)  
  
## <a name="see-also"></a><span data-ttu-id="f1cef-282">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f1cef-282">See Also</span></span>  
 <span data-ttu-id="f1cef-283">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f1cef-283">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 [<span data-ttu-id="f1cef-284">应用事务日志备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f1cef-284">Apply Transaction Log Backups &#40;SQL Server&#41;</span></span>](apply-transaction-log-backups-sql-server.md)  
  
  
