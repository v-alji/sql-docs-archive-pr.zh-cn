---
title: MSSQLSERVER_3456 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3456 (Database Engine error)
ms.assetid: d11b2b2c-3ae4-4023-b82f-05b561bfacce
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f13316bdd3147bb0ad63c8d4a2fb18f1fce74006
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689926"
---
# <a name="mssqlserver_3456"></a><span data-ttu-id="26256-102">MSSQLSERVER_3456</span><span class="sxs-lookup"><span data-stu-id="26256-102">MSSQLSERVER_3456</span></span>
    
## <a name="details"></a><span data-ttu-id="26256-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="26256-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="26256-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="26256-104">Product Name</span></span>|<span data-ttu-id="26256-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="26256-105">SQL Server</span></span>|  
|<span data-ttu-id="26256-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="26256-106">Event ID</span></span>|<span data-ttu-id="26256-107">3456</span><span class="sxs-lookup"><span data-stu-id="26256-107">3456</span></span>|  
|<span data-ttu-id="26256-108">事件源</span><span class="sxs-lookup"><span data-stu-id="26256-108">Event Source</span></span>|<span data-ttu-id="26256-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="26256-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="26256-110">组件</span><span class="sxs-lookup"><span data-stu-id="26256-110">Component</span></span>|<span data-ttu-id="26256-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="26256-111">SQLEngine</span></span>|  
|<span data-ttu-id="26256-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="26256-112">Symbolic Name</span></span>|<span data-ttu-id="26256-113">REC_REDOLSNMISMATCH</span><span class="sxs-lookup"><span data-stu-id="26256-113">REC_REDOLSNMISMATCH</span></span>|  
|<span data-ttu-id="26256-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="26256-114">Message Text</span></span>|<span data-ttu-id="26256-115">对于事务 ID %S_XID，无法在数据库 '%.\*ls' (数据库 ID 为 %d)的页 %S_PGID 上重做日志记录 %S_LSN。</span><span class="sxs-lookup"><span data-stu-id="26256-115">Could not redo log record %S_LSN, for transaction ID %S_XID, on page %S_PGID, database '%.\*ls' (database ID %d).</span></span> <span data-ttu-id="26256-116">页:LSN = %S_LSN，类型 = %ld。</span><span class="sxs-lookup"><span data-stu-id="26256-116">Page: LSN = %S_LSN, type = %ld.</span></span> <span data-ttu-id="26256-117">日志:操作码 = %ld，上下文 %ld，上一页的 LSN: %S_LSN。</span><span class="sxs-lookup"><span data-stu-id="26256-117">Log: OpCode = %ld, context %ld, PrevPageLSN: %S_LSN.</span></span> <span data-ttu-id="26256-118">请从数据库备份还原该数据库，或者修复它。</span><span class="sxs-lookup"><span data-stu-id="26256-118">Restore from a backup of the database, or repair the database.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="26256-119">说明</span><span class="sxs-lookup"><span data-stu-id="26256-119">Explanation</span></span>  
 <span data-ttu-id="26256-120">还原操作无法重做事务日志。</span><span class="sxs-lookup"><span data-stu-id="26256-120">The restore operation was unable to redo the transaction log.</span></span> <span data-ttu-id="26256-121">此错误使数据库进入 SUSPECT 状态。</span><span class="sxs-lookup"><span data-stu-id="26256-121">This error has placed the database into the SUSPECT state.</span></span> <span data-ttu-id="26256-122">主文件组以及可能其他文件组可疑并可能受损。</span><span class="sxs-lookup"><span data-stu-id="26256-122">The primary filegroup, and possibly other filegroups, are suspect and may be damaged.</span></span> <span data-ttu-id="26256-123">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 启动过程中无法恢复数据库，因此无法使用该数据库。</span><span class="sxs-lookup"><span data-stu-id="26256-123">The database cannot be recovered during startup of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and is therefore unavailable.</span></span> <span data-ttu-id="26256-124">需要用户执行操作来解决问题。</span><span class="sxs-lookup"><span data-stu-id="26256-124">User action is required to resolve the problem.</span></span>  
  
 <span data-ttu-id="26256-125">请注意，如果对于 **tempdb**发生此错误，则 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例关闭。</span><span class="sxs-lookup"><span data-stu-id="26256-125">Note that if this error occurs for **tempdb**, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance shuts down.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="26256-126">用户操作</span><span class="sxs-lookup"><span data-stu-id="26256-126">User Action</span></span>  
 <span data-ttu-id="26256-127">此错误可能是由在某次尝试启动服务器实例或恢复数据库的过程中系统上存在的暂时性条件导致的。</span><span class="sxs-lookup"><span data-stu-id="26256-127">This error can be caused by a transient condition that existed on the system during a given attempt to start up the server instance or to recover a database.</span></span> <span data-ttu-id="26256-128">此错误也可能是由当您每次尝试启动数据库时发生的永久性错误导致的。</span><span class="sxs-lookup"><span data-stu-id="26256-128">This error can also be caused by a permanent failure that occurs every time that you attempt to start the database.</span></span> <span data-ttu-id="26256-129">有关原因的信息，请检查 Windows 事件日志以了解有关指示特定故障的先前错误。</span><span class="sxs-lookup"><span data-stu-id="26256-129">For information about the cause, examine the Windows Event Log for a previous error that indicates the specific failure.</span></span>  
  
 <span data-ttu-id="26256-130">有关错误 3456 出现原因的信息，请检查 Windows 事件日志以了解有关指示特定故障的先前错误。</span><span class="sxs-lookup"><span data-stu-id="26256-130">For information about the cause of this occurrence of error 3456, examine the Windows Event Log for a previous error that indicates the specific failure.</span></span> <span data-ttu-id="26256-131">相应的用户操作取决于 Windows 事件日志中的信息是否指示该 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误由暂时条件或永久性故障导致。</span><span class="sxs-lookup"><span data-stu-id="26256-131">The appropriate user action depends on whether the information in the Windows Event Log indicates that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error was caused by a transient condition or a permanent failure.</span></span> <span data-ttu-id="26256-132">有关排除 3456 错误的用户操作的信息，请参阅 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 联机丛书。</span><span class="sxs-lookup"><span data-stu-id="26256-132">For information about the user actions for troubleshooting error 3456, see [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26256-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="26256-133">See Also</span></span>  
 <span data-ttu-id="26256-134">[ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="26256-134">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 <span data-ttu-id="26256-135">[DBCC CHECKDB &#40;Transact-sql&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="26256-135">[DBCC CHECKDB &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) </span></span>  
 <span data-ttu-id="26256-136">[完整数据库还原（简单恢复模式）](../backup-restore/complete-database-restores-simple-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="26256-136">[Complete Database Restores &#40;Simple Recovery Model&#41;](../backup-restore/complete-database-restores-simple-recovery-model.md) </span></span>  
 <span data-ttu-id="26256-137">[MSSQLSERVER_824](mssqlserver-824-database-engine-error.md) </span><span class="sxs-lookup"><span data-stu-id="26256-137">[MSSQLSERVER_824](mssqlserver-824-database-engine-error.md) </span></span>  
 [<span data-ttu-id="26256-138">sys.databases (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="26256-138">sys.databases &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
  
