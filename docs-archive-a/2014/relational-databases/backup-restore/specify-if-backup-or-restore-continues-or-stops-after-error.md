---
title: 指定备份或还原操作在遇到错误后是继续还是停止 (SQL Server) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- errors [SQL Server], backups
- backing up databases [SQL Server], errors
- backups [SQL Server], errors
- database backups [SQL Server], errors
ms.assetid: 042be17a-b9b0-4629-b6bb-b87a8bc6c316
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 87cccec6f7eea18f2750d3b0be81b577b0eb170a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590218"
---
# <a name="specify-whether-a-backup-or-restore-operation-continues-or-stops-after-encountering-an-error-sql-server"></a><span data-ttu-id="71b55-102">指定备份或还原操作在遇到错误后是继续还是停止 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="71b55-102">Specify Whether a Backup or Restore Operation Continues or Stops After Encountering an Error (SQL Server)</span></span>
  <span data-ttu-id="71b55-103">本主题介绍如何通过使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 指定在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中遇到错误后备份或还原操作是继续还是停止。</span><span class="sxs-lookup"><span data-stu-id="71b55-103">This topic describes how to specify whether a backup or restore operation continues or stops after encountering an error in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="71b55-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="71b55-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="71b55-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="71b55-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="71b55-106">安全性</span><span class="sxs-lookup"><span data-stu-id="71b55-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="71b55-107">**若要指定备份或还原操作在遇到错误后是停止还是继续，请使用：**</span><span class="sxs-lookup"><span data-stu-id="71b55-107">**To specify whether a backup or restore operation continues after encountering an error, using:**</span></span>  
  
     [<span data-ttu-id="71b55-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="71b55-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="71b55-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="71b55-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="71b55-110">开始之前</span><span class="sxs-lookup"><span data-stu-id="71b55-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="71b55-111">Security</span><span class="sxs-lookup"><span data-stu-id="71b55-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="71b55-112">权限</span><span class="sxs-lookup"><span data-stu-id="71b55-112">Permissions</span></span>  
 <span data-ttu-id="71b55-113">BACKUP</span><span class="sxs-lookup"><span data-stu-id="71b55-113">BACKUP</span></span>  
 <span data-ttu-id="71b55-114">默认情况下，为 **sysadmin** 固定服务器角色以及 **db_owner** 和 **db_backupoperator** 固定数据库角色的成员授予 BACKUP DATABASE 和 BACKUP LOG 权限。</span><span class="sxs-lookup"><span data-stu-id="71b55-114">BACKUP DATABASE and BACKUP LOG permissions default to members of the **sysadmin** fixed server role and the **db_owner** and **db_backupoperator** fixed database roles.</span></span>  
  
 <span data-ttu-id="71b55-115">备份设备的物理文件的所有权和权限问题可能会妨碍备份操作。</span><span class="sxs-lookup"><span data-stu-id="71b55-115">Ownership and permission problems on the backup device's physical file can interfere with a backup operation.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="71b55-116">必须能够读取和写入设备；运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务的帐户必须具有写入权限。</span><span class="sxs-lookup"><span data-stu-id="71b55-116">must be able to read and write to the device; the account under which the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service runs must have write permissions.</span></span> <span data-ttu-id="71b55-117">但是，用于在系统表中为备份设备添加项目的 [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql)不检查文件访问权限。</span><span class="sxs-lookup"><span data-stu-id="71b55-117">However, [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql), which adds an entry for a backup device in the system tables, does not check file access permissions.</span></span> <span data-ttu-id="71b55-118">备份设备物理文件的这些问题可能直到为备份或还原而访问物理资源时才会出现。</span><span class="sxs-lookup"><span data-stu-id="71b55-118">Such problems on the backup device's physical file may not appear until the physical resource is accessed when the backup or restore is attempted.</span></span>  
  
 <span data-ttu-id="71b55-119">RESTORE</span><span class="sxs-lookup"><span data-stu-id="71b55-119">RESTORE</span></span>  
 <span data-ttu-id="71b55-120">如果不存在要还原的数据库，则用户必须有 CREATE DATABASE 权限才能执行 RESTORE。</span><span class="sxs-lookup"><span data-stu-id="71b55-120">If the database being restored does not exist, the user must have CREATE DATABASE permissions to be able to execute RESTORE.</span></span> <span data-ttu-id="71b55-121">如果数据库存在，则 RESTORE 权限默认授予 **sysadmin** 和 **dbcreator** 固定服务器角色成员以及数据库的所有者 (**dbo**)（对于 FROM DATABASE_SNAPSHOT 选项，数据库始终存在）。</span><span class="sxs-lookup"><span data-stu-id="71b55-121">If the database exists, RESTORE permissions default to members of the **sysadmin** and **dbcreator** fixed server roles and the owner (**dbo**) of the database (for the FROM DATABASE_SNAPSHOT option, the database always exists).</span></span>  
  
 <span data-ttu-id="71b55-122">RESTORE 权限被授予那些成员身份信息始终可由服务器使用的角色。</span><span class="sxs-lookup"><span data-stu-id="71b55-122">RESTORE permissions are given to roles in which membership information is always readily available to the server.</span></span> <span data-ttu-id="71b55-123">因为只有在固定数据库可以访问且没有损坏时（在执行 RESTORE 时并不会总是这样）才能检查固定数据库角色成员身份，所以 **db_owner** 固定数据库角色成员没有 RESTORE 权限。</span><span class="sxs-lookup"><span data-stu-id="71b55-123">Because fixed database role membership can be checked only when the database is accessible and undamaged, which is not always the case when RESTORE is executed, members of the **db_owner** fixed database role do not have RESTORE permissions.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="71b55-124">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="71b55-124">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-specify-whether-backup-continues-or-stops-after-an-error-is-encountered"></a><span data-ttu-id="71b55-125">指定备份操作在遇到错误后是继续还是停止</span><span class="sxs-lookup"><span data-stu-id="71b55-125">To specify whether backup continues or stops after an error is encountered</span></span>  
  
1.  <span data-ttu-id="71b55-126">执行以下步骤以便 [创建数据库备份](create-a-full-database-backup-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="71b55-126">Follow the steps to [create a database backup](create-a-full-database-backup-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="71b55-127">在 **“选项”** 页的 **“可靠性”** 部分中，单击 **“写入介质前检查校验和”** 和 **“出错时继续”** 。</span><span class="sxs-lookup"><span data-stu-id="71b55-127">On the **Options** page, in the **Reliability** section, click **Perform checksum before writing to media** and **Continue on error**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="71b55-128">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="71b55-128">Using Transact-SQL</span></span>  
  
#### <a name="to-specify-whether-a-backup-operation-continues-or-stops-after-encountering-an-error"></a><span data-ttu-id="71b55-129">指定备份操作在遇到错误后是继续还是停止</span><span class="sxs-lookup"><span data-stu-id="71b55-129">To specify whether a backup operation continues or stops after encountering an error</span></span>  
  
1.  <span data-ttu-id="71b55-130">连接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="71b55-130">Connect to the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="71b55-131">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="71b55-131">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="71b55-132">在 [BACKUP](/sql/t-sql/statements/backup-transact-sql) 语句中，指定 CONTINUE_AFTER ERROR 选项可继续操作，指定 STOP_ON_ERROR 选项可停止操作。</span><span class="sxs-lookup"><span data-stu-id="71b55-132">In the [BACKUP](/sql/t-sql/statements/backup-transact-sql) statement, specify the CONTINUE_AFTER ERROR option to continue or the STOP_ON_ERROR option to stop.</span></span> <span data-ttu-id="71b55-133">默认行为是遇到错误后停止。</span><span class="sxs-lookup"><span data-stu-id="71b55-133">The default behavior is to stop after encountering an error.</span></span> <span data-ttu-id="71b55-134">下面的示例指示备份操作在遇到错误时仍继续。</span><span class="sxs-lookup"><span data-stu-id="71b55-134">This example instructs the backup operation to continue despite encountering an error.</span></span>  
  
```sql  
BACKUP DATABASE AdventureWorks2012   
 TO DISK = 'Z:\SQLServerBackups\AdvWorksData.bak'  
   WITH CHECKSUM, CONTINUE_AFTER_ERROR;  
GO  
```  
  
#### <a name="to-specify-whether-a-restore-operation-continues-or-stops-after-encountering-an-error"></a><span data-ttu-id="71b55-135">指定还原操作在遇到错误后是继续还是停止</span><span class="sxs-lookup"><span data-stu-id="71b55-135">To specify whether a restore operation continues or stops after encountering an error</span></span>  
  
1.  <span data-ttu-id="71b55-136">连接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="71b55-136">Connect to the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="71b55-137">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="71b55-137">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="71b55-138">在 [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) 语句中，指定 CONTINUE_AFTER ERROR 选项可继续操作，指定 STOP_ON_ERROR 选项可停止操作。</span><span class="sxs-lookup"><span data-stu-id="71b55-138">In the [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) statement, specify the CONTINUE_AFTER ERROR option to continue or the STOP_ON_ERROR option to stop.</span></span> <span data-ttu-id="71b55-139">默认行为是遇到错误后停止。</span><span class="sxs-lookup"><span data-stu-id="71b55-139">The default behavior is to stop after encountering an error.</span></span> <span data-ttu-id="71b55-140">下面的示例指示还原操作在遇到错误时仍继续。</span><span class="sxs-lookup"><span data-stu-id="71b55-140">This example instructs the restore operation to continue despite encountering an error.</span></span>  
  
```sql  
RESTORE DATABASE AdventureWorks2012   
 FROM DISK = 'Z:\SQLServerBackups\AdvWorksData.bak'   
   WITH CHECKSUM, CONTINUE_AFTER_ERROR;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="71b55-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="71b55-141">See Also</span></span>  
 <span data-ttu-id="71b55-142">[RESTORE FILELISTONLY (Transact-SQL)](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="71b55-142">[RESTORE FILELISTONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql) </span></span>  
 <span data-ttu-id="71b55-143">[RESTORE HEADERONLY (Transact-SQL)](/sql/t-sql/statements/restore-statements-headeronly-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="71b55-143">[RESTORE HEADERONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-headeronly-transact-sql) </span></span>  
 <span data-ttu-id="71b55-144">[RESTORE LABELONLY (Transact-SQL)](/sql/t-sql/statements/restore-statements-labelonly-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="71b55-144">[RESTORE LABELONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-labelonly-transact-sql) </span></span>  
 <span data-ttu-id="71b55-145">[RESTORE VERIFYONLY (Transact-SQL)](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="71b55-145">[RESTORE VERIFYONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql) </span></span>  
 <span data-ttu-id="71b55-146">[BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="71b55-146">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="71b55-147">[backupset (Transact-SQL)](/sql/relational-databases/system-tables/backupset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="71b55-147">[backupset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql) </span></span>  
 <span data-ttu-id="71b55-148">[RESTORE 参数 (Transact-SQL)](/sql/t-sql/statements/restore-statements-arguments-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="71b55-148">[RESTORE Arguments &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql) </span></span>  
 <span data-ttu-id="71b55-149">[备份和还原期间可能出现的媒体错误 (SQL Server)](possible-media-errors-during-backup-and-restore-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="71b55-149">[Possible Media Errors During Backup and Restore &#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md) </span></span>  
 [<span data-ttu-id="71b55-150">在备份或还原期间启用或禁用备份校验和 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="71b55-150">Enable or Disable Backup Checksums During Backup or Restore &#40;SQL Server&#41;</span></span>](enable-or-disable-backup-checksums-during-backup-or-restore-sql-server.md)  
  
  
