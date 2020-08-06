---
title: MSSQLSERVER_3159 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3159 (Database Engine error)
ms.assetid: c93c1003-0e3a-40aa-9873-44a0f5b8b57e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6b469842b2aab15980c72ea01e46270c55ef29e5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586724"
---
# <a name="mssqlserver_3159"></a><span data-ttu-id="63479-102">MSSQLSERVER_3159</span><span class="sxs-lookup"><span data-stu-id="63479-102">MSSQLSERVER_3159</span></span>
    
## <a name="details"></a><span data-ttu-id="63479-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="63479-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="63479-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="63479-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="63479-105">事件 ID</span><span class="sxs-lookup"><span data-stu-id="63479-105">Event ID</span></span>|<span data-ttu-id="63479-106">3159</span><span class="sxs-lookup"><span data-stu-id="63479-106">3159</span></span>|  
|<span data-ttu-id="63479-107">事件源</span><span class="sxs-lookup"><span data-stu-id="63479-107">Event Source</span></span>|<span data-ttu-id="63479-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="63479-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="63479-109">组件</span><span class="sxs-lookup"><span data-stu-id="63479-109">Component</span></span>|<span data-ttu-id="63479-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="63479-110">SQLEngine</span></span>|  
|<span data-ttu-id="63479-111">符号名称</span><span class="sxs-lookup"><span data-stu-id="63479-111">Symbolic Name</span></span>|<span data-ttu-id="63479-112">LDDB_LOGNOTBACKEDUP</span><span class="sxs-lookup"><span data-stu-id="63479-112">LDDB_LOGNOTBACKEDUP</span></span>|  
|<span data-ttu-id="63479-113">消息正文</span><span class="sxs-lookup"><span data-stu-id="63479-113">Message Text</span></span>|<span data-ttu-id="63479-114">数据库 "%ls" 的日志尾部尚未备份。</span><span class="sxs-lookup"><span data-stu-id="63479-114">The tail of the log for the database "%ls" has not been backed up.</span></span> <span data-ttu-id="63479-115">如果该日志包含您不希望丢失的工作，则使用 BACKUP LOG WITH NORECOVERY 对其进行备份。</span><span class="sxs-lookup"><span data-stu-id="63479-115">Use BACKUP LOG WITH NORECOVERY to back up the log if it contains work that you do not want to lose.</span></span> <span data-ttu-id="63479-116">使用 RESTORE 语句的 WITH REPLACE 或 WITH STOPAT 子句覆盖该日志的内容。</span><span class="sxs-lookup"><span data-stu-id="63479-116">Use the WITH REPLACE or WITH STOPAT clause of the RESTORE statement to just overwrite the contents of the log.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="63479-117">说明</span><span class="sxs-lookup"><span data-stu-id="63479-117">Explanation</span></span>  
 <span data-ttu-id="63479-118">在大多数情况下，在完整恢复模式或大容量日志恢复模式下，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 要求您备份日志尾部以捕获尚未备份的日志记录。</span><span class="sxs-lookup"><span data-stu-id="63479-118">In most cases, under the full or bulk-logged recovery models, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] requires that you back up the tail of the log to capture the log records that have not yet been backed up.</span></span> <span data-ttu-id="63479-119">还原操作之前对日志尾部执行的日志备份称为“结尾日志备份”。</span><span class="sxs-lookup"><span data-stu-id="63479-119">A log backup taken of the tail of the log just before a restore operation is called a tail-log backup.</span></span>  
  
 <span data-ttu-id="63479-120">将数据库恢复到故障点时，结尾日志备份是恢复计划中的最后一个相关备份。</span><span class="sxs-lookup"><span data-stu-id="63479-120">When you are recovering a database to the point of a failure, the tail-log backup is the last backup of interest in the recovery plan.</span></span> <span data-ttu-id="63479-121">如果无法备份日志尾部，则只能将数据库恢复为发生故障前创建的最后一个备份。</span><span class="sxs-lookup"><span data-stu-id="63479-121">If you cannot back up the tail of the log, you can recover a database only to the end of the last backup that was created before the failure.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="63479-122">通常要求您在开始还原数据库前执行结尾日志备份。</span><span class="sxs-lookup"><span data-stu-id="63479-122">usually requires that you take a tail-log backup before you start to restore a database.</span></span> <span data-ttu-id="63479-123">结尾日志备份可以防止工作丢失并确保日志链的完整性。</span><span class="sxs-lookup"><span data-stu-id="63479-123">The tail-log backup prevents work loss and keeps the log chain intact.</span></span> <span data-ttu-id="63479-124">但是，并非所有还原方案都要求执行结尾日志备份。</span><span class="sxs-lookup"><span data-stu-id="63479-124">However, not all restore scenarios require a tail-log backup.</span></span> <span data-ttu-id="63479-125">如果先前的日志备份中包含恢复点，或者您准备移动或替换（覆盖）数据库，并且在最新备份后不需要将该数据库恢复到某一时间点，则不一定需要结尾日志备份。</span><span class="sxs-lookup"><span data-stu-id="63479-125">You do not have to have a tail-log backup if the recovery point is included in an earlier log backup, or if you are moving or replacing (overwriting) the database and do not need to restore it to a point of time after the most recent backup.</span></span> <span data-ttu-id="63479-126">并且，如果日志文件受损且无法创建结尾日志备份，则必须在不使用结尾日志备份的情况下还原数据库。</span><span class="sxs-lookup"><span data-stu-id="63479-126">Also, if the log files are damaged and a tail-log backup cannot be created, you must restore the database without using a tail-log backup.</span></span> <span data-ttu-id="63479-127">最新日志备份后提交的任何事务都将丢失。</span><span class="sxs-lookup"><span data-stu-id="63479-127">Any transactions committed after the latest log backup are lost.</span></span> <span data-ttu-id="63479-128">有关详细信息，请参阅本主题下文中的“不使用结尾日志备份执行还原操作”。</span><span class="sxs-lookup"><span data-stu-id="63479-128">For more information, see "Restoring Without Using a Tail-Log Backup," later in this topic.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="63479-129">应尽可能避免使用 REPLACE，在使用该选项之前必须慎重考虑。</span><span class="sxs-lookup"><span data-stu-id="63479-129">REPLACE should be used rarely, and only after careful consideration.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="63479-130">用户操作</span><span class="sxs-lookup"><span data-stu-id="63479-130">User Action</span></span>  
 <span data-ttu-id="63479-131">执行结尾日志备份，然后重试还原操作。</span><span class="sxs-lookup"><span data-stu-id="63479-131">Take a tail-log backup, and retry the restore operation.</span></span>  
  
 <span data-ttu-id="63479-132">如果不能备份日志尾部，则使用 RESTORE 语句中的 WITH STOPAT 或 WITH REPLACE 子句。</span><span class="sxs-lookup"><span data-stu-id="63479-132">If you cannot back up the tail of the log, use WITH STOPAT or WITH REPLACE in your RESTORE statements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63479-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="63479-133">See Also</span></span>  
 <span data-ttu-id="63479-134">[将 SQL Server 数据库还原到某个时间点（完整恢复模式）](../backup-restore/restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="63479-134">[Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;](../backup-restore/restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md) </span></span>  
 <span data-ttu-id="63479-135">[在数据库损坏时备份事务日志 &#40;SQL Server&#41;](../backup-restore/back-up-the-transaction-log-when-the-database-is-damaged-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="63479-135">[Back Up the Transaction Log When the Database Is Damaged &#40;SQL Server&#41;](../backup-restore/back-up-the-transaction-log-when-the-database-is-damaged-sql-server.md) </span></span>  
 <span data-ttu-id="63479-136">[备份事务日志 (SQL Server)](../backup-restore/back-up-a-transaction-log-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="63479-136">[Back Up a Transaction Log &#40;SQL Server&#41;](../backup-restore/back-up-a-transaction-log-sql-server.md) </span></span>  
 [<span data-ttu-id="63479-137">结尾日志备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="63479-137">Tail-Log Backups &#40;SQL Server&#41;</span></span>](../backup-restore/tail-log-backups-sql-server.md)  
  
  
