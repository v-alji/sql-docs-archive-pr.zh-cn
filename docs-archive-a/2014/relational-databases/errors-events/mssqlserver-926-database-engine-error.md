---
title: MSSQLSERVER_926 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 926 (Database Engine error)
ms.assetid: 57e01668-883b-4be4-84a8-a111caaf0486
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ae6796c9f4869d45223ab1283a68fc2bfe78aa11
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581234"
---
# <a name="mssqlserver_926"></a><span data-ttu-id="fd974-102">MSSQLSERVER_926</span><span class="sxs-lookup"><span data-stu-id="fd974-102">MSSQLSERVER_926</span></span>
    
## <a name="details"></a><span data-ttu-id="fd974-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="fd974-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fd974-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="fd974-104">Product Name</span></span>|<span data-ttu-id="fd974-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="fd974-105">SQL Server</span></span>|  
|<span data-ttu-id="fd974-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="fd974-106">Event ID</span></span>|<span data-ttu-id="fd974-107">926</span><span class="sxs-lookup"><span data-stu-id="fd974-107">926</span></span>|  
|<span data-ttu-id="fd974-108">事件源</span><span class="sxs-lookup"><span data-stu-id="fd974-108">Event Source</span></span>|<span data-ttu-id="fd974-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="fd974-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="fd974-110">组件</span><span class="sxs-lookup"><span data-stu-id="fd974-110">Component</span></span>|<span data-ttu-id="fd974-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="fd974-111">SQLEngine</span></span>|  
|<span data-ttu-id="fd974-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="fd974-112">Symbolic Name</span></span>|<span data-ttu-id="fd974-113">DB_SUSPECT</span><span class="sxs-lookup"><span data-stu-id="fd974-113">DB_SUSPECT</span></span>|  
|<span data-ttu-id="fd974-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="fd974-114">Message Text</span></span>|<span data-ttu-id="fd974-115">无法打开数据库 '%.\*ls'。</span><span class="sxs-lookup"><span data-stu-id="fd974-115">Database '%.\*ls' cannot be opened.</span></span> <span data-ttu-id="fd974-116">恢复操作已将该数据库标记为 SUSPECT。</span><span class="sxs-lookup"><span data-stu-id="fd974-116">It has been marked SUSPECT by recovery.</span></span> <span data-ttu-id="fd974-117">有关详细信息，请参阅 SQL Server 错误日志。</span><span class="sxs-lookup"><span data-stu-id="fd974-117">See the SQL Server errorlog for more information.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="fd974-118">说明</span><span class="sxs-lookup"><span data-stu-id="fd974-118">Explanation</span></span>  
 <span data-ttu-id="fd974-119">由于将数据库变为一致事务状态的恢复进程失败，因此该数据库被标记为可疑。</span><span class="sxs-lookup"><span data-stu-id="fd974-119">The database is marked as suspect because it failed the recovery process that brings a database to a consistent transactional state.</span></span> <span data-ttu-id="fd974-120">这可能出现在下列操作过程中：</span><span class="sxs-lookup"><span data-stu-id="fd974-120">This can occur during the following operations:</span></span>  
  
-   <span data-ttu-id="fd974-121">启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的实例。</span><span class="sxs-lookup"><span data-stu-id="fd974-121">Starting up an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="fd974-122">附加数据库。</span><span class="sxs-lookup"><span data-stu-id="fd974-122">Attaching a database.</span></span>  
  
-   <span data-ttu-id="fd974-123">使用 RESTORE 数据库或 RESTORE LOG 过程。</span><span class="sxs-lookup"><span data-stu-id="fd974-123">Using the RESTORE database or RESTORE LOG procedures.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="fd974-124">用户操作</span><span class="sxs-lookup"><span data-stu-id="fd974-124">User Action</span></span>  
 <span data-ttu-id="fd974-125">检查 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误日志并确定错误原因。</span><span class="sxs-lookup"><span data-stu-id="fd974-125">Inspect the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log and determine the cause of the error.</span></span> <span data-ttu-id="fd974-126">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 自恢复失败后已重新启动，请参见先前的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误日志以查看恢复失败的原因。</span><span class="sxs-lookup"><span data-stu-id="fd974-126">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has been restarted since the failed recovery, look at previous [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error logs to see the reason why recovery failed.</span></span>  
  
 <span data-ttu-id="fd974-127">如果恢复是由于持久性 I/O 错误、页撕裂或其他可能的硬件问题而失败，请解决底层硬件的问题并使用备份还原数据库。</span><span class="sxs-lookup"><span data-stu-id="fd974-127">If the recovery failed because of a persistent I/O error, a torn page, or other possible hardware problem, resolve the underlying hardware problem and restore the database by using a backup.</span></span> <span data-ttu-id="fd974-128">如果没有可用的备份，请考虑 DBCC CHECKDB 的修复选项。</span><span class="sxs-lookup"><span data-stu-id="fd974-128">If no backups are available, consider the repair options of DBCC CHECKDB.</span></span>  
  
 <span data-ttu-id="fd974-129">如果您无法解决此问题，请与主要支持提供商联系。</span><span class="sxs-lookup"><span data-stu-id="fd974-129">If you are unable to resolve this problem, contact your primary support provider.</span></span> <span data-ttu-id="fd974-130">保存 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误日志以便进行查看。</span><span class="sxs-lookup"><span data-stu-id="fd974-130">Have the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log available for review.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd974-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fd974-131">See Also</span></span>  
 <span data-ttu-id="fd974-132">[SQL Server 数据库的备份和还原](../backup-restore/back-up-and-restore-of-sql-server-databases.md) </span><span class="sxs-lookup"><span data-stu-id="fd974-132">[Back Up and Restore of SQL Server Databases](../backup-restore/back-up-and-restore-of-sql-server-databases.md) </span></span>  
 <span data-ttu-id="fd974-133">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="fd974-133">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 <span data-ttu-id="fd974-134">[sys.sys数据库 &#40;Transact-sql&#41;](/sql/relational-databases/system-compatibility-views/sys-sysdatabases-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="fd974-134">[sys.sysdatabases &#40;Transact-SQL&#41;](/sql/relational-databases/system-compatibility-views/sys-sysdatabases-transact-sql) </span></span>  
 [<span data-ttu-id="fd974-135">数据库分离和附加 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="fd974-135">Database Detach and Attach &#40;SQL Server&#41;</span></span>](../../relational-databases/databases/database-detach-and-attach-sql-server.md)  
  
  
