---
title: 从设备还原备份 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- restoring databases [SQL Server], device restores
- backup devices [SQL Server], restoring from
- database restores [SQL Server], device restores
- devices [SQL Server]
ms.assetid: 6e139de7-7de2-4d18-9df0-beac31ba7ff1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 50d7f7b8e255aea470a1065df669c0cc3169a8dd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688953"
---
# <a name="restore-a-backup-from-a-device-sql-server"></a><span data-ttu-id="00e59-102">从设备还原备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="00e59-102">Restore a Backup from a Device (SQL Server)</span></span>
  <span data-ttu-id="00e59-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中从设备还原备份。</span><span class="sxs-lookup"><span data-stu-id="00e59-103">This topic describes how to restore a backup from a device in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="00e59-104">有关 SQL Server 备份到 Azure Blob 存储服务的信息，请参阅[SQL Server 通过 Azure Blob 存储服务进行备份和还原](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)。</span><span class="sxs-lookup"><span data-stu-id="00e59-104">For information on SQL Server backup to the Azure Blob storage service, see, [SQL Server Backup and Restore with Azure Blob Storage Service](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md).</span></span>  
  
 <span data-ttu-id="00e59-105">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="00e59-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="00e59-106">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="00e59-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="00e59-107">安全性</span><span class="sxs-lookup"><span data-stu-id="00e59-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="00e59-108">**若要从设备还原备份，请使用：**</span><span class="sxs-lookup"><span data-stu-id="00e59-108">**To restore a backup from a device, using:**</span></span>  
  
     [<span data-ttu-id="00e59-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="00e59-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="00e59-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="00e59-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="00e59-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="00e59-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="00e59-112">Security</span><span class="sxs-lookup"><span data-stu-id="00e59-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="00e59-113">权限</span><span class="sxs-lookup"><span data-stu-id="00e59-113">Permissions</span></span>  
 <span data-ttu-id="00e59-114">如果不存在要还原的数据库，则用户必须有 CREATE DATABASE 权限才能执行 RESTORE。</span><span class="sxs-lookup"><span data-stu-id="00e59-114">If the database being restored does not exist, the user must have CREATE DATABASE permissions to be able to execute RESTORE.</span></span> <span data-ttu-id="00e59-115">如果数据库存在，则 RESTORE 权限默认授予 **sysadmin** 和 **dbcreator** 固定服务器角色成员以及数据库的所有者 (**dbo**)（对于 FROM DATABASE_SNAPSHOT 选项，数据库始终存在）。</span><span class="sxs-lookup"><span data-stu-id="00e59-115">If the database exists, RESTORE permissions default to members of the **sysadmin** and **dbcreator** fixed server roles and the owner (**dbo**) of the database (for the FROM DATABASE_SNAPSHOT option, the database always exists).</span></span>  
  
 <span data-ttu-id="00e59-116">RESTORE 权限被授予那些成员身份信息始终可由服务器使用的角色。</span><span class="sxs-lookup"><span data-stu-id="00e59-116">RESTORE permissions are given to roles in which membership information is always readily available to the server.</span></span> <span data-ttu-id="00e59-117">因为只有在固定数据库可以访问且没有损坏时（在执行 RESTORE 时并不会总是这样）才能检查固定数据库角色成员身份，所以 **db_owner** 固定数据库角色成员没有 RESTORE 权限。</span><span class="sxs-lookup"><span data-stu-id="00e59-117">Because fixed database role membership can be checked only when the database is accessible and undamaged, which is not always the case when RESTORE is executed, members of the **db_owner** fixed database role do not have RESTORE permissions.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="00e59-118">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="00e59-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-restore-a-backup-from-a-device"></a><span data-ttu-id="00e59-119">从设备还原备份</span><span class="sxs-lookup"><span data-stu-id="00e59-119">To restore a backup from a device</span></span>  
  
1.  <span data-ttu-id="00e59-120">连接到相应的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 实例之后，在“对象资源管理器”中，单击服务器名称以展开服务器树。</span><span class="sxs-lookup"><span data-stu-id="00e59-120">After connecting to the appropriate instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="00e59-121">展开 **“数据库”** ，然后根据数据库的不同，选择用户数据库，或展开 **“系统数据库”** ，再选择系统数据库。</span><span class="sxs-lookup"><span data-stu-id="00e59-121">Expand **Databases**, and, depending on the database, either select a user database or expand **System Databases** and select a system database.</span></span>  
  
3.  <span data-ttu-id="00e59-122">右键单击数据库，指向“任务”  ，再单击“还原”  。</span><span class="sxs-lookup"><span data-stu-id="00e59-122">Right-click the database, point to **Tasks**, and then click **Restore**.</span></span>  
  
4.  <span data-ttu-id="00e59-123">单击所需的还原操作类型（“数据库”  、“文件和文件组”  或“事务日志”  ）。</span><span class="sxs-lookup"><span data-stu-id="00e59-123">Click the type of restore operation you want (**Database**, **Files and Filegroups**, or **Transaction Log**).</span></span> <span data-ttu-id="00e59-124">这将打开相应的还原对话框。</span><span class="sxs-lookup"><span data-stu-id="00e59-124">This opens the corresponding restore dialog box.</span></span>  
  
5.  <span data-ttu-id="00e59-125">在 **“常规”** 页的 **“还原的源”** 部分，单击 **“源设备”** 。</span><span class="sxs-lookup"><span data-stu-id="00e59-125">On the **General** page, in the **Restore source** section, click **From device**.</span></span>  
  
6.  <span data-ttu-id="00e59-126">单击 **“源设备”** 文本框中的浏览按钮，这将打开 **“指定备份”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="00e59-126">Click the browse button for the **From device** text box, which opens the **Specify Backup** dialog box.</span></span>  
  
7.  <span data-ttu-id="00e59-127">在 **“备份介质”** 文本框中，选择 **“备份设备”** ，然后单击 **“添加”** 按钮以打开 **“选择备份设备”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="00e59-127">In the **Backup media** text box, select **Backup Device**, and click the **Add** button to open the **Select Backup Device** dialog box.</span></span>  
  
8.  <span data-ttu-id="00e59-128">在 **“备份设备”** 文本框中，选择要用于还原操作的设备。</span><span class="sxs-lookup"><span data-stu-id="00e59-128">In the **Backup device** text box, select the device you want to use for the restore operation.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="00e59-129">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="00e59-129">Using Transact-SQL</span></span>  
  
#### <a name="to-restore-a-backup-from-a-device"></a><span data-ttu-id="00e59-130">从设备还原备份</span><span class="sxs-lookup"><span data-stu-id="00e59-130">To restore a backup from a device</span></span>  
  
1.  <span data-ttu-id="00e59-131">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="00e59-131">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="00e59-132">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="00e59-132">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="00e59-133">在 [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) 语句中，指定用于备份操作的逻辑备份设备或物理备份设备。</span><span class="sxs-lookup"><span data-stu-id="00e59-133">In the [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) statement, specify a logical or physical backup device to use for the backup operation.</span></span> <span data-ttu-id="00e59-134">此示例从具有物理名称 `Z:\SQLServerBackups\AdventureWorks2012.bak`的磁盘文件还原。</span><span class="sxs-lookup"><span data-stu-id="00e59-134">This example restores from a disk file that has the physical name `Z:\SQLServerBackups\AdventureWorks2012.bak`.</span></span>  
  
```sql  
RESTORE DATABASE AdventureWorks2012  
   FROM DISK = 'Z:\SQLServerBackups\AdventureWorks2012.bak' ;  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="00e59-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="00e59-135">See Also</span></span>  
 <span data-ttu-id="00e59-136">[RESTORE FILELISTONLY (Transact-SQL)](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="00e59-136">[RESTORE FILELISTONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql) </span></span>  
 <span data-ttu-id="00e59-137">[RESTORE HEADERONLY (Transact-SQL)](/sql/t-sql/statements/restore-statements-headeronly-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="00e59-137">[RESTORE HEADERONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-headeronly-transact-sql) </span></span>  
 <span data-ttu-id="00e59-138">[RESTORE LABELONLY (Transact-SQL)](/sql/t-sql/statements/restore-statements-labelonly-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="00e59-138">[RESTORE LABELONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-labelonly-transact-sql) </span></span>  
 <span data-ttu-id="00e59-139">[RESTORE VERIFYONLY (Transact-SQL)](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="00e59-139">[RESTORE VERIFYONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql) </span></span>  
 <span data-ttu-id="00e59-140">[在简单恢复模式下还原数据库备份 (Transact-SQL)](restore-a-database-backup-under-the-simple-recovery-model-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="00e59-140">[Restore a Database Backup Under the Simple Recovery Model &#40;Transact-SQL&#41;](restore-a-database-backup-under-the-simple-recovery-model-transact-sql.md) </span></span>  
 <span data-ttu-id="00e59-141">[还原数据库备份 &#40;SQL Server Management Studio&#41;](restore-a-database-backup-using-ssms.md) </span><span class="sxs-lookup"><span data-stu-id="00e59-141">[Restore a Database Backup &#40;SQL Server Management Studio&#41;](restore-a-database-backup-using-ssms.md) </span></span>  
 <span data-ttu-id="00e59-142">[还原差异数据库备份 (SQL Server)](restore-a-differential-database-backup-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="00e59-142">[Restore a Differential Database Backup &#40;SQL Server&#41;](restore-a-differential-database-backup-sql-server.md) </span></span>  
 <span data-ttu-id="00e59-143">[将数据库还原到新位置 (SQL Server)](restore-a-database-to-a-new-location-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="00e59-143">[Restore a Database to a New Location &#40;SQL Server&#41;](restore-a-database-to-a-new-location-sql-server.md) </span></span>  
 <span data-ttu-id="00e59-144">[备份文件和文件组 (SQL Server)](back-up-files-and-filegroups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="00e59-144">[Back Up Files and Filegroups &#40;SQL Server&#41;](back-up-files-and-filegroups-sql-server.md) </span></span>  
 <span data-ttu-id="00e59-145">[备份事务日志 (SQL Server)](back-up-a-transaction-log-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="00e59-145">[Back Up a Transaction Log &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md) </span></span>  
 [<span data-ttu-id="00e59-146">创建差异数据库备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="00e59-146">Create a Differential Database Backup &#40;SQL Server&#41;</span></span>](create-a-differential-database-backup-sql-server.md)  
  
  
