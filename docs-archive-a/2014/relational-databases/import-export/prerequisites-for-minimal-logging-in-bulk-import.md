---
title: 在批量导入中按最小方式记录日志的前提条件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- minimal logging [SQL Server]
- logged bulk copy [SQL Server]
- logs [SQL Server], minimal logging
- minimally logged operations [SQL Server]
- bulk importing [SQL Server], minimal logging
ms.assetid: bd1dac6b-6ef8-4735-ad4e-67bb42dc4f66
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4711e25dcfcc99e14894e47166638673c61a6831
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693360"
---
# <a name="prerequisites-for-minimal-logging-in-bulk-import"></a><span data-ttu-id="f402f-102">在批量导入中按最小方式记录日志的前提条件</span><span class="sxs-lookup"><span data-stu-id="f402f-102">Prerequisites for Minimal Logging in Bulk Import</span></span>
  <span data-ttu-id="f402f-103">对于完整恢复模式下的数据库，大容量导入执行的所有行插入操作都会完整地记录在事务日志中。</span><span class="sxs-lookup"><span data-stu-id="f402f-103">For a database under the full recovery model, all row-insert operations that are performed by bulk import are fully logged in the transaction log.</span></span> <span data-ttu-id="f402f-104">如果使用完整恢复模式，大型数据导入会导致填充事务日志的速度很快。</span><span class="sxs-lookup"><span data-stu-id="f402f-104">Large data imports can cause the transaction log to fill rapidly if the full recovery model is used.</span></span> <span data-ttu-id="f402f-105">相反，对于简单恢复模式或大容量日志恢复模式，大容量导入操作的最小日志记录减少了大容量导入操作填满日志空间的可能性。</span><span class="sxs-lookup"><span data-stu-id="f402f-105">In contrast, under the simple recovery model or bulk-logged recovery model, minimal logging of bulk-import operations reduces the possibility that a bulk-import operation will fill the log space.</span></span> <span data-ttu-id="f402f-106">另外，最小日志记录的效率也比按完整方式记录日志高。</span><span class="sxs-lookup"><span data-stu-id="f402f-106">Minimal logging is also more efficient than full logging.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f402f-107">大容量日志恢复模式旨在于大容量操作期间临时替换完整的恢复模式。</span><span class="sxs-lookup"><span data-stu-id="f402f-107">The bulk-logged recovery model is designed to temporarily replace the full recovery model during large bulk operations.</span></span>  
  
## <a name="table-requirements-for-minimally-logging-bulk-import-operations"></a><span data-ttu-id="f402f-108">在大容量导入操作中最小日志记录的表要求</span><span class="sxs-lookup"><span data-stu-id="f402f-108">Table Requirements for Minimally Logging Bulk-Import Operations</span></span>  
 <span data-ttu-id="f402f-109">最小日志记录要求目标表满足下列条件：</span><span class="sxs-lookup"><span data-stu-id="f402f-109">Minimal logging requires that the target table meets the following conditions:</span></span>  
  
-   <span data-ttu-id="f402f-110">当前没有复制表。</span><span class="sxs-lookup"><span data-stu-id="f402f-110">The table is not being replicated.</span></span>  
  
-   <span data-ttu-id="f402f-111">指定了表锁定（使用 TABLOCK）。</span><span class="sxs-lookup"><span data-stu-id="f402f-111">Table locking is specified (using TABLOCK).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f402f-112">尽管在最小日志记录的大容量导入操作过程中，数据插入操作没有记录在事务日志中，但每当为表分配新区时， [!INCLUDE[ssDE](../../includes/ssde-md.md)] 仍会记录区分配信息。</span><span class="sxs-lookup"><span data-stu-id="f402f-112">Although data insertions are not logged in the transaction log during a minimally logged bulk-import operation, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] still logs extent allocations each time a new extent is allocated to the table.</span></span>  
  
-   <span data-ttu-id="f402f-113">表不是内存优化表。</span><span class="sxs-lookup"><span data-stu-id="f402f-113">Table is not a memory-optimized table.</span></span>  
  
 <span data-ttu-id="f402f-114">对于某个表，是否进行最小日志记录还取决于该表是否有索引，如果有，则还取决于该表是否为空：</span><span class="sxs-lookup"><span data-stu-id="f402f-114">Whether minimal logging can occur for a table also depends on whether the table is indexed and, if so, whether the table is empty:</span></span>  
  
-   <span data-ttu-id="f402f-115">如果表没有索引，则按最小方式记录数据页。</span><span class="sxs-lookup"><span data-stu-id="f402f-115">If the table has no indexes, data pages are minimally logged.</span></span>  
  
-   <span data-ttu-id="f402f-116">如果表没有聚集索引但是有一个或多个非聚集索引，则始终按最小方式记录数据页。</span><span class="sxs-lookup"><span data-stu-id="f402f-116">If the table has no clustered index but has one or more nonclustered indexes, data pages are always minimally logged.</span></span> <span data-ttu-id="f402f-117">但是，记录索引页的方式取决于该表是否为空：</span><span class="sxs-lookup"><span data-stu-id="f402f-117">How index pages are logged, however, depends on whether the table is empty:</span></span>  
  
    -   <span data-ttu-id="f402f-118">如果该表为空，则按最小方式记录索引页。</span><span class="sxs-lookup"><span data-stu-id="f402f-118">If the table is empty, index pages are minimally logged.</span></span>  
  
    -   <span data-ttu-id="f402f-119">如果该表不为空，则按完整方式记录索引页。</span><span class="sxs-lookup"><span data-stu-id="f402f-119">If table is non-empty, index pages are fully logged.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="f402f-120">如果您以空表开始并分多批大容量导入数据，则对于第一批，将按最小方式记录索引页和数据页，但从第二批开始，将只按最小方式记录数据页。</span><span class="sxs-lookup"><span data-stu-id="f402f-120">If you start with an empty table and bulk import the data in multiple batches, both index and data pages are minimally logged for the first batch, but beginning with the second batch, only data pages are minimally logged.</span></span>  
  
-   <span data-ttu-id="f402f-121">如果表有聚集索引且为空，则按最小方式记录数据页和索引页。</span><span class="sxs-lookup"><span data-stu-id="f402f-121">If the table has a clustered index and is empty, both data and index pages are minimally logged.</span></span> <span data-ttu-id="f402f-122">相反，如果表有聚集索引且不为空，则无论采用何种恢复模式，均按完整方式记录数据页和索引页。</span><span class="sxs-lookup"><span data-stu-id="f402f-122">In contrast, if a table has a clustered index and is non-empty, data pages and index pages are both fully logged regardless of the recovery model.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f402f-123">如果您以空表开始并分批大容量导入数据，对于第一批，将按最小方式记录索引页和数据页，但从第二批开始，将只按大容量方式记录数据页。</span><span class="sxs-lookup"><span data-stu-id="f402f-123">If you start with an empty table and bulk import the data in batches, both index and data pages are minimally logged for the first batch, but from the second batch onwards, only data pages are bulk logged.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f402f-124">启用事务复制时，将完全记录 BULK INSERT 操作，即使处于大容量日志恢复模式下。</span><span class="sxs-lookup"><span data-stu-id="f402f-124">When transactional replication is enabled, BULK INSERT operations are fully logged even under the Bulk Logged recovery model.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="f402f-125">相关任务</span><span class="sxs-lookup"><span data-stu-id="f402f-125">Related Tasks</span></span>  
  
-   [<span data-ttu-id="f402f-126">查看或更改数据库的恢复模式 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f402f-126">View or Change the Recovery Model of a Database &#40;SQL Server&#41;</span></span>](../backup-restore/view-or-change-the-recovery-model-of-a-database-sql-server.md)  
  

  
## <a name="see-also"></a><span data-ttu-id="f402f-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f402f-127">See Also</span></span>  
 <span data-ttu-id="f402f-128">[恢复模式 (SQL Server)](../backup-restore/recovery-models-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f402f-128">[Recovery Models &#40;SQL Server&#41;](../backup-restore/recovery-models-sql-server.md) </span></span>  
 <span data-ttu-id="f402f-129">[bcp 实用工具](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="f402f-129">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 <span data-ttu-id="f402f-130">[BULK INSERT (Transact-SQL)](/sql/t-sql/statements/bulk-insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f402f-130">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span></span>  
 <span data-ttu-id="f402f-131">[OPENROWSET (Transact-SQL)](/sql/t-sql/functions/openrowset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f402f-131">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span></span>  
 <span data-ttu-id="f402f-132">[BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f402f-132">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="f402f-133">[ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f402f-133">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 <span data-ttu-id="f402f-134">[表提示 (Transact-SQL)](/sql/t-sql/queries/hints-transact-sql-table) </span><span class="sxs-lookup"><span data-stu-id="f402f-134">[Table Hints &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-table) </span></span>  
 [<span data-ttu-id="f402f-135">INSERT (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="f402f-135">INSERT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/insert-transact-sql)  
  
  
