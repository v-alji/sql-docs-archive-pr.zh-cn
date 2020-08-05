---
title: 在完整恢复模式下将数据库还原到故障点， (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- point of failure [SQL Server]
- restoring databases [SQL Server], point of failure
- database restores [SQL Server], point of failure
ms.assetid: 04106e18-bbf7-4a5e-a2e1-3d65319814d5
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 95b73660ebb44f4daffe6eaefd873699cfbbd8ca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581318"
---
# <a name="restore-a-database-to-the-point-of-failure-under-the-full-recovery-model-transact-sql"></a><span data-ttu-id="fd0e8-102">在完整恢复模式下将数据库还原到故障点 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="fd0e8-102">Restore a Database to the Point of Failure Under the Full Recovery Model (Transact-SQL)</span></span>
  <span data-ttu-id="fd0e8-103">本主题说明如何还原到故障点。</span><span class="sxs-lookup"><span data-stu-id="fd0e8-103">This topic explains how to restore to the point of failure.</span></span> <span data-ttu-id="fd0e8-104">本主题仅与那些使用完整或大容量日志恢复模式的数据库相关。</span><span class="sxs-lookup"><span data-stu-id="fd0e8-104">The topic is relevant only for databases that are using the full or bulk-logged recovery models.</span></span>  
  
### <a name="to-restore-to-the-point-of-failure"></a><span data-ttu-id="fd0e8-105">还原到故障点</span><span class="sxs-lookup"><span data-stu-id="fd0e8-105">To restore to the point of failure</span></span>  
  
1.  <span data-ttu-id="fd0e8-106">通过运行以下基本 [BACKUP](/sql/t-sql/statements/backup-transact-sql) 语句来备份日志尾部：</span><span class="sxs-lookup"><span data-stu-id="fd0e8-106">Back up the tail of the log by running the following basic [BACKUP](/sql/t-sql/statements/backup-transact-sql) statement:</span></span>  
  
    ```  
    BACKUP LOG <database_name> TO <backup_device>   
       WITH NORECOVERY, NO_TRUNCATE;  
    ```  
  
2.  <span data-ttu-id="fd0e8-107">通过运行以下基本 [RESTORE DATABASE](/sql/t-sql/statements/restore-statements-transact-sql) 语句来还原完整数据库备份：</span><span class="sxs-lookup"><span data-stu-id="fd0e8-107">Restore a full database backup by running the following basic [RESTORE DATABASE](/sql/t-sql/statements/restore-statements-transact-sql) statement:</span></span>  
  
    ```  
    RESTORE DATABASE <database_name> FROM <backup_device>   
       WITH NORECOVERY;  
    ```  
  
3.  <span data-ttu-id="fd0e8-108">或者，通过运行以下基本 RESTORE DATABASE 语句来还原差异数据库备份：</span><span class="sxs-lookup"><span data-stu-id="fd0e8-108">Optionally, restore a differential database backup by running the following basic RESTORE DATABASE statement:</span></span>  
  
    ```  
    RESTORE DATABASE <database_name> FROM <backup_device>   
       WITH NORECOVERY;  
    ```  
  
4.  <span data-ttu-id="fd0e8-109">通过在 RESTORE LOG 语句中指定 WITH NORECOVERY 以应用每个事务日志（包括步骤 1 中创建的结尾日志备份）：</span><span class="sxs-lookup"><span data-stu-id="fd0e8-109">Apply each transaction log, including the tail-log backup you created in step 1, by specifying WITH NORECOVERY in the RESTORE LOG statement:</span></span>  
  
    ```  
    RESTORE LOG <database_name> FROM <backup_device>   
       WITH NORECOVERY;  
    ```  
  
5.  <span data-ttu-id="fd0e8-110">通过运行以下 RESTORE DATABASE 语句来恢复数据库：</span><span class="sxs-lookup"><span data-stu-id="fd0e8-110">Recover the database by running the following RESTORE DATABASE statement:</span></span>  
  
    ```  
    RESTORE DATABASE <database_name>   
       WITH RECOVERY;  
    ```  
  
## <a name="example"></a><span data-ttu-id="fd0e8-111">示例</span><span class="sxs-lookup"><span data-stu-id="fd0e8-111">Example</span></span>  
 <span data-ttu-id="fd0e8-112">必须先完成下列准备工作，才能运行此示例：</span><span class="sxs-lookup"><span data-stu-id="fd0e8-112">Before you can run the example, you must complete the following preparations:</span></span>  
  
1.  <span data-ttu-id="fd0e8-113">[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 数据库的默认恢复模式是简单恢复模式。</span><span class="sxs-lookup"><span data-stu-id="fd0e8-113">The default recovery model of the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database is the simple recovery model.</span></span> <span data-ttu-id="fd0e8-114">由于该恢复模式不支持还原到故障点，因此请将 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 设置为使用完整恢复模式，方法是运行以下 [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) 语句：</span><span class="sxs-lookup"><span data-stu-id="fd0e8-114">Because this recovery model does not support restoring to the point of a failure, set [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] to use the full recovery model by running the following [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) statement:</span></span>  
  
    ```  
    USE master;  
    GO  
    ALTER DATABASE AdventureWorks2012 SET RECOVERY FULL;  
    ```  
  
2.  <span data-ttu-id="fd0e8-115">通过使用以下 BACKUP 语句，创建数据库的完整数据库备份：</span><span class="sxs-lookup"><span data-stu-id="fd0e8-115">Create a full database back of the database by using the following BACKUP statement:</span></span>  
  
    ```  
    BACKUP DATABASE AdventureWorks2012 TO DISK = 'C:\AdventureWorks2012_Data.bck';  
    ```  
  
3.  <span data-ttu-id="fd0e8-116">创建例程日志备份：</span><span class="sxs-lookup"><span data-stu-id="fd0e8-116">Create a routine log backup:</span></span>  
  
    ```  
    BACKUP LOG AdventureWorks2012 TO DISK = 'C:\AdventureWorks2012_Log.bck';  
    ```  
  
 <span data-ttu-id="fd0e8-117">以下示例在创建 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 数据库的结尾日志备份后，将还原先前创建的备份。</span><span class="sxs-lookup"><span data-stu-id="fd0e8-117">The following example restores the backups that are created previously, after creating a tail-log backup of the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span> <span data-ttu-id="fd0e8-118">（此步骤假设可以访问日志磁盘。）</span><span class="sxs-lookup"><span data-stu-id="fd0e8-118">(This step assumes that the log disk can be accessed.)</span></span>  
  
 <span data-ttu-id="fd0e8-119">首先，该示例将创建捕获活动日志的数据库结尾日志备份，并使数据库处于还原状态。</span><span class="sxs-lookup"><span data-stu-id="fd0e8-119">First, the example creates a tail-log backup of the database that captures the active log and leaves the database in the Restoring state.</span></span> <span data-ttu-id="fd0e8-120">然后，该示例将还原数据库备份，应用先前创建的例程日志备份，并应用结尾日志备份。</span><span class="sxs-lookup"><span data-stu-id="fd0e8-120">Then, the example restores the database backup, applies the routine log backup created previously, and applies the tail-log backup.</span></span> <span data-ttu-id="fd0e8-121">最后，该示例将在单独的步骤中恢复数据库。</span><span class="sxs-lookup"><span data-stu-id="fd0e8-121">Finally, the example recovers the database in a separate step.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fd0e8-122">默认行为是将数据库恢复作为还原最终备份语句的一部分。</span><span class="sxs-lookup"><span data-stu-id="fd0e8-122">The default behavior is to recover a database as part of the statement that restores the final backup.</span></span>  
  
```  
/* Example of restoring a to the point of failure */  
-- Step 1: Create a tail-log backup by using WITH NORECOVERY.  
BACKUP LOG AdventureWorks2012  
   TO DISK = 'C:\AdventureWorks2012_Log.bck'  
   WITH NORECOVERY;  
GO  
-- Step 2: Restore the full database backup.  
RESTORE DATABASE AdventureWorks2012  
   FROM DISK = 'C:\AdventureWorks2012_Data.bck'  
   WITH NORECOVERY;  
GO  
-- Step 3: Restore the first transaction log backup.  
RESTORE LOG AdventureWorks2012  
   FROM DISK = 'C:\AdventureWorks2012_Log.bck'  
   WITH NORECOVERY;  
GO  
-- Step 4: Restore the tail-log backup.  
RESTORE LOG AdventureWorks2012  
   FROM  DISK = 'C:\AdventureWorks2012_Log.bck'  
   WITH NORECOVERY;  
GO  
-- Step 5: Recover the database.  
RESTORE DATABASE AdventureWorks2012  
   WITH RECOVERY;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="fd0e8-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fd0e8-123">See Also</span></span>  
 <span data-ttu-id="fd0e8-124">[BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="fd0e8-124">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 [<span data-ttu-id="fd0e8-125">RESTORE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="fd0e8-125">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
