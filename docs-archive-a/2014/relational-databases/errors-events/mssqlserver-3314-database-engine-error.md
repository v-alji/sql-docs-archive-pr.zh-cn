---
title: MSSQLSERVER_3314 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3314 (Database Engine error)
ms.assetid: f3a5ca6a-b502-4cab-b3b1-4bc753763fa9
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ff3b891b438f71d70f5dd62174eae2c5a07d29a6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589605"
---
# <a name="mssqlserver_3314"></a><span data-ttu-id="cbe98-102">MSSQLSERVER_3314</span><span class="sxs-lookup"><span data-stu-id="cbe98-102">MSSQLSERVER_3314</span></span>
    
## <a name="details"></a><span data-ttu-id="cbe98-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="cbe98-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cbe98-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="cbe98-104">Product Name</span></span>|<span data-ttu-id="cbe98-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="cbe98-105">SQL Server</span></span>|  
|<span data-ttu-id="cbe98-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="cbe98-106">Event ID</span></span>|<span data-ttu-id="cbe98-107">3314</span><span class="sxs-lookup"><span data-stu-id="cbe98-107">3314</span></span>|  
|<span data-ttu-id="cbe98-108">事件源</span><span class="sxs-lookup"><span data-stu-id="cbe98-108">Event Source</span></span>|<span data-ttu-id="cbe98-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="cbe98-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="cbe98-110">组件</span><span class="sxs-lookup"><span data-stu-id="cbe98-110">Component</span></span>|<span data-ttu-id="cbe98-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="cbe98-111">SQLEngine</span></span>|  
|<span data-ttu-id="cbe98-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="cbe98-112">Symbolic Name</span></span>|<span data-ttu-id="cbe98-113">ERR_LOG_RID2</span><span class="sxs-lookup"><span data-stu-id="cbe98-113">ERR_LOG_RID2</span></span>|  
|<span data-ttu-id="cbe98-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="cbe98-114">Message Text</span></span>|<span data-ttu-id="cbe98-115">在数据库 '%.\*ls' 中撤消日志记录下的操作时，在日志记录 %S_LSN 处出错。</span><span class="sxs-lookup"><span data-stu-id="cbe98-115">During undoing of a logged operation in database '%.\*ls', an error occurred at log record ID %S_LSN.</span></span> <span data-ttu-id="cbe98-116">通常，这一特定故障以前在 Windows 事件日志服务中会记录为错误。</span><span class="sxs-lookup"><span data-stu-id="cbe98-116">Typically, the specific failure is logged previously as an error in the Windows Event Log service.</span></span> <span data-ttu-id="cbe98-117">请利用备份还原数据库或文件，或者修复该数据库。</span><span class="sxs-lookup"><span data-stu-id="cbe98-117">Restore the database or file from a backup, or repair the database.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="cbe98-118">说明</span><span class="sxs-lookup"><span data-stu-id="cbe98-118">Explanation</span></span>  
 <span data-ttu-id="cbe98-119">这是撤消恢复的累积错误。</span><span class="sxs-lookup"><span data-stu-id="cbe98-119">This is a rollup error for undo recovery.</span></span> <span data-ttu-id="cbe98-120">此错误使数据库进入 SUSPECT 状态。</span><span class="sxs-lookup"><span data-stu-id="cbe98-120">This error has placed the database into the SUSPECT state.</span></span> <span data-ttu-id="cbe98-121">主文件组以及可能其他文件组可疑并可能受损。</span><span class="sxs-lookup"><span data-stu-id="cbe98-121">The primary filegroup, and possibly other filegroups, are suspect and may be damaged.</span></span> <span data-ttu-id="cbe98-122">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 启动过程中无法恢复数据库，因此无法使用该数据库。</span><span class="sxs-lookup"><span data-stu-id="cbe98-122">The database cannot be recovered during startup of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and is therefore unavailable.</span></span> <span data-ttu-id="cbe98-123">需要用户执行操作来解决问题。</span><span class="sxs-lookup"><span data-stu-id="cbe98-123">User action is required to resolve the problem.</span></span>  
  
 <span data-ttu-id="cbe98-124">请注意，如果对于 **tempdb**发生此错误，则 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例关闭。</span><span class="sxs-lookup"><span data-stu-id="cbe98-124">Note that if this error occurs for **tempdb**, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance shuts down.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="cbe98-125">用户操作</span><span class="sxs-lookup"><span data-stu-id="cbe98-125">User Action</span></span>  
 <span data-ttu-id="cbe98-126">此错误可能是由在某次尝试启动服务器实例或恢复数据库的过程中系统上存在的暂时性条件导致的。</span><span class="sxs-lookup"><span data-stu-id="cbe98-126">This error can be caused by a transient condition that existed on the system during a given attempt to start up the server instance or to recover a database.</span></span> <span data-ttu-id="cbe98-127">此错误也可能是由当您每次尝试启动数据库时发生的永久性错误导致的。</span><span class="sxs-lookup"><span data-stu-id="cbe98-127">This error can also be caused by a permanent failure that occurs every time that you attempt to start the database.</span></span> <span data-ttu-id="cbe98-128">有关原因的信息，请检查 Windows 事件日志以了解有关指示特定故障的先前错误。</span><span class="sxs-lookup"><span data-stu-id="cbe98-128">For information about the cause, examine the Windows Event Log for a previous error that indicates the specific failure.</span></span>  
  
 <span data-ttu-id="cbe98-129">有关错误 3314 出现原因的信息，请检查 Windows 事件日志以了解有关指示特定故障的先前错误。</span><span class="sxs-lookup"><span data-stu-id="cbe98-129">For information about the cause of this occurrence of error 3314, examine the Windows Event Log for a previous error that indicates the specific failure.</span></span> <span data-ttu-id="cbe98-130">相应的用户操作取决于 Windows 事件日志中的信息是否指示该 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误由暂时条件或永久性故障导致。</span><span class="sxs-lookup"><span data-stu-id="cbe98-130">The appropriate user action depends on whether the information in the Windows Event Log indicates that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error was caused by a transient condition or a permanent failure.</span></span> <span data-ttu-id="cbe98-131">有关排除 3314 错误的用户操作的信息，请参阅 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 联机丛书。</span><span class="sxs-lookup"><span data-stu-id="cbe98-131">For information about the user actions for troubleshooting error 3314, see [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbe98-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cbe98-132">See Also</span></span>  
 <span data-ttu-id="cbe98-133">[ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="cbe98-133">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 <span data-ttu-id="cbe98-134">[DBCC CHECKDB &#40;Transact-sql&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="cbe98-134">[DBCC CHECKDB &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) </span></span>  
 <span data-ttu-id="cbe98-135">[完整数据库还原（简单恢复模式）](../backup-restore/complete-database-restores-simple-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="cbe98-135">[Complete Database Restores &#40;Simple Recovery Model&#41;](../backup-restore/complete-database-restores-simple-recovery-model.md) </span></span>  
 <span data-ttu-id="cbe98-136">[MSSQLSERVER_824](mssqlserver-824-database-engine-error.md) </span><span class="sxs-lookup"><span data-stu-id="cbe98-136">[MSSQLSERVER_824](mssqlserver-824-database-engine-error.md) </span></span>  
 [<span data-ttu-id="cbe98-137">sys.databases (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="cbe98-137">sys.databases &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
  
