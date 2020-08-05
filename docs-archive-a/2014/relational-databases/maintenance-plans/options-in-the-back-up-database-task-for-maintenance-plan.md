---
title: “备份数据库”任务（维护计划）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.backup.f1
- sql12.swb.maint.maintplanproperties.logbackup.f1
helpviewer_keywords:
- Back Up Database Task dialog box
ms.assetid: ed1ef012-fa14-4ba5-bafe-d1527ba065b3
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 952730f09deeede360dff5e2bd83f8cdc8a20a67
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580716"
---
# <a name="back-up-database-task-maintenance-plan"></a><span data-ttu-id="c664b-102">“备份数据库”任务（维护计划）</span><span class="sxs-lookup"><span data-stu-id="c664b-102">Back Up Database Task (Maintenance Plan)</span></span>
  <span data-ttu-id="c664b-103">使用 **“‘备份数据库’任务”** 对话框可以将备份任务添加到维护计划。</span><span class="sxs-lookup"><span data-stu-id="c664b-103">Use the **Back Up Database Task** dialog to add a backup task to the maintenance plan.</span></span> <span data-ttu-id="c664b-104">备份数据库非常重要，因为当发生系统或硬件故障（或用户错误）对数据库造成某种破坏时，就需要用备份副本来还原数据。</span><span class="sxs-lookup"><span data-stu-id="c664b-104">Backing up the database is important in case of system or hardware failure (or user errors) that cause the database to be damaged in some way, thus requiring a backed-up copy to be restored.</span></span> <span data-ttu-id="c664b-105">此任务可用于执行完整备份、差异备份、文件和文件组备份以及事务日志备份。</span><span class="sxs-lookup"><span data-stu-id="c664b-105">This task allows you to perform full, differential, files and filegroups, and transaction log backups.</span></span>  
  
 <span data-ttu-id="c664b-106">**创建备份数据库任务**</span><span class="sxs-lookup"><span data-stu-id="c664b-106">**To create a backup database task**</span></span>  
  
-   [<span data-ttu-id="c664b-107">创建维护计划</span><span class="sxs-lookup"><span data-stu-id="c664b-107">Create a Maintenance Plan</span></span>](create-a-maintenance-plan.md)  
  
## <a name="options"></a><span data-ttu-id="c664b-108">选项</span><span class="sxs-lookup"><span data-stu-id="c664b-108">Options</span></span>  
 <span data-ttu-id="c664b-109">**Connection**</span><span class="sxs-lookup"><span data-stu-id="c664b-109">**Connection**</span></span>  
 <span data-ttu-id="c664b-110">选择执行此任务时使用的服务器连接。</span><span class="sxs-lookup"><span data-stu-id="c664b-110">Select the server connection to use when performing this task.</span></span>  
  
 <span data-ttu-id="c664b-111">**新建**</span><span class="sxs-lookup"><span data-stu-id="c664b-111">**New**</span></span>  
 <span data-ttu-id="c664b-112">创建一个新的服务器连接，在执行此任务时使用。</span><span class="sxs-lookup"><span data-stu-id="c664b-112">Create a new server connection to use when performing this task.</span></span> <span data-ttu-id="c664b-113">下面对 **“新建连接”** 对话框进行了介绍。</span><span class="sxs-lookup"><span data-stu-id="c664b-113">The **New Connection** dialog box is described below.</span></span>  
  
 <span data-ttu-id="c664b-114">**数据库**</span><span class="sxs-lookup"><span data-stu-id="c664b-114">**Databases**</span></span>  
 <span data-ttu-id="c664b-115">指定受此任务影响的数据库。</span><span class="sxs-lookup"><span data-stu-id="c664b-115">Specify the databases affected by this task.</span></span> <span data-ttu-id="c664b-116">选择后，下拉列表会提供以下选项：“所有数据库”、“所有系统数据库”、“所有用户数据库”、“特定数据库”   。</span><span class="sxs-lookup"><span data-stu-id="c664b-116">When selected, the drop down list provides the following options: **All databases**, **All system databases**, **All user databases**, **These specific databases**.</span></span>  
  
 <span data-ttu-id="c664b-117">**“所有数据库”**</span><span class="sxs-lookup"><span data-stu-id="c664b-117">**All databases**</span></span>  
 <span data-ttu-id="c664b-118">生成的维护计划将对所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库运行维护任务。</span><span class="sxs-lookup"><span data-stu-id="c664b-118">Generate a maintenance plan that runs maintenance tasks against all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases.</span></span>  
  
 <span data-ttu-id="c664b-119">**所有系统数据库(master、msdb 和 model)**</span><span class="sxs-lookup"><span data-stu-id="c664b-119">**All system databases (master, msdb, model)**</span></span>  
 <span data-ttu-id="c664b-120">生成的维护计划将对每个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 系统数据库运行维护任务。</span><span class="sxs-lookup"><span data-stu-id="c664b-120">Generate a maintenance plan that runs maintenance tasks against each of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system databases.</span></span> <span data-ttu-id="c664b-121">对用户创建的数据库不运行维护任务。</span><span class="sxs-lookup"><span data-stu-id="c664b-121">No maintenance tasks are run against user-created databases.</span></span>  
  
 <span data-ttu-id="c664b-122">**所有用户数据库(master、model、msdb、tempdb 除外)**</span><span class="sxs-lookup"><span data-stu-id="c664b-122">**All user databases (excluding master, model, msdb, tempdb)**</span></span>  
 <span data-ttu-id="c664b-123">生成的维护计划将对用户创建的所有数据库运行维护任务。</span><span class="sxs-lookup"><span data-stu-id="c664b-123">Generate a maintenance plan that runs maintenance tasks against all user-created databases.</span></span> <span data-ttu-id="c664b-124">但不会对 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 系统数据库运行任何维护任务。</span><span class="sxs-lookup"><span data-stu-id="c664b-124">No maintenance tasks are run against the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system databases.</span></span>  
  
 <span data-ttu-id="c664b-125">**以下数据库**</span><span class="sxs-lookup"><span data-stu-id="c664b-125">**These databases**</span></span>  
 <span data-ttu-id="c664b-126">生成的维护计划将只对所选数据库运行维护任务。</span><span class="sxs-lookup"><span data-stu-id="c664b-126">Generate a maintenance plan that runs maintenance tasks against only those databases that are selected.</span></span> <span data-ttu-id="c664b-127">如果选择此选项，则必须至少在列表中选择一个数据库。</span><span class="sxs-lookup"><span data-stu-id="c664b-127">At least one database in the list must be selected if this option is chosen.</span></span>  
  
 <span data-ttu-id="c664b-128">**备份类型**</span><span class="sxs-lookup"><span data-stu-id="c664b-128">**Backup type**</span></span>  
 <span data-ttu-id="c664b-129">显示要执行的备份类型。</span><span class="sxs-lookup"><span data-stu-id="c664b-129">Shows the type of backup to be performed.</span></span>  
  
 <span data-ttu-id="c664b-130">**备份组件**</span><span class="sxs-lookup"><span data-stu-id="c664b-130">**Backup component**</span></span>  
 <span data-ttu-id="c664b-131">选择“数据库”将备份整个数据库。</span><span class="sxs-lookup"><span data-stu-id="c664b-131">Select **Database** to back up the entire database.</span></span> <span data-ttu-id="c664b-132">选择 **“文件和文件组”** 将只备份部分数据库。</span><span class="sxs-lookup"><span data-stu-id="c664b-132">Select **File and filegroups** to back up only a portion of the database.</span></span> <span data-ttu-id="c664b-133">如果选择此选项，请提供文件或文件组名称。</span><span class="sxs-lookup"><span data-stu-id="c664b-133">If selected, provide the file or filegroup name.</span></span> <span data-ttu-id="c664b-134">如果在 **“数据库”** 框中选择了多个数据库，只能对 **“备份组件”** 指定 **“数据库”** 。</span><span class="sxs-lookup"><span data-stu-id="c664b-134">When multiple databases are selected in the **Databases** box, only specify **Databases** for the **Backup components**.</span></span> <span data-ttu-id="c664b-135">若要执行文件或文件组备份，请为每个数据库创建一个任务。</span><span class="sxs-lookup"><span data-stu-id="c664b-135">To perform file or filegroup backups, create a task for each database.</span></span>  
  
 <span data-ttu-id="c664b-136">**备份集过期时间**</span><span class="sxs-lookup"><span data-stu-id="c664b-136">**Backup set will expire**</span></span>  
 <span data-ttu-id="c664b-137">指定可用其他备份集覆盖此备份集的时间。</span><span class="sxs-lookup"><span data-stu-id="c664b-137">Specify when the backup set can be overwritten by another backup set.</span></span>  
  
 <span data-ttu-id="c664b-138">**备份到**</span><span class="sxs-lookup"><span data-stu-id="c664b-138">**Back up to**</span></span>  
 <span data-ttu-id="c664b-139">将数据库备份到文件或磁带。</span><span class="sxs-lookup"><span data-stu-id="c664b-139">Back up the database to a file or to tape.</span></span> <span data-ttu-id="c664b-140">只有连接到该数据库所在计算机的磁带设备才可用。</span><span class="sxs-lookup"><span data-stu-id="c664b-140">Only tape devices attached to the computer containing the database are available.</span></span>  
  
 <span data-ttu-id="c664b-141">**跨一个或多个文件备份数据库**</span><span class="sxs-lookup"><span data-stu-id="c664b-141">**Back up databases across one or more files**</span></span>  
 <span data-ttu-id="c664b-142">单击“添加”将打开“选择备份目标”对话框，并提供一个或多个磁盘位置，或磁带设备。</span><span class="sxs-lookup"><span data-stu-id="c664b-142">Click **Add** to open the **Select Backup Destination** dialog box, and provide one or more a disk location, or tape device.</span></span>  
  
 <span data-ttu-id="c664b-143">**如果备份文件存在**</span><span class="sxs-lookup"><span data-stu-id="c664b-143">**If backup files exist**</span></span>  
 <span data-ttu-id="c664b-144">选择“追加”可以将此备份添加到文件的末尾。</span><span class="sxs-lookup"><span data-stu-id="c664b-144">Select **Append** to add this backup to the end of the file.</span></span> <span data-ttu-id="c664b-145">选择 **“覆盖”** 可以删除文件中的任意旧备份，并用此新备份替换它们。</span><span class="sxs-lookup"><span data-stu-id="c664b-145">Select **Overwrite**, to remove any old backup in the file and replace them with this new backup.</span></span>  
  
 <span data-ttu-id="c664b-146">**为每个数据库创建备份文件**</span><span class="sxs-lookup"><span data-stu-id="c664b-146">**Create a backup file for every database**</span></span>  
 <span data-ttu-id="c664b-147">在文件夹框中指定的位置创建一个备份文件。</span><span class="sxs-lookup"><span data-stu-id="c664b-147">Create a backup file in the location specified in the folder box.</span></span> <span data-ttu-id="c664b-148">将为选定的每个数据库创建一个文件。</span><span class="sxs-lookup"><span data-stu-id="c664b-148">One file will be created for each database selected.</span></span>  
  
 <span data-ttu-id="c664b-149">**为每个数据库创建一个子目录**</span><span class="sxs-lookup"><span data-stu-id="c664b-149">**Create a sub-directory for each database**</span></span>  
 <span data-ttu-id="c664b-150">选择此选项可以将每个数据库置于一个子文件夹中。</span><span class="sxs-lookup"><span data-stu-id="c664b-150">Select to place each database in a subfolder.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="c664b-151">尽管维护计划可以创建子目录，但维护任务不能删除子目录。</span><span class="sxs-lookup"><span data-stu-id="c664b-151">Although maintenance plans can create subdirectories, maintenance tasks cannot delete subdirectories.</span></span> <span data-ttu-id="c664b-152">此功能减少了使用清除维护任务删除文件的恶意攻击的可能性。</span><span class="sxs-lookup"><span data-stu-id="c664b-152">This feature reduces the possibility of a malicious attack that uses the Maintenance Cleanup task to delete files.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="c664b-153">此子目录将从父目录中继承权限。</span><span class="sxs-lookup"><span data-stu-id="c664b-153">The subdirectory inherits permissions from the parent directory.</span></span> <span data-ttu-id="c664b-154">请限制相关权限，以避免未经授权的访问。</span><span class="sxs-lookup"><span data-stu-id="c664b-154">Restrict permissions to avoid unauthorized access.</span></span>  
  
 <span data-ttu-id="c664b-155">**文件夹**</span><span class="sxs-lookup"><span data-stu-id="c664b-155">**Folder**</span></span>  
 <span data-ttu-id="c664b-156">指定用来放置自动创建的数据库文件的文件夹。</span><span class="sxs-lookup"><span data-stu-id="c664b-156">Specify the folder to contain the automatically created database files.</span></span>  
  
 <span data-ttu-id="c664b-157">**备份文件扩展名**</span><span class="sxs-lookup"><span data-stu-id="c664b-157">**Backup file extension**</span></span>  
 <span data-ttu-id="c664b-158">指定备份文件要使用的扩展名。</span><span class="sxs-lookup"><span data-stu-id="c664b-158">Specify the extension to use for the backup files.</span></span> <span data-ttu-id="c664b-159">默认为 **.bak**。</span><span class="sxs-lookup"><span data-stu-id="c664b-159">The default is **.bak**.</span></span>  
  
 <span data-ttu-id="c664b-160">**验证备份完整性**</span><span class="sxs-lookup"><span data-stu-id="c664b-160">**Verify backup integrity**</span></span>  
 <span data-ttu-id="c664b-161">验证备份集是否完整以及所有卷是否都可读。</span><span class="sxs-lookup"><span data-stu-id="c664b-161">Verify that the backup set is complete and that all volumes are readable.</span></span>  
  
 <span data-ttu-id="c664b-162">**备份日志尾部，并使数据库处于还原状态**</span><span class="sxs-lookup"><span data-stu-id="c664b-162">**Back up the tail of the log, and leave the database in the restoring state**</span></span>  
 <span data-ttu-id="c664b-163">在还原数据库前，执行作为最后一个步骤的日志备份。</span><span class="sxs-lookup"><span data-stu-id="c664b-163">Perform a log backup as the last step before restoring a database.</span></span> <span data-ttu-id="c664b-164">有关详细信息，请参阅[结尾日志备份 (SQL Server)](../backup-restore/tail-log-backups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="c664b-164">For more information, see [Tail-Log Backups &#40;SQL Server&#41;](../backup-restore/tail-log-backups-sql-server.md).</span></span>  
  
 <span data-ttu-id="c664b-165">**设置备份压缩**</span><span class="sxs-lookup"><span data-stu-id="c664b-165">**Set backup compression**</span></span>  
 <span data-ttu-id="c664b-166">在 [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] （或更高版本）中，选择以下 [备份压缩](../backup-restore/backup-compression-sql-server.md) 值之一：</span><span class="sxs-lookup"><span data-stu-id="c664b-166">In [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] (or a later version), select one the following [backup compression](../backup-restore/backup-compression-sql-server.md) values:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c664b-167">**使用默认服务器设置**</span><span class="sxs-lookup"><span data-stu-id="c664b-167">**Use the default server setting**</span></span>|<span data-ttu-id="c664b-168">单击此选项可使用服务器级别默认值。</span><span class="sxs-lookup"><span data-stu-id="c664b-168">Click to use the server-level default.</span></span><br /><br /> <span data-ttu-id="c664b-169">此默认值可通过 **backup compression default** 服务器配置选项进行设置。</span><span class="sxs-lookup"><span data-stu-id="c664b-169">This default is set by the **backup compression default** server-configuration option.</span></span> <span data-ttu-id="c664b-170">有关如何查看此选项当前设置的信息，请参阅 [查看或配置 backup compression default 服务器配置选项](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)。</span><span class="sxs-lookup"><span data-stu-id="c664b-170">For information about how to view the current setting of this option,  see [View or Configure the backup compression default Server Configuration Option](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md).</span></span>|  
|<span data-ttu-id="c664b-171">**压缩备份**</span><span class="sxs-lookup"><span data-stu-id="c664b-171">**Compress backup**</span></span>|<span data-ttu-id="c664b-172">单击此选项可压缩备份，而不考虑服务器级别默认值。</span><span class="sxs-lookup"><span data-stu-id="c664b-172">Click to compress the backup, regardless of the server-level default.</span></span><br /><br /> <span data-ttu-id="c664b-173">**\*\* 重要说明 \*\*** 默认情况下，压缩会大大提高 CPU 使用率，并且压缩进程占用的额外 CPU 可能会对并发操作造成不利影响。</span><span class="sxs-lookup"><span data-stu-id="c664b-173">**\*\* Important \*\*** By default, compression significantly increases CPU usage, and the additional CPU consumed by the compression process might adversely affect concurrent operations.</span></span> <span data-ttu-id="c664b-174">因此，你可能需要在会话中创建低优先级的压缩备份，其 CPU 使用率受 [资源调控器](../resource-governor/resource-governor.md)限制。</span><span class="sxs-lookup"><span data-stu-id="c664b-174">Therefore, you might want to create low-priority compressed backups in a session whose CPU usage is limited by [Resource Governor](../resource-governor/resource-governor.md).</span></span> <span data-ttu-id="c664b-175">有关详细信息，请参阅本主题后面的 [使用资源调控器限制备份压缩的 CPU 使用量 (Transact-SQL)](../backup-restore/use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md)限制。</span><span class="sxs-lookup"><span data-stu-id="c664b-175">For more information, see [Use Resource Governor to Limit CPU Usage by Backup Compression &#40;Transact-SQL&#41;](../backup-restore/use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md).</span></span>|  
|<span data-ttu-id="c664b-176">**不压缩备份**</span><span class="sxs-lookup"><span data-stu-id="c664b-176">**Do not compress backup**</span></span>|<span data-ttu-id="c664b-177">单击此选项可创建未压缩的备份，而不考虑服务器级别默认值。</span><span class="sxs-lookup"><span data-stu-id="c664b-177">Click to create an uncompressed backup, regardless of the server-level default.</span></span>|  
  
 <span data-ttu-id="c664b-178">**查看 T-SQL**</span><span class="sxs-lookup"><span data-stu-id="c664b-178">**View T-SQL**</span></span>  
 <span data-ttu-id="c664b-179">根据所选选项，查看针对此任务的服务器执行的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句。</span><span class="sxs-lookup"><span data-stu-id="c664b-179">View the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements performed against the server for this task, based on the selected options.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c664b-180">当受影响的对象很多时，可能需要相当长的时间才可显示。</span><span class="sxs-lookup"><span data-stu-id="c664b-180">When the number of objects affected is large, this display can take a considerable amount of time.</span></span>  
  
## <a name="new-connection-dialog-box"></a><span data-ttu-id="c664b-181">“新建连接”对话框</span><span class="sxs-lookup"><span data-stu-id="c664b-181">New Connection Dialog Box</span></span>  
 <span data-ttu-id="c664b-182">**连接名称**</span><span class="sxs-lookup"><span data-stu-id="c664b-182">**Connection name**</span></span>  
 <span data-ttu-id="c664b-183">输入新连接的名称。</span><span class="sxs-lookup"><span data-stu-id="c664b-183">Enter a name for the new connection.</span></span>  
  
 <span data-ttu-id="c664b-184">**选择或输入服务器名称**</span><span class="sxs-lookup"><span data-stu-id="c664b-184">**Select or enter a server name**</span></span>  
 <span data-ttu-id="c664b-185">选择执行此任务时所要连接的服务器。</span><span class="sxs-lookup"><span data-stu-id="c664b-185">Select a server to connect to when performing this task.</span></span>  
  
 <span data-ttu-id="c664b-186">**“刷新”**</span><span class="sxs-lookup"><span data-stu-id="c664b-186">**Refresh**</span></span>  
 <span data-ttu-id="c664b-187">刷新可用服务器的列表。</span><span class="sxs-lookup"><span data-stu-id="c664b-187">Refresh the list of available servers.</span></span>  
  
 <span data-ttu-id="c664b-188">**输入登录服务器所需的信息**</span><span class="sxs-lookup"><span data-stu-id="c664b-188">**Enter information to log on to the server**</span></span>  
 <span data-ttu-id="c664b-189">指定如何对服务器进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="c664b-189">Specify how to authenticate against the server.</span></span>  
  
 <span data-ttu-id="c664b-190">**使用 Windows 集成安全性**</span><span class="sxs-lookup"><span data-stu-id="c664b-190">**Use Windows integrated security**</span></span>  
 <span data-ttu-id="c664b-191">使用 Windows 身份验证连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="c664b-191">Connect to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] with Windows Authentication.</span></span>  
  
 <span data-ttu-id="c664b-192">**使用特定用户名和密码**</span><span class="sxs-lookup"><span data-stu-id="c664b-192">**Use a specific user name and password**</span></span>  
 <span data-ttu-id="c664b-193">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="c664b-193">Connect to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="c664b-194">此选项不可用。</span><span class="sxs-lookup"><span data-stu-id="c664b-194">This option is not available.</span></span>  
  
 <span data-ttu-id="c664b-195">**用户名**</span><span class="sxs-lookup"><span data-stu-id="c664b-195">**User name**</span></span>  
 <span data-ttu-id="c664b-196">提供一个在进行身份验证时要使用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名。</span><span class="sxs-lookup"><span data-stu-id="c664b-196">Provide a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login to use when authenticating.</span></span> <span data-ttu-id="c664b-197">此选项不可用。</span><span class="sxs-lookup"><span data-stu-id="c664b-197">This option is not available.</span></span>  
  
 <span data-ttu-id="c664b-198">**密码**</span><span class="sxs-lookup"><span data-stu-id="c664b-198">**Password**</span></span>  
 <span data-ttu-id="c664b-199">提供一个在进行身份验证时要使用的密码。</span><span class="sxs-lookup"><span data-stu-id="c664b-199">Provide a password to use when authenticating.</span></span> <span data-ttu-id="c664b-200">此选项不可用。</span><span class="sxs-lookup"><span data-stu-id="c664b-200">This option is not available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c664b-201">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c664b-201">See Also</span></span>  
 [<span data-ttu-id="c664b-202">BACKUP (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="c664b-202">BACKUP &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/backup-transact-sql)  
  
  
