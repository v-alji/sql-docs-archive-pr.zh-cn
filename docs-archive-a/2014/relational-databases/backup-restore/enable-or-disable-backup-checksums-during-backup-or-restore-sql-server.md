---
title: 在备份或还原期间启用或禁用备份校验和 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- backup checksums [SQL Server]
- disabling checksums
- checksums [SQL Server]
ms.assetid: 6786bd1e-ad97-430a-8dfb-d4ba952d6c4d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a239dcdfca689be8555117104264d66a2ac037f1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694004"
---
# <a name="enable-or-disable-backup-checksums-during-backup-or-restore-sql-server"></a><span data-ttu-id="a31ea-102">在备份或还原期间启用或禁用备份校验和 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="a31ea-102">Enable or Disable Backup Checksums During Backup or Restore (SQL Server)</span></span>
  <span data-ttu-id="a31ea-103">本主题说明当备份或还原数据库时如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中启用或禁用备份校验和。</span><span class="sxs-lookup"><span data-stu-id="a31ea-103">This topic describes how to enable or disable backup checksums when you are backing up or restoring a database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="a31ea-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="a31ea-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="a31ea-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="a31ea-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="a31ea-106">安全性</span><span class="sxs-lookup"><span data-stu-id="a31ea-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="a31ea-107">**若要启用或禁用备份校验和，请使用：**</span><span class="sxs-lookup"><span data-stu-id="a31ea-107">**To enable or disable backup checksums, using:**</span></span>  
  
     [<span data-ttu-id="a31ea-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a31ea-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="a31ea-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a31ea-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="a31ea-110">开始之前</span><span class="sxs-lookup"><span data-stu-id="a31ea-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="a31ea-111">Security</span><span class="sxs-lookup"><span data-stu-id="a31ea-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="a31ea-112">权限</span><span class="sxs-lookup"><span data-stu-id="a31ea-112">Permissions</span></span>  
 <span data-ttu-id="a31ea-113">BACKUP</span><span class="sxs-lookup"><span data-stu-id="a31ea-113">BACKUP</span></span>  
 <span data-ttu-id="a31ea-114">默认情况下，为 **sysadmin** 固定服务器角色以及 **db_owner** 和 **db_backupoperator** 固定数据库角色的成员授予 BACKUP DATABASE 和 BACKUP LOG 权限。</span><span class="sxs-lookup"><span data-stu-id="a31ea-114">BACKUP DATABASE and BACKUP LOG permissions default to members of the **sysadmin** fixed server role and the **db_owner** and **db_backupoperator** fixed database roles.</span></span>  
  
 <span data-ttu-id="a31ea-115">备份设备的物理文件的所有权和权限问题可能会妨碍备份操作。</span><span class="sxs-lookup"><span data-stu-id="a31ea-115">Ownership and permission problems on the backup device's physical file can interfere with a backup operation.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="a31ea-116">必须能够读取和写入设备；运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务的帐户必须具有写入权限。</span><span class="sxs-lookup"><span data-stu-id="a31ea-116">must be able to read and write to the device; the account under which the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service runs must have write permissions.</span></span> <span data-ttu-id="a31ea-117">但是，用于在系统表中为备份设备添加项目的 [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql)不检查文件访问权限。</span><span class="sxs-lookup"><span data-stu-id="a31ea-117">However, [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql), which adds an entry for a backup device in the system tables, does not check file access permissions.</span></span> <span data-ttu-id="a31ea-118">备份设备物理文件的这些问题可能直到为备份或还原而访问物理资源时才会出现。</span><span class="sxs-lookup"><span data-stu-id="a31ea-118">Such problems on the backup device's physical file may not appear until the physical resource is accessed when the backup or restore is attempted.</span></span>  
  
 <span data-ttu-id="a31ea-119">RESTORE</span><span class="sxs-lookup"><span data-stu-id="a31ea-119">RESTORE</span></span>  
 <span data-ttu-id="a31ea-120">如果不存在要还原的数据库，则用户必须有 CREATE DATABASE 权限才能执行 RESTORE。</span><span class="sxs-lookup"><span data-stu-id="a31ea-120">If the database being restored does not exist, the user must have CREATE DATABASE permissions to be able to execute RESTORE.</span></span> <span data-ttu-id="a31ea-121">如果数据库存在，则 RESTORE 权限默认授予 **sysadmin** 和 **dbcreator** 固定服务器角色成员以及数据库的所有者 (**dbo**)（对于 FROM DATABASE_SNAPSHOT 选项，数据库始终存在）。</span><span class="sxs-lookup"><span data-stu-id="a31ea-121">If the database exists, RESTORE permissions default to members of the **sysadmin** and **dbcreator** fixed server roles and the owner (**dbo**) of the database (for the FROM DATABASE_SNAPSHOT option, the database always exists).</span></span>  
  
 <span data-ttu-id="a31ea-122">RESTORE 权限被授予那些成员身份信息始终可由服务器使用的角色。</span><span class="sxs-lookup"><span data-stu-id="a31ea-122">RESTORE permissions are given to roles in which membership information is always readily available to the server.</span></span> <span data-ttu-id="a31ea-123">因为只有在固定数据库可以访问且没有损坏时（在执行 RESTORE 时并不会总是这样）才能检查固定数据库角色成员身份，所以 **db_owner** 固定数据库角色成员没有 RESTORE 权限。</span><span class="sxs-lookup"><span data-stu-id="a31ea-123">Because fixed database role membership can be checked only when the database is accessible and undamaged, which is not always the case when RESTORE is executed, members of the **db_owner** fixed database role do not have RESTORE permissions.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="a31ea-124">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a31ea-124">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-enable-or-disable-checksums-during-a-backup-operation"></a><span data-ttu-id="a31ea-125">在备份操作期间启用或禁用校验和</span><span class="sxs-lookup"><span data-stu-id="a31ea-125">To enable or disable checksums during a backup operation</span></span>  
  
1.  <span data-ttu-id="a31ea-126">执行以下步骤以便 [创建数据库备份](create-a-full-database-backup-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="a31ea-126">Follow the steps to [create a database backup](create-a-full-database-backup-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="a31ea-127">在 **“选项”** 页的 **“可靠性”** 部分中，单击 **“写入介质前检查校验和”** 。</span><span class="sxs-lookup"><span data-stu-id="a31ea-127">On the **Options** page, in the **Reliability** section, click **Perform checksum before writing to media**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="a31ea-128">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a31ea-128">Using Transact-SQL</span></span>  
  
#### <a name="to-enable-or-disable-backup-checksum-for-a-backup-operation"></a><span data-ttu-id="a31ea-129">为备份操作启用或禁用备份校验和</span><span class="sxs-lookup"><span data-stu-id="a31ea-129">To enable or disable backup checksum for a backup operation</span></span>  
  
1.  <span data-ttu-id="a31ea-130">连接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a31ea-130">Connect to the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="a31ea-131">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="a31ea-131">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="a31ea-132">若要启用备份校验和，请在 [BACKUP](/sql/t-sql/statements/backup-transact-sql) 语句中指定 WITH CHECKSUM 选项。</span><span class="sxs-lookup"><span data-stu-id="a31ea-132">To enable backup checksums in a [BACKUP](/sql/t-sql/statements/backup-transact-sql) statement, specify the WITH CHECKSUM option.</span></span> <span data-ttu-id="a31ea-133">若要禁用备份校验和，请指定 WITH NO_CHECKSUM 选项。</span><span class="sxs-lookup"><span data-stu-id="a31ea-133">To disable backup checksums, specify the WITH NO_CHECKSUM option.</span></span> <span data-ttu-id="a31ea-134">这是默认行为，但压缩备份除外。</span><span class="sxs-lookup"><span data-stu-id="a31ea-134">This is the default behavior, except for a compressed backup.</span></span> <span data-ttu-id="a31ea-135">下面的示例指定执行校验和。</span><span class="sxs-lookup"><span data-stu-id="a31ea-135">The following example specifies that checksums be performed.</span></span>  
  
```sql  
BACKUP DATABASE AdventureWorks2012   
 TO DISK = 'Z:\SQLServerBackups\AdvWorksData.bak'  
   WITH CHECKSUM;  
GO  
```  
  
#### <a name="to-enable-or-disable-backup-checksum-for-a-restore-operation"></a><span data-ttu-id="a31ea-136">为还原操作启用或禁用备份校验和</span><span class="sxs-lookup"><span data-stu-id="a31ea-136">To enable or disable backup checksum for a restore operation</span></span>  
  
1.  <span data-ttu-id="a31ea-137">连接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a31ea-137">Connect to the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="a31ea-138">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="a31ea-138">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="a31ea-139">若要启用备份校验和，请在 [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) 语句中指定 WITH CHECKSUM 选项。</span><span class="sxs-lookup"><span data-stu-id="a31ea-139">To enable backup checksums in a [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) statement, specify the WITH CHECKSUM option.</span></span> <span data-ttu-id="a31ea-140">这是压缩备份的默认行为。</span><span class="sxs-lookup"><span data-stu-id="a31ea-140">This is the default behavior for a compressed backup.</span></span> <span data-ttu-id="a31ea-141">若要禁用备份校验和，请指定 WITH NO_CHECKSUM 选项。</span><span class="sxs-lookup"><span data-stu-id="a31ea-141">To disable backup checksums, specify the WITH NO_CHECKSUM option.</span></span> <span data-ttu-id="a31ea-142">这是默认行为，但压缩备份除外。</span><span class="sxs-lookup"><span data-stu-id="a31ea-142">This is the default behavior, except for a compressed backup.</span></span> <span data-ttu-id="a31ea-143">下面的示例指定执行备份校验和。</span><span class="sxs-lookup"><span data-stu-id="a31ea-143">The following example specifies that backup checksums be performed.</span></span>  
  
```sql  
RESTORE DATABASE AdventureWorks2012   
 FROM DISK = 'Z:\SQLServerBackups\AdvWorksData.bak'  
   WITH CHECKSUM;  
GO  
```  
  
> [!WARNING]  
>  <span data-ttu-id="a31ea-144">在明确请求 CHECKSUM 进行还原操作并且备份包含备份校验和时，与默认情况相同，将同时验证备份校验和及页校验和。</span><span class="sxs-lookup"><span data-stu-id="a31ea-144">If you explicitly request CHECKSUM for a restore operation and if the backup contains backup checksums, backup checksums and page checksums are both verified, as in the default case.</span></span> <span data-ttu-id="a31ea-145">但是，如果备份集不包含备份校验和，还原操作将失败，并显示一条消息指明校验和不存在。</span><span class="sxs-lookup"><span data-stu-id="a31ea-145">However, if the backup set lacks backup checksums, the restore operation fails with a message indicating that checksums are not present.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a31ea-146">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a31ea-146">See Also</span></span>  
 <span data-ttu-id="a31ea-147">[RESTORE FILELISTONLY (Transact-SQL)](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a31ea-147">[RESTORE FILELISTONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql) </span></span>  
 <span data-ttu-id="a31ea-148">[RESTORE HEADERONLY (Transact-SQL)](/sql/t-sql/statements/restore-statements-headeronly-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a31ea-148">[RESTORE HEADERONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-headeronly-transact-sql) </span></span>  
 <span data-ttu-id="a31ea-149">[RESTORE LABELONLY (Transact-SQL)](/sql/t-sql/statements/restore-statements-labelonly-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a31ea-149">[RESTORE LABELONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-labelonly-transact-sql) </span></span>  
 <span data-ttu-id="a31ea-150">[RESTORE VERIFYONLY (Transact-SQL)](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a31ea-150">[RESTORE VERIFYONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql) </span></span>  
 <span data-ttu-id="a31ea-151">[BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a31ea-151">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="a31ea-152">[backupset (Transact-SQL)](/sql/relational-databases/system-tables/backupset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a31ea-152">[backupset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql) </span></span>  
 <span data-ttu-id="a31ea-153">[RESTORE 参数 (Transact-SQL)](/sql/t-sql/statements/restore-statements-arguments-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a31ea-153">[RESTORE Arguments &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql) </span></span>  
 <span data-ttu-id="a31ea-154">[备份和还原期间可能出现的媒体错误 (SQL Server)](possible-media-errors-during-backup-and-restore-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a31ea-154">[Possible Media Errors During Backup and Restore &#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md) </span></span>  
 [<span data-ttu-id="a31ea-155">指定备份或还原操作在遇到错误后是继续还是停止 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="a31ea-155">Specify Whether a Backup or Restore Operation Continues or Stops After Encountering an Error &#40;SQL Server&#41;</span></span>](specify-if-backup-or-restore-continues-or-stops-after-error.md)  
  
  
