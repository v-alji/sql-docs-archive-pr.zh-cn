---
title: 将文件还原到新位置 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- restoring files [SQL Server], how-to topics
- restoring databases [SQL Server], moving
- restoring files [SQL Server], steps
- file restores [SQL Server], how-to topics
- filegroups [SQL Server], restoring
- restoring filegroups [SQL Server]
ms.assetid: b4f4791d-646e-4632-9980-baae9cb1aade
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2a8336e5d186fb72df4e0a17fdd9affccab4ee57
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689443"
---
# <a name="restore-files-to-a-new-location-sql-server"></a><span data-ttu-id="20ba1-102">将文件还原到新位置 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="20ba1-102">Restore Files to a New Location (SQL Server)</span></span>
  <span data-ttu-id="20ba1-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中将文件还原到新位置。</span><span class="sxs-lookup"><span data-stu-id="20ba1-103">This topic describes how to restore files to a new location in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="20ba1-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="20ba1-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="20ba1-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="20ba1-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="20ba1-106">限制和局限</span><span class="sxs-lookup"><span data-stu-id="20ba1-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="20ba1-107">安全性</span><span class="sxs-lookup"><span data-stu-id="20ba1-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="20ba1-108">**若要将文件还原到新位置，可使用：**</span><span class="sxs-lookup"><span data-stu-id="20ba1-108">**To restore files to a new location, using:**</span></span>  
  
     [<span data-ttu-id="20ba1-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="20ba1-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="20ba1-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="20ba1-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="20ba1-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="20ba1-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="20ba1-112">限制和局限</span><span class="sxs-lookup"><span data-stu-id="20ba1-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="20ba1-113">还原文件的系统管理员必须是唯一一位当前使用要还原的数据库的人。</span><span class="sxs-lookup"><span data-stu-id="20ba1-113">The system administrator restoring the files must be the only person currently using the database to be restored.</span></span>  
  
-   <span data-ttu-id="20ba1-114">不允许在显式或隐式事务中使用 RESTORE。</span><span class="sxs-lookup"><span data-stu-id="20ba1-114">RESTORE is not allowed in an explicit or implicit transaction.</span></span>  
  
-   <span data-ttu-id="20ba1-115">在完整恢复模式或大容量日志恢复模式下，必须先备份活动事务日志（称为日志尾部），然后才能还原文件。</span><span class="sxs-lookup"><span data-stu-id="20ba1-115">Under the full or bulk-logged recovery model, before you can restore files, you must back up the active transaction log (known as the tail of the log).</span></span> <span data-ttu-id="20ba1-116">有关详细信息，请参阅 [备份事务日志 (SQL Server)](back-up-a-transaction-log-sql-server.md)数据库还原到一个新位置并且可以选择重命名该数据库。</span><span class="sxs-lookup"><span data-stu-id="20ba1-116">For more information, see [Back Up a Transaction Log &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md).</span></span>  
  
-   <span data-ttu-id="20ba1-117">若要还原已加密的数据库，您必须有权访问用于对数据库进行加密的证书或非对称密钥。</span><span class="sxs-lookup"><span data-stu-id="20ba1-117">To restore a database that is encrypted, you must have access to the certificate or asymmetric key that was used to encrypt the database.</span></span> <span data-ttu-id="20ba1-118">如果没有证书或非对称密钥，数据库将无法还原。</span><span class="sxs-lookup"><span data-stu-id="20ba1-118">Without the certificate or asymmetric key, the database cannot be restored.</span></span> <span data-ttu-id="20ba1-119">因此，只要需要该备份，就必须保留用于对数据库加密密钥进行加密的证书。</span><span class="sxs-lookup"><span data-stu-id="20ba1-119">As a result, the certificate that is used to encrypt the database encryption key must be retained as long as the backup is needed.</span></span> <span data-ttu-id="20ba1-120">有关详细信息，请参阅 [SQL Server Certificates and Asymmetric Keys](../security/sql-server-certificates-and-asymmetric-keys.md)。</span><span class="sxs-lookup"><span data-stu-id="20ba1-120">For more information, see [SQL Server Certificates and Asymmetric Keys](../security/sql-server-certificates-and-asymmetric-keys.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="20ba1-121">Security</span><span class="sxs-lookup"><span data-stu-id="20ba1-121">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="20ba1-122">权限</span><span class="sxs-lookup"><span data-stu-id="20ba1-122">Permissions</span></span>  
 <span data-ttu-id="20ba1-123">如果不存在要还原的数据库，则用户必须有 CREATE DATABASE 权限才能执行 RESTORE。</span><span class="sxs-lookup"><span data-stu-id="20ba1-123">If the database being restored does not exist, the user must have CREATE DATABASE permissions to be able to execute RESTORE.</span></span> <span data-ttu-id="20ba1-124">如果数据库存在，则 RESTORE 权限默认授予 **sysadmin** 和 **dbcreator** 固定服务器角色成员以及数据库的所有者 (**dbo**)（对于 FROM DATABASE_SNAPSHOT 选项，数据库始终存在）。</span><span class="sxs-lookup"><span data-stu-id="20ba1-124">If the database exists, RESTORE permissions default to members of the **sysadmin** and **dbcreator** fixed server roles and the owner (**dbo**) of the database (for the FROM DATABASE_SNAPSHOT option, the database always exists).</span></span>  
  
 <span data-ttu-id="20ba1-125">RESTORE 权限被授予那些成员身份信息始终可由服务器使用的角色。</span><span class="sxs-lookup"><span data-stu-id="20ba1-125">RESTORE permissions are given to roles in which membership information is always readily available to the server.</span></span> <span data-ttu-id="20ba1-126">因为只有在固定数据库可以访问且没有损坏时（在执行 RESTORE 时并不会总是这样）才能检查固定数据库角色成员身份，所以 **db_owner** 固定数据库角色成员没有 RESTORE 权限。</span><span class="sxs-lookup"><span data-stu-id="20ba1-126">Because fixed database role membership can be checked only when the database is accessible and undamaged, which is not always the case when RESTORE is executed, members of the **db_owner** fixed database role do not have RESTORE permissions.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="20ba1-127">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="20ba1-127">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-restore-files-to-a-new-location"></a><span data-ttu-id="20ba1-128">将文件还原到新位置</span><span class="sxs-lookup"><span data-stu-id="20ba1-128">To restore files to a new location</span></span>  
  
1.  <span data-ttu-id="20ba1-129">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]的实例，再依次展开该实例、 **“数据库”** 。</span><span class="sxs-lookup"><span data-stu-id="20ba1-129">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], expand that instance, and then expand **Databases**.</span></span>  
  
2.  <span data-ttu-id="20ba1-130">右键单击所需数据库，指向“任务”  ，再指向“还原”  ，然后单击“文件和文件组”  。</span><span class="sxs-lookup"><span data-stu-id="20ba1-130">Right-click the database that you want, point to **Tasks**, point to **Restore**, and then click **Files and Filegroups**.</span></span>  
  
3.  <span data-ttu-id="20ba1-131">在 **“常规”** 页上的 **目标数据库** 列表框中，输入要还原的数据库。</span><span class="sxs-lookup"><span data-stu-id="20ba1-131">On the **General** page, in the **To database** list box, enter the database to restore.</span></span> <span data-ttu-id="20ba1-132">您可以输入新的数据库，也可以从下拉列表中选择现有的数据库。</span><span class="sxs-lookup"><span data-stu-id="20ba1-132">You can enter a new database or choose an existing database from the drop-down list.</span></span> <span data-ttu-id="20ba1-133">该列表包含了服务器上除系统数据库 **master** 和 **tempdb**之外的所有数据库。</span><span class="sxs-lookup"><span data-stu-id="20ba1-133">The list includes all databases on the server, excluding the system databases **master** and **tempdb**.</span></span>  
  
4.  <span data-ttu-id="20ba1-134">若要指定要还原的备份集的源和位置，请单击以下选项之一：</span><span class="sxs-lookup"><span data-stu-id="20ba1-134">To specify the source and location of the backup sets to restore, click one of the following options:</span></span>  
  
    -   <span data-ttu-id="20ba1-135">**源数据库**</span><span class="sxs-lookup"><span data-stu-id="20ba1-135">**From database**</span></span>  
  
         <span data-ttu-id="20ba1-136">在列表框中输入数据库名称。</span><span class="sxs-lookup"><span data-stu-id="20ba1-136">Enter a database name in the list box.</span></span> <span data-ttu-id="20ba1-137">此列表仅包含根据 **msdb** 备份历史记录已进行过备份的数据库。</span><span class="sxs-lookup"><span data-stu-id="20ba1-137">This list contains only databases that have been backed up according to the **msdb** backup history.</span></span>  
  
    -   <span data-ttu-id="20ba1-138">**源设备**</span><span class="sxs-lookup"><span data-stu-id="20ba1-138">**From device**</span></span>  
  
         <span data-ttu-id="20ba1-139">单击浏览按钮。</span><span class="sxs-lookup"><span data-stu-id="20ba1-139">Click the browse button.</span></span> <span data-ttu-id="20ba1-140">在 **“指定备份设备”** 对话框的 **“备份介质类型”** 列表框中，选择列出的设备类型之一。</span><span class="sxs-lookup"><span data-stu-id="20ba1-140">In the **Specify backup devices** dialog box, select one of the listed device types in the **Backup media type** list box.</span></span> <span data-ttu-id="20ba1-141">若要为 **“备份介质”** 列表框选择一个或多个设备，请单击 **“添加”** 。</span><span class="sxs-lookup"><span data-stu-id="20ba1-141">To select one or more devices for the **Backup media** list box, click **Add**.</span></span>  
  
         <span data-ttu-id="20ba1-142">将所需设备添加到 **“备份介质”** 列表框后，单击 **“确定”** 返回到 **“常规”** 页。</span><span class="sxs-lookup"><span data-stu-id="20ba1-142">After you add the devices you want to the **Backup media** list box, click **OK** to return to the **General** page.</span></span>  
  
5.  <span data-ttu-id="20ba1-143">在 **“选择用于还原的备份集”** 网格中，选择用于还原的备份。</span><span class="sxs-lookup"><span data-stu-id="20ba1-143">In the **Select the backup sets to restore** grid, select the backups to restore.</span></span> <span data-ttu-id="20ba1-144">此网格将显示对于指定位置可用的备份。</span><span class="sxs-lookup"><span data-stu-id="20ba1-144">This grid displays the backups available for the specified location.</span></span> <span data-ttu-id="20ba1-145">默认情况下，系统会推荐一个恢复计划。</span><span class="sxs-lookup"><span data-stu-id="20ba1-145">By default, a recovery plan is suggested.</span></span> <span data-ttu-id="20ba1-146">若要覆盖建议的恢复计划，可以更改网格中的选择。</span><span class="sxs-lookup"><span data-stu-id="20ba1-146">To override the suggested recovery plan, you can change the selections in the grid.</span></span> <span data-ttu-id="20ba1-147">任何依赖于已取消选择备份的备份，也将被自动取消选择。</span><span class="sxs-lookup"><span data-stu-id="20ba1-147">Any backups that depend on a deselected backup are deselected automatically.</span></span>  
  
    |<span data-ttu-id="20ba1-148">列标题</span><span class="sxs-lookup"><span data-stu-id="20ba1-148">Column head</span></span>|<span data-ttu-id="20ba1-149">值</span><span class="sxs-lookup"><span data-stu-id="20ba1-149">Values</span></span>|  
    |-----------------|------------|  
    |<span data-ttu-id="20ba1-150">**还原**</span><span class="sxs-lookup"><span data-stu-id="20ba1-150">**Restore**</span></span>|<span data-ttu-id="20ba1-151">选中的复选框指示要还原的备份集。</span><span class="sxs-lookup"><span data-stu-id="20ba1-151">The selected check boxes indicate the backup sets to be restored.</span></span>|  
    |<span data-ttu-id="20ba1-152">**名称**</span><span class="sxs-lookup"><span data-stu-id="20ba1-152">**Name**</span></span>|<span data-ttu-id="20ba1-153">备份集的名称。</span><span class="sxs-lookup"><span data-stu-id="20ba1-153">The name of the backup set.</span></span>|  
    |<span data-ttu-id="20ba1-154">**文件类型**</span><span class="sxs-lookup"><span data-stu-id="20ba1-154">**File Type**</span></span>|<span data-ttu-id="20ba1-155">指定备份中数据的类型：数据、日志，或 Filestream 数据    。</span><span class="sxs-lookup"><span data-stu-id="20ba1-155">Specifies the type of data in the backup: **Data**, **Log**, or **Filestream Data**.</span></span> <span data-ttu-id="20ba1-156">包含在表中的数据备份在 **“数据”** 文件中。</span><span class="sxs-lookup"><span data-stu-id="20ba1-156">Data that is contained in tables is in **Data** files.</span></span> <span data-ttu-id="20ba1-157">事务日志数据备份在 **“日志”** 文件中。</span><span class="sxs-lookup"><span data-stu-id="20ba1-157">Transaction log data is in **Log** files.</span></span> <span data-ttu-id="20ba1-158">存储在文件系统上的二进制大型对象 (BLOB) 数据备份在 **Filestream 数据** 文件中。</span><span class="sxs-lookup"><span data-stu-id="20ba1-158">Binary large object (BLOB) data that is stored on the file system is in **Filestream Data** files.</span></span>|  
    |<span data-ttu-id="20ba1-159">类型 </span><span class="sxs-lookup"><span data-stu-id="20ba1-159">**Type**</span></span>|<span data-ttu-id="20ba1-160">执行的备份类型：“完整”、“差异”或“事务日志”  。</span><span class="sxs-lookup"><span data-stu-id="20ba1-160">The type of backup performed: **Full**, **Differential**, or **Transaction Log**.</span></span>|  
    |<span data-ttu-id="20ba1-161">**Server**</span><span class="sxs-lookup"><span data-stu-id="20ba1-161">**Server**</span></span>|<span data-ttu-id="20ba1-162">执行备份操作的数据库引擎实例的名称。</span><span class="sxs-lookup"><span data-stu-id="20ba1-162">The name of the Database-Engine instance that performed the backup operation.</span></span>|  
    |<span data-ttu-id="20ba1-163">**文件逻辑名称**</span><span class="sxs-lookup"><span data-stu-id="20ba1-163">**File Logical Name**</span></span>|<span data-ttu-id="20ba1-164">文件的逻辑名称。</span><span class="sxs-lookup"><span data-stu-id="20ba1-164">The logical name of the file.</span></span>|  
    |<span data-ttu-id="20ba1-165">**Database**</span><span class="sxs-lookup"><span data-stu-id="20ba1-165">**Database**</span></span>|<span data-ttu-id="20ba1-166">备份操作中涉及的数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="20ba1-166">The name of the database involved in the backup operation.</span></span>|  
    |<span data-ttu-id="20ba1-167">**开始日期**</span><span class="sxs-lookup"><span data-stu-id="20ba1-167">**Start Date**</span></span>|<span data-ttu-id="20ba1-168">备份操作开始的日期和时间，按客户端的区域设置显示。</span><span class="sxs-lookup"><span data-stu-id="20ba1-168">The date and time when the backup operation began, presented in the regional setting of the client.</span></span>|  
    |<span data-ttu-id="20ba1-169">**完成日期**</span><span class="sxs-lookup"><span data-stu-id="20ba1-169">**Finish Date**</span></span>|<span data-ttu-id="20ba1-170">备份操作完成的日期和时间，按客户端的区域设置显示。</span><span class="sxs-lookup"><span data-stu-id="20ba1-170">The date and time when the backup operation finished, presented in the regional setting of the client.</span></span>|  
    |<span data-ttu-id="20ba1-171">**大小**</span><span class="sxs-lookup"><span data-stu-id="20ba1-171">**Size**</span></span>|<span data-ttu-id="20ba1-172">备份集的大小（字节）。</span><span class="sxs-lookup"><span data-stu-id="20ba1-172">The size of the backup set in bytes.</span></span>|  
    |<span data-ttu-id="20ba1-173">**用户名**</span><span class="sxs-lookup"><span data-stu-id="20ba1-173">**User Name**</span></span>|<span data-ttu-id="20ba1-174">执行备份操作的用户的名称。</span><span class="sxs-lookup"><span data-stu-id="20ba1-174">The name of the user who performed the backup operation.</span></span>|  
  
6.  <span data-ttu-id="20ba1-175">在 **“选择页”** 窗格中，单击 **“选项”** 页。</span><span class="sxs-lookup"><span data-stu-id="20ba1-175">In the **Select a page** pane, click the **Options** page.</span></span>  
  
7.  <span data-ttu-id="20ba1-176">在 **“将数据库文件还原为”** 网格中，为要移动的文件指定新的位置。</span><span class="sxs-lookup"><span data-stu-id="20ba1-176">In the **Restore database files as** grid, specify a new location for the file or files that you want to move.</span></span>  
  
    |<span data-ttu-id="20ba1-177">列标题</span><span class="sxs-lookup"><span data-stu-id="20ba1-177">Column head</span></span>|<span data-ttu-id="20ba1-178">值</span><span class="sxs-lookup"><span data-stu-id="20ba1-178">Values</span></span>|  
    |-----------------|------------|  
    |<span data-ttu-id="20ba1-179">**原始文件名**</span><span class="sxs-lookup"><span data-stu-id="20ba1-179">**Original File Name**</span></span>|<span data-ttu-id="20ba1-180">源备份文件的完整路径。</span><span class="sxs-lookup"><span data-stu-id="20ba1-180">The full path of a source backup file.</span></span>|  
    |<span data-ttu-id="20ba1-181">**文件类型**</span><span class="sxs-lookup"><span data-stu-id="20ba1-181">**File Type**</span></span>|<span data-ttu-id="20ba1-182">指定备份中数据的类型：数据、日志，或 Filestream 数据    。</span><span class="sxs-lookup"><span data-stu-id="20ba1-182">Specifies the type of data in the backup: **Data**, **Log**, or **Filestream Data**.</span></span> <span data-ttu-id="20ba1-183">包含在表中的数据备份在 **“数据”** 文件中。</span><span class="sxs-lookup"><span data-stu-id="20ba1-183">Data that is contained in tables is in **Data** files.</span></span> <span data-ttu-id="20ba1-184">事务日志数据备份在 **“日志”** 文件中。</span><span class="sxs-lookup"><span data-stu-id="20ba1-184">Transaction log data is in **Log** files.</span></span> <span data-ttu-id="20ba1-185">存储在文件系统上的二进制大型对象 (BLOB) 数据备份在 **Filestream 数据** 文件中。</span><span class="sxs-lookup"><span data-stu-id="20ba1-185">Binary large object (BLOB) data that is stored on the file system is in **Filestream Data** files.</span></span>|  
    |<span data-ttu-id="20ba1-186">**还原为**</span><span class="sxs-lookup"><span data-stu-id="20ba1-186">**Restore As**</span></span>|<span data-ttu-id="20ba1-187">要还原的数据库文件的完整路径。</span><span class="sxs-lookup"><span data-stu-id="20ba1-187">The full path of the database file to be restored.</span></span> <span data-ttu-id="20ba1-188">若要指定新的还原文件，请单击文本框，再编辑建议的路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="20ba1-188">To specify a new restore file, click the text box and edit the suggested path and file name.</span></span> <span data-ttu-id="20ba1-189">更改 **“还原为”** 列中的路径或文件名等效于在 [!INCLUDE[tsql](../../includes/tsql-md.md)] RESTORE 语句中使用 MOVE 选项。</span><span class="sxs-lookup"><span data-stu-id="20ba1-189">Changing the path or file name in the **Restore As** column is equivalent to using the MOVE option in a [!INCLUDE[tsql](../../includes/tsql-md.md)] RESTORE statement.</span></span>|  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="20ba1-190">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="20ba1-190">Using Transact-SQL</span></span>  
  
#### <a name="to-restore-files-to-a-new-location"></a><span data-ttu-id="20ba1-191">将文件还原到新位置</span><span class="sxs-lookup"><span data-stu-id="20ba1-191">To restore files to a new location</span></span>  
  
1.  <span data-ttu-id="20ba1-192">（可选）执行 RESTORE FILELISTONLY 语句，以确定完整数据库备份中的文件数及名称。</span><span class="sxs-lookup"><span data-stu-id="20ba1-192">Optionally, execute the RESTORE FILELISTONLY statement to determine the number and names of the files in the full database backup.</span></span>  
  
2.  <span data-ttu-id="20ba1-193">执行 RESTORE DATABASE 语句可以还原完整数据库备份，同时指定：</span><span class="sxs-lookup"><span data-stu-id="20ba1-193">Execute the RESTORE DATABASE statement to restore the full database backup, specifying:</span></span>  
  
    -   <span data-ttu-id="20ba1-194">要还原的数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="20ba1-194">The name of the database to restore.</span></span>  
  
    -   <span data-ttu-id="20ba1-195">从中还原完整数据库备份的备份设备。</span><span class="sxs-lookup"><span data-stu-id="20ba1-195">The backup device from where the full database backup will be restored.</span></span>  
  
    -   <span data-ttu-id="20ba1-196">为每个要还原到新位置的文件指定 MOVE 子句。</span><span class="sxs-lookup"><span data-stu-id="20ba1-196">The MOVE clause for each file to restore to a new location.</span></span>  
  
    -   <span data-ttu-id="20ba1-197">NORECOVERY 子句。</span><span class="sxs-lookup"><span data-stu-id="20ba1-197">The NORECOVERY clause.</span></span>  
  
3.  <span data-ttu-id="20ba1-198">如果在创建文件备份之后对文件进行了修改，则执行 RESTORE LOG 语句以应用事务日志备份，同时指定下列内容：</span><span class="sxs-lookup"><span data-stu-id="20ba1-198">If the files have been modified after the file backup was created, execute the RESTORE LOG statement to apply the transaction log backup, specifying:</span></span>  
  
    -   <span data-ttu-id="20ba1-199">事务日志将应用到的数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="20ba1-199">The name of the database to which the transaction log will be applied.</span></span>  
  
    -   <span data-ttu-id="20ba1-200">要还原的事务日志备份的备份设备。</span><span class="sxs-lookup"><span data-stu-id="20ba1-200">The backup device from where the transaction log backup will be restored.</span></span>  
  
    -   <span data-ttu-id="20ba1-201">如果在应用当前事务日志备份之后还要应用其他事务日志备份，则指定 NORECOVERY 子句；否则指定 RECOVERY 子句。</span><span class="sxs-lookup"><span data-stu-id="20ba1-201">The NORECOVERY clause if you have another transaction log backup to apply after the current one; otherwise, specify the RECOVERY clause.</span></span>  
  
         <span data-ttu-id="20ba1-202">事务日志备份（如果已应用）必须包含备份文件和文件组时的时间。</span><span class="sxs-lookup"><span data-stu-id="20ba1-202">The transaction log backups, if applied, must cover the time when the files and filegroups were backed up.</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="20ba1-203">示例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="20ba1-203">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="20ba1-204">以下示例将 `MyNwind` 数据库中原来位于驱动器 C 上的两个文件还原到驱动器 D 上的新位置。为了将数据库还原到当前时间，还将应用两个事务日志。</span><span class="sxs-lookup"><span data-stu-id="20ba1-204">This example restores two of the files for the `MyNwind` database that were originally located on Drive C to new locations on Drive D. Two transaction logs will also be applied to restore the database to the current time.</span></span> <span data-ttu-id="20ba1-205">`RESTORE FILELISTONLY` 语句用于确定待还原数据库内的文件的数目及其逻辑名称和物理名称。</span><span class="sxs-lookup"><span data-stu-id="20ba1-205">The `RESTORE FILELISTONLY` statement is used to determine the number and logical and physical names of the files in the database being restored.</span></span>  
  
```sql  
USE master;  
GO  
-- First determine the number and names of the files in the backup.  
RESTORE FILELISTONLY  
   FROM MyNwind_1;  
-- Restore the files for MyNwind.  
RESTORE DATABASE MyNwind  
   FROM MyNwind_1  
   WITH NORECOVERY,  
   MOVE 'MyNwind_data_1' TO 'D:\MyData\MyNwind_data_1.mdf',   
   MOVE 'MyNwind_data_2' TO 'D:\MyData\MyNwind_data_2.ndf';  
GO  
-- Apply the first transaction log backup.  
RESTORE LOG MyNwind  
   FROM MyNwind_log1  
   WITH NORECOVERY;  
GO  
-- Apply the last transaction log backup.  
RESTORE LOG MyNwind  
   FROM MyNwind_log2  
   WITH RECOVERY;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="20ba1-206">另请参阅</span><span class="sxs-lookup"><span data-stu-id="20ba1-206">See Also</span></span>  
 <span data-ttu-id="20ba1-207">[还原数据库备份 &#40;SQL Server Management Studio&#41;](restore-a-database-backup-using-ssms.md) </span><span class="sxs-lookup"><span data-stu-id="20ba1-207">[Restore a Database Backup &#40;SQL Server Management Studio&#41;](restore-a-database-backup-using-ssms.md) </span></span>  
 <span data-ttu-id="20ba1-208">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="20ba1-208">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 <span data-ttu-id="20ba1-209">[通过备份和还原来复制数据库](../databases/copy-databases-with-backup-and-restore.md) </span><span class="sxs-lookup"><span data-stu-id="20ba1-209">[Copy Databases with Backup and Restore](../databases/copy-databases-with-backup-and-restore.md) </span></span>  
 [<span data-ttu-id="20ba1-210">还原文件和文件组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="20ba1-210">Restore Files and Filegroups &#40;SQL Server&#41;</span></span>](restore-files-and-filegroups-sql-server.md)  
  
  
