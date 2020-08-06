---
title: 恢复到日志序列号 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- log sequence numbers [SQL Server]
- STOPBEFOREMARK option [RESTORE statement]
- STOPATMARK option [RESTORE statement]
- point in time recovery [SQL Server]
- restoring databases [SQL Server], point in time
- recovery [SQL Server], databases
- restoring [SQL Server], point in time
- LSNs
- database recovery [SQL Server]
- database restores [SQL Server], point in time
ms.assetid: f7b3de5b-198d-448d-8c71-1cdd9239676c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4df55c3468fc009d86cffd58a837d6935f5ce14b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589171"
---
# <a name="recover-to-a-log-sequence-number-sql-server"></a><span data-ttu-id="16ada-102">恢复到日志序列号 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="16ada-102">Recover to a Log Sequence Number (SQL Server)</span></span>
  <span data-ttu-id="16ada-103">本主题仅与使用完整恢复模式或大容量日志恢复模式的数据库相关。</span><span class="sxs-lookup"><span data-stu-id="16ada-103">This topic is relevant only for databases that are using the full or bulk-logged recovery models.</span></span>  
  
 <span data-ttu-id="16ada-104">您可以使用日志序列号 (LSN) 定义还原操作的恢复点。</span><span class="sxs-lookup"><span data-stu-id="16ada-104">You can use a log sequence number (LSN) to define the recovery point for a restore operation.</span></span> <span data-ttu-id="16ada-105">但是，这是为工具供应商提供的专用功能，不太可能广泛使用。</span><span class="sxs-lookup"><span data-stu-id="16ada-105">However, this is a specialized feature that is intended for tools vendors and is unlikely to be generally useful.</span></span>  
  
##  <a name="overview-of-log-sequence-numbers"></a><a name="LSNs"></a> <span data-ttu-id="16ada-106">日志序列号的概述</span><span class="sxs-lookup"><span data-stu-id="16ada-106">Overview of Log Sequence Numbers</span></span>  
 <span data-ttu-id="16ada-107">RESTORE 顺序期间，在内部使用 LSN 跟踪数据还原到的时间点。</span><span class="sxs-lookup"><span data-stu-id="16ada-107">LSNs are used internally during a RESTORE sequence to track the point in time to which data has been restored.</span></span> <span data-ttu-id="16ada-108">还原备份后，数据被还原到与进行备份的时间点相对应的 LSN。</span><span class="sxs-lookup"><span data-stu-id="16ada-108">When a backup is restored, the data is restored to the LSN corresponding to the point in time at which the backup was taken.</span></span> <span data-ttu-id="16ada-109">差异和日志备份将还原的数据库推到稍后的时间，该时间与一个更高的 LSN 相对应。</span><span class="sxs-lookup"><span data-stu-id="16ada-109">Differential and log backups advance the restored database to a later time, which corresponds to a higher LSN.</span></span>  
  
 <span data-ttu-id="16ada-110">事务日志中的每个记录都由一个日志序列号 (LSN) 唯一标识。</span><span class="sxs-lookup"><span data-stu-id="16ada-110">Every record in the transaction log is uniquely identified by a log sequence number (LSN).</span></span> <span data-ttu-id="16ada-111">LSN 是这样排序的：如果 LSN2 大于 LSN1，则 LSN2 所标识的日志记录描述的更改发生在日志记录 LSN1 描述的更改之后。</span><span class="sxs-lookup"><span data-stu-id="16ada-111">LSNs are ordered such that if LSN2 is greater than LSN1, the change described by the log record referred to by LSN2 occurred after the change described by the log record LSN.</span></span>  
  
 <span data-ttu-id="16ada-112">发生重大事件的日志记录的 LSN 对于构造正确的还原顺序可能很有用。</span><span class="sxs-lookup"><span data-stu-id="16ada-112">The LSN of a log record at which a significant event occurred can be useful for constructing correct restore sequences.</span></span> <span data-ttu-id="16ada-113">因为 Lsn 是有序的，所以可以比较它们的相等性和不相等性 (，即、 **\<**, **>** **=** **\<=**, **>=**) 。</span><span class="sxs-lookup"><span data-stu-id="16ada-113">Because LSNs are ordered, they can be compared for equality and inequality (that is, **\<**, **>**, **=**, **\<=**, **>=**).</span></span> <span data-ttu-id="16ada-114">构造还原顺序时，这种比较很有用。</span><span class="sxs-lookup"><span data-stu-id="16ada-114">Such comparisons are useful when constructing restore sequences.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="16ada-115">LSN 是数据类型为 `numeric` 的值 (25,0)。</span><span class="sxs-lookup"><span data-stu-id="16ada-115">LSNs are values of data type `numeric`(25,0).</span></span> <span data-ttu-id="16ada-116">算术运算（例如加法或减法）对 LSN 没有任何意义，请不要与 LSN 一起使用。</span><span class="sxs-lookup"><span data-stu-id="16ada-116">Arithmetic operations (for example, addition or subtraction) are not meaningful and must not be used with LSNs.</span></span>  
  

  
## <a name="viewing-lsns-used-by-backup-and-restore"></a><span data-ttu-id="16ada-117">查看备份和还原使用的 LSN</span><span class="sxs-lookup"><span data-stu-id="16ada-117">Viewing LSNs Used by Backup and Restore</span></span>  
 <span data-ttu-id="16ada-118">使用下列一种或几种方法可以查看发生给定备份和还原事件的日志记录的 LSN：</span><span class="sxs-lookup"><span data-stu-id="16ada-118">The LSN of a log record at which a given backup and restore event occurred is viewable using one or more of the following:</span></span>  
  
-   [<span data-ttu-id="16ada-119">backupset</span><span class="sxs-lookup"><span data-stu-id="16ada-119">backupset</span></span>](/sql/relational-databases/system-tables/backupset-transact-sql)  
  
-   [<span data-ttu-id="16ada-120">backupfile</span><span class="sxs-lookup"><span data-stu-id="16ada-120">backupfile</span></span>](/sql/relational-databases/system-tables/backupfile-transact-sql)  
  
-   <span data-ttu-id="16ada-121">[sys.database_files](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql)； [sys.master_files](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="16ada-121">[sys.database_files](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql); [sys.master_files](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql)</span></span>  
  
-   [<span data-ttu-id="16ada-122">RESTORE HEADERONLY</span><span class="sxs-lookup"><span data-stu-id="16ada-122">RESTORE HEADERONLY</span></span>](/sql/t-sql/statements/restore-statements-headeronly-transact-sql)  
  
-   [<span data-ttu-id="16ada-123">RESTORE FILELISTONLY</span><span class="sxs-lookup"><span data-stu-id="16ada-123">RESTORE FILELISTONLY</span></span>](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql)  
  
> [!NOTE]  
>  <span data-ttu-id="16ada-124">LSN 还显示在某些消息正文中。</span><span class="sxs-lookup"><span data-stu-id="16ada-124">LSNs also appear in some message texts.</span></span>  
  
## <a name="transact-sql-syntax-for-restoring-to-an-lsn"></a><span data-ttu-id="16ada-125">还原到 LSN 的 Transact-SQL 语法</span><span class="sxs-lookup"><span data-stu-id="16ada-125">Transact-SQL Syntax for Restoring to an LSN</span></span>  
 <span data-ttu-id="16ada-126">通过使用 [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) 语句，可以在 LSN 处或刚好在 LSN 之前停止，如下所示：</span><span class="sxs-lookup"><span data-stu-id="16ada-126">By using a [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) statement, you can stop at or immediately before the LSN, as follows:</span></span>  
  
-   <span data-ttu-id="16ada-127">使用 WITH STOPATMARK ='lsn:<lsn_number>' 子句，其中 lsn:\<lsnNumber> 是一个字符串，它指出包含指定 LSN 的日志记录是恢复点。</span><span class="sxs-lookup"><span data-stu-id="16ada-127">Use the WITH STOPATMARK **='** lsn:_<lsn_number>_**'** clause, where lsn:*\<lsnNumber>* is a string that specifies that the log record that contains the specified LSN is the recovery point.</span></span>  
  
     <span data-ttu-id="16ada-128">STOPATMARK 前滚到 LSN，并且前滚中包括该日志记录。</span><span class="sxs-lookup"><span data-stu-id="16ada-128">STOPATMARK roll forwards to the LSN and includes that log record in the roll forward.</span></span>  
  
-   <span data-ttu-id="16ada-129">使用 WITH STOPBEFOREMARK ='lsn:<lsn_number>' 子句，其中 lsn:\<lsnNumber> 是一个字符串，它指出包含指定 LSN 编号的日志记录之前的日志记录是恢复点。</span><span class="sxs-lookup"><span data-stu-id="16ada-129">Use the WITH STOPBEFOREMARK **='** lsn:_<lsn_number>_**'** clause, where lsn:*\<lsnNumber>* is a string that specifies that the log record immediately before the log record that contains the specified LSN number is the recovery point.</span></span>  
  
     <span data-ttu-id="16ada-130">STOPBEFOREMARK 前滚到 LSN，并从前滚中排除该日志记录。</span><span class="sxs-lookup"><span data-stu-id="16ada-130">STOPBEFOREMARK rolls forward to the LSN and excludes that log record from the roll forward.</span></span>  
  
 <span data-ttu-id="16ada-131">通常会选择要包括或排除的特定事务。</span><span class="sxs-lookup"><span data-stu-id="16ada-131">Typically, a specific transaction is selected to be included or excluded.</span></span> <span data-ttu-id="16ada-132">虽然实践中并不总是如此，但指定的日志记录就是事务提交记录。</span><span class="sxs-lookup"><span data-stu-id="16ada-132">Although not required, in practice, the specified log record is a transaction-commit record.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="16ada-133">示例</span><span class="sxs-lookup"><span data-stu-id="16ada-133">Examples</span></span>  
 <span data-ttu-id="16ada-134">以下示例假定 `AdventureWorks` 数据库已更改为使用完整恢复模式。</span><span class="sxs-lookup"><span data-stu-id="16ada-134">The following example assumes that the `AdventureWorks` database has been changed to use the full recovery model.</span></span>  
  
```  
RESTORE LOG AdventureWorks FROM DISK = 'c:\adventureworks_log.bak'   
WITH STOPATMARK = 'lsn:15000000040000037'  
GO  
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="16ada-135">相关任务</span><span class="sxs-lookup"><span data-stu-id="16ada-135">Related Tasks</span></span>  
  
-   [<span data-ttu-id="16ada-136">还原数据库备份 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="16ada-136">Restore a Database Backup &#40;SQL Server Management Studio&#41;</span></span>](restore-a-database-backup-using-ssms.md)  
  
-   [<span data-ttu-id="16ada-137">备份事务日志 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="16ada-137">Back Up a Transaction Log &#40;SQL Server&#41;</span></span>](back-up-a-transaction-log-sql-server.md)  
  
-   [<span data-ttu-id="16ada-138">还原事务日志备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="16ada-138">Restore a Transaction Log Backup &#40;SQL Server&#41;</span></span>](restore-a-transaction-log-backup-sql-server.md)  
  
-   [<span data-ttu-id="16ada-139">在完整恢复模式下将数据库还原到故障点 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="16ada-139">Restore a Database to the Point of Failure Under the Full Recovery Model &#40;Transact-SQL&#41;</span></span>](restore-database-to-point-of-failure-full-recovery.md)  
  
-   [<span data-ttu-id="16ada-140">将数据库还原到标记的事务 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="16ada-140">Restore a Database to a Marked Transaction &#40;SQL Server Management Studio&#41;</span></span>](restore-a-database-to-a-marked-transaction-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="16ada-141">将 SQL Server 数据库还原到某个时间点（完整恢复模式）</span><span class="sxs-lookup"><span data-stu-id="16ada-141">Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;</span></span>](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)  
  
## <a name="see-also"></a><span data-ttu-id="16ada-142">另请参阅</span><span class="sxs-lookup"><span data-stu-id="16ada-142">See Also</span></span>  
 <span data-ttu-id="16ada-143">[应用事务日志备份 (SQL Server)](transaction-log-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="16ada-143">[Apply Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span></span>  
 <span data-ttu-id="16ada-144">[事务日志 (SQL Server)](../logs/the-transaction-log-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="16ada-144">[The Transaction Log &#40;SQL Server&#41;](../logs/the-transaction-log-sql-server.md) </span></span>  
 [<span data-ttu-id="16ada-145">RESTORE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="16ada-145">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
