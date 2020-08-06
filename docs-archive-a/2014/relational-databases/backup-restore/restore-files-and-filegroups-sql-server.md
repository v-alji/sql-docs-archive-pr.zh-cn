---
title: 还原文件和文件组 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.restorefilesandfilegrps.general.f1
- sql12.swb.restorefilesandfilegrps.options.f1
- sql12.swb.bselectfilegrpsfiles.f1
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], restoring files and filegroups
- restoring [SQL Server], files
ms.assetid: 72603b21-3065-4b56-8b01-11b707911b05
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d2576f1326cb50fa197b1623aaa1326d70137823
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689445"
---
# <a name="restore-files-and-filegroups-sql-server"></a><span data-ttu-id="763c0-102">还原文件和文件组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="763c0-102">Restore Files and Filegroups (SQL Server)</span></span>
  <span data-ttu-id="763c0-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中还原文件和文件组。</span><span class="sxs-lookup"><span data-stu-id="763c0-103">This topic describes how to restore files and filegroups in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="763c0-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="763c0-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="763c0-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="763c0-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="763c0-106">限制和局限</span><span class="sxs-lookup"><span data-stu-id="763c0-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
-   [<span data-ttu-id="763c0-107">安全性</span><span class="sxs-lookup"><span data-stu-id="763c0-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="763c0-108">**若要还原文件和文件组，请使用：**</span><span class="sxs-lookup"><span data-stu-id="763c0-108">**To restore files and filegroups, using:**</span></span>  
  
     [<span data-ttu-id="763c0-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="763c0-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="763c0-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="763c0-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="763c0-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="763c0-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="763c0-112">限制和局限</span><span class="sxs-lookup"><span data-stu-id="763c0-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="763c0-113">还原文件和文件组的系统管理员必须是唯一一位当前使用要还原的数据库的人。</span><span class="sxs-lookup"><span data-stu-id="763c0-113">The system administrator restoring the files and filegroups must be the only person currently using the database to be restored.</span></span>  
  
-   <span data-ttu-id="763c0-114">不允许在显式或隐式事务中使用 RESTORE。</span><span class="sxs-lookup"><span data-stu-id="763c0-114">RESTORE is not allowed in an explicit or implicit transaction.</span></span>  
  
-   <span data-ttu-id="763c0-115">在简单恢复模式下，文件必须属于只读文件组。</span><span class="sxs-lookup"><span data-stu-id="763c0-115">Under the simple recovery model, the file must belong to a read-only filegroup.</span></span>  
  
-   <span data-ttu-id="763c0-116">在完整恢复模式或大容量日志恢复模式下，必须先备份活动事务日志（称为日志尾部），然后才能还原文件。</span><span class="sxs-lookup"><span data-stu-id="763c0-116">Under the full or bulk-logged recovery model, before you can restore files, you must back up the active transaction log (known as the tail of the log).</span></span> <span data-ttu-id="763c0-117">有关详细信息，请参阅 [备份事务日志 (SQL Server)](back-up-a-transaction-log-sql-server.md)数据库还原到一个新位置并且可以选择重命名该数据库。</span><span class="sxs-lookup"><span data-stu-id="763c0-117">For more information, see [Back Up a Transaction Log &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md).</span></span>  
  
-   <span data-ttu-id="763c0-118">若要还原已加密的数据库，您必须有权访问用于对数据库进行加密的证书或非对称密钥。</span><span class="sxs-lookup"><span data-stu-id="763c0-118">To restore a database that is encrypted, you must have access to the certificate or asymmetric key that was used to encrypt the database.</span></span> <span data-ttu-id="763c0-119">如果没有证书或非对称密钥，数据库将无法还原。</span><span class="sxs-lookup"><span data-stu-id="763c0-119">Without the certificate or asymmetric key, the database cannot be restored.</span></span> <span data-ttu-id="763c0-120">因此，只要需要该备份，就必须保留用于对数据库加密密钥进行加密的证书。</span><span class="sxs-lookup"><span data-stu-id="763c0-120">As a result, the certificate that is used to encrypt the database encryption key must be retained as long as the backup is needed.</span></span> <span data-ttu-id="763c0-121">有关详细信息，请参阅 [SQL Server Certificates and Asymmetric Keys](../security/sql-server-certificates-and-asymmetric-keys.md)。</span><span class="sxs-lookup"><span data-stu-id="763c0-121">For more information, see [SQL Server Certificates and Asymmetric Keys](../security/sql-server-certificates-and-asymmetric-keys.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="763c0-122">Security</span><span class="sxs-lookup"><span data-stu-id="763c0-122">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="763c0-123">权限</span><span class="sxs-lookup"><span data-stu-id="763c0-123">Permissions</span></span>  
 <span data-ttu-id="763c0-124">如果不存在要还原的数据库，则用户必须有 CREATE DATABASE 权限才能执行 RESTORE。</span><span class="sxs-lookup"><span data-stu-id="763c0-124">If the database being restored does not exist, the user must have CREATE DATABASE permissions to be able to execute RESTORE.</span></span> <span data-ttu-id="763c0-125">如果数据库存在，则 RESTORE 权限默认授予 **sysadmin** 和 **dbcreator** 固定服务器角色成员以及数据库的所有者 (**dbo**)（对于 FROM DATABASE_SNAPSHOT 选项，数据库始终存在）。</span><span class="sxs-lookup"><span data-stu-id="763c0-125">If the database exists, RESTORE permissions default to members of the **sysadmin** and **dbcreator** fixed server roles and the owner (**dbo**) of the database (for the FROM DATABASE_SNAPSHOT option, the database always exists).</span></span>  
  
 <span data-ttu-id="763c0-126">RESTORE 权限被授予那些成员身份信息始终可由服务器使用的角色。</span><span class="sxs-lookup"><span data-stu-id="763c0-126">RESTORE permissions are given to roles in which membership information is always readily available to the server.</span></span> <span data-ttu-id="763c0-127">因为只有在固定数据库可以访问且没有损坏时（在执行 RESTORE 时并不会总是这样）才能检查固定数据库角色成员身份，所以 **db_owner** 固定数据库角色成员没有 RESTORE 权限。</span><span class="sxs-lookup"><span data-stu-id="763c0-127">Because fixed database role membership can be checked only when the database is accessible and undamaged, which is not always the case when RESTORE is executed, members of the **db_owner** fixed database role do not have RESTORE permissions.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="763c0-128">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="763c0-128">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-restore-files-and-filegroups"></a><span data-ttu-id="763c0-129">还原文件和文件组</span><span class="sxs-lookup"><span data-stu-id="763c0-129">To restore files and filegroups</span></span>  
  
1.  <span data-ttu-id="763c0-130">连接到相应的 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]实例之后，在对象资源管理器中，单击服务器名称以展开服务器树。</span><span class="sxs-lookup"><span data-stu-id="763c0-130">After you connect to the appropriate instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="763c0-131">展开 **“数据库”** 。</span><span class="sxs-lookup"><span data-stu-id="763c0-131">Expand **Databases**.</span></span> <span data-ttu-id="763c0-132"> 根据具体的数据库，选择一个用户数据库，或展开“系统数据库”并选择一个系统数据库。</span><span class="sxs-lookup"><span data-stu-id="763c0-132">Depending on the database, either select a user database or expand **System Databases**, and then select a system database.</span></span>  
  
3.  <span data-ttu-id="763c0-133">右键单击数据库，指向“任务”  ，再单击“还原”  。</span><span class="sxs-lookup"><span data-stu-id="763c0-133">Right-click the database, point to **Tasks**, and then click **Restore**.</span></span>  
  
4.  <span data-ttu-id="763c0-134">单击 **“文件和文件组”** ，将打开 **“还原文件和文件组”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="763c0-134">Click **Files and Filegroups**, which opens the **Restore Files and Filegroups** dialog box.</span></span>  
  
5.  <span data-ttu-id="763c0-135">在 **“常规”** 页上的 **目标数据库** 列表框中，输入要还原的数据库。</span><span class="sxs-lookup"><span data-stu-id="763c0-135">On the **General** page, in the **To database** list box, enter the database to restore.</span></span> <span data-ttu-id="763c0-136">您可以输入新的数据库，也可以从下拉列表中选择现有的数据库。</span><span class="sxs-lookup"><span data-stu-id="763c0-136">You can enter a new database or choose an existing database from the drop-down list.</span></span> <span data-ttu-id="763c0-137">该列表包含了服务器上除系统数据库 **master** 和 **tempdb**之外的所有数据库。</span><span class="sxs-lookup"><span data-stu-id="763c0-137">The list includes all databases on the server, excluding the system databases **master** and **tempdb**.</span></span>  
  
6.  <span data-ttu-id="763c0-138">若要指定要还原的备份集的源和位置，请单击以下选项之一：</span><span class="sxs-lookup"><span data-stu-id="763c0-138">To specify the source and location of the backup sets to restore, click one of the following options:</span></span>  
  
    -   <span data-ttu-id="763c0-139">**源数据库**</span><span class="sxs-lookup"><span data-stu-id="763c0-139">**From database**</span></span>  
  
         <span data-ttu-id="763c0-140">在列表框中输入数据库名称。</span><span class="sxs-lookup"><span data-stu-id="763c0-140">Enter a database name in the list box.</span></span> <span data-ttu-id="763c0-141">此列表仅包含根据 **msdb** 备份历史记录已进行过备份的数据库。</span><span class="sxs-lookup"><span data-stu-id="763c0-141">This list contains only databases that have been backed up according to the **msdb** backup history.</span></span>  
  
    -   <span data-ttu-id="763c0-142">**源设备**</span><span class="sxs-lookup"><span data-stu-id="763c0-142">**From device**</span></span>  
  
         <span data-ttu-id="763c0-143">单击浏览按钮。</span><span class="sxs-lookup"><span data-stu-id="763c0-143">Click the browse button.</span></span> <span data-ttu-id="763c0-144">在 **“指定备份设备”** 对话框的 **“备份介质类型”** 列表框中，选择列出的设备类型之一。</span><span class="sxs-lookup"><span data-stu-id="763c0-144">In the **Specify backup devices** dialog box, select one of the listed device types in the **Backup media type** list box.</span></span> <span data-ttu-id="763c0-145">若要为 **“备份介质”** 列表框选择一个或多个设备，请单击 **“添加”** 。</span><span class="sxs-lookup"><span data-stu-id="763c0-145">To select one or more devices for the **Backup media** list box, click **Add**.</span></span>  
  
         <span data-ttu-id="763c0-146">将所需设备添加到 **“备份介质”** 列表框后，单击 **“确定”** 返回到 **“常规”** 页。</span><span class="sxs-lookup"><span data-stu-id="763c0-146">After you add the devices you want to the **Backup media** list box, click **OK** to return to the **General** page.</span></span>  
  
7.  <span data-ttu-id="763c0-147">在 **“选择用于还原的备份集”** 网格中，选择用于还原的备份。</span><span class="sxs-lookup"><span data-stu-id="763c0-147">In the **Select the backup sets to restore** grid, select the backups to restore.</span></span> <span data-ttu-id="763c0-148">此网格将显示对于指定位置可用的备份。</span><span class="sxs-lookup"><span data-stu-id="763c0-148">This grid displays the backups available for the specified location.</span></span> <span data-ttu-id="763c0-149">默认情况下，系统会推荐一个恢复计划。</span><span class="sxs-lookup"><span data-stu-id="763c0-149">By default, a recovery plan is suggested.</span></span> <span data-ttu-id="763c0-150">若要覆盖建议的恢复计划，可以更改网格中的选择。</span><span class="sxs-lookup"><span data-stu-id="763c0-150">To override the suggested recovery plan, you can change the selections in the grid.</span></span> <span data-ttu-id="763c0-151">任何依赖于已取消选择备份的备份，也将被自动取消选择。</span><span class="sxs-lookup"><span data-stu-id="763c0-151">Any backups that depend on a deselected backup are deselected automatically.</span></span>  
  
    |<span data-ttu-id="763c0-152">列标题</span><span class="sxs-lookup"><span data-stu-id="763c0-152">Column head</span></span>|<span data-ttu-id="763c0-153">值</span><span class="sxs-lookup"><span data-stu-id="763c0-153">Values</span></span>|  
    |-----------------|------------|  
    |<span data-ttu-id="763c0-154">**还原**</span><span class="sxs-lookup"><span data-stu-id="763c0-154">**Restore**</span></span>|<span data-ttu-id="763c0-155">选中的复选框指示要还原的备份集。</span><span class="sxs-lookup"><span data-stu-id="763c0-155">The selected check boxes indicate the backup sets to be restored.</span></span>|  
    |<span data-ttu-id="763c0-156">**名称**</span><span class="sxs-lookup"><span data-stu-id="763c0-156">**Name**</span></span>|<span data-ttu-id="763c0-157">备份集的名称。</span><span class="sxs-lookup"><span data-stu-id="763c0-157">The name of the backup set.</span></span>|  
    |<span data-ttu-id="763c0-158">**文件类型**</span><span class="sxs-lookup"><span data-stu-id="763c0-158">**File Type**</span></span>|<span data-ttu-id="763c0-159">指定备份中数据的类型：数据、日志，或 Filestream 数据    。</span><span class="sxs-lookup"><span data-stu-id="763c0-159">Specifies the type of data in the backup: **Data**, **Log**, or **Filestream Data**.</span></span> <span data-ttu-id="763c0-160">包含在表中的数据备份在 **“数据”** 文件中。</span><span class="sxs-lookup"><span data-stu-id="763c0-160">Data that is contained in tables is in **Data** files.</span></span> <span data-ttu-id="763c0-161">事务日志数据备份在 **“日志”** 文件中。</span><span class="sxs-lookup"><span data-stu-id="763c0-161">Transaction log data is in **Log** files.</span></span> <span data-ttu-id="763c0-162">存储在文件系统上的二进制大型对象 (BLOB) 数据备份在 **Filestream 数据** 文件中。</span><span class="sxs-lookup"><span data-stu-id="763c0-162">Binary large object (BLOB) data that is stored on the file system is in **Filestream Data** files.</span></span>|  
    |<span data-ttu-id="763c0-163">类型 </span><span class="sxs-lookup"><span data-stu-id="763c0-163">**Type**</span></span>|<span data-ttu-id="763c0-164">执行的备份类型：“完整”、“差异”或“事务日志”  。</span><span class="sxs-lookup"><span data-stu-id="763c0-164">The type of backup performed: **Full**, **Differential**, or **Transaction Log**.</span></span>|  
    |<span data-ttu-id="763c0-165">**Server**</span><span class="sxs-lookup"><span data-stu-id="763c0-165">**Server**</span></span>|<span data-ttu-id="763c0-166">执行备份操作的数据库引擎实例的名称。</span><span class="sxs-lookup"><span data-stu-id="763c0-166">The name of the Database-Engine instance that performed the backup operation.</span></span>|  
    |<span data-ttu-id="763c0-167">**文件逻辑名称**</span><span class="sxs-lookup"><span data-stu-id="763c0-167">**File Logical Name**</span></span>|<span data-ttu-id="763c0-168">文件的逻辑名称。</span><span class="sxs-lookup"><span data-stu-id="763c0-168">The logical name of the file.</span></span>|  
    |<span data-ttu-id="763c0-169">**Database**</span><span class="sxs-lookup"><span data-stu-id="763c0-169">**Database**</span></span>|<span data-ttu-id="763c0-170">备份操作中涉及的数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="763c0-170">The name of the database involved in the backup operation.</span></span>|  
    |<span data-ttu-id="763c0-171">**开始日期**</span><span class="sxs-lookup"><span data-stu-id="763c0-171">**Start Date**</span></span>|<span data-ttu-id="763c0-172">备份操作开始的日期和时间，按客户端的区域设置显示。</span><span class="sxs-lookup"><span data-stu-id="763c0-172">The date and time when the backup operation began, presented in the regional setting of the client.</span></span>|  
    |<span data-ttu-id="763c0-173">**完成日期**</span><span class="sxs-lookup"><span data-stu-id="763c0-173">**Finish Date**</span></span>|<span data-ttu-id="763c0-174">备份操作完成的日期和时间，按客户端的区域设置显示。</span><span class="sxs-lookup"><span data-stu-id="763c0-174">The date and time when the backup operation finished, presented in the regional setting of the client.</span></span>|  
    |<span data-ttu-id="763c0-175">**大小**</span><span class="sxs-lookup"><span data-stu-id="763c0-175">**Size**</span></span>|<span data-ttu-id="763c0-176">备份集的大小（字节）。</span><span class="sxs-lookup"><span data-stu-id="763c0-176">The size of the backup set in bytes.</span></span>|  
    |<span data-ttu-id="763c0-177">**用户名**</span><span class="sxs-lookup"><span data-stu-id="763c0-177">**User Name**</span></span>|<span data-ttu-id="763c0-178">执行备份操作的用户的名称。</span><span class="sxs-lookup"><span data-stu-id="763c0-178">The name of the user who performed the backup operation.</span></span>|  
  
8.  <span data-ttu-id="763c0-179">若要查看或选择高级选项，请在 **“选择页”** 窗格中单击 **“选项”** 。</span><span class="sxs-lookup"><span data-stu-id="763c0-179">To view or select the advanced options, click **Options** in the **Select a page pane**.</span></span>  
  
9. <span data-ttu-id="763c0-180">在 **“还原选项”** 面板中，可以根据您的实际情况选择下列任意选项。</span><span class="sxs-lookup"><span data-stu-id="763c0-180">In the **Restore options** panel, you can choose any of the following options, if appropriate for your situation.</span></span>  
  
     <span data-ttu-id="763c0-181">**还原为文件组**</span><span class="sxs-lookup"><span data-stu-id="763c0-181">**Restore as filegroup**</span></span>  
     <span data-ttu-id="763c0-182">指示要还原整个文件组。</span><span class="sxs-lookup"><span data-stu-id="763c0-182">Indicates that an entire filegroup is being restored.</span></span>  
  
     <span data-ttu-id="763c0-183">**覆盖现有数据库**</span><span class="sxs-lookup"><span data-stu-id="763c0-183">**Overwrite the existing database**</span></span>  
     <span data-ttu-id="763c0-184">指定还原操作应覆盖所有现有数据库及其相关文件，即使已存在同名的其他数据库或文件。</span><span class="sxs-lookup"><span data-stu-id="763c0-184">Specifies that the restore operation should overwrite any existing databases and their related files, even if another database or file already exists with the same name.</span></span>  
  
     <span data-ttu-id="763c0-185">选择此选项等效于在 [!INCLUDE[tsql](../../includes/tsql-md.md)] RESTORE 语句中使用 REPLACE 选项。</span><span class="sxs-lookup"><span data-stu-id="763c0-185">Selecting this option is equivalent to using the REPLACE option in a [!INCLUDE[tsql](../../includes/tsql-md.md)] RESTORE statement.</span></span>  
  
     <span data-ttu-id="763c0-186">**还原每个备份之前进行提示**</span><span class="sxs-lookup"><span data-stu-id="763c0-186">**Prompt before restoring each backup**</span></span>  
     <span data-ttu-id="763c0-187">在还原每个备份设置前要求您进行确认。</span><span class="sxs-lookup"><span data-stu-id="763c0-187">Asks you for confirmation before restoring each backup set.</span></span>  
  
     <span data-ttu-id="763c0-188">如果对于不同介质集必须更换磁带，例如在服务器具有一个磁带设备时，此选项非常有用。</span><span class="sxs-lookup"><span data-stu-id="763c0-188">This option is particularly useful where you must swap tapes for different media sets, such as when the server has one tape device.</span></span>  
  
     <span data-ttu-id="763c0-189">**限制访问还原的数据库**</span><span class="sxs-lookup"><span data-stu-id="763c0-189">**Restrict access to the restored database**</span></span>  
     <span data-ttu-id="763c0-190">使还原的数据库仅供 **db_owner**、 **dbcreator**或 **sysadmin**的成员使用。</span><span class="sxs-lookup"><span data-stu-id="763c0-190">Makes the restored database available only to the members of **db_owner**, **dbcreator**, or **sysadmin**.</span></span>  
  
     <span data-ttu-id="763c0-191">选择此选项等效于在 [!INCLUDE[tsql](../../includes/tsql-md.md)] RESTORE 语句中使用 RESTRICTED_USER 选项。</span><span class="sxs-lookup"><span data-stu-id="763c0-191">Selecting this option is synonymous to using the RESTRICTED_USER option in a [!INCLUDE[tsql](../../includes/tsql-md.md)] RESTORE statement.</span></span>  
  
10. <span data-ttu-id="763c0-192">还可以通过在 **“将数据库文件还原为”** 网格中指定每个文件的新还原目标，从而将数据库还原到新的位置。</span><span class="sxs-lookup"><span data-stu-id="763c0-192">Optionally, you can restore the database to a new location by specifying a new restore destination for each file in the **Restore database files as** grid.</span></span>  
  
    |<span data-ttu-id="763c0-193">列标题</span><span class="sxs-lookup"><span data-stu-id="763c0-193">Column head</span></span>|<span data-ttu-id="763c0-194">值</span><span class="sxs-lookup"><span data-stu-id="763c0-194">Values</span></span>|  
    |-----------------|------------|  
    |<span data-ttu-id="763c0-195">**原始文件名**</span><span class="sxs-lookup"><span data-stu-id="763c0-195">**Original File Name**</span></span>|<span data-ttu-id="763c0-196">源备份文件的完整路径。</span><span class="sxs-lookup"><span data-stu-id="763c0-196">The full path of a source backup file.</span></span>|  
    |<span data-ttu-id="763c0-197">**文件类型**</span><span class="sxs-lookup"><span data-stu-id="763c0-197">**File Type**</span></span>|<span data-ttu-id="763c0-198">指定备份中数据的类型：数据、日志，或 Filestream 数据    。</span><span class="sxs-lookup"><span data-stu-id="763c0-198">Specifies the type of data in the backup: **Data**, **Log**, or **Filestream Data**.</span></span> <span data-ttu-id="763c0-199">包含在表中的数据备份在 **“数据”** 文件中。</span><span class="sxs-lookup"><span data-stu-id="763c0-199">Data that is contained in tables is in **Data** files.</span></span> <span data-ttu-id="763c0-200">事务日志数据备份在 **“日志”** 文件中。</span><span class="sxs-lookup"><span data-stu-id="763c0-200">Transaction log data is in **Log** files.</span></span> <span data-ttu-id="763c0-201">存储在文件系统上的二进制大型对象 (BLOB) 数据备份在 **Filestream 数据** 文件中。</span><span class="sxs-lookup"><span data-stu-id="763c0-201">Binary large object (BLOB) data that is stored on the file system is in **Filestream Data** files.</span></span>|  
    |<span data-ttu-id="763c0-202">**还原为**</span><span class="sxs-lookup"><span data-stu-id="763c0-202">**Restore As**</span></span>|<span data-ttu-id="763c0-203">要还原的数据库文件的完整路径。</span><span class="sxs-lookup"><span data-stu-id="763c0-203">The full path of the database file to be restored.</span></span> <span data-ttu-id="763c0-204">若要指定新的还原文件，请单击文本框，再编辑建议的路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="763c0-204">To specify a new restore file, click the text box and edit the suggested path and file name.</span></span> <span data-ttu-id="763c0-205">更改 **“还原为”** 列中的路径或文件名等效于在 [!INCLUDE[tsql](../../includes/tsql-md.md)] RESTORE 语句中使用 MOVE 选项。</span><span class="sxs-lookup"><span data-stu-id="763c0-205">Changing the path or file name in the **Restore As** column is equivalent to using the MOVE option in a [!INCLUDE[tsql](../../includes/tsql-md.md)] RESTORE statement.</span></span>|  
  
11. <span data-ttu-id="763c0-206">**“恢复状态”** 面板确定还原操作之后的数据库状态。</span><span class="sxs-lookup"><span data-stu-id="763c0-206">The **Recovery state** panel determines the state of the database after the restore operation.</span></span>  
  
     <span data-ttu-id="763c0-207">**回退未提交的事务，使数据库处于可以使用的状态。无法还原其他事务日志。(RESTORE WITH RECOVERY)**</span><span class="sxs-lookup"><span data-stu-id="763c0-207">**Leave the database ready for use by rolling back the uncommitted transactions. Additional transaction logs cannot be restored. (RESTORE WITH RECOVERY)**</span></span>  
     <span data-ttu-id="763c0-208">恢复数据库。</span><span class="sxs-lookup"><span data-stu-id="763c0-208">Recovers the database.</span></span> <span data-ttu-id="763c0-209">此选项为默认行为。</span><span class="sxs-lookup"><span data-stu-id="763c0-209">This is the default behavior.</span></span> <span data-ttu-id="763c0-210">请仅在要还原所有必要的备份时选择此选项。</span><span class="sxs-lookup"><span data-stu-id="763c0-210">Choose this option only if you are restoring all of the necessary backups now.</span></span> <span data-ttu-id="763c0-211">此选项等效于在 [!INCLUDE[tsql](../../includes/tsql-md.md)] RESTORE 语句中指定 WITH RECOVERY。</span><span class="sxs-lookup"><span data-stu-id="763c0-211">This option is equivalent to specifying WITH RECOVERY in a [!INCLUDE[tsql](../../includes/tsql-md.md)] RESTORE statement.</span></span>  
  
     <span data-ttu-id="763c0-212">**不对数据库执行任何操作，不回退未提交的事务。可以还原其他事务日志。(RESTORE WITH NORECOVERY)**</span><span class="sxs-lookup"><span data-stu-id="763c0-212">**Leave the database non-operational, and don't roll back the uncommitted transactions. Additional transaction logs can be restored. (RESTORE WITH NORECOVERY)**</span></span>  
     <span data-ttu-id="763c0-213">使数据库处于还原状态。</span><span class="sxs-lookup"><span data-stu-id="763c0-213">Leaves the database in the restoring state.</span></span> <span data-ttu-id="763c0-214">若要恢复数据库，则将需要使用前面的 RESTORE WITH RECOVERY 选项（请参阅上面的内容）来执行另一个还原操作。</span><span class="sxs-lookup"><span data-stu-id="763c0-214">To recover the database, you will need to perform another restore using the preceding RESTORE WITH RECOVERY option (see above).</span></span> <span data-ttu-id="763c0-215">此选项等效于在 [!INCLUDE[tsql](../../includes/tsql-md.md)] RESTORE 语句中指定 WITH NORECOVERY。</span><span class="sxs-lookup"><span data-stu-id="763c0-215">This option is equivalent to specifying WITH NORECOVERY in a [!INCLUDE[tsql](../../includes/tsql-md.md)] RESTORE statement.</span></span>  
  
     <span data-ttu-id="763c0-216">如果选择此选项， **“保留复制设置”** 选项将不可用。</span><span class="sxs-lookup"><span data-stu-id="763c0-216">If you select this option, the **Preserve replication settings** option is unavailable.</span></span>  
  
     <span data-ttu-id="763c0-217">**使数据库处于只读模式。回滚未提交的事务，但将回滚操作保存在一个文件中，以便可使恢复效果逆转。(RESTORE WITH STANDBY)**</span><span class="sxs-lookup"><span data-stu-id="763c0-217">**Leave the database in read-only mode. Roll back the uncommitted transactions, but save the rollback operation in a file so the recovery effects can be undone. (RESTORE WITH STANDBY)**</span></span>  
     <span data-ttu-id="763c0-218">使数据库处于备用状态。</span><span class="sxs-lookup"><span data-stu-id="763c0-218">Leaves the database in a standby state.</span></span> <span data-ttu-id="763c0-219">此选项等效于在 [!INCLUDE[tsql](../../includes/tsql-md.md)] RESTORE 语句中指定 WITH STANDBY。</span><span class="sxs-lookup"><span data-stu-id="763c0-219">This option is equivalent to specifying WITH STANDBY in a [!INCLUDE[tsql](../../includes/tsql-md.md)] RESTORE statement.</span></span>  
  
     <span data-ttu-id="763c0-220">选择此选项需要您指定一个备用文件。</span><span class="sxs-lookup"><span data-stu-id="763c0-220">Choosing this option requires that you specify a standby file.</span></span>  
  
     <span data-ttu-id="763c0-221">**回滚撤消文件**</span><span class="sxs-lookup"><span data-stu-id="763c0-221">**Rollback undo file**</span></span>  
     <span data-ttu-id="763c0-222">在“回滚撤消文件”  文本框中指定备用文件名称。</span><span class="sxs-lookup"><span data-stu-id="763c0-222">Specify a standby file name in the **Rollback undo file** text box.</span></span> <span data-ttu-id="763c0-223">如果使数据库处于只读模式 (RESTORE WITH STANDBY)，则必须选中此选项。</span><span class="sxs-lookup"><span data-stu-id="763c0-223">This option is required if you leave the database in read-only mode (RESTORE WITH STANDBY).</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="763c0-224">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="763c0-224">Using Transact-SQL</span></span>  
  
#### <a name="to-restore-files-and-filegroups"></a><span data-ttu-id="763c0-225">还原文件和文件组</span><span class="sxs-lookup"><span data-stu-id="763c0-225">To restore files and filegroups</span></span>  
  
1.  <span data-ttu-id="763c0-226">执行 RESTORE DATABASE 语句以还原文件和文件组备份，同时指定下列内容：</span><span class="sxs-lookup"><span data-stu-id="763c0-226">Execute the RESTORE DATABASE statement to restore the file and filegroup backup, specifying:</span></span>  
  
    -   <span data-ttu-id="763c0-227">要还原的数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="763c0-227">The name of the database to restore.</span></span>  
  
    -   <span data-ttu-id="763c0-228">从中还原完整数据库备份的备份设备。</span><span class="sxs-lookup"><span data-stu-id="763c0-228">The backup device from where the full database backup will be restored.</span></span>  
  
    -   <span data-ttu-id="763c0-229">每个要还原文件的 FILE 子句。</span><span class="sxs-lookup"><span data-stu-id="763c0-229">The FILE clause for each file to restore.</span></span>  
  
    -   <span data-ttu-id="763c0-230">每个要还原文件组的 FILEGROUP 子句。</span><span class="sxs-lookup"><span data-stu-id="763c0-230">The FILEGROUP clause for each filegroup to restore.</span></span>  
  
    -   <span data-ttu-id="763c0-231">NORECOVERY 子句。</span><span class="sxs-lookup"><span data-stu-id="763c0-231">The NORECOVERY clause.</span></span> <span data-ttu-id="763c0-232">如果在创建备份之后没有对文件进行修改，则指定 RECOVERY 子句。</span><span class="sxs-lookup"><span data-stu-id="763c0-232">If the files have not been modified after the backup was created, specify the RECOVERY clause.</span></span>  
  
2.  <span data-ttu-id="763c0-233">如果在创建文件备份之后对文件进行了修改，则执行 RESTORE LOG 语句以应用事务日志备份，同时指定下列内容：</span><span class="sxs-lookup"><span data-stu-id="763c0-233">If the files have been modified after the file backup was created, execute the RESTORE LOG statement to apply the transaction log backup, specifying:</span></span>  
  
    -   <span data-ttu-id="763c0-234">事务日志将应用到的数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="763c0-234">The name of the database to which the transaction log will be applied.</span></span>  
  
    -   <span data-ttu-id="763c0-235">要还原的事务日志备份的备份设备。</span><span class="sxs-lookup"><span data-stu-id="763c0-235">The backup device from where the transaction log backup will be restored.</span></span>  
  
    -   <span data-ttu-id="763c0-236">如果在应用当前事务日志备份之后还要应用其他事务日志备份，则指定 NORECOVERY 子句；否则指定 RECOVERY 子句。</span><span class="sxs-lookup"><span data-stu-id="763c0-236">The NORECOVERY clause if you have another transaction log backup to apply after the current one; otherwise, specify the RECOVERY clause.</span></span>  
  
         <span data-ttu-id="763c0-237">事务日志备份（如果可用）必须包括截止到日志结尾处的文件和文件组备份（除非已还原所有数据库文件）。</span><span class="sxs-lookup"><span data-stu-id="763c0-237">The transaction log backups, if applied, must cover the time when the files and filegroups were backed up until the end of log (unless ALL database files are restored).</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="763c0-238">示例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="763c0-238">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="763c0-239">以下示例将还原 `MyDatabase` 数据库的文件和文件组。</span><span class="sxs-lookup"><span data-stu-id="763c0-239">This example restores the files and filegroups for the `MyDatabase` database.</span></span> <span data-ttu-id="763c0-240">为了将数据库还原到当前时间，将应用两个事务日志。</span><span class="sxs-lookup"><span data-stu-id="763c0-240">To restore the database to the current time, two transaction logs are applied.</span></span>  
  
```sql  
USE master;  
GO  
-- Restore the files and filesgroups for MyDatabase.  
RESTORE DATABASE MyDatabase  
   FILE = 'MyDatabase_data_1',  
   FILEGROUP = 'new_customers',  
   FILE = 'MyDatabase_data_2',  
   FILEGROUP = 'first_qtr_sales'  
   FROM MyDatabase_1  
   WITH NORECOVERY;  
GO  
-- Apply the first transaction log backup.  
RESTORE LOG MyDatabase  
   FROM MyDatabase_log1  
   WITH NORECOVERY;  
GO  
-- Apply the last transaction log backup.  
RESTORE LOG MyDatabase  
   FROM MyDatabase_log2  
   WITH RECOVERY;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="763c0-241">另请参阅</span><span class="sxs-lookup"><span data-stu-id="763c0-241">See Also</span></span>  
 <span data-ttu-id="763c0-242">[还原数据库备份 &#40;SQL Server Management Studio&#41;](restore-a-database-backup-using-ssms.md) </span><span class="sxs-lookup"><span data-stu-id="763c0-242">[Restore a Database Backup &#40;SQL Server Management Studio&#41;](restore-a-database-backup-using-ssms.md) </span></span>  
 <span data-ttu-id="763c0-243">[备份文件和文件组 (SQL Server)](back-up-files-and-filegroups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="763c0-243">[Back Up Files and Filegroups &#40;SQL Server&#41;](back-up-files-and-filegroups-sql-server.md) </span></span>  
 <span data-ttu-id="763c0-244">[创建完整数据库备份 (SQL Server)](create-a-full-database-backup-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="763c0-244">[Create a Full Database Backup &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md) </span></span>  
 <span data-ttu-id="763c0-245">[备份事务日志 (SQL Server)](back-up-a-transaction-log-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="763c0-245">[Back Up a Transaction Log &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md) </span></span>  
 <span data-ttu-id="763c0-246">[还原事务日志备份 (SQL Server)](restore-a-transaction-log-backup-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="763c0-246">[Restore a Transaction Log Backup &#40;SQL Server&#41;](restore-a-transaction-log-backup-sql-server.md) </span></span>  
 [<span data-ttu-id="763c0-247">RESTORE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="763c0-247">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
