---
title: 配置日志传送 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- log shipping [SQL Server], enabling
- log shipping [SQL Server], configuring
ms.assetid: c42aa04a-4945-4417-b4c7-50589d727e9c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 269b0ae2980435e507128cc87606f7eb702c2b7f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688148"
---
# <a name="configure-log-shipping-sql-server"></a><span data-ttu-id="127d2-102">配置日志传送 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="127d2-102">Configure Log Shipping (SQL Server)</span></span>
  <span data-ttu-id="127d2-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中配置日志传送。</span><span class="sxs-lookup"><span data-stu-id="127d2-103">This topic describes how to configure log shipping in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] <span data-ttu-id="127d2-104">及更高版本支持备份压缩。</span><span class="sxs-lookup"><span data-stu-id="127d2-104">and later versions support backup compression.</span></span> <span data-ttu-id="127d2-105">创建日志传送配置时，可以控制日志备份的备份压缩行为。</span><span class="sxs-lookup"><span data-stu-id="127d2-105">When creating a log shipping configuration, you can control the backup compression behavior of log backups.</span></span> <span data-ttu-id="127d2-106">有关详细信息，请参阅[备份压缩 (SQL Server)](../../relational-databases/backup-restore/backup-compression-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="127d2-106">For more information, see [Backup Compression &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-compression-sql-server.md).</span></span>  
  
 <span data-ttu-id="127d2-107">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="127d2-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="127d2-108">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="127d2-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="127d2-109">先决条件</span><span class="sxs-lookup"><span data-stu-id="127d2-109">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="127d2-110">安全性</span><span class="sxs-lookup"><span data-stu-id="127d2-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="127d2-111">**若要配置日志传送，请使用：**</span><span class="sxs-lookup"><span data-stu-id="127d2-111">**To configure log shipping, using:**</span></span>  
  
     [<span data-ttu-id="127d2-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="127d2-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="127d2-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="127d2-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   [<span data-ttu-id="127d2-114">相关任务</span><span class="sxs-lookup"><span data-stu-id="127d2-114">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="127d2-115">开始之前</span><span class="sxs-lookup"><span data-stu-id="127d2-115">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="127d2-116">先决条件</span><span class="sxs-lookup"><span data-stu-id="127d2-116">Prerequisites</span></span>  
  
-   <span data-ttu-id="127d2-117">主数据库必须使用完整恢复模式或大容量日志恢复模式，将数据库切换为简单恢复模式会导致日志传送停止工作。</span><span class="sxs-lookup"><span data-stu-id="127d2-117">The primary database must use the full or bulk-logged recovery model; switching the database to simple recovery will cause log shipping to stop functioning.</span></span>  
  
-   <span data-ttu-id="127d2-118">在配置日志传送之前，您必须创建共享，以便辅助服务器可以访问事务日志备份。</span><span class="sxs-lookup"><span data-stu-id="127d2-118">Before you configure log shipping, you must create a share to make the transaction log backups available to the secondary server.</span></span> <span data-ttu-id="127d2-119">这是对生成事务日志备份的目录的共享。</span><span class="sxs-lookup"><span data-stu-id="127d2-119">This is a share of the directory where the transaction log backups will be generated.</span></span> <span data-ttu-id="127d2-120">例如，如果将事务日志备份到目录 C:\data\tlogs\\，则可以对该目录创建 \\\\*primaryserver*\tlogs 共享。</span><span class="sxs-lookup"><span data-stu-id="127d2-120">For example, if you back up your transaction logs to the directory c:\data\tlogs\\, you could create the \\\\*primaryserver*\tlogs share of that directory.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="127d2-121">Security</span><span class="sxs-lookup"><span data-stu-id="127d2-121">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="127d2-122">权限</span><span class="sxs-lookup"><span data-stu-id="127d2-122">Permissions</span></span>  
 <span data-ttu-id="127d2-123">日志传送存储过程要求 **sysadmin** 固定服务器角色中的成员身份。</span><span class="sxs-lookup"><span data-stu-id="127d2-123">The log-shipping stored procedures require membership in the **sysadmin** fixed server role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="127d2-124">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="127d2-124">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-log-shipping"></a><span data-ttu-id="127d2-125">配置日志传送</span><span class="sxs-lookup"><span data-stu-id="127d2-125">To configure log shipping</span></span>  
  
1.  <span data-ttu-id="127d2-126">右键单击要在日志传送配置中用作主数据库的数据库，然后单击 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="127d2-126">Right click the database you want to use as your primary database in the log shipping configuration, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="127d2-127">在 **“选择页”** 下，单击 **“事务日志传送”** 。</span><span class="sxs-lookup"><span data-stu-id="127d2-127">Under **Select a page**, click **Transaction Log Shipping**.</span></span>  
  
3.  <span data-ttu-id="127d2-128">选中 **“将此数据库启用为日志传送配置中的主数据库”** 复选框。</span><span class="sxs-lookup"><span data-stu-id="127d2-128">Select the **Enable this as a primary database in a log shipping configuration** check box.</span></span>  
  
4.  <span data-ttu-id="127d2-129">在 **“事务日志备份”** 下，单击 **“备份设置”** 。</span><span class="sxs-lookup"><span data-stu-id="127d2-129">Under **Transaction log backups**, click **Backup Settings**.</span></span>  
  
5.  <span data-ttu-id="127d2-130">在 **“备份文件夹的网络路径”** 框中，键入为事务日志备份文件夹创建的共享的网络路径。</span><span class="sxs-lookup"><span data-stu-id="127d2-130">In the **Network path to the backup folder** box, type the network path to the share you created for the transaction log backup folder.</span></span>  
  
6.  <span data-ttu-id="127d2-131">如果备份文件夹位于主服务器上，在 **“如果备份文件夹位于主服务器上，则键入该文件夹的本地路径”** 框中键入该备份文件夹的本地路径。</span><span class="sxs-lookup"><span data-stu-id="127d2-131">If the backup folder is located on the primary server, type the local path to the backup folder in the **If the backup folder is located on the primary server, type a local path to the folder** box.</span></span> <span data-ttu-id="127d2-132">（如果备份文件夹不在主服务器上，此框可以保留为空。）</span><span class="sxs-lookup"><span data-stu-id="127d2-132">(If the backup folder is not on the primary server, you can leave this box empty.)</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="127d2-133">如果主服务器上的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务帐户运行在本地系统帐户下，则必须在主服务器上创建备份文件夹，并指定该文件夹的本地路径。</span><span class="sxs-lookup"><span data-stu-id="127d2-133">If the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service account on your primary server runs under the local system account, you must create your backup folder on the primary server and specify a local path to that folder.</span></span>  
  
7.  <span data-ttu-id="127d2-134">配置 **“删除文件，如果其保留时间超过”** 和 **“在以下时间内没有执行备份时报警”** 参数。</span><span class="sxs-lookup"><span data-stu-id="127d2-134">Configure the **Delete files older than** and **Alert if no backup occurs within** parameters.</span></span>  
  
8.  <span data-ttu-id="127d2-135">请注意 **“备份作业”** 下的 **“计划”** 框中列出的备份计划。</span><span class="sxs-lookup"><span data-stu-id="127d2-135">Note the backup schedule listed in the **Schedule** box under **Backup job**.</span></span> <span data-ttu-id="127d2-136">如果想要为安装自定义计划，则单击 **“计划”** 并根据需要调整 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理计划。</span><span class="sxs-lookup"><span data-stu-id="127d2-136">If you want to customize the schedule for your installation, then click **Schedule** and adjust the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent schedule as needed.</span></span>  
  
9. [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="127d2-137">支持 [备份压缩](../../relational-databases/backup-restore/backup-compression-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="127d2-137">supports [backup compression](../../relational-databases/backup-restore/backup-compression-sql-server.md).</span></span> <span data-ttu-id="127d2-138">创建日志传送配置时，可以通过选择以下选项之一来控制日志备份的备份压缩行为：“使用默认服务器设置”、“压缩备份”或“不压缩备份”  。</span><span class="sxs-lookup"><span data-stu-id="127d2-138">When creating a log shipping configuration, you can control the backup compression behavior of log backups by choosing one of the following options: **Use the default server setting**, **Compress backup**, or **Do not compress backup**.</span></span> <span data-ttu-id="127d2-139">有关详细信息，请参阅 [Log Shipping Transaction Log Backup Settings](../../relational-databases/databases/log-shipping-transaction-log-backup-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="127d2-139">For more information, see [Log Shipping Transaction Log Backup Settings](../../relational-databases/databases/log-shipping-transaction-log-backup-settings.md).</span></span>  
  
10. <span data-ttu-id="127d2-140">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="127d2-140">Click **OK**.</span></span>  
  
11. <span data-ttu-id="127d2-141">在 **“辅助服务器实例和数据库”** 下，单击 **“添加”** 。</span><span class="sxs-lookup"><span data-stu-id="127d2-141">Under **Secondary server instances and databases**, click **Add**.</span></span>  
  
12. <span data-ttu-id="127d2-142">单击 **“连接”** ，连接到要用作辅助服务器的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="127d2-142">Click **Connect** and connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that you want to use as your secondary server.</span></span>  
  
13. <span data-ttu-id="127d2-143">在 **“辅助数据库”** 框中，从列表中选择一个数据库或键入想要创建的数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="127d2-143">In the **Secondary Database** box, choose a database from the list or type the name of the database you want to create.</span></span>  
  
14. <span data-ttu-id="127d2-144">在 **“初始化辅助数据库”** 选项卡上，选择要用于初始化辅助数据库的选项。</span><span class="sxs-lookup"><span data-stu-id="127d2-144">On the **Initialize Secondary database** tab, choose the option that you want to use to initialize the secondary database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="127d2-145">如果选择让 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 从数据库备份中初始化辅助数据库，则辅助数据库的数据文件和日志文件将与 **master** 数据库的数据文件和日志文件放置在同一位置。</span><span class="sxs-lookup"><span data-stu-id="127d2-145">If you choose to have [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] initialize the secondary database from a database backup, the data and log files of the secondary database are placed in the same location as the data and log files of the **master** database.</span></span> <span data-ttu-id="127d2-146">此位置可能不同于主数据库的数据文件和日志文件所在的位置。</span><span class="sxs-lookup"><span data-stu-id="127d2-146">This location is likely to be different than the location of the data and log files of the primary database.</span></span>  
  
15. <span data-ttu-id="127d2-147">在 **“复制文件”** 选项卡上的 **“复制文件的目标文件夹”** 框中，键入应该将事务日志备份复制到其中的文件夹的路径。</span><span class="sxs-lookup"><span data-stu-id="127d2-147">On the **Copy Files** tab, in the **Destination folder for copied files** box, type the path of the folder into which the transaction logs backups should be copied.</span></span> <span data-ttu-id="127d2-148">该文件夹通常位于辅助服务器上。</span><span class="sxs-lookup"><span data-stu-id="127d2-148">This folder is often located on the secondary server.</span></span>  
  
16. <span data-ttu-id="127d2-149">请注意 **“复制作业”** 下的 **“计划”** 框中列出的复制计划。</span><span class="sxs-lookup"><span data-stu-id="127d2-149">Note the copy schedule listed in the **Schedule** box under **Copy job**.</span></span> <span data-ttu-id="127d2-150">如果要自定义安装计划，请单击 **“计划”** ，然后根据需要调整 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理计划。</span><span class="sxs-lookup"><span data-stu-id="127d2-150">If you want to customize the schedule for your installation, click **Schedule** and then adjust the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent schedule as needed.</span></span> <span data-ttu-id="127d2-151">此计划应为大致的备份计划。</span><span class="sxs-lookup"><span data-stu-id="127d2-151">This schedule should approximate the backup schedule.</span></span>  
  
17. <span data-ttu-id="127d2-152">在 **“还原”** 选项卡上的 **“还原备份时的数据库状态”** 下，选择 **“无恢复模式”** 或 **“备用模式”** 选项。</span><span class="sxs-lookup"><span data-stu-id="127d2-152">On the **Restore** tab, under **Database state when restoring backups**, choose the **No recovery mode** or **Standby mode** option.</span></span>  
  
18. <span data-ttu-id="127d2-153">如果选择了 **“备用模式”** 选项，请选择是否要在进行还原操作时从辅助数据库断开用户连接。</span><span class="sxs-lookup"><span data-stu-id="127d2-153">If you chose the **Standby mode** option, choose if you want to disconnect users from the secondary database while the restore operation is underway.</span></span>  
  
19. <span data-ttu-id="127d2-154">如果希望延迟辅助服务器上的还原进程，请在 **“延迟还原备份操作至少”** 下选择延迟时间。</span><span class="sxs-lookup"><span data-stu-id="127d2-154">If you want to delay the restore process on the secondary server, choose a delay time under **Delay restoring backups at least**.</span></span>  
  
20. <span data-ttu-id="127d2-155">在 **“在以下时间内没有执行还原时报警”** 下选择警报阈值。</span><span class="sxs-lookup"><span data-stu-id="127d2-155">Choose an alert threshold under **Alert if no restore occurs within**.</span></span>  
  
21. <span data-ttu-id="127d2-156">请注意 **“还原作业”** 下 **“计划”** 框中列出的还原计划。</span><span class="sxs-lookup"><span data-stu-id="127d2-156">Note the restore schedule listed in the **Schedule** box under **Restore job**.</span></span> <span data-ttu-id="127d2-157">如果要自定义安装计划，请单击 **“计划”** ，然后根据需要调整 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理计划。</span><span class="sxs-lookup"><span data-stu-id="127d2-157">If you want to customize the schedule for your installation, click **Schedule** and then adjust the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent schedule as needed.</span></span> <span data-ttu-id="127d2-158">此计划应为大致的备份计划。</span><span class="sxs-lookup"><span data-stu-id="127d2-158">This schedule should approximate the backup schedule.</span></span>  
  
22. <span data-ttu-id="127d2-159">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="127d2-159">Click **OK**.</span></span>  
  
23. <span data-ttu-id="127d2-160">在 **“监视服务器实例”** 下，选中 **“使用监视服务器实例”** 复选框，然后单击 **“设置”** 。</span><span class="sxs-lookup"><span data-stu-id="127d2-160">Under **Monitor server instance**, select the **Use a monitor server instance** check box, and then click **Settings**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="127d2-161">若要监视此日志传送配置，必须现在添加监视服务器。</span><span class="sxs-lookup"><span data-stu-id="127d2-161">To monitor this log shipping configuration, you must add the monitor server now.</span></span> <span data-ttu-id="127d2-162">若要以后添加监视服务器，则需要先删除此日志传送配置，然后将其替换为包含监视服务器的新配置。</span><span class="sxs-lookup"><span data-stu-id="127d2-162">To add the monitor server later, you would need to remove this log shipping configuration and then replace it with a new configuration that includes a monitor server.</span></span>  
  
24. <span data-ttu-id="127d2-163">单击 **“连接”** 连接到想要用作监视服务器的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="127d2-163">Click **Connect** and connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that you want to use as your monitor server.</span></span>  
  
25. <span data-ttu-id="127d2-164">在 **“监视器连接”** 下，选择备份、副本以及还原作业所使用的连接方法来连接到监视器服务器。</span><span class="sxs-lookup"><span data-stu-id="127d2-164">Under **Monitor connections**, choose the connection method to be used by the backup, copy, and restore jobs to connect to the monitor server.</span></span>  
  
26. <span data-ttu-id="127d2-165">在 **“历史记录保持期”** 下，选择想要保留日志传送历史记录的时间长度。</span><span class="sxs-lookup"><span data-stu-id="127d2-165">Under **History retention**, choose the length of time you want to retain a record of your log shipping history.</span></span>  
  
27. <span data-ttu-id="127d2-166">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="127d2-166">Click **OK**.</span></span>  
  
28. <span data-ttu-id="127d2-167">在 **“数据库属性”** 对话框中，单击 **“确定”** 开始配置进程。</span><span class="sxs-lookup"><span data-stu-id="127d2-167">On the **Database Properties** dialog box, click **OK** to begin the configuration process.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="127d2-168">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="127d2-168">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-log-shipping"></a><span data-ttu-id="127d2-169">配置日志传送</span><span class="sxs-lookup"><span data-stu-id="127d2-169">To configure log shipping</span></span>  
  
1.  <span data-ttu-id="127d2-170">通过在辅助服务器上还原主数据库的完整备份，初始化辅助数据库。</span><span class="sxs-lookup"><span data-stu-id="127d2-170">Initialize the secondary database by restoring a full backup of the primary database on the secondary server.</span></span>  
  
2.  <span data-ttu-id="127d2-171">在主服务器上，执行 [sp_add_log_shipping_primary_database](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-primary-database-transact-sql) 以添加主数据库。</span><span class="sxs-lookup"><span data-stu-id="127d2-171">On the primary server, execute [sp_add_log_shipping_primary_database](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-primary-database-transact-sql) to add a primary database.</span></span> <span data-ttu-id="127d2-172">存储过程将返回备份作业 ID 和主 ID。</span><span class="sxs-lookup"><span data-stu-id="127d2-172">The stored procedure returns the backup job ID and primary ID.</span></span>  
  
3.  <span data-ttu-id="127d2-173">在主服务器上执行 [sp_add_jobschedule](/sql/relational-databases/system-stored-procedures/sp-add-jobschedule-transact-sql) ，以为备份作业添加计划。</span><span class="sxs-lookup"><span data-stu-id="127d2-173">On the primary server, execute [sp_add_jobschedule](/sql/relational-databases/system-stored-procedures/sp-add-jobschedule-transact-sql) to add a schedule for the backup job.</span></span>  
  
4.  <span data-ttu-id="127d2-174">在监视服务器上，执行 [sp_add_log_shipping_alert_job](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-alert-job-transact-sql) 以添加警报作业。</span><span class="sxs-lookup"><span data-stu-id="127d2-174">On the monitor server, execute [sp_add_log_shipping_alert_job](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-alert-job-transact-sql) to add the alert job.</span></span>  
  
5.  <span data-ttu-id="127d2-175">在主服务器上，启用备份作业。</span><span class="sxs-lookup"><span data-stu-id="127d2-175">On the primary server, enable the backup job.</span></span>  
  
6.  <span data-ttu-id="127d2-176">在辅助服务器上，执行 [sp_add_log_shipping_secondary_primary](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-secondary-primary-transact-sql) ，提供主服务器和数据库的详细信息。</span><span class="sxs-lookup"><span data-stu-id="127d2-176">On the secondary server, execute [sp_add_log_shipping_secondary_primary](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-secondary-primary-transact-sql) supplying the details of the primary server and database.</span></span> <span data-ttu-id="127d2-177">此存储过程返回辅助 ID 以及复制和还原作业 ID。</span><span class="sxs-lookup"><span data-stu-id="127d2-177">This stored procedure returns the secondary ID and the copy and restore job IDs.</span></span>  
  
7.  <span data-ttu-id="127d2-178">在辅助服务器上，执行 [sp_add_jobschedule](/sql/relational-databases/system-stored-procedures/sp-add-jobschedule-transact-sql) 以设置复制和还原作业的计划。</span><span class="sxs-lookup"><span data-stu-id="127d2-178">On the secondary server, execute [sp_add_jobschedule](/sql/relational-databases/system-stored-procedures/sp-add-jobschedule-transact-sql) to set the schedule for the copy and restore jobs.</span></span>  
  
8.  <span data-ttu-id="127d2-179">在辅助服务器上，执行 [sp_add_log_shipping_secondary_database](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-secondary-database-transact-sql) 以添加辅助数据库。</span><span class="sxs-lookup"><span data-stu-id="127d2-179">On the secondary server, execute [sp_add_log_shipping_secondary_database](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-secondary-database-transact-sql) to add a secondary database.</span></span>  
  
9. <span data-ttu-id="127d2-180">在主服务器上，执行 [sp_add_log_shipping_primary_secondary](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-primary-secondary-transact-sql) 向主服务器添加有关新辅助数据库的必需信息。</span><span class="sxs-lookup"><span data-stu-id="127d2-180">On the primary server, execute [sp_add_log_shipping_primary_secondary](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-primary-secondary-transact-sql) to add the required information about the new secondary database to the primary server.</span></span>  
  
10. <span data-ttu-id="127d2-181">在辅助服务器上，启用复制和还原作业。</span><span class="sxs-lookup"><span data-stu-id="127d2-181">On the secondary server, enable the copy and restore jobs.</span></span> <span data-ttu-id="127d2-182">有关详细信息，请参阅 [Disable or Enable a Job](../../ssms/agent/disable-or-enable-a-job.md)。</span><span class="sxs-lookup"><span data-stu-id="127d2-182">For more information, see [Disable or Enable a Job](../../ssms/agent/disable-or-enable-a-job.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="127d2-183">相关任务</span><span class="sxs-lookup"><span data-stu-id="127d2-183">Related Tasks</span></span>  
  
-   [<span data-ttu-id="127d2-184">将日志传送升级到 SQL Server 2014 &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="127d2-184">Upgrade Log Shipping to SQL Server 2014 &#40;Transact-SQL&#41;</span></span>](upgrading-log-shipping-to-sql-server-2016-transact-sql.md)  
  
-   [<span data-ttu-id="127d2-185">向日志传送配置添加辅助数据库 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="127d2-185">Add a Secondary Database to a Log Shipping Configuration &#40;SQL Server&#41;</span></span>](add-a-secondary-database-to-a-log-shipping-configuration-sql-server.md)  
  
-   [<span data-ttu-id="127d2-186">从日志传送配置中删除辅助数据库 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="127d2-186">Remove a Secondary Database from a Log Shipping Configuration &#40;SQL Server&#41;</span></span>](remove-a-secondary-database-from-a-log-shipping-configuration-sql-server.md)  
  
-   [<span data-ttu-id="127d2-187">删除日志传送 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="127d2-187">Remove Log Shipping &#40;SQL Server&#41;</span></span>](remove-log-shipping-sql-server.md)  
  
-   [<span data-ttu-id="127d2-188">查看日志传送报告 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="127d2-188">View the Log Shipping Report &#40;SQL Server Management Studio&#41;</span></span>](view-the-log-shipping-report-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="127d2-189">监视日志传送 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="127d2-189">Monitor Log Shipping &#40;Transact-SQL&#41;</span></span>](monitor-log-shipping-transact-sql.md)  
  
-   [<span data-ttu-id="127d2-190">故障转移到日志传送辅助服务器 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="127d2-190">Fail Over to a Log Shipping Secondary &#40;SQL Server&#41;</span></span>](fail-over-to-a-log-shipping-secondary-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="127d2-191">另请参阅</span><span class="sxs-lookup"><span data-stu-id="127d2-191">See Also</span></span>  
 <span data-ttu-id="127d2-192">[关于日志传送 (SQL Server)](about-log-shipping-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="127d2-192">[About Log Shipping &#40;SQL Server&#41;](about-log-shipping-sql-server.md) </span></span>  
 [<span data-ttu-id="127d2-193">日志传送表和存储过程</span><span class="sxs-lookup"><span data-stu-id="127d2-193">Log Shipping Tables and Stored Procedures</span></span>](log-shipping-tables-and-stored-procedures.md)  
  
  
