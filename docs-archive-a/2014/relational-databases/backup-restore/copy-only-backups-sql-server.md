---
title: 仅复制备份 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- copy-only backups [SQL Server]
- COPY_ONLY option [BACKUP statement]
- backups [SQL Server], copy-only backups
ms.assetid: f82d6918-a5a7-4af8-868e-4247f5b00c52
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: fc74d7b1bba2a0163ac9edefb5d465c54ef6296c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591410"
---
# <a name="copy-only-backups-sql-server"></a><span data-ttu-id="b3da8-102">仅复制备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="b3da8-102">Copy-Only Backups (SQL Server)</span></span>
  <span data-ttu-id="b3da8-103">*仅复制备份*是[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]独立于常规备份序列[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的备份。</span><span class="sxs-lookup"><span data-stu-id="b3da8-103">A *copy-only backup* is a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup that is independent of the sequence of conventional [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backups.</span></span> <span data-ttu-id="b3da8-104">通常，进行备份会更改数据库并影响其后备份的还原方式。</span><span class="sxs-lookup"><span data-stu-id="b3da8-104">Usually, taking a backup changes the database and affects how later backups are restored.</span></span> <span data-ttu-id="b3da8-105">但是，有时在不影响数据库总体备份和还原过程的情况下，为特殊目的而进行备份还是有用的。</span><span class="sxs-lookup"><span data-stu-id="b3da8-105">However, occasionally, it is useful to take a backup for a special purpose without affecting the overall backup and restore procedures for the database.</span></span> <span data-ttu-id="b3da8-106">仅复制备份就是用于此目的。</span><span class="sxs-lookup"><span data-stu-id="b3da8-106">Copy-only backups serve this purpose.</span></span>  
  
 <span data-ttu-id="b3da8-107">仅复制备份的类型如下所示：</span><span class="sxs-lookup"><span data-stu-id="b3da8-107">The types of copy-only backups are as follows:</span></span>  
  
-   <span data-ttu-id="b3da8-108">仅复制完整备份（所有恢复模式）</span><span class="sxs-lookup"><span data-stu-id="b3da8-108">Copy-only full backups (all recovery models)</span></span>  
  
     <span data-ttu-id="b3da8-109">仅复制备份不能用作差异基准或差异备份，并且不影响差异基准。</span><span class="sxs-lookup"><span data-stu-id="b3da8-109">A copy-only backup cannot serve as a differential base or differential backup and does not affect the differential base.</span></span>  
  
     <span data-ttu-id="b3da8-110">还原仅复制完整备份与还原任何其他完整备份相同。</span><span class="sxs-lookup"><span data-stu-id="b3da8-110">Restoring a copy-only full backup is the same as restoring any other full backup.</span></span>  
  
-   <span data-ttu-id="b3da8-111">仅复制日志备份（仅限于完整恢复模式和大容量日志恢复模式）</span><span class="sxs-lookup"><span data-stu-id="b3da8-111">Copy-only log backups (full recovery model and bulk-logged recovery model only)</span></span>  
  
     <span data-ttu-id="b3da8-112">仅复制日志备份保留当前日志存档点，因此，不影响常规日志备份的序列。</span><span class="sxs-lookup"><span data-stu-id="b3da8-112">A copy-only log backup preserves the existing log archive point and, therefore, does not affect the sequencing of regular log backups.</span></span> <span data-ttu-id="b3da8-113">通常不必进行仅复制日志备份。</span><span class="sxs-lookup"><span data-stu-id="b3da8-113">Copy-only log backups are typically unnecessary.</span></span> <span data-ttu-id="b3da8-114">相反，您可以创建新的常规日志备份（使用 WITH NORECOVERY），然后将该备份与还原序列所需的任何以前的日志备份一起使用。</span><span class="sxs-lookup"><span data-stu-id="b3da8-114">Instead, you can create a new routine log backup (using WITH NORECOVERY) and use that backup together with any previous log backups that are required for the restore sequence.</span></span> <span data-ttu-id="b3da8-115">但是，仅复制日志备份有时可用于执行联机还原。</span><span class="sxs-lookup"><span data-stu-id="b3da8-115">However, a copy-only log backup can sometimes be useful for performing an online restore.</span></span> <span data-ttu-id="b3da8-116">关于这方面的示例，请参阅[示例：读/写文件的联机还原（完整恢复模式）](example-online-restore-of-a-read-write-file-full-recovery-model.md)。</span><span class="sxs-lookup"><span data-stu-id="b3da8-116">For an example of this, see [Example: Online Restore of a Read-Write File &#40;Full Recovery Model&#41;](example-online-restore-of-a-read-write-file-full-recovery-model.md).</span></span>  
  
     <span data-ttu-id="b3da8-117">事务日志从不在仅复制备份后出现截断。</span><span class="sxs-lookup"><span data-stu-id="b3da8-117">The transaction log is never truncated after a copy-only backup.</span></span>  
  
 <span data-ttu-id="b3da8-118">仅复制备份记录在 **backupset** 表的 [is_copy_only](/sql/relational-databases/system-tables/backupset-transact-sql) 列中。</span><span class="sxs-lookup"><span data-stu-id="b3da8-118">Copy-only backups are recorded in the **is_copy_only** column of the [backupset](/sql/relational-databases/system-tables/backupset-transact-sql) table.</span></span>  
  
## <a name="to-create-a-copy-only-backup"></a><span data-ttu-id="b3da8-119">创建仅复制备份</span><span class="sxs-lookup"><span data-stu-id="b3da8-119">To Create a Copy-Only Backup</span></span>  
 <span data-ttu-id="b3da8-120">您可以通过使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、 [!INCLUDE[tsql](../../../includes/tsql-md.md)]或 PowerShell 创建仅复制备份。</span><span class="sxs-lookup"><span data-stu-id="b3da8-120">You can create a copy-only backup by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell.</span></span>  
  
###  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="b3da8-121">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b3da8-121">Using SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="b3da8-122">在 **“备份数据库”** 对话框的 **“常规”** 页上，选择 **“仅复制备份”** 选项。</span><span class="sxs-lookup"><span data-stu-id="b3da8-122">On the **General** page of the **Back Up Database** dialog box, select the **Copy Only Backup** option.</span></span>  
  
###  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="b3da8-123">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b3da8-123">Using Transact-SQL</span></span>  
 <span data-ttu-id="b3da8-124">基本 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 语法如下所示：</span><span class="sxs-lookup"><span data-stu-id="b3da8-124">The essential [!INCLUDE[tsql](../../../includes/tsql-md.md)] syntax is as follows:</span></span>  
  
-   <span data-ttu-id="b3da8-125">对于仅复制完整备份：</span><span class="sxs-lookup"><span data-stu-id="b3da8-125">For a copy-only full backup:</span></span>  
  
     <span data-ttu-id="b3da8-126">备份数据库*database_name*到 \<backup_device*> \* .。。COPY_ONLY .。。</span><span class="sxs-lookup"><span data-stu-id="b3da8-126">BACKUP DATABASE *database_name* TO \<backup_device*>\* ... WITH COPY_ONLY ...</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b3da8-127">使用 DIFFERENTIAL 选项指定时，COPY_ONLY 不起作用。</span><span class="sxs-lookup"><span data-stu-id="b3da8-127">COPY_ONLY has no effect when specified with the DIFFERENTIAL option.</span></span>  
  
-   <span data-ttu-id="b3da8-128">对于仅复制日志备份：</span><span class="sxs-lookup"><span data-stu-id="b3da8-128">For a copy-only log backup:</span></span>  
  
     <span data-ttu-id="b3da8-129">备份日志*database_name*到 *\<*backup_device*>* .。。COPY_ONLY .。。</span><span class="sxs-lookup"><span data-stu-id="b3da8-129">BACKUP LOG *database_name* TO *\<*backup_device*>* ... WITH COPY_ONLY ...</span></span>  
  
###  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="b3da8-130">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="b3da8-130">Using PowerShell</span></span>  
  
<span data-ttu-id="b3da8-131">将 `Backup-SqlDatabase` cmdlet 与 `-CopyOnly` 参数一起使用。</span><span class="sxs-lookup"><span data-stu-id="b3da8-131">Use the `Backup-SqlDatabase` cmdlet with the `-CopyOnly` parameter.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="b3da8-132">相关任务</span><span class="sxs-lookup"><span data-stu-id="b3da8-132">Related Tasks</span></span>  

### <a name="to-create-a-full-or-log-backup"></a><span data-ttu-id="b3da8-133">创建完整备份或日志备份</span><span class="sxs-lookup"><span data-stu-id="b3da8-133">To create a full or log backup</span></span>
  
-   [<span data-ttu-id="b3da8-134">创建完整数据库备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="b3da8-134">Create a Full Database Backup &#40;SQL Server&#41;</span></span>](create-a-full-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="b3da8-135">备份事务日志 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="b3da8-135">Back Up a Transaction Log &#40;SQL Server&#41;</span></span>](back-up-a-transaction-log-sql-server.md)  
  
### <a name="to-view-copy-only-backups"></a><span data-ttu-id="b3da8-136">查看仅复制备份</span><span class="sxs-lookup"><span data-stu-id="b3da8-136">To view copy-only backups</span></span>
  
-   [<span data-ttu-id="b3da8-137">backupset (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b3da8-137">backupset &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-tables/backupset-transact-sql)  
  
### <a name="to-set-up-and-use-the-sql-server-powershell-provider"></a><span data-ttu-id="b3da8-138">设置和使用 SQL Server PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="b3da8-138">To set up and use the SQL Server PowerShell provider</span></span>
  
-   [<span data-ttu-id="b3da8-139">SQL Server PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="b3da8-139">SQL Server PowerShell Provider</span></span>](../../powershell/sql-server-powershell-provider.md)  

## <a name="see-also"></a><span data-ttu-id="b3da8-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b3da8-140">See Also</span></span>  
 <span data-ttu-id="b3da8-141">[备份概述 (SQL Server)](backup-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="b3da8-141">[Backup Overview &#40;SQL Server&#41;](backup-overview-sql-server.md) </span></span>  
 <span data-ttu-id="b3da8-142">[恢复模式 (SQL Server)](recovery-models-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="b3da8-142">[Recovery Models &#40;SQL Server&#41;](recovery-models-sql-server.md) </span></span>  
 <span data-ttu-id="b3da8-143">[通过备份和还原来复制数据库](../databases/copy-databases-with-backup-and-restore.md) </span><span class="sxs-lookup"><span data-stu-id="b3da8-143">[Copy Databases with Backup and Restore](../databases/copy-databases-with-backup-and-restore.md) </span></span>  
 [<span data-ttu-id="b3da8-144">还原和恢复概述 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="b3da8-144">Restore and Recovery Overview &#40;SQL Server&#41;</span></span>](restore-and-recovery-overview-sql-server.md)  
