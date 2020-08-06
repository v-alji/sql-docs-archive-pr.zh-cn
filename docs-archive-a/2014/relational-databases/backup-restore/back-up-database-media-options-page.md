---
title: 备份数据库（“介质选项”页）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- swb.backupdatabase.mediaoptions.f1
- sql12.swb.backupdatabase.mediaoptions.f1
ms.assetid: eff36228-710c-4ed5-9af5-95859575dc0f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: cd09eb091a7f488f891bc2e69d19ad039b65e065
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691264"
---
# <a name="back-up-database-media-options-page"></a><span data-ttu-id="df3d3-102">备份数据库（“介质选项”页）</span><span class="sxs-lookup"><span data-stu-id="df3d3-102">Back Up Database (Media Options Page)</span></span>
  <span data-ttu-id="df3d3-103">使用  **“备份数据库”** 对话框的 **“介质选项”** 页可以查看或修改数据库介质选项。</span><span class="sxs-lookup"><span data-stu-id="df3d3-103">Use the  **Media Options** page of the **Back Up Database** dialog box to view or modify database media options.</span></span>  
  
 <span data-ttu-id="df3d3-104">**使用 SQL Server Management Studio 创建备份**</span><span class="sxs-lookup"><span data-stu-id="df3d3-104">**To create a backup by using SQL Server Management Studio**</span></span>  
  
-   [<span data-ttu-id="df3d3-105">创建完整数据库备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="df3d3-105">Create a Full Database Backup &#40;SQL Server&#41;</span></span>](create-a-full-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="df3d3-106">创建差异数据库备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="df3d3-106">Create a Differential Database Backup &#40;SQL Server&#41;</span></span>](create-a-differential-database-backup-sql-server.md)  
  
> [!IMPORTANT]  
>  <span data-ttu-id="df3d3-107">可以定义用于创建数据库备份的数据库维护计划。</span><span class="sxs-lookup"><span data-stu-id="df3d3-107">You can define a database maintenance plan to create database backups.</span></span> <span data-ttu-id="df3d3-108">有关详细信息，请参阅[维护计划](../maintenance-plans/maintenance-plans.md)和[使用维护计划向导](../maintenance-plans/use-the-maintenance-plan-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="df3d3-108">For more information, see [Maintenance Plans](../maintenance-plans/maintenance-plans.md) and [Use the Maintenance Plan Wizard](../maintenance-plans/use-the-maintenance-plan-wizard.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="df3d3-109">使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 指定备份任务时，可以通过单击“脚本”  按钮，再为脚本选择一个目标，生成对应的 [!INCLUDE[tsql](../../includes/tsql-md.md)][BACKUP](/sql/t-sql/statements/backup-transact-sql) 脚本。</span><span class="sxs-lookup"><span data-stu-id="df3d3-109">When you specify a backup task by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], you can generate the corresponding [!INCLUDE[tsql](../../includes/tsql-md.md)][BACKUP](/sql/t-sql/statements/backup-transact-sql) script by clicking the **Script** button and then selecting a destination for the script.</span></span>  
  
## <a name="options"></a><span data-ttu-id="df3d3-110">选项</span><span class="sxs-lookup"><span data-stu-id="df3d3-110">Options</span></span>  
  
### <a name="overwrite-media"></a><span data-ttu-id="df3d3-111">覆盖介质</span><span class="sxs-lookup"><span data-stu-id="df3d3-111">Overwrite media</span></span>  
 <span data-ttu-id="df3d3-112">**“覆盖介质”** 面板中的选项可以控制如何将备份写入介质。</span><span class="sxs-lookup"><span data-stu-id="df3d3-112">The options of the **Overwrite media** panel control how the backup is written to the media.</span></span> <span data-ttu-id="df3d3-113">如果在“备份数据库”对话框的“常规”页上选择了 URL（Azure 存储）作为备份目标，则禁用“覆盖介质”部分下的选项。</span><span class="sxs-lookup"><span data-stu-id="df3d3-113">IF you selected URL (Azure Storage) as the backup destination on the General page of the Back Up Database dialog box, the options under the Overwrite media section are disabled.</span></span> <span data-ttu-id="df3d3-114">可使用 `BACKUP TO URL.. WITH FORMAT` Transact-SQL 语句覆盖备份。</span><span class="sxs-lookup"><span data-stu-id="df3d3-114">You can overwrite a backup using the `BACKUP TO URL.. WITH FORMAT` Transact-SQL statement.</span></span> <span data-ttu-id="df3d3-115">有关详细信息，请参阅 [SQL Server Backup to URL](sql-server-backup-to-url.md)。</span><span class="sxs-lookup"><span data-stu-id="df3d3-115">For more information, see [SQL Server Backup to URL](sql-server-backup-to-url.md).</span></span>  
  
 <span data-ttu-id="df3d3-116">仅支持选项 **“备份到新介质集并清除所有现有备份集”** 与加密选项一起使用。</span><span class="sxs-lookup"><span data-stu-id="df3d3-116">Only the option, **Backup to a new media, and erase all existing backup sets** is supported with encryption options.</span></span> <span data-ttu-id="df3d3-117">如果选择 **“备份到现有介质”** 部分下的选项，则将禁用 **“备份选项”** 页上的加密选项。</span><span class="sxs-lookup"><span data-stu-id="df3d3-117">If you select the options under the **Back up to existing media** section, the encryptions options on the **Backup Options** page will be disabled.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="df3d3-118">有关媒体集的信息，请参阅 [媒体集、媒体簇和备份集 (SQL Server)](media-sets-media-families-and-backup-sets-sql-server.md)实例的计算机附连有磁带机时，此选项才可用。</span><span class="sxs-lookup"><span data-stu-id="df3d3-118">For information about media sets, see [Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md).</span></span>  
  
 <span data-ttu-id="df3d3-119">**备份到现有介质集**</span><span class="sxs-lookup"><span data-stu-id="df3d3-119">**Back up to the existing media set**</span></span>  
 <span data-ttu-id="df3d3-120">将数据库备份到现有介质集。</span><span class="sxs-lookup"><span data-stu-id="df3d3-120">Back up a database to an existing media set.</span></span> <span data-ttu-id="df3d3-121">选择此选项按钮将激活三个选项。</span><span class="sxs-lookup"><span data-stu-id="df3d3-121">Selecting this option button activates three options.</span></span>  
  
 <span data-ttu-id="df3d3-122">选择以下选项之一：</span><span class="sxs-lookup"><span data-stu-id="df3d3-122">Choose one of the following options:</span></span>  
  
 <span data-ttu-id="df3d3-123">**追加到现有备份集**</span><span class="sxs-lookup"><span data-stu-id="df3d3-123">**Append to the existing backup set**</span></span>  
 <span data-ttu-id="df3d3-124">将备份集追加到现有介质集，并保留以前的所有备份。</span><span class="sxs-lookup"><span data-stu-id="df3d3-124">Append the backup set to the existing media set, preserving any prior backups.</span></span>  
  
 <span data-ttu-id="df3d3-125">**覆盖所有现有备份集**</span><span class="sxs-lookup"><span data-stu-id="df3d3-125">**Overwrite all existing backup sets**</span></span>  
 <span data-ttu-id="df3d3-126">将现有介质集上以前的所有备份替换为当前备份。</span><span class="sxs-lookup"><span data-stu-id="df3d3-126">Replace any prior backups on the existing media set with the current backup.</span></span>  
  
 <span data-ttu-id="df3d3-127">**检查介质集名称和备份集过期时间**</span><span class="sxs-lookup"><span data-stu-id="df3d3-127">**Check media set name and backup set expiration**</span></span>  
 <span data-ttu-id="df3d3-128">如果备份到现有介质集，还可以要求备份操作验证备份集的名称和过期时间。</span><span class="sxs-lookup"><span data-stu-id="df3d3-128">Optionally, if backing up to an existing media set, require the backup operation to verify the name and the expiration date of the backup sets.</span></span>  
  
 <span data-ttu-id="df3d3-129">**介质集名称**</span><span class="sxs-lookup"><span data-stu-id="df3d3-129">**Media set name**</span></span>  
 <span data-ttu-id="df3d3-130">如果选中了“检查媒体集名称和备份集过期时间”\*\*\*\*，还可以指定用于此备份操作的媒体集的名称。</span><span class="sxs-lookup"><span data-stu-id="df3d3-130">If **Check media set name and backup set expiration** is selected, optionally, specify the name of the media set to be used for this backup operation.</span></span>  
  
 <span data-ttu-id="df3d3-131">**备份到新介质集并清除所有现有备份集**</span><span class="sxs-lookup"><span data-stu-id="df3d3-131">**Back up to a new media set, and erase all existing backup sets**</span></span>  
 <span data-ttu-id="df3d3-132">使用新介质集，并清除以前的备份集。</span><span class="sxs-lookup"><span data-stu-id="df3d3-132">Use a new media set, erasing the previous backup sets.</span></span>  
  
 <span data-ttu-id="df3d3-133">单击此选项可以激活以下选项：</span><span class="sxs-lookup"><span data-stu-id="df3d3-133">Clicking this option activates the following options:</span></span>  
  
 <span data-ttu-id="df3d3-134">**新建介质集名称**</span><span class="sxs-lookup"><span data-stu-id="df3d3-134">**New media set name**</span></span>  
 <span data-ttu-id="df3d3-135">根据需要，可以输入介质集的新名称。</span><span class="sxs-lookup"><span data-stu-id="df3d3-135">Optionally, enter a new name for the media set.</span></span>  
  
 <span data-ttu-id="df3d3-136">**新建介质集说明**</span><span class="sxs-lookup"><span data-stu-id="df3d3-136">**New media set description**</span></span>  
 <span data-ttu-id="df3d3-137">根据需要，可以输入新介质集的贴切说明。</span><span class="sxs-lookup"><span data-stu-id="df3d3-137">Optionally, enter a meaningful description of the new media set.</span></span> <span data-ttu-id="df3d3-138">此说明应该足够具体，可以准确地表述内容。</span><span class="sxs-lookup"><span data-stu-id="df3d3-138">This description should be specific enough to communicate the contents accurately.</span></span>  
  
### <a name="reliability"></a><span data-ttu-id="df3d3-139">可靠性</span><span class="sxs-lookup"><span data-stu-id="df3d3-139">Reliability</span></span>  
 <span data-ttu-id="df3d3-140">**“事务日志”** 面板中的选项可以控制备份操作的错误管理。</span><span class="sxs-lookup"><span data-stu-id="df3d3-140">The options of the **Transaction log** panel control error management by the backup operation.</span></span>  
  
 <span data-ttu-id="df3d3-141">**完成后验证备份**</span><span class="sxs-lookup"><span data-stu-id="df3d3-141">**Verify backup when finished**</span></span>  
 <span data-ttu-id="df3d3-142">验证备份集是否完整以及所有卷是否都可读。</span><span class="sxs-lookup"><span data-stu-id="df3d3-142">Verify that the backup set is complete and that all volumes are readable.</span></span>  
  
 <span data-ttu-id="df3d3-143">**写入介质前执行校验和**</span><span class="sxs-lookup"><span data-stu-id="df3d3-143">**Perform checksum before writing to media**</span></span>  
 <span data-ttu-id="df3d3-144">在写入备份介质前验证校验和。</span><span class="sxs-lookup"><span data-stu-id="df3d3-144">Verify the checksums before writing to the backup media.</span></span> <span data-ttu-id="df3d3-145">选择此选项等效于在 [!INCLUDE[tsql](../../includes/tsql-md.md)]的 BACKUP 语句中指定 CHECKSUM 选项。</span><span class="sxs-lookup"><span data-stu-id="df3d3-145">Selecting this option is equivalent to specifying the CHECKSUM option in the BACKUP statement of [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="df3d3-146">选择此选项可能会增大工作负荷，并降低备份操作的备份吞吐量。</span><span class="sxs-lookup"><span data-stu-id="df3d3-146">Selecting this option may increase the workload, and decrease the backup throughput of the backup operation.</span></span> <span data-ttu-id="df3d3-147">有关校验和的详细信息，请参阅[在备份和还原期间可能的媒体错误 (SQL Server)](possible-media-errors-during-backup-and-restore-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="df3d3-147">For information about backup checksums, see [Possible Media Errors During Backup and Restore &#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md).</span></span>  
  
 <span data-ttu-id="df3d3-148">**出错时继续**</span><span class="sxs-lookup"><span data-stu-id="df3d3-148">**Continue on error**</span></span>  
 <span data-ttu-id="df3d3-149">备份操作继续进行，即使在遇到一个或多个错误后。</span><span class="sxs-lookup"><span data-stu-id="df3d3-149">The backup operation is to continue even after encountering one or more errors.</span></span>  
  
### <a name="transaction-log"></a><span data-ttu-id="df3d3-150">事务日志</span><span class="sxs-lookup"><span data-stu-id="df3d3-150">Transaction log</span></span>  
 <span data-ttu-id="df3d3-151">**“事务日志”** 面板中的选项可以控制事务日志备份的行为。</span><span class="sxs-lookup"><span data-stu-id="df3d3-151">The options of the **Transaction log** panel control the behavior of a transaction log backup.</span></span> <span data-ttu-id="df3d3-152">这些选项只在完整恢复模式或大容量日志恢复模式下相关。</span><span class="sxs-lookup"><span data-stu-id="df3d3-152">These options are relevant only under the full recovery model or bulk-logged recovery model.</span></span> <span data-ttu-id="df3d3-153">仅在 **“备份数据库”** 对话框的 **“常规”** 页上的 [“备份类型”](../../integration-services/general-page-of-integration-services-designers-options.md) 字段中选中了 **“事务日志”** 时，才会激活这些选项。</span><span class="sxs-lookup"><span data-stu-id="df3d3-153">They are activated only if **Transaction log** has been selected in the **Backup type** field on the [General](../../integration-services/general-page-of-integration-services-designers-options.md) page of the **Back Up Database** dialog box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="df3d3-154">有关事务日志备份的信息，请参阅[事务日志备份 (SQL Server)](transaction-log-backups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="df3d3-154">For information about transaction log backups, see [Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md).</span></span>  
  
 <span data-ttu-id="df3d3-155">**截断事务日志**</span><span class="sxs-lookup"><span data-stu-id="df3d3-155">**Truncate the transaction log**</span></span>  
 <span data-ttu-id="df3d3-156">备份事务日志并将其截断，以释放日志空间。</span><span class="sxs-lookup"><span data-stu-id="df3d3-156">Back up the transaction log and truncate it to free log space.</span></span> <span data-ttu-id="df3d3-157">数据库仍然处于联机状态。</span><span class="sxs-lookup"><span data-stu-id="df3d3-157">The database remains online.</span></span> <span data-ttu-id="df3d3-158">这是默认选项。</span><span class="sxs-lookup"><span data-stu-id="df3d3-158">This is the default option.</span></span>  
  
 <span data-ttu-id="df3d3-159">**备份日志尾部，并使数据库处于还原状态**</span><span class="sxs-lookup"><span data-stu-id="df3d3-159">**Back up the tail of the log, and leave the database in the restoring state**</span></span>  
 <span data-ttu-id="df3d3-160">备份日志尾部并使数据库处于还原状态。</span><span class="sxs-lookup"><span data-stu-id="df3d3-160">Back up the tail of the log and leave the database in a restoring state.</span></span> <span data-ttu-id="df3d3-161">此选项创建 *结尾日志备份*，通常用于在准备还原数据库时备份尚未备份的日志（活动日志）。</span><span class="sxs-lookup"><span data-stu-id="df3d3-161">This option creates a *tail-log backup*, which backs up logs that have not yet been backed up (the active log), typically, in preparation for restoring a database.</span></span> <span data-ttu-id="df3d3-162">在数据库完全还原之前，用户将无法使用。</span><span class="sxs-lookup"><span data-stu-id="df3d3-162">The database will be unavailable to users until it is completely restored.</span></span>  
  
 <span data-ttu-id="df3d3-163">选择此选项等效于在 [BACKUP](/sql/t-sql/statements/backup-transact-sql) 语句 ([!INCLUDE[tsql](../../includes/tsql-md.md)]) 中指定“WITH NO_TRUNCATE, NORECOVERY”。</span><span class="sxs-lookup"><span data-stu-id="df3d3-163">Selecting this option is equivalent to specifying WITH NO_TRUNCATE, NORECOVERY in a [BACKUP](/sql/t-sql/statements/backup-transact-sql) statement ([!INCLUDE[tsql](../../includes/tsql-md.md)]).</span></span> <span data-ttu-id="df3d3-164">有关详细信息，请参阅[结尾日志备份 (SQL Server)](tail-log-backups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="df3d3-164">For more information, see [Tail-Log Backups &#40;SQL Server&#41;](tail-log-backups-sql-server.md).</span></span>  
  
### <a name="tape-drive"></a><span data-ttu-id="df3d3-165">磁带机</span><span class="sxs-lookup"><span data-stu-id="df3d3-165">Tape drive</span></span>  
 <span data-ttu-id="df3d3-166">**“磁带机”** 面板中的选项可以控制备份操作期间的磁带管理。</span><span class="sxs-lookup"><span data-stu-id="df3d3-166">The options of the **Tape drive** panel control tape management during the backup operation.</span></span> <span data-ttu-id="df3d3-167">仅在 **“备份数据库”** 对话框的 **“常规”** 页上的 [“目标”](../../integration-services/general-page-of-integration-services-designers-options.md) 面板中选中了 **“磁带”** ，才会激活这些选项。</span><span class="sxs-lookup"><span data-stu-id="df3d3-167">These options are activated only if **Tape** has been selected in the **Destination** panel on the [General](../../integration-services/general-page-of-integration-services-designers-options.md) page of the **Back Up Database** dialog box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="df3d3-168">有关如何使用磁带设备的信息，请参阅[备份设备 (SQL Server)](backup-devices-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="df3d3-168">For information about how to use tape devices, see [Backup Devices &#40;SQL Server&#41;](backup-devices-sql-server.md).</span></span>  
  
 <span data-ttu-id="df3d3-169">**备份后卸载磁带**</span><span class="sxs-lookup"><span data-stu-id="df3d3-169">**Unload the tape after backup**</span></span>  
 <span data-ttu-id="df3d3-170">在备份完成后，卸载磁带。</span><span class="sxs-lookup"><span data-stu-id="df3d3-170">After the backup is complete, unload the tape.</span></span>  
  
 <span data-ttu-id="df3d3-171">**卸载前倒带**</span><span class="sxs-lookup"><span data-stu-id="df3d3-171">**Rewind the tape before unloading**</span></span>  
 <span data-ttu-id="df3d3-172">在卸载磁带前，释放并进行倒带。</span><span class="sxs-lookup"><span data-stu-id="df3d3-172">Before unloading the tape, release and rewind it.</span></span> <span data-ttu-id="df3d3-173">仅在选中了 **“备份后卸载磁带”** 的时候，才会启用该选项。</span><span class="sxs-lookup"><span data-stu-id="df3d3-173">This is enabled only if **Unload the tape after backup** is selected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df3d3-174">另请参阅</span><span class="sxs-lookup"><span data-stu-id="df3d3-174">See Also</span></span>  
 <span data-ttu-id="df3d3-175">[BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="df3d3-175">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="df3d3-176">[备份事务日志 (SQL Server)](back-up-a-transaction-log-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="df3d3-176">[Back Up a Transaction Log &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md) </span></span>  
 <span data-ttu-id="df3d3-177">[备份文件和文件组 (SQL Server)](back-up-files-and-filegroups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="df3d3-177">[Back Up Files and Filegroups &#40;SQL Server&#41;](back-up-files-and-filegroups-sql-server.md) </span></span>  
 [<span data-ttu-id="df3d3-178">在数据库损坏时备份事务日志 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="df3d3-178">Back Up the Transaction Log When the Database Is Damaged &#40;SQL Server&#41;</span></span>](back-up-the-transaction-log-when-the-database-is-damaged-sql-server.md)  
  
  
