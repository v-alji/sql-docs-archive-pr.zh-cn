---
title: 还原数据库（“选项”页）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.restoredb.options.f1
ms.assetid: 9a75d48b-c25f-40f3-8ea1-32cfa8211754
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d60474b5d72ab9745500325dfd523f83f155343c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581325"
---
# <a name="restore-database-options-page"></a><span data-ttu-id="d0d81-102">还原数据库（“选项”页）</span><span class="sxs-lookup"><span data-stu-id="d0d81-102">Restore Database (Options Page)</span></span>
  <span data-ttu-id="d0d81-103">使用 **“还原数据库”** 对话框的 **“选项”** 页可修改还原操作的行为和结果。</span><span class="sxs-lookup"><span data-stu-id="d0d81-103">Use the **Options** page of the **Restore Database** dialog box to modify the behavior and outcome of the restore operation.</span></span>  
  
 <span data-ttu-id="d0d81-104">**使用 SQL Server Management Studio 还原数据库备份**</span><span class="sxs-lookup"><span data-stu-id="d0d81-104">**To use SQL Server Management Studio to restore a database backup**</span></span>  
  
-   [<span data-ttu-id="d0d81-105">RESTORE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d0d81-105">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
-   [<span data-ttu-id="d0d81-106">为磁带驱动器定义逻辑备份设备 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="d0d81-106">Define a Logical Backup Device for a Tape Drive &#40;SQL Server&#41;</span></span>](define-a-logical-backup-device-for-a-tape-drive-sql-server.md)  
  
> [!NOTE]  
>  <span data-ttu-id="d0d81-107">使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]指定还原任务时，您可以为此还原操作生成一个包含 RESTORE 语句的对应的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 脚本。</span><span class="sxs-lookup"><span data-stu-id="d0d81-107">When you specify a restore task by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], you can generate a corresponding [!INCLUDE[tsql](../../includes/tsql-md.md)] script containing the RESTORE statements for this restore operation.</span></span> <span data-ttu-id="d0d81-108">若要生成该脚本，请单击 **“脚本”** ，然后为脚本选择一个目标。</span><span class="sxs-lookup"><span data-stu-id="d0d81-108">To generate the script, click **Script** and then select a destination for the script.</span></span> <span data-ttu-id="d0d81-109">有关 RESTORE 语法的信息，请参阅 [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="d0d81-109">For information about the RESTORE syntax, see [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql).</span></span>  
  
## <a name="options"></a><span data-ttu-id="d0d81-110">选项</span><span class="sxs-lookup"><span data-stu-id="d0d81-110">Options</span></span>  
  
### <a name="restore-options"></a><span data-ttu-id="d0d81-111">还原选项</span><span class="sxs-lookup"><span data-stu-id="d0d81-111">Restore options</span></span>  
 <span data-ttu-id="d0d81-112">若要修改还原操作行为的各个方面，请使用使用 **“还原选项”** 面板中的选项。</span><span class="sxs-lookup"><span data-stu-id="d0d81-112">To modify aspects of the behavior of the restore operation, use the options of the **Restore options** panel.</span></span>  
  
 <span data-ttu-id="d0d81-113">**覆盖现有数据库 [WITH REPLACE]**</span><span class="sxs-lookup"><span data-stu-id="d0d81-113">**Overwrite the existing database [WITH REPLACE]**</span></span>  
 <span data-ttu-id="d0d81-114">还原操作将覆盖当前使用你指定的数据库名称（在“还原数据库”对话框中“[常规](../../integration-services/general-page-of-integration-services-designers-options.md)”页上“还原到”字段中指定）的任何数据库文件。  </span><span class="sxs-lookup"><span data-stu-id="d0d81-114">The restore operation will overwrite the files of any database that is currently using the database name that you are specifying in the **Restore to**field on the [General](../../integration-services/general-page-of-integration-services-designers-options.md) page of the **Restore Database** dialog box.</span></span> <span data-ttu-id="d0d81-115">即使将备份从其他数据库还原到现有的数据库名称，现有数据库的文件也将被覆盖。</span><span class="sxs-lookup"><span data-stu-id="d0d81-115">The files of the existing database will be overwritten even if you are restoring backups from a different database to the existing database name.</span></span> <span data-ttu-id="d0d81-116">选择此选项等效于在 [RESTORE](/sql/t-sql/statements/restore-statements-arguments-transact-sql) 语句 ([!INCLUDE[tsql](../../includes/tsql-md.md)]) 中使用 REPLACE 选项。</span><span class="sxs-lookup"><span data-stu-id="d0d81-116">Selecting this option is equivalent to using the REPLACE option in a [RESTORE](/sql/t-sql/statements/restore-statements-arguments-transact-sql) statement ([!INCLUDE[tsql](../../includes/tsql-md.md)]).</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="d0d81-117">只有在仔细考虑后，才能使用此选项。</span><span class="sxs-lookup"><span data-stu-id="d0d81-117">Use this option only after careful consideration.</span></span> <span data-ttu-id="d0d81-118">有关详细信息，请参阅 [RESTORE Arguments (Transact-SQL)](/sql/t-sql/statements/restore-statements-arguments-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="d0d81-118">For more information, see [RESTORE Arguments &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql).</span></span>  
  
 <span data-ttu-id="d0d81-119">**保留复制设置 [WITH KEEP_REPLICATION]**</span><span class="sxs-lookup"><span data-stu-id="d0d81-119">**Preserve the replication settings [WITH KEEP_REPLICATION]**</span></span>  
 <span data-ttu-id="d0d81-120">将已发布的数据库还原到创建该数据库的服务器之外的服务器时，保留复制设置。</span><span class="sxs-lookup"><span data-stu-id="d0d81-120">Preserves the replication settings when restoring a published database to a server other than the server where the database was created.</span></span> <span data-ttu-id="d0d81-121">此选项只适用于在创建备份时对数据库进行了复制的情况。</span><span class="sxs-lookup"><span data-stu-id="d0d81-121">This option is relevant only if the database was replicated when the backup was created.</span></span>  
  
 <span data-ttu-id="d0d81-122">仅在选择“回滚未提交的事务，使数据库处于可以使用的状态”  选项（在本表的后面部分中说明）时，此选项才可用，其功能等效于使用 RECOVERY 选项还原备份。</span><span class="sxs-lookup"><span data-stu-id="d0d81-122">This option is available only with the **Leave the database ready for use by rolling back the uncommitted transactions** option (described later in this table), which is equivalent to restoring a backup with the RECOVERY option.</span></span>  
  
 <span data-ttu-id="d0d81-123">选择此选项等效于在 [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) 语句中使用 KEEP_REPLICATION 选项。</span><span class="sxs-lookup"><span data-stu-id="d0d81-123">Selecting this option is equivalent to using the KEEP_REPLICATION option in a [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) statement.</span></span>  
  
 <span data-ttu-id="d0d81-124">有关详细信息，请参阅 [备份和还原复制的数据库](../replication/administration/back-up-and-restore-replicated-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="d0d81-124">For more information, see [Back Up and Restore Replicated Databases](../replication/administration/back-up-and-restore-replicated-databases.md).</span></span>  
  
 <span data-ttu-id="d0d81-125">**限制还原数据库的访问 [WITH RESTRICTED_USER]**</span><span class="sxs-lookup"><span data-stu-id="d0d81-125">**Restrict access to the restored database [WITH RESTRICTED_USER]**</span></span>  
 <span data-ttu-id="d0d81-126">使还原的数据库仅供 **db_owner**、 **dbcreator**或 **sysadmin**的成员使用。</span><span class="sxs-lookup"><span data-stu-id="d0d81-126">Makes the restored database available only to the members of **db_owner**, **dbcreator**, or **sysadmin**.</span></span>  
  
 <span data-ttu-id="d0d81-127">选择此选项等效于在 RESTORE 语句中使用 RESTRICTED_USER 选项。</span><span class="sxs-lookup"><span data-stu-id="d0d81-127">Selecting this option is synonymous to using the RESTRICTED_USER option in a RESTORE statement.</span></span>  
  
### <a name="recovery-state"></a><span data-ttu-id="d0d81-128">恢复状态</span><span class="sxs-lookup"><span data-stu-id="d0d81-128">Recovery state</span></span>  
 <span data-ttu-id="d0d81-129">若要在完成存储操作后确定数据库的状态，则必须选择 **“恢复状态”** 面板中的选项之一。</span><span class="sxs-lookup"><span data-stu-id="d0d81-129">To determine the state of the database after the store operation, you must select one of the options of the **Recovery state** panel.</span></span>  
  
 <span data-ttu-id="d0d81-130">**RESTORE WITH RECOVERY**</span><span class="sxs-lookup"><span data-stu-id="d0d81-130">**RESTORE WITH RECOVERY**</span></span>  
 <span data-ttu-id="d0d81-131">在还原了在[“常规”](../../integration-services/general-page-of-integration-services-designers-options.md)页的“用于还原的备份集”  网格中选中的最后一个备份之后，恢复数据库。</span><span class="sxs-lookup"><span data-stu-id="d0d81-131">Recovers the database after restoring the final backup checked in the **Backup sets to restore**grid on the [General page](../../integration-services/general-page-of-integration-services-designers-options.md).</span></span> <span data-ttu-id="d0d81-132">这是默认选项，等效于在 [RESTORE](/sql/t-sql/statements/restore-statements-arguments-transact-sql) 语句 ([!INCLUDE[tsql](../../includes/tsql-md.md)]) 中指定 WITH RECOVERY。</span><span class="sxs-lookup"><span data-stu-id="d0d81-132">This is the default option and is equivalent to specifying WITH RECOVERY in a [RESTORE](/sql/t-sql/statements/restore-statements-arguments-transact-sql) statement ([!INCLUDE[tsql](../../includes/tsql-md.md)]).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d0d81-133">在完整恢复模式或大容量日志恢复模式下，只有在需要还原所有日志文件时才选择此选项。</span><span class="sxs-lookup"><span data-stu-id="d0d81-133">Under the full recovery model or bulk-logged recovery model, choose this option only if you are restoring all the log files now.</span></span>  
  
 <span data-ttu-id="d0d81-134">**RESTORE WITH NORECOVERY**</span><span class="sxs-lookup"><span data-stu-id="d0d81-134">**RESTORE WITH NORECOVERY**</span></span>  
 <span data-ttu-id="d0d81-135">使数据库处于还原状态。</span><span class="sxs-lookup"><span data-stu-id="d0d81-135">Leaves the database in the restoring state.</span></span> <span data-ttu-id="d0d81-136">这允许您还原当前恢复路径中的其他备份。</span><span class="sxs-lookup"><span data-stu-id="d0d81-136">This allows you to restore additional backups in the current recovery path.</span></span> <span data-ttu-id="d0d81-137">若要恢复数据库，则必须使用 RESTORE WITH RECOVERY 选项（请参阅前面的选项）来执行还原操作。</span><span class="sxs-lookup"><span data-stu-id="d0d81-137">To recover the database, you will have to perform a restore operation by using the RESTORE WITH RECOVERY option (see the preceding option).</span></span>  
  
 <span data-ttu-id="d0d81-138">此选项等效于在 RESTORE 语句中指定 WITH NORECOVERY。</span><span class="sxs-lookup"><span data-stu-id="d0d81-138">This option is equivalent to specifying WITH NORECOVERY in a RESTORE statement.</span></span>  
  
 <span data-ttu-id="d0d81-139">如果选择此选项， **“保留复制设置”** 选项将不可用。</span><span class="sxs-lookup"><span data-stu-id="d0d81-139">If you select this option, the **Preserve replication settings** option is unavailable.</span></span>  
  
 <span data-ttu-id="d0d81-140">**RESTORE WITH STANDBY**</span><span class="sxs-lookup"><span data-stu-id="d0d81-140">**RESTORE WITH STANDBY**</span></span>  
 <span data-ttu-id="d0d81-141">使数据库处于备用状态，在该状态下只能对数据库进行有限的只读访问。</span><span class="sxs-lookup"><span data-stu-id="d0d81-141">Leaves the database in a standby state, in which the database is available for limited read-only access.</span></span> <span data-ttu-id="d0d81-142">此选项等效于在 RESTORE 语句中指定 WITH STANDBY。</span><span class="sxs-lookup"><span data-stu-id="d0d81-142">This option is equivalent to specifying WITH STANDBY in a RESTORE statement.</span></span>  
  
 <span data-ttu-id="d0d81-143">选择该选项要求您在 **“备用文件”** 文本框中指定一个备用文件。</span><span class="sxs-lookup"><span data-stu-id="d0d81-143">Choosing this option requires that you specify a standby file in the **Standby file** text box.</span></span> <span data-ttu-id="d0d81-144">备用文件允许撤消恢复效果。</span><span class="sxs-lookup"><span data-stu-id="d0d81-144">The standby file allows the recovery effects to be undone.</span></span>  
  
 <span data-ttu-id="d0d81-145">**“备用文件”**</span><span class="sxs-lookup"><span data-stu-id="d0d81-145">**Standby file**</span></span>  
 <span data-ttu-id="d0d81-146">指定备用文件。</span><span class="sxs-lookup"><span data-stu-id="d0d81-146">Specifies a standby file.</span></span> <span data-ttu-id="d0d81-147">您可以浏览到该备用文件，也可以在文本框中直接输入其路径名。</span><span class="sxs-lookup"><span data-stu-id="d0d81-147">You can browse for the standby file or enter its pathname directly in the text box.</span></span>  
  
### <a name="tail-log-backup"></a><span data-ttu-id="d0d81-148">结尾日志备份</span><span class="sxs-lookup"><span data-stu-id="d0d81-148">Tail-Log backup</span></span>  
 <span data-ttu-id="d0d81-149">允许您指定结尾日志备份与数据库还原一起执行。</span><span class="sxs-lookup"><span data-stu-id="d0d81-149">Allows you to designate that a tail-log backup be performed along with the database restore.</span></span>  
  
 <span data-ttu-id="d0d81-150">**在还原前执行结尾日志备份**</span><span class="sxs-lookup"><span data-stu-id="d0d81-150">**Take tail-Log backup before restoring**</span></span>  
 <span data-ttu-id="d0d81-151">选中此复选框可以指定应执行结尾日志备份。</span><span class="sxs-lookup"><span data-stu-id="d0d81-151">Check this box to designate that a tail-log backup should be performed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d0d81-152">如果你在[“备份时间线”](backup-timeline.md) 对话框中选择的时间点要求结尾日志备份，则将选择此框并且你将不能对其进行编辑。</span><span class="sxs-lookup"><span data-stu-id="d0d81-152">If the point-in-time you have selected in the [Backup Timeline](backup-timeline.md) dialog box requires a tail-log backup, this box will be selected and you will not be able to edit it.</span></span>  
  
 <span data-ttu-id="d0d81-153">**“备份文件”**</span><span class="sxs-lookup"><span data-stu-id="d0d81-153">**Backup file**</span></span>  
 <span data-ttu-id="d0d81-154">为日志的结尾指定备份文件。</span><span class="sxs-lookup"><span data-stu-id="d0d81-154">Specifies a backup file for the tail of the log.</span></span> <span data-ttu-id="d0d81-155">您可以浏览备份文件，也可以在文本框中直接输入其名称。</span><span class="sxs-lookup"><span data-stu-id="d0d81-155">You can browse for the backup file or enter its name directly in the text box.</span></span>  
  
### <a name="server-connections"></a><span data-ttu-id="d0d81-156">服务器连接</span><span class="sxs-lookup"><span data-stu-id="d0d81-156">Server connections</span></span>  
 <span data-ttu-id="d0d81-157">可用于关闭现有的数据库连接。</span><span class="sxs-lookup"><span data-stu-id="d0d81-157">Allows you to close existing database connections.</span></span>  
  
 <span data-ttu-id="d0d81-158">**关闭现有连接**</span><span class="sxs-lookup"><span data-stu-id="d0d81-158">**Close existing connections**</span></span>  
 <span data-ttu-id="d0d81-159">如果存在与数据库的活动连接，则还原操作可能会失败。</span><span class="sxs-lookup"><span data-stu-id="d0d81-159">Restore operations may fail if there are active connections to the database.</span></span> <span data-ttu-id="d0d81-160">选中 **“关闭现有连接”** 以确保关闭 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 和数据库之间的所有活动连接。</span><span class="sxs-lookup"><span data-stu-id="d0d81-160">Check the **Close existing connections option** to ensure that all active connections between [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] and the database are closed.</span></span> <span data-ttu-id="d0d81-161">此复选框可在执行还原操作之前将数据库设置为单用户模式，并在该操作完成后将数据库设置为多用户模式。</span><span class="sxs-lookup"><span data-stu-id="d0d81-161">This check box sets the database to single user mode before performing the restore operations, and sets the database to multi-user mode when complete.</span></span>  
  
### <a name="prompt"></a><span data-ttu-id="d0d81-162">Prompt</span><span class="sxs-lookup"><span data-stu-id="d0d81-162">Prompt</span></span>  
 <span data-ttu-id="d0d81-163">**还原每个备份之前进行提示**</span><span class="sxs-lookup"><span data-stu-id="d0d81-163">**Prompt before restoring each backup**</span></span>  
 <span data-ttu-id="d0d81-164">指定在还原了每个备份之后，将显示“继续还原”  对话框，询问你是否要继续还原顺序。</span><span class="sxs-lookup"><span data-stu-id="d0d81-164">Specifies that after each backup is restored, the **Continue with Restore** dialog box will be displayed to inquire whether you want to continue the restore sequence.</span></span> <span data-ttu-id="d0d81-165">该对话框将显示下一个介质集（如果已知）的名称以及下一个备份集的名称和说明。</span><span class="sxs-lookup"><span data-stu-id="d0d81-165">This dialog box displays the name of the next media set (if known) and the name and description of the next backup set.</span></span>  
  
 <span data-ttu-id="d0d81-166">此选项允许您在还原了任何备份后暂停还原顺序。</span><span class="sxs-lookup"><span data-stu-id="d0d81-166">This option allows you to pause a restore sequence after restoring any of the backups.</span></span> <span data-ttu-id="d0d81-167">如果必须为不同介质集更换磁带，例如在服务器仅具有一个磁带设备时，此选项非常有用。</span><span class="sxs-lookup"><span data-stu-id="d0d81-167">This option is particularly useful when you must swap tapes for different media sets; for example, when your server has only one tape device.</span></span> <span data-ttu-id="d0d81-168">准备就绪后，请单击 **“确定”** 以继续。</span><span class="sxs-lookup"><span data-stu-id="d0d81-168">When you are ready to proceed, click **OK**.</span></span>  
  
 <span data-ttu-id="d0d81-169">可以通过单击 **“否”** 中断还原顺序。</span><span class="sxs-lookup"><span data-stu-id="d0d81-169">You can interrupt a restore sequence by clicking **No**.</span></span> <span data-ttu-id="d0d81-170">这样可以使数据库保持还原状态。</span><span class="sxs-lookup"><span data-stu-id="d0d81-170">This leaves the database is in the restoring state.</span></span> <span data-ttu-id="d0d81-171">在日后方便的时候，可以通过恢复执行 **“继续还原”** 对话框中所列出的下一个备份，继续该还原顺序。</span><span class="sxs-lookup"><span data-stu-id="d0d81-171">At your convenience, you can later continue the restore sequence by resuming with the next backup described in the **Continue with Restore** dialog box.</span></span> <span data-ttu-id="d0d81-172">还原下一个备份的过程取决于其是否包含数据或事务日志，如下所示：</span><span class="sxs-lookup"><span data-stu-id="d0d81-172">The procedure restoring the next backup depends on whether it contains data or transaction log, as follows:</span></span>  
  
-   <span data-ttu-id="d0d81-173">如果下一个备份是完整备份或差异备份，请再次使用 **“还原数据库”** 任务。</span><span class="sxs-lookup"><span data-stu-id="d0d81-173">If the next backup is a full or differential backup, use the **Restore Database** task again.</span></span>  
  
-   <span data-ttu-id="d0d81-174">如果下一个备份是文件备份，请使用 **“还原文件和文件组”** 任务。</span><span class="sxs-lookup"><span data-stu-id="d0d81-174">If the next backup is a file backup, use the **Restore Files and Filegroup**s task.</span></span> <span data-ttu-id="d0d81-175">有关详细信息，请参阅[还原文件和文件组 (SQL Server)](restore-files-and-filegroups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="d0d81-175">For more information, see [Restore Files and Filegroups &#40;SQL Server&#41;](restore-files-and-filegroups-sql-server.md).</span></span>  
  
-   <span data-ttu-id="d0d81-176">如果下一个备份是日志备份，请使用 **“还原事务日志”** 任务。</span><span class="sxs-lookup"><span data-stu-id="d0d81-176">If the next backup is a log backup, use the **Restore Transaction Log** task.</span></span> <span data-ttu-id="d0d81-177">有关通过还原事务日志来继续还原顺序的信息，请参阅 [还原事务日志备份 (SQL Server)](restore-a-transaction-log-backup-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="d0d81-177">For information about resuming a restore sequence by restoring a transaction log, see [Restore a Transaction Log Backup &#40;SQL Server&#41;](restore-a-transaction-log-backup-sql-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0d81-178">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d0d81-178">See Also</span></span>  
 <span data-ttu-id="d0d81-179">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d0d81-179">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 <span data-ttu-id="d0d81-180">[从设备还原备份 (SQL Server)](restore-a-backup-from-a-device-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d0d81-180">[Restore a Backup from a Device &#40;SQL Server&#41;](restore-a-backup-from-a-device-sql-server.md) </span></span>  
 <span data-ttu-id="d0d81-181">[还原事务日志备份 (SQL Server)](restore-a-transaction-log-backup-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d0d81-181">[Restore a Transaction Log Backup &#40;SQL Server&#41;](restore-a-transaction-log-backup-sql-server.md) </span></span>  
 <span data-ttu-id="d0d81-182">[媒体集、媒体簇和备份集 (SQL Server)](media-sets-media-families-and-backup-sets-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d0d81-182">[Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md) </span></span>  
 <span data-ttu-id="d0d81-183">[应用事务日志备份 (SQL Server)](transaction-log-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d0d81-183">[Apply Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span></span>  
 [<span data-ttu-id="d0d81-184">还原数据库（“常规”页）</span><span class="sxs-lookup"><span data-stu-id="d0d81-184">Restore Database &#40;General Page&#41;</span></span>](../../integration-services/general-page-of-integration-services-designers-options.md)  
  
  
