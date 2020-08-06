---
title: 将数据库还原到新位置 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- restoring databases [SQL Server], moving
- database restores [SQL Server], creating new databases
- restoring [SQL Server], with move
- restoring databases [SQL Server], creating new databases
- database backups [SQL Server], creating new database from
- backing up databases [SQL Server], creating new database from
- restoring databases [SQL Server], renaming
- database creation [SQL Server], restoring with move
ms.assetid: 4da76d61-5e11-4bee-84f5-b305240d9f42
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 89b42f439b5622074327506b9f2ca2b2358cd12f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589165"
---
# <a name="restore-a-database-to-a-new-location-sql-server"></a><span data-ttu-id="ab023-102">将数据库还原到新位置 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ab023-102">Restore a Database to a New Location (SQL Server)</span></span>
  <span data-ttu-id="ab023-103">本主题介绍如何使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 或 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中将 [!INCLUDE[tsql](../../includes/tsql-md.md)]数据库还原到一个新位置并且可以选择重命名该数据库。</span><span class="sxs-lookup"><span data-stu-id="ab023-103">This topic describes how to restore a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database to a new location, and optionally rename the database, in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="ab023-104">您可以在同一服务器实例或不同服务器实例上将数据库移到新的目录路径或者创建数据库的副本。</span><span class="sxs-lookup"><span data-stu-id="ab023-104">You can move a database to a new directory path or create a copy of a database on either the same server instance or a different server instance.</span></span>  
  
 <span data-ttu-id="ab023-105">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="ab023-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="ab023-106">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="ab023-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="ab023-107">限制和局限</span><span class="sxs-lookup"><span data-stu-id="ab023-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="ab023-108">先决条件</span><span class="sxs-lookup"><span data-stu-id="ab023-108">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="ab023-109">建议</span><span class="sxs-lookup"><span data-stu-id="ab023-109">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="ab023-110">安全性</span><span class="sxs-lookup"><span data-stu-id="ab023-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="ab023-111">**若要将数据库还原到一个新位置并且可以选择重命名该数据库，请使用：**</span><span class="sxs-lookup"><span data-stu-id="ab023-111">**To restore a database to a new location, and optionally rename the database, using:**</span></span>  
  
     [<span data-ttu-id="ab023-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ab023-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="ab023-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ab023-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   [<span data-ttu-id="ab023-114">相关任务</span><span class="sxs-lookup"><span data-stu-id="ab023-114">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ab023-115">开始之前</span><span class="sxs-lookup"><span data-stu-id="ab023-115">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="ab023-116">限制和局限</span><span class="sxs-lookup"><span data-stu-id="ab023-116">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="ab023-117">还原完整数据库备份的系统管理员必须是当前使用要还原的数据库的唯一人员。</span><span class="sxs-lookup"><span data-stu-id="ab023-117">The system administrator restoring a full database backup must be the only person currently using the database to be restored.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="ab023-118">先决条件</span><span class="sxs-lookup"><span data-stu-id="ab023-118">Prerequisites</span></span>  
  
-   <span data-ttu-id="ab023-119">在完整恢复模式或大容量日志恢复模式下，必须先备份活动事务日志，然后才能还原数据库。</span><span class="sxs-lookup"><span data-stu-id="ab023-119">Under the full or bulk-logged recovery model, before you can restore a database, you must back up the active transaction log.</span></span> <span data-ttu-id="ab023-120">有关详细信息，请参阅 [备份事务日志 (SQL Server)](back-up-a-transaction-log-sql-server.md)数据库还原到一个新位置并且可以选择重命名该数据库。</span><span class="sxs-lookup"><span data-stu-id="ab023-120">For more information, see [Back Up a Transaction Log &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md).</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="ab023-121">建议</span><span class="sxs-lookup"><span data-stu-id="ab023-121">Recommendations</span></span>  
  
-   <span data-ttu-id="ab023-122">若要还原已加密的数据库，您必须有权访问用于对数据库进行加密的证书或非对称密钥。</span><span class="sxs-lookup"><span data-stu-id="ab023-122">To restore a database that is encrypted, you must have access to the certificate or asymmetric key that was used to encrypt the database.</span></span> <span data-ttu-id="ab023-123">如果没有证书或非对称密钥，数据库将无法还原。</span><span class="sxs-lookup"><span data-stu-id="ab023-123">Without the certificate or asymmetric key, the database cannot be restored.</span></span> <span data-ttu-id="ab023-124">因此，只要需要该备份，就必须保留用于对数据库加密密钥进行加密的证书。</span><span class="sxs-lookup"><span data-stu-id="ab023-124">As a result, the certificate that is used to encrypt the database encryption key must be retained as long as the backup is needed.</span></span> <span data-ttu-id="ab023-125">有关详细信息，请参阅 [SQL Server Certificates and Asymmetric Keys](../security/sql-server-certificates-and-asymmetric-keys.md)。</span><span class="sxs-lookup"><span data-stu-id="ab023-125">For more information, see [SQL Server Certificates and Asymmetric Keys](../security/sql-server-certificates-and-asymmetric-keys.md).</span></span>  
  
-   <span data-ttu-id="ab023-126">有关移动数据库的其他注意事项的信息，请参阅[通过备份和还原来复制数据库](../databases/copy-databases-with-backup-and-restore.md)。</span><span class="sxs-lookup"><span data-stu-id="ab023-126">For information about additional considerations for moving a database, see [Copy Databases with Backup and Restore](../databases/copy-databases-with-backup-and-restore.md).</span></span>  
  
-   <span data-ttu-id="ab023-127">如果您将 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 或更高版本的数据库还原为 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]，将自动升级该数据库。</span><span class="sxs-lookup"><span data-stu-id="ab023-127">If you restore a [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] or higher  database to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], the database is automatically upgraded.</span></span> <span data-ttu-id="ab023-128">通常，该数据库将立即可用。</span><span class="sxs-lookup"><span data-stu-id="ab023-128">Typically, the database becomes available immediately.</span></span> <span data-ttu-id="ab023-129">但是，如果 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 数据库具有全文检索，则升级过程将导入、重置或重新生成它们，具体取决于  **upgrade_option** 服务器属性的设置。</span><span class="sxs-lookup"><span data-stu-id="ab023-129">However, if a [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] database has full-text indexes, the upgrade process either imports, resets, or rebuilds them, depending on the setting of the  **upgrade_option** server property.</span></span> <span data-ttu-id="ab023-130">如果将升级选项设置为“导入”(**upgrade_option** = 2) 或“重新生成”(**upgrade_option** = 0)，在升级过程中将无法使用全文检索。</span><span class="sxs-lookup"><span data-stu-id="ab023-130">If the upgrade option is set to import (**upgrade_option** = 2) or rebuild (**upgrade_option** = 0), the full-text indexes will be unavailable during the upgrade.</span></span> <span data-ttu-id="ab023-131">导入可能需要数小时，而重新生成所需的时间最多时可能十倍于此，具体取决于要编制索引的数据量。</span><span class="sxs-lookup"><span data-stu-id="ab023-131">Depending the amount of data being indexed, importing can take several hours, and rebuilding can take up to ten times longer.</span></span> <span data-ttu-id="ab023-132">另请注意，如果将升级选项设置为“导入”，并且全文目录不可用，则会重新生成关联的全文索引。</span><span class="sxs-lookup"><span data-stu-id="ab023-132">Note also that when the upgrade option is set to import, the associated full-text indexes are rebuilt if a full-text catalog is not available.</span></span> <span data-ttu-id="ab023-133">若要更改 **upgrade_option** 服务器属性的设置，请使用 [sp_fulltext_service](/sql/relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="ab023-133">To change the setting of the **upgrade_option** server property, use [sp_fulltext_service](/sql/relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="ab023-134">Security</span><span class="sxs-lookup"><span data-stu-id="ab023-134">Security</span></span>  
 <span data-ttu-id="ab023-135">出于安全性考虑，我们建议您不要从未知或不信任的源附加或还原数据库。</span><span class="sxs-lookup"><span data-stu-id="ab023-135">For security purposes, we recommend that you do not attach or restore databases from unknown or untrusted sources.</span></span> <span data-ttu-id="ab023-136">此类数据库可能包含恶意代码，这些代码可能会执行非预期的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 代码，或者通过修改架构或物理数据库结构导致错误。</span><span class="sxs-lookup"><span data-stu-id="ab023-136">Such databases could contain malicious code that might execute unintended [!INCLUDE[tsql](../../includes/tsql-md.md)] code or cause errors by modifying the schema or the physical database structure.</span></span> <span data-ttu-id="ab023-137">使用来自未知源或不可信源的数据库前，请在非生产服务器上针对数据库运行 [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) ，然后检查数据库中的代码，例如存储过程或其他用户定义代码。</span><span class="sxs-lookup"><span data-stu-id="ab023-137">Before you use a database from an unknown or untrusted source, run [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) on the database on a nonproduction server and also examine the code, such as stored procedures or other user-defined code, in the database.</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ab023-138">权限</span><span class="sxs-lookup"><span data-stu-id="ab023-138">Permissions</span></span>  
 <span data-ttu-id="ab023-139">如果不存在要还原的数据库，则用户必须有 CREATE DATABASE 权限才能执行 RESTORE。</span><span class="sxs-lookup"><span data-stu-id="ab023-139">If the database being restored does not exist, the user must have CREATE DATABASE permissions to be able to execute RESTORE.</span></span> <span data-ttu-id="ab023-140">如果该数据库存在，则 RESTORE 权限默认授予 **sysadmin** 和 **dbcreator** 固定服务器角色成员以及该数据库的所有者 (**dbo**)。</span><span class="sxs-lookup"><span data-stu-id="ab023-140">If the database exists, RESTORE permissions default to members of the **sysadmin** and **dbcreator** fixed server roles and the owner (**dbo**) of the database.</span></span>  
  
 <span data-ttu-id="ab023-141">RESTORE 权限被授予那些成员身份信息始终可由服务器使用的角色。</span><span class="sxs-lookup"><span data-stu-id="ab023-141">RESTORE permissions are given to roles in which membership information is always readily available to the server.</span></span> <span data-ttu-id="ab023-142">因为只有在固定数据库可以访问且没有损坏时（在执行 RESTORE 时并不会总是这样）才能检查固定数据库角色成员身份，所以 **db_owner** 固定数据库角色成员没有 RESTORE 权限。</span><span class="sxs-lookup"><span data-stu-id="ab023-142">Because fixed database role membership can be checked only when the database is accessible and undamaged, which is not always the case when RESTORE is executed, members of the **db_owner** fixed database role do not have RESTORE permissions.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="ab023-143">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ab023-143">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-restore-a-database-to-a-new-location-and-optionally-rename-the-database"></a><span data-ttu-id="ab023-144">将数据库还原到一个新位置并且可以选择重命名该数据库</span><span class="sxs-lookup"><span data-stu-id="ab023-144">To restore a database to a new location, and optionally rename the database</span></span>  
  
1.  <span data-ttu-id="ab023-145">连接到相应的 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]实例，然后在对象资源管理器中，单击服务器名称以展开服务器树。</span><span class="sxs-lookup"><span data-stu-id="ab023-145">Connect to the appropriate instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="ab023-146">右键单击“数据库”，然后单击“还原数据库”   。</span><span class="sxs-lookup"><span data-stu-id="ab023-146">Right-click **Databases**, and then click **Restore Database**.</span></span> <span data-ttu-id="ab023-147">**“还原数据库”** 对话框随即打开。</span><span class="sxs-lookup"><span data-stu-id="ab023-147">The **Restore Database** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="ab023-148">在 **“常规”** 页上，使用 **“源”** 部分指定要还原的备份集的源和位置。</span><span class="sxs-lookup"><span data-stu-id="ab023-148">On the **General** page, use the **Source** section to specify the source and location of the backup sets to restore.</span></span> <span data-ttu-id="ab023-149">选择以下选项之一：</span><span class="sxs-lookup"><span data-stu-id="ab023-149">Select one of the following options:</span></span>  
  
    -   <span data-ttu-id="ab023-150">**Database**</span><span class="sxs-lookup"><span data-stu-id="ab023-150">**Database**</span></span>  
  
         <span data-ttu-id="ab023-151">从下拉列表中选择要还原的数据库。</span><span class="sxs-lookup"><span data-stu-id="ab023-151">Select the database to restore from the drop-down list.</span></span> <span data-ttu-id="ab023-152">此列表仅包含已根据 **msdb** 备份历史记录进行备份的数据库。</span><span class="sxs-lookup"><span data-stu-id="ab023-152">The list contains only databases that have been backed up according to the **msdb** backup history.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ab023-153">如果备份是从另一台服务器执行的，则目标服务器不具有指定数据库的备份历史记录信息。</span><span class="sxs-lookup"><span data-stu-id="ab023-153">If the backup is taken from a different server, the destination server will not have the backup history information for the specified database.</span></span> <span data-ttu-id="ab023-154">这种情况下，请选择 **“设备”** 以手动指定要还原的文件或设备。</span><span class="sxs-lookup"><span data-stu-id="ab023-154">In this case, select **Device** to manually specify the file or device to restore.</span></span>  
  
    1.  <span data-ttu-id="ab023-155">**设备**</span><span class="sxs-lookup"><span data-stu-id="ab023-155">**Device**</span></span>  
  
         <span data-ttu-id="ab023-156">单击“浏览”按钮 ( **...** ) 以打开“选择备份设备”  对话框。</span><span class="sxs-lookup"><span data-stu-id="ab023-156">Click the browse (**...**) button to open the **Select backup devices** dialog box.</span></span> <span data-ttu-id="ab023-157">在 **“备份介质类型”** 框中，从列出的设备类型中选择一种。</span><span class="sxs-lookup"><span data-stu-id="ab023-157">In the **Backup media type** box, select one of the listed device types.</span></span> <span data-ttu-id="ab023-158">若要为 **“备份介质”** 框选择一个或多个设备，请单击 **“添加”** 。</span><span class="sxs-lookup"><span data-stu-id="ab023-158">To select one or more devices for the **Backup media** box, click **Add**.</span></span>  
  
         <span data-ttu-id="ab023-159">将所需设备添加到 **“备份介质”** 列表框后，单击 **“确定”** 返回到 **“常规”** 页。</span><span class="sxs-lookup"><span data-stu-id="ab023-159">After you add the devices you want to the **Backup media** list box, click **OK** to return to the **General** page.</span></span>  
  
         <span data-ttu-id="ab023-160">在“源:设备:数据库”列表框中，选择应还原的数据库名称 **。**</span><span class="sxs-lookup"><span data-stu-id="ab023-160">In the **Source: Device: Database** list box, select the name of the database which should be restored.</span></span>  
  
         <span data-ttu-id="ab023-161">**注意** ：此列表仅在选择了 **“设备”** 时才可用。</span><span class="sxs-lookup"><span data-stu-id="ab023-161">**Note** This list is only available when **Device** is selected.</span></span> <span data-ttu-id="ab023-162">只有在所选设备上具有备份的数据库才可用。</span><span class="sxs-lookup"><span data-stu-id="ab023-162">Only databases that have backups on the selected device will be available.</span></span>  
  
4.  <span data-ttu-id="ab023-163">在 **“目标”** 部分中， **“数据库”** 框自动填充要还原的数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="ab023-163">In the **Destination** section, the **Database** box is automatically populated with the name of the database to be restored.</span></span> <span data-ttu-id="ab023-164">若要更改数据库名称，请在 **“数据库”** 框中输入新名称。</span><span class="sxs-lookup"><span data-stu-id="ab023-164">To change the name of the database, enter the new name in the **Database** box.</span></span>  
  
5.  <span data-ttu-id="ab023-165">在 **“还原到”** 框中，保留默认选项 **“至最近一次进行的备份”** ，或者单击 **“时间线”** 访问 **“备份时间线”** 对话框以手动选择要停止恢复操作的时间点。</span><span class="sxs-lookup"><span data-stu-id="ab023-165">In the **Restore to** box, leave the default as **To the last backup taken** or click on **Timeline** to access the **Backup Timeline** dialog box to manually select a point in time to stop the recovery action.</span></span> <span data-ttu-id="ab023-166">请参阅 [Backup Timeline](backup-timeline.md) 以获取有关指定特定时间点的详细信息。</span><span class="sxs-lookup"><span data-stu-id="ab023-166">See [Backup Timeline](backup-timeline.md) for more information on designating a specific point in time.</span></span>  
  
6.  <span data-ttu-id="ab023-167">在 **“要还原的备份集”** 网格中，选择要还原的备份。</span><span class="sxs-lookup"><span data-stu-id="ab023-167">In the **Backup sets to restore** grid, select the backups to restore.</span></span> <span data-ttu-id="ab023-168">此网格将显示对于指定位置可用的备份。</span><span class="sxs-lookup"><span data-stu-id="ab023-168">This grid displays the backups available for the specified location.</span></span> <span data-ttu-id="ab023-169">默认情况下，系统会推荐一个恢复计划。</span><span class="sxs-lookup"><span data-stu-id="ab023-169">By default, a recovery plan is suggested.</span></span> <span data-ttu-id="ab023-170">若要覆盖建议的恢复计划，可以更改网格中的选择。</span><span class="sxs-lookup"><span data-stu-id="ab023-170">To override the suggested recovery plan, you can change the selections in the grid.</span></span> <span data-ttu-id="ab023-171">当取消选择某个早期备份时，将自动取消选择那些需要还原该早期备份才能进行的备份。</span><span class="sxs-lookup"><span data-stu-id="ab023-171">Backups that depend on the restoration of an earlier backup are automatically deselected when the earlier backup is deselected.</span></span>  
  
     <span data-ttu-id="ab023-172">有关“用于还原的备份集”  网格中的列的信息，请参阅[还原数据库（“常规”页）](../../integration-services/general-page-of-integration-services-designers-options.md)。</span><span class="sxs-lookup"><span data-stu-id="ab023-172">For information about the columns in the **Backup sets to restore** grid, see [Restore Database &#40;General Page&#41;](../../integration-services/general-page-of-integration-services-designers-options.md).</span></span>  
  
7.  <span data-ttu-id="ab023-173">若要指定数据库文件的新位置，请选择 **“文件”** 页，然后单击 **“将所有文件重新定位到文件夹”** 。</span><span class="sxs-lookup"><span data-stu-id="ab023-173">To specify the new location of the database files, select the **Files** page, and then click **Relocate all files to folder**.</span></span> <span data-ttu-id="ab023-174">为 **“数据文件的文件夹”** 和 **“日志文件的文件夹”** 提供一个新位置。</span><span class="sxs-lookup"><span data-stu-id="ab023-174">Provide a new location for the **Data file folder** and **Log file folder**.</span></span> <span data-ttu-id="ab023-175">有关该网格的详细信息，请参阅[还原数据库（“文件”页）](restore-database-files-page.md)。</span><span class="sxs-lookup"><span data-stu-id="ab023-175">For more information about this grid, see [Restore Database &#40;Files Page&#41;](restore-database-files-page.md).</span></span>  
  
8.  <span data-ttu-id="ab023-176">在 **“选项”** 页上，根据要求调整选项。</span><span class="sxs-lookup"><span data-stu-id="ab023-176">On the **Options** page, adjust the options if you want.</span></span> <span data-ttu-id="ab023-177">有关这些选项的详细信息，请参阅[还原数据库（“选项”页）](restore-database-options-page.md)。</span><span class="sxs-lookup"><span data-stu-id="ab023-177">For more information about these options, see [Restore Database &#40;Options Page&#41;](restore-database-options-page.md).</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="ab023-178">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ab023-178">Using Transact-SQL</span></span>  
  
#### <a name="to-restore-a-database-to-a-new-location-and-optionally-rename-the-database"></a><span data-ttu-id="ab023-179">将数据库还原到一个新位置并且可以选择重命名该数据库</span><span class="sxs-lookup"><span data-stu-id="ab023-179">To restore a database to a new location, and optionally rename the database</span></span>  
  
1.  <span data-ttu-id="ab023-180">（可选）确定包含要还原的完整数据库备份的备份集中文件的逻辑名称和物理名称。</span><span class="sxs-lookup"><span data-stu-id="ab023-180">Optionally, determine the logical and physical names of the files in the backup set that contains the full database backup that you want to restore.</span></span> <span data-ttu-id="ab023-181">此语句返回备份集内包含的数据库和日志文件的列表。</span><span class="sxs-lookup"><span data-stu-id="ab023-181">This statement returns a list of the database and log files contained in the backup set.</span></span> <span data-ttu-id="ab023-182">基本语法如下：</span><span class="sxs-lookup"><span data-stu-id="ab023-182">The basic syntax is as follows:</span></span>  
  
     <span data-ttu-id="ab023-183">RESTORE FILELISTONLY FROM *<backup_device>* WITH FILE = *backup_set_file_number*</span><span class="sxs-lookup"><span data-stu-id="ab023-183">RESTORE FILELISTONLY FROM *<backup_device>* WITH FILE = *backup_set_file_number*</span></span>  
  
     <span data-ttu-id="ab023-184">其中，*backup_set_file_number* 指示备份在介质集中的位置。</span><span class="sxs-lookup"><span data-stu-id="ab023-184">Here, *backup_set_file_number* indicates the position of the backup in the media set.</span></span> <span data-ttu-id="ab023-185">您可以通过使用 [RESTORE HEADERONLY](/sql/t-sql/statements/restore-statements-headeronly-transact-sql) 语句来获取备份集的位置。</span><span class="sxs-lookup"><span data-stu-id="ab023-185">You can obtain the position of a backup set by using the [RESTORE HEADERONLY](/sql/t-sql/statements/restore-statements-headeronly-transact-sql) statement.</span></span> <span data-ttu-id="ab023-186">有关详细信息，请参阅 [RESTORE 参数 (Transact-SQL)](/sql/t-sql/statements/restore-statements-arguments-transact-sql) 中的“指定备份集”。</span><span class="sxs-lookup"><span data-stu-id="ab023-186">For more information, see "Specifying a Backup Set" in [RESTORE Arguments &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql).</span></span>  
  
     <span data-ttu-id="ab023-187">此语句还支持多个 WITH 选项。</span><span class="sxs-lookup"><span data-stu-id="ab023-187">This statement also supports a number of WITH options.</span></span> <span data-ttu-id="ab023-188">有关详细信息，请参阅 [RESTORE FILELISTONLY (Transact-SQL)](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="ab023-188">For more information, see [RESTORE FILELISTONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql).</span></span>  
  
2.  <span data-ttu-id="ab023-189">使用 [RESTORE DATABASE](/sql/t-sql/statements/restore-statements-transact-sql) 语句还原完整数据库备份。</span><span class="sxs-lookup"><span data-stu-id="ab023-189">Use the [RESTORE DATABASE](/sql/t-sql/statements/restore-statements-transact-sql) statement to restore the full database backup.</span></span> <span data-ttu-id="ab023-190">默认情况下，数据文件和日志文件还原到它们的原位置。</span><span class="sxs-lookup"><span data-stu-id="ab023-190">By default, data and log files are restored to their original locations.</span></span> <span data-ttu-id="ab023-191">若要重新定位数据库，请使用 MOVE 选项重新定位每个数据库文件并避免与现有文件发生冲突。</span><span class="sxs-lookup"><span data-stu-id="ab023-191">To relocate a database, use the MOVE option to relocate each of the database files and to avoid collisions with existing files.</span></span>  
  
     <span data-ttu-id="ab023-192">将数据库还原到新位置并使其具有新名称的基本 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语法如下：</span><span class="sxs-lookup"><span data-stu-id="ab023-192">The basic [!INCLUDE[tsql](../../includes/tsql-md.md)] syntax for restoring the database to a new location and a new name is:</span></span>  
  
     <span data-ttu-id="ab023-193">RESTORE DATABASE *new_database_name*</span><span class="sxs-lookup"><span data-stu-id="ab023-193">RESTORE DATABASE *new_database_name*</span></span>  
  
     <span data-ttu-id="ab023-194">FROM *backup_device* [ ,...*n* ]</span><span class="sxs-lookup"><span data-stu-id="ab023-194">FROM *backup_device* [ ,...*n* ]</span></span>  
  
     <span data-ttu-id="ab023-195">[ WITH</span><span class="sxs-lookup"><span data-stu-id="ab023-195">[ WITH</span></span>  
  
     <span data-ttu-id="ab023-196">{</span><span class="sxs-lookup"><span data-stu-id="ab023-196">{</span></span>  
  
     <span data-ttu-id="ab023-197">[ **RECOVERY** |NORECOVERY</span><span class="sxs-lookup"><span data-stu-id="ab023-197">[ **RECOVERY** | NORECOVERY ]</span></span>  
  
     <span data-ttu-id="ab023-198">[ , ] [ FILE ={ *backup_set_file_number* | @*backup_set_file_number* } ]</span><span class="sxs-lookup"><span data-stu-id="ab023-198">[ , ] [ FILE ={ *backup_set_file_number* | @*backup_set_file_number* } ]</span></span>  
  
     <span data-ttu-id="ab023-199">[ , ] MOVE '*logical_file_name_in_backup*' TO '*operating_system_file_name*' [ ,...*n* ]</span><span class="sxs-lookup"><span data-stu-id="ab023-199">[ , ] MOVE '*logical_file_name_in_backup*' TO '*operating_system_file_name*' [ ,...*n* ]</span></span>  
  
     <span data-ttu-id="ab023-200">}</span><span class="sxs-lookup"><span data-stu-id="ab023-200">}</span></span>  
  
     <span data-ttu-id="ab023-201">;</span><span class="sxs-lookup"><span data-stu-id="ab023-201">;</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ab023-202">准备将数据库重新定位到其他磁盘上时，应当验证是否有足够的可用空间并确定与现有文件之间的任何潜在冲突。</span><span class="sxs-lookup"><span data-stu-id="ab023-202">When preparing to relocate a database on a different disk, you should verify that sufficient space is available and identify any potential collisions with existing files.</span></span> <span data-ttu-id="ab023-203">这涉及到使用 [RESTORE VERIFYONLY](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql) 语句，该语句指定您计划在 RESTORE DATABASE 语句中使用的相同 MOVE 参数。</span><span class="sxs-lookup"><span data-stu-id="ab023-203">This involves using a [RESTORE VERIFYONLY](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql) statement that specifies the same MOVE parameters that you plan to use in your RESTORE DATABASE statement.</span></span>  
  
     <span data-ttu-id="ab023-204">下表介绍了此 RESTORE 语句在将数据库还原到新位置时所涉及的参数。</span><span class="sxs-lookup"><span data-stu-id="ab023-204">The following table describes arguments of this RESTORE statement in terms of restoring a database to a new location.</span></span> <span data-ttu-id="ab023-205">有关这些参数的详细信息，请参阅 [RESTORE (Transact-SQL)](/sql/t-sql/statements/restore-statements-transact-sql)数据库还原到一个新位置并且可以选择重命名该数据库。</span><span class="sxs-lookup"><span data-stu-id="ab023-205">For more information about these arguments, see [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql).</span></span>  
  
     <span data-ttu-id="ab023-206">*new_database_name*</span><span class="sxs-lookup"><span data-stu-id="ab023-206">*new_database_name*</span></span>  
     <span data-ttu-id="ab023-207">数据库的新名称。</span><span class="sxs-lookup"><span data-stu-id="ab023-207">The new name for the database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ab023-208">如果要将数据库还原到其他服务器实例，则可以使用原始数据库名称而不是新名称。</span><span class="sxs-lookup"><span data-stu-id="ab023-208">If you are restoring the database to a different server instance, you can use the original database name instead of a new name.</span></span>  
  
     <span data-ttu-id="ab023-209">*backup_device* [ `,` ...*n* ]</span><span class="sxs-lookup"><span data-stu-id="ab023-209">*backup_device* [ `,`...*n* ]</span></span>  
     <span data-ttu-id="ab023-210">指定包含 1 到 64 个备份设备的逗号分隔的列表，数据库备份将从这些备份设备中还原。</span><span class="sxs-lookup"><span data-stu-id="ab023-210">Specifies a comma-separated list of from 1 to 64 backup devices from which the database backup is to be restored.</span></span> <span data-ttu-id="ab023-211">您可以指定物理备份设备，也可以指定对应的逻辑备份设备（如果已定义）。</span><span class="sxs-lookup"><span data-stu-id="ab023-211">You can specify a physical backup device, or you can specify a corresponding logical backup device, if defined.</span></span> <span data-ttu-id="ab023-212">若要指定物理备份设备，请使用 DISK 或 TAPE 选项：</span><span class="sxs-lookup"><span data-stu-id="ab023-212">To specify a physical backup device, use the DISK or TAPE option:</span></span>  
  
     <span data-ttu-id="ab023-213">{ DISK | TAPE } `=` *physical_backup_device_name*</span><span class="sxs-lookup"><span data-stu-id="ab023-213">{ DISK | TAPE } `=`*physical_backup_device_name*</span></span>  
  
     <span data-ttu-id="ab023-214">有关详细信息，请参阅 [备份设备 (SQL Server)](backup-devices-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="ab023-214">For more information, see [Backup Devices &#40;SQL Server&#41;](backup-devices-sql-server.md).</span></span>  
  
     <span data-ttu-id="ab023-215">{ **RECOVERY** | NORECOVERY }</span><span class="sxs-lookup"><span data-stu-id="ab023-215">{ **RECOVERY** | NORECOVERY }</span></span>  
     <span data-ttu-id="ab023-216">如果数据库使用完整恢复模式，则可能需要在还原该数据库后应用事务日志备份。</span><span class="sxs-lookup"><span data-stu-id="ab023-216">If the database uses the full recovery model, you might need to apply transaction log backups after you restore the database.</span></span> <span data-ttu-id="ab023-217">在这种情况下，请指定 NORECOVERY 选项。</span><span class="sxs-lookup"><span data-stu-id="ab023-217">In this case, specify the NORECOVERY option.</span></span>  
  
     <span data-ttu-id="ab023-218">否则，请使用默认值 RECOVERY 选项。</span><span class="sxs-lookup"><span data-stu-id="ab023-218">Otherwise, use the RECOVERY option, which is the default.</span></span>  
  
     <span data-ttu-id="ab023-219">FILE = { *backup_set_file_number* | @*backup_set_file_number* }</span><span class="sxs-lookup"><span data-stu-id="ab023-219">FILE = { *backup_set_file_number* | @*backup_set_file_number* }</span></span>  
     <span data-ttu-id="ab023-220">标识要还原的备份集。</span><span class="sxs-lookup"><span data-stu-id="ab023-220">Identifies the backup set to be restored.</span></span> <span data-ttu-id="ab023-221">例如， *backup_set_file_number* 为 **1** 指示备份介质中的第一个备份集， *backup_set_file_number* 为 **2** 指示第二个备份集。</span><span class="sxs-lookup"><span data-stu-id="ab023-221">For example, a *backup_set_file_number* of **1** indicates the first backup set on the backup medium and a *backup_set_file_number* of **2** indicates the second backup set.</span></span> <span data-ttu-id="ab023-222">你可以通过使用 *RESTORE HEADERONLY* 语句来获取备份集的 [backup_set_file_number](/sql/t-sql/statements/restore-statements-headeronly-transact-sql) 。</span><span class="sxs-lookup"><span data-stu-id="ab023-222">You can obtain the *backup_set_file_number* of a backup set by using the [RESTORE HEADERONLY](/sql/t-sql/statements/restore-statements-headeronly-transact-sql) statement.</span></span>  
  
     <span data-ttu-id="ab023-223">未指定此选项时，默认为使用备份设备上的第一个备份集。</span><span class="sxs-lookup"><span data-stu-id="ab023-223">When this option is not specified, the default is to use the first backup set on the backup device.</span></span>  
  
     <span data-ttu-id="ab023-224">有关详细信息，请参阅 [RESTORE 参数 (Transact-SQL)](/sql/t-sql/statements/restore-statements-arguments-transact-sql) 中的“指定备份集”。</span><span class="sxs-lookup"><span data-stu-id="ab023-224">For more information, see "Specifying a Backup Set," in [RESTORE Arguments &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql).</span></span>  
  
     <span data-ttu-id="ab023-225">将 **" *`logical_file_name_in_backup`* "** 移动到 **" *`operating_system_file_name`* "** [ `,` .。。*n* ]</span><span class="sxs-lookup"><span data-stu-id="ab023-225">MOVE **'*`logical_file_name_in_backup`*'** TO **'*`operating_system_file_name`*'** [ `,`...*n* ]</span></span>  
     <span data-ttu-id="ab023-226">指定由 *logical_file_name_in_backup* 指定的数据或日志文件将还原到 *operating_system_file_name*指定的位置。</span><span class="sxs-lookup"><span data-stu-id="ab023-226">Specifies that the data or log file specified by *logical_file_name_in_backup* is to be restored to the location specified by *operating_system_file_name*.</span></span> <span data-ttu-id="ab023-227">请为每个要从备份集还原到新位置的逻辑文件指定 MOVE 语句。</span><span class="sxs-lookup"><span data-stu-id="ab023-227">Specify a MOVE statement for every logical file you want to restore from the backup set to a new location.</span></span>  
  
    |<span data-ttu-id="ab023-228">选项</span><span class="sxs-lookup"><span data-stu-id="ab023-228">Option</span></span>|<span data-ttu-id="ab023-229">说明</span><span class="sxs-lookup"><span data-stu-id="ab023-229">Description</span></span>|  
    |------------|-----------------|  
    |<span data-ttu-id="ab023-230">*logical_file_name_in_backup*</span><span class="sxs-lookup"><span data-stu-id="ab023-230">*logical_file_name_in_backup*</span></span>|<span data-ttu-id="ab023-231">指定备份集中数据文件或日志文件的逻辑名称。</span><span class="sxs-lookup"><span data-stu-id="ab023-231">Specifies the logical name of a data or log file in the backup set.</span></span> <span data-ttu-id="ab023-232">创建备份集时，备份集中的数据或日志文件的逻辑文件名与其在数据库中的逻辑名称匹配。</span><span class="sxs-lookup"><span data-stu-id="ab023-232">The logical file name of a data or log file in a backup set matches its logical name in the database when the backup set was created.</span></span><br /><br /> <span data-ttu-id="ab023-233">注意：若要从备份集中获取逻辑文件列表，请使用 [RESTORE FILELISTONLY](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="ab023-233">Note: To obtain a list of the logical files from the backup set, use [RESTORE FILELISTONLY](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql).</span></span>|  
    |<span data-ttu-id="ab023-234">*operating_system_file_name*</span><span class="sxs-lookup"><span data-stu-id="ab023-234">*operating_system_file_name*</span></span>|<span data-ttu-id="ab023-235">指定由 *logical_file_name_in_backup*指定的文件的新位置。</span><span class="sxs-lookup"><span data-stu-id="ab023-235">Specifies a new location for the file specified by *logical_file_name_in_backup*.</span></span> <span data-ttu-id="ab023-236">文件将还原到此位置。</span><span class="sxs-lookup"><span data-stu-id="ab023-236">The file will be restored to this location.</span></span><br /><br /> <span data-ttu-id="ab023-237">或者， *operating_system_file_name* 指定已还原文件的新文件名。</span><span class="sxs-lookup"><span data-stu-id="ab023-237">Optionally, *operating_system_file_name* specifies a new file name for the restored file.</span></span> <span data-ttu-id="ab023-238">如果您在相同服务器实例上创建现有数据库的副本，则此操作是必需的。</span><span class="sxs-lookup"><span data-stu-id="ab023-238">This is necessary if you are creating a copy of an existing database on the same server instance.</span></span>|  
    |<span data-ttu-id="ab023-239">*n*</span><span class="sxs-lookup"><span data-stu-id="ab023-239">*n*</span></span>|<span data-ttu-id="ab023-240">是指示可以指定其他 MOVE 语句的占位符。</span><span class="sxs-lookup"><span data-stu-id="ab023-240">Is a placeholder indicating that you can specify additional MOVE statements.</span></span>|  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="ab023-241">示例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="ab023-241">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="ab023-242">此示例通过还原 `MyAdvWorks` 示例数据库的备份创建名为 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 的一个新数据库，该数据库包括两个文件： [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]_Data 和 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]_Log。</span><span class="sxs-lookup"><span data-stu-id="ab023-242">This example creates a new database named `MyAdvWorks` by restoring a backup of the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database, which includes two files: [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]_Data and [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]_Log.</span></span> <span data-ttu-id="ab023-243">此数据库使用简单恢复模式。</span><span class="sxs-lookup"><span data-stu-id="ab023-243">This database uses the simple recovery model.</span></span> <span data-ttu-id="ab023-244">[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 数据库已经存在于服务器实例上，因此备份中的文件必须还原到一个新位置。</span><span class="sxs-lookup"><span data-stu-id="ab023-244">The [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database already exists on the server instance, so the files in the backup must be restored to a new location.</span></span> <span data-ttu-id="ab023-245">RESTORE FILELISTONLY 语句用于确定数据库中要还原的文件数和名称。</span><span class="sxs-lookup"><span data-stu-id="ab023-245">The RESTORE FILELISTONLY statement is used to determine the number and names of the files in the database being restored.</span></span> <span data-ttu-id="ab023-246">该数据库备份是备份设备上的第一个备份集。</span><span class="sxs-lookup"><span data-stu-id="ab023-246">The database backup is the first backup set on the backup device.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ab023-247">备份和还原事务日志的示例（包括时点还原）使用从 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 创建的 `MyAdvWorks_FullRM` 数据库的方式与下面的 `MyAdvWorks` 示例相同。</span><span class="sxs-lookup"><span data-stu-id="ab023-247">The examples of backing up and restoring the transaction log, including point-in-time restores, use the `MyAdvWorks_FullRM` database that is created from [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] just like the following `MyAdvWorks` example.</span></span> <span data-ttu-id="ab023-248">但是，必须通过使用以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句对最终生成的 `MyAdvWorks_FullRM` 数据库进行更改，以便使用完整恢复模式：ALTER DATABASE <database_name> SET RECOVERY FULL。</span><span class="sxs-lookup"><span data-stu-id="ab023-248">However, the resulting `MyAdvWorks_FullRM` database must be changed to use the full recovery model by using the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement: ALTER DATABASE <database_name> SET RECOVERY FULL.</span></span>  
  
```sql  
USE master;  
GO  
-- First determine the number and names of the files in the backup.  
-- AdventureWorks2012_Backup is the name of the backup device.  
RESTORE FILELISTONLY  
   FROM AdventureWorks2012_Backup;  
-- Restore the files for MyAdvWorks.  
RESTORE DATABASE MyAdvWorks  
   FROM AdventureWorks2012_Backup  
   WITH RECOVERY,  
   MOVE 'AdventureWorks2012_Data' TO 'D:\MyData\MyAdvWorks_Data.mdf',   
   MOVE 'AdventureWorks2012_Log' TO 'F:\MyLog\MyAdvWorks_Log.ldf';  
GO  
  
```  
  
 <span data-ttu-id="ab023-249">有关如何创建 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 数据库的完整数据库备份的示例，请参阅 [创建完整数据库备份 (SQL Server)](create-a-full-database-backup-sql-server.md)数据库还原到一个新位置并且可以选择重命名该数据库。</span><span class="sxs-lookup"><span data-stu-id="ab023-249">For an example of how to create a full database backup of the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database, see [Create a Full Database Backup &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="ab023-250">相关任务</span><span class="sxs-lookup"><span data-stu-id="ab023-250">Related Tasks</span></span>  
  
-   [<span data-ttu-id="ab023-251">创建完整数据库备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ab023-251">Create a Full Database Backup &#40;SQL Server&#41;</span></span>](create-a-full-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="ab023-252">还原数据库备份 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="ab023-252">Restore a Database Backup &#40;SQL Server Management Studio&#41;</span></span>](restore-a-database-backup-using-ssms.md)  
  
-   [<span data-ttu-id="ab023-253">备份事务日志 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ab023-253">Back Up a Transaction Log &#40;SQL Server&#41;</span></span>](back-up-a-transaction-log-sql-server.md)  
  
-   [<span data-ttu-id="ab023-254">还原事务日志备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ab023-254">Restore a Transaction Log Backup &#40;SQL Server&#41;</span></span>](restore-a-transaction-log-backup-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="ab023-255">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ab023-255">See Also</span></span>  
 <span data-ttu-id="ab023-256">[当数据库在其他服务器实例上可用时管理元数据 (SQL Server)](../databases/manage-metadata-when-making-a-database-available-on-another-server.md) </span><span class="sxs-lookup"><span data-stu-id="ab023-256">[Manage Metadata When Making a Database Available on Another Server Instance &#40;SQL Server&#41;](../databases/manage-metadata-when-making-a-database-available-on-another-server.md) </span></span>  
 <span data-ttu-id="ab023-257">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ab023-257">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 [<span data-ttu-id="ab023-258">通过备份和还原来复制数据库</span><span class="sxs-lookup"><span data-stu-id="ab023-258">Copy Databases with Backup and Restore</span></span>](../databases/copy-databases-with-backup-and-restore.md)  
  
  
