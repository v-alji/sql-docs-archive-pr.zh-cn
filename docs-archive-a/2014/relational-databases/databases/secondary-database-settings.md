---
title: 辅助数据库设置 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.databaseproperties.logshipping.settings.dest.f1
ms.assetid: f992ffc9-ee42-43fe-acec-512032f0ded1
author: stevestein
ms.author: sstein
ms.openlocfilehash: 265d6beda830e2090392918ae14d10c8b7752d02
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581277"
---
# <a name="secondary-database-settings"></a><span data-ttu-id="9645d-102">辅助数据库设置</span><span class="sxs-lookup"><span data-stu-id="9645d-102">Secondary Database Settings</span></span>
  <span data-ttu-id="9645d-103">使用此对话框可以配置和修改日志传送配置中辅助数据库的属性。</span><span class="sxs-lookup"><span data-stu-id="9645d-103">Use this dialog box to configure and to modify the properties of a secondary database in the log shipping configuration.</span></span>  
  
 <span data-ttu-id="9645d-104">有关日志传送概念的说明，请参阅 [关于日志传送 (SQL Server)](../../database-engine/log-shipping/about-log-shipping-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="9645d-104">For an explanation of log shipping concepts, see [About Log Shipping &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="9645d-105">选项</span><span class="sxs-lookup"><span data-stu-id="9645d-105">Options</span></span>  
 <span data-ttu-id="9645d-106">**辅助服务器实例**</span><span class="sxs-lookup"><span data-stu-id="9645d-106">**Secondary server instance**</span></span>  
 <span data-ttu-id="9645d-107">显示日志传送配置中当前配置为辅助服务器的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的名称。</span><span class="sxs-lookup"><span data-stu-id="9645d-107">Displays the name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] currently configured to be a secondary server in the log shipping configuration.</span></span>  
  
 <span data-ttu-id="9645d-108">**辅助数据库**</span><span class="sxs-lookup"><span data-stu-id="9645d-108">**Secondary database**</span></span>  
 <span data-ttu-id="9645d-109">显示日志传送配置的辅助数据库名称。</span><span class="sxs-lookup"><span data-stu-id="9645d-109">Displays the name of the secondary database for the log shipping configuration.</span></span> <span data-ttu-id="9645d-110">将新的辅助数据库添加到日志传送配置时，可以从列表中选择数据库或在该框中键入新数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="9645d-110">When adding a new secondary database to a log shipping configuration, you can choose a database from the list or type the name of a new of the database into the box.</span></span> <span data-ttu-id="9645d-111">如果输入新数据库的名称，则必须在 **“初始化”** 选项卡上选择一个选项，该选项卡可将主数据库的完整数据库备份还原到辅助数据库中。</span><span class="sxs-lookup"><span data-stu-id="9645d-111">If you enter the name of a new database, you must select an option on the **Initialization** tab that restores a full database backup of the primary database into the secondary database.</span></span> <span data-ttu-id="9645d-112">新数据库将作为还原操作的一部分进行创建。</span><span class="sxs-lookup"><span data-stu-id="9645d-112">The new database is created as part of the restore operation.</span></span>  
  
 <span data-ttu-id="9645d-113">**“连接”**</span><span class="sxs-lookup"><span data-stu-id="9645d-113">**Connect**</span></span>  
 <span data-ttu-id="9645d-114">连接到日志传送配置中用作辅助服务器的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="9645d-114">Connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] for use as a secondary server in the log shipping configuration.</span></span> <span data-ttu-id="9645d-115">用于连接的帐户必须是辅助服务器实例上 sysadmin 固定服务器角色的成员。</span><span class="sxs-lookup"><span data-stu-id="9645d-115">The account used to connect must be a member of the sysadmin fixed server role on the secondary server instance.</span></span>  
  
 <span data-ttu-id="9645d-116">**“初始化”选项卡**</span><span class="sxs-lookup"><span data-stu-id="9645d-116">**Initialize tab**</span></span>  
 <span data-ttu-id="9645d-117">选项如下：</span><span class="sxs-lookup"><span data-stu-id="9645d-117">The options are as follows:</span></span>  
  
 <span data-ttu-id="9645d-118">**是，生成主数据库的完整备份并将其还原到辅助数据库**</span><span class="sxs-lookup"><span data-stu-id="9645d-118">**Yes, generate a full backup of the primary database and restore it to the secondary database**</span></span>  
 <span data-ttu-id="9645d-119">通过备份主数据库并在辅助服务器上还原该数据库，让 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 配置辅助数据库。</span><span class="sxs-lookup"><span data-stu-id="9645d-119">Have [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] configure your secondary database by backing up the primary database and restoring it on the secondary server.</span></span> <span data-ttu-id="9645d-120">如果在 **“辅助数据库”** 框中输入新的数据库名称，数据库将作为还原操作的一部分进行创建。</span><span class="sxs-lookup"><span data-stu-id="9645d-120">If you entered a new database name in the **Secondary database** box, the database will be created as part of the restore operation.</span></span>  
  
 <span data-ttu-id="9645d-121">**还原选项**</span><span class="sxs-lookup"><span data-stu-id="9645d-121">**Restore Options**</span></span>  
 <span data-ttu-id="9645d-122">若要将辅助数据库的数据和日志文件还原到辅助服务器上的非默认位置，请单击此按钮。</span><span class="sxs-lookup"><span data-stu-id="9645d-122">Click if you want to restore the data and log files for the secondary database into nondefault locations on the secondary server.</span></span>  
  
 <span data-ttu-id="9645d-123">单击此按钮将打开 **“还原选项”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="9645d-123">This button opens the **Restore Options** dialog box.</span></span> <span data-ttu-id="9645d-124">在该对话框中，可以指定非默认文件夹的路径，用于驻留辅助数据库及其日志。</span><span class="sxs-lookup"><span data-stu-id="9645d-124">There, you can specify paths to nondefault folders where you want the secondary database and its log to reside.</span></span> <span data-ttu-id="9645d-125">如果指定其中的一个文件夹，则必须指定这两个路径。</span><span class="sxs-lookup"><span data-stu-id="9645d-125">If you specify either folder, you must specify both.</span></span>  
  
 <span data-ttu-id="9645d-126">这些路径必须引用辅助服务器上的本地驱动器。</span><span class="sxs-lookup"><span data-stu-id="9645d-126">The paths must refer to drives that are local to the secondary server.</span></span> <span data-ttu-id="9645d-127">另外，这些路径必须以本地驱动器号和冒号开头（例如， `C:`）。</span><span class="sxs-lookup"><span data-stu-id="9645d-127">Also, the paths must begin with a local drive letter and colon (for example, `C:`).</span></span> <span data-ttu-id="9645d-128">映射的驱动器号或网络路径无效。</span><span class="sxs-lookup"><span data-stu-id="9645d-128">Mapped drive letters or network paths are invalid.</span></span>  
  
 <span data-ttu-id="9645d-129">如果单击 **“还原选项”** 按钮后决定使用默认文件夹，建议取消 **“还原选项”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="9645d-129">If you click the **Restore Options** button and then decide that you want to use the default folders, we recommend that you cancel the **Restore Options** dialog box.</span></span> <span data-ttu-id="9645d-130">如果已经指定非默认位置，但现在要使用默认位置，请再次单击 **“还原选项”** ，清除文本框，再单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="9645d-130">If you have already specified nondefault locations and now want to use the default locations instead, click **Restore Options** again, clear the text boxes, and click OK.</span></span>  
  
 <span data-ttu-id="9645d-131">**是，将主数据库的现有备份还原到辅助数据库**</span><span class="sxs-lookup"><span data-stu-id="9645d-131">**Yes, restore an existing backup of the primary database to the secondary database**</span></span>  
 <span data-ttu-id="9645d-132">让 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 使用主数据库的现有备份初始化辅助数据库。</span><span class="sxs-lookup"><span data-stu-id="9645d-132">Have [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] use an existing backup of your primary database to initialize the secondary database.</span></span> <span data-ttu-id="9645d-133">在 **“备份文件”** 框中键入该备份的位置。</span><span class="sxs-lookup"><span data-stu-id="9645d-133">Type the location of that backup in the **Backup file** box.</span></span> <span data-ttu-id="9645d-134">如果在“辅助数据库”框中输入新的数据库名称，数据库将作为还原操作的一部分进行创建。</span><span class="sxs-lookup"><span data-stu-id="9645d-134">If you entered a new database name in the Secondary database box, the database will be created as part of the restore operation.</span></span>  
  
 <span data-ttu-id="9645d-135">**“备份文件”**</span><span class="sxs-lookup"><span data-stu-id="9645d-135">**Backup file**</span></span>  
 <span data-ttu-id="9645d-136">如果选择“是，将主数据库的现有备份还原到辅助数据库”  选项，请键入要用于初始化辅助数据库的完整数据库备份的路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="9645d-136">Type the path and filename of the full database backup you want to use to initialize the secondary database if you chose the **Yes, restore and existing backup of the primary database to the secondary database option**.</span></span>  
  
 <span data-ttu-id="9645d-137">**还原选项**</span><span class="sxs-lookup"><span data-stu-id="9645d-137">**Restore Options**</span></span>  
 <span data-ttu-id="9645d-138">参阅本主题前面对此按钮的说明。</span><span class="sxs-lookup"><span data-stu-id="9645d-138">See the description of this button earlier in this topic.</span></span>  
  
 <span data-ttu-id="9645d-139">**否，辅助数据库已初始化**</span><span class="sxs-lookup"><span data-stu-id="9645d-139">**No, the secondary database is initialized**</span></span>  
 <span data-ttu-id="9645d-140">指定辅助数据库已初始化并准备接受主数据库的事务日志备份。</span><span class="sxs-lookup"><span data-stu-id="9645d-140">Specify that the secondary database is already initialized and ready to accept transaction log backups from the primary database.</span></span> <span data-ttu-id="9645d-141">如果在 **“辅助数据库”** 框中键入新的数据库名称，则此选项不可用。</span><span class="sxs-lookup"><span data-stu-id="9645d-141">This option is not available if you typed a new database name in the **Secondary database** box.</span></span>  
  
 <span data-ttu-id="9645d-142">**“复制文件”选项卡**</span><span class="sxs-lookup"><span data-stu-id="9645d-142">**Copy Files tab**</span></span>  
 <span data-ttu-id="9645d-143">选项如下：</span><span class="sxs-lookup"><span data-stu-id="9645d-143">The options are as follows:</span></span>  
  
 <span data-ttu-id="9645d-144">**复制文件的目标文件夹**</span><span class="sxs-lookup"><span data-stu-id="9645d-144">**Destination folder for copied files**</span></span>  
 <span data-ttu-id="9645d-145">键入事务日志备份应复制到的路径以还原到辅助数据库。</span><span class="sxs-lookup"><span data-stu-id="9645d-145">Type the path to which transaction log backups should be copied for restoration to the secondary database.</span></span> <span data-ttu-id="9645d-146">通常，此路径为辅助服务器上文件夹的本地路径。</span><span class="sxs-lookup"><span data-stu-id="9645d-146">This is usually a local path to a folder located on the secondary server.</span></span> <span data-ttu-id="9645d-147">但是，如果该文件夹位于其他服务器，则必须指定该文件夹的 UNC 路径。</span><span class="sxs-lookup"><span data-stu-id="9645d-147">If the folder is located on another server, however, you must specify a UNC path to the folder.</span></span> <span data-ttu-id="9645d-148">辅助服务器实例的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务帐户必须具有此文件夹的读取权限。</span><span class="sxs-lookup"><span data-stu-id="9645d-148">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service account of the secondary server instance must have Read permissions on this folder.</span></span> <span data-ttu-id="9645d-149">此外，还必须向代理帐户授予此网络共享的读写权限。通过代理帐户，复制作业和还原作业将在辅助服务器实例上的该帐户下运行。</span><span class="sxs-lookup"><span data-stu-id="9645d-149">You must also grant read and write permissions on this network share to the proxy accounts under which the copy and restore jobs will run at the secondary server instances.</span></span> <span data-ttu-id="9645d-150">默认情况下，这是辅助服务器实例的 SQL Server 代理服务帐户，但是 sysadmin 可以为该作业选择其他代理帐户。</span><span class="sxs-lookup"><span data-stu-id="9645d-150">By default, this is the SQL Server Agent service account of the secondary server instance, but a sysadmin can choose other proxy accounts for the jobs.</span></span>  
  
 <span data-ttu-id="9645d-151">**在以下时间后删除复制的文件**</span><span class="sxs-lookup"><span data-stu-id="9645d-151">**Delete copied files after**</span></span>  
 <span data-ttu-id="9645d-152">选择希望复制的事务日志备份文件在删除前保留在目标文件夹中的时间。</span><span class="sxs-lookup"><span data-stu-id="9645d-152">Choose the length of time you want the copied transaction log backup files to remain in the destination folder before being deleted.</span></span>  
  
 <span data-ttu-id="9645d-153">**作业名称**</span><span class="sxs-lookup"><span data-stu-id="9645d-153">**Job name**</span></span>  
 <span data-ttu-id="9645d-154">显示用于将事务日志备份文件从主服务器复制到辅助服务器的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业的名称。</span><span class="sxs-lookup"><span data-stu-id="9645d-154">Displays the name of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job used to copy transaction log backup files from the primary server to the secondary server.</span></span> <span data-ttu-id="9645d-155">首次创建此作业时，可以通过在该框中键入内容来更改名称。</span><span class="sxs-lookup"><span data-stu-id="9645d-155">When first creating this job, you can change the name by typing in the box.</span></span>  
  
 <span data-ttu-id="9645d-156">**“计划”**</span><span class="sxs-lookup"><span data-stu-id="9645d-156">**Schedule**</span></span>  
 <span data-ttu-id="9645d-157">显示用于将事务日志备份从主服务器复制到辅助服务器的 SQL Server 代理复制作业的当前计划。</span><span class="sxs-lookup"><span data-stu-id="9645d-157">Displays the current schedule for the SQL Server Agent copy job to copy transaction log backups from the primary server to the secondary server.</span></span> <span data-ttu-id="9645d-158">通过单击 **“计划...”** 可以修改此计划。</span><span class="sxs-lookup"><span data-stu-id="9645d-158">You can modify this schedule by clicking **Schedule...**.</span></span>  
  
 <span data-ttu-id="9645d-159">**“计划...”**</span><span class="sxs-lookup"><span data-stu-id="9645d-159">**Schedule...**</span></span>  
 <span data-ttu-id="9645d-160">修改用于将事务日志备份从主服务器复制到辅助服务器的 SQL Server 代理作业的参数。</span><span class="sxs-lookup"><span data-stu-id="9645d-160">Modify the parameters of the SQL Server Agent job that copies transaction log backups from the primary server to the secondary server.</span></span>  
  
 <span data-ttu-id="9645d-161">**禁用此作业**</span><span class="sxs-lookup"><span data-stu-id="9645d-161">**Disable this job**</span></span>  
 <span data-ttu-id="9645d-162">挂起 SQL Server 代理复制作业。</span><span class="sxs-lookup"><span data-stu-id="9645d-162">Suspend the SQL Server Agent copy job.</span></span>  
  
 <span data-ttu-id="9645d-163">**“还原事务日志”选项卡**</span><span class="sxs-lookup"><span data-stu-id="9645d-163">**Restore Transaction Log tab**</span></span>  
 <span data-ttu-id="9645d-164">选项如下：</span><span class="sxs-lookup"><span data-stu-id="9645d-164">The options are as follows:</span></span>  
  
 <span data-ttu-id="9645d-165">**在还原备份时断开数据库中用户的连接**</span><span class="sxs-lookup"><span data-stu-id="9645d-165">**Disconnect users in the database when restoring backups**</span></span>  
 <span data-ttu-id="9645d-166">在还原事务日志备份时，自动断开用户与辅助数据库的连接。</span><span class="sxs-lookup"><span data-stu-id="9645d-166">Automatically disconnect users from the secondary database while transaction log backups are being restored.</span></span>  
  
 <span data-ttu-id="9645d-167">**无恢复模式**</span><span class="sxs-lookup"><span data-stu-id="9645d-167">**No recovery mode**</span></span>  
 <span data-ttu-id="9645d-168">使辅助数据库处于 NORECOVERY 模式。</span><span class="sxs-lookup"><span data-stu-id="9645d-168">Leave the secondary database in NORECOVERY mode.</span></span>  
  
 <span data-ttu-id="9645d-169">**备用模式**</span><span class="sxs-lookup"><span data-stu-id="9645d-169">**Standby mode**</span></span>  
 <span data-ttu-id="9645d-170">使辅助数据库处于 STANDBY 模式。</span><span class="sxs-lookup"><span data-stu-id="9645d-170">Leave the secondary database in STANDBY mode.</span></span> <span data-ttu-id="9645d-171">此模式允许对数据库执行只读操作。</span><span class="sxs-lookup"><span data-stu-id="9645d-171">This mode will allow read-only operations to be performed on the database.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="9645d-172">如果更改现有辅助数据库的恢复模式（例如，从“无恢复模式”  到“备用模式”  ），则更改仅在下一次日志备份还原到数据库后才会生效。</span><span class="sxs-lookup"><span data-stu-id="9645d-172">If you change the recovery mode of an existing secondary database, for example, from **No recovery mode** to **Standby mode**, the change takes effect only after the next log backup is restored to the database.</span></span>  
  
 <span data-ttu-id="9645d-173">**延迟还原备份操作至少**</span><span class="sxs-lookup"><span data-stu-id="9645d-173">**Delay restoring backups at least**</span></span>  
 <span data-ttu-id="9645d-174">选择将事务日志备份还原到辅助数据库之前的延迟时间（如果有）。</span><span class="sxs-lookup"><span data-stu-id="9645d-174">Choose the delay before transaction log backups are restored to the secondary database, if any.</span></span>  
  
 <span data-ttu-id="9645d-175">**在以下时间内没有执行还原时报警**</span><span class="sxs-lookup"><span data-stu-id="9645d-175">**Alert if no restore occurs within**</span></span>  
 <span data-ttu-id="9645d-176">选择在引发警报以报告未执行事务日志还原之前，希望日志传送等待的时间。</span><span class="sxs-lookup"><span data-stu-id="9645d-176">Choose the amount of time you want log shipping to wait before raising an alert that no transaction log restores have occurred.</span></span>  
  
 <span data-ttu-id="9645d-177">**作业名称**</span><span class="sxs-lookup"><span data-stu-id="9645d-177">**Job name**</span></span>  
 <span data-ttu-id="9645d-178">显示用于将事务日志备份还原到辅助数据库的 SQL Server 代理作业的名称。</span><span class="sxs-lookup"><span data-stu-id="9645d-178">Displays the name of the SQL Server Agent job used to restore transaction log backups to the secondary database.</span></span> <span data-ttu-id="9645d-179">首次创建此作业时，可以通过在该框中键入内容来更改名称。</span><span class="sxs-lookup"><span data-stu-id="9645d-179">When first creating this job, you can change the name by typing in the box.</span></span>  
  
 <span data-ttu-id="9645d-180">**“计划”**</span><span class="sxs-lookup"><span data-stu-id="9645d-180">**Schedule**</span></span>  
 <span data-ttu-id="9645d-181">显示用于将事务日志备份还原到辅助数据库的 SQL Server 代理作业的当前计划。</span><span class="sxs-lookup"><span data-stu-id="9645d-181">Displays the current schedule for the SQL Server Agent job used for restoring transaction log backups to the secondary database.</span></span> <span data-ttu-id="9645d-182">通过单击 **“计划...”** 可以修改此选项。</span><span class="sxs-lookup"><span data-stu-id="9645d-182">You can modify this option by clicking **Schedule...**.</span></span>  
  
 <span data-ttu-id="9645d-183">**“计划...”**</span><span class="sxs-lookup"><span data-stu-id="9645d-183">**Schedule...**</span></span>  
 <span data-ttu-id="9645d-184">修改与 SQL Server 代理还原作业相关联的参数。</span><span class="sxs-lookup"><span data-stu-id="9645d-184">Modify the parameters associate with the SQL Server Agent restore job.</span></span>  
  
 <span data-ttu-id="9645d-185">**禁用此作业**</span><span class="sxs-lookup"><span data-stu-id="9645d-185">**Disable this job**</span></span>  
 <span data-ttu-id="9645d-186">挂起对辅助数据库的还原操作。</span><span class="sxs-lookup"><span data-stu-id="9645d-186">Suspend restore operations to the secondary database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9645d-187">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9645d-187">See Also</span></span>  
 <span data-ttu-id="9645d-188">[SQL Server 数据库的备份和还原](../backup-restore/back-up-and-restore-of-sql-server-databases.md) </span><span class="sxs-lookup"><span data-stu-id="9645d-188">[Back Up and Restore of SQL Server Databases](../backup-restore/back-up-and-restore-of-sql-server-databases.md) </span></span>  
 [<span data-ttu-id="9645d-189">关于日志传送 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="9645d-189">About Log Shipping &#40;SQL Server&#41;</span></span>](../../database-engine/log-shipping/about-log-shipping-sql-server.md)  
  
  
