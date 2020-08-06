---
title: MSSQL_ENG003165 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG003165 error
ms.assetid: 707d33dd-644e-4cc9-ac51-dddd49031530
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e1702588ba6ac1beeb33b87a7afc7fc330271559
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576673"
---
# <a name="mssql_eng003165"></a><span data-ttu-id="8c470-102">MSSQL_ENG003165</span><span class="sxs-lookup"><span data-stu-id="8c470-102">MSSQL_ENG003165</span></span>
    
## <a name="message-details"></a><span data-ttu-id="8c470-103">消息详细信息</span><span class="sxs-lookup"><span data-stu-id="8c470-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8c470-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="8c470-104">Product Name</span></span>|<span data-ttu-id="8c470-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="8c470-105">SQL Server</span></span>|  
|<span data-ttu-id="8c470-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="8c470-106">Event ID</span></span>|<span data-ttu-id="8c470-107">3165</span><span class="sxs-lookup"><span data-stu-id="8c470-107">3165</span></span>|  
|<span data-ttu-id="8c470-108">事件源</span><span class="sxs-lookup"><span data-stu-id="8c470-108">Event Source</span></span>|<span data-ttu-id="8c470-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="8c470-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="8c470-110">组件</span><span class="sxs-lookup"><span data-stu-id="8c470-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="8c470-111">符号名称</span><span class="sxs-lookup"><span data-stu-id="8c470-111">Symbolic Name</span></span>||  
|<span data-ttu-id="8c470-112">消息正文</span><span class="sxs-lookup"><span data-stu-id="8c470-112">Message Text</span></span>|<span data-ttu-id="8c470-113">数据库 '%ls' 已还原，但在还原/删除复制时出错。</span><span class="sxs-lookup"><span data-stu-id="8c470-113">Database '%ls' was restored; however, an error was encountered while replication was being restored/removed.</span></span> <span data-ttu-id="8c470-114">该数据库仍保留为脱机状态。</span><span class="sxs-lookup"><span data-stu-id="8c470-114">The database has been left offline.</span></span> <span data-ttu-id="8c470-115">请参阅 SQL Server 联机丛书中的主题 MSSQL_ENG003165。</span><span class="sxs-lookup"><span data-stu-id="8c470-115">See the topic MSSQL_ENG003165 in SQL Server Books Online.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="8c470-116">说明</span><span class="sxs-lookup"><span data-stu-id="8c470-116">Explanation</span></span>  
 <span data-ttu-id="8c470-117">如果在还原已复制数据库的备份时出现问题，将引发此错误：</span><span class="sxs-lookup"><span data-stu-id="8c470-117">This error is raised if a problem occurs restoring a backup of a replicated database:</span></span>  
  
-   <span data-ttu-id="8c470-118">如果将备份还原到对其创建备份的同一数据库和服务器，此错误将指示无法正确还原复制设置。</span><span class="sxs-lookup"><span data-stu-id="8c470-118">If the backup is being restored to the same database and server on which it was taken, the error indicates that replication settings could not be restored properly.</span></span>  
  
-   <span data-ttu-id="8c470-119">如果将备份还原到其他数据库或服务器，此错误将指示无法正确删除复制设置（默认情况下，如果是在其他数据库或服务器上，则删除复制设置）。</span><span class="sxs-lookup"><span data-stu-id="8c470-119">If the backup is being restored to a different database or server, the error indicates that replication settings could not be removed properly (by default, replication settings are removed if the database or server is different).</span></span>  
  
 <span data-ttu-id="8c470-120">该错误可能是由已还原数据库的状态与一个或多个包含复制元数据的系统数据库 **msdb**、 **master**或分发数据库的状态不匹配造成的。</span><span class="sxs-lookup"><span data-stu-id="8c470-120">The error is probably the result of a mismatch between the state of the restored database and one or more system databases that contain replication metadata: **msdb**, **master**, or the distribution database.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="8c470-121">用户操作</span><span class="sxs-lookup"><span data-stu-id="8c470-121">User Action</span></span>  
 <span data-ttu-id="8c470-122">若要解决此问题，请执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="8c470-122">To resolve this issue:</span></span>  
  
1.  <span data-ttu-id="8c470-123">执行 ALTER DATABASE 以使数据库联机；例如： `ALTER DATABASE AdventureWorks SET ONLINE`。</span><span class="sxs-lookup"><span data-stu-id="8c470-123">Execute ALTER DATABASE to bring the database online; for example: `ALTER DATABASE AdventureWorks SET ONLINE`.</span></span> <span data-ttu-id="8c470-124">有关详细信息，请参阅 [ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="8c470-124">For more information, see [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span> <span data-ttu-id="8c470-125">如果要保留复制设置，请转到步骤 2。</span><span class="sxs-lookup"><span data-stu-id="8c470-125">If you want to preserve replication settings, go to step 2.</span></span> <span data-ttu-id="8c470-126">否则，转到步骤 3。</span><span class="sxs-lookup"><span data-stu-id="8c470-126">If not, go to step 3.</span></span>  
  
2.  <span data-ttu-id="8c470-127">执行 [sp_restoredbreplication (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-restoredbreplication-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="8c470-127">Execute [sp_restoredbreplication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-restoredbreplication-transact-sql).</span></span> <span data-ttu-id="8c470-128">如果此存储过程成功执行，则还原完成。</span><span class="sxs-lookup"><span data-stu-id="8c470-128">If this stored procedure executes successfully, the restore is complete.</span></span> <span data-ttu-id="8c470-129">如果此存储过程未成功执行，请转到步骤 3。</span><span class="sxs-lookup"><span data-stu-id="8c470-129">If it does not execute successfully, go to step 3.</span></span>  
  
3.  <span data-ttu-id="8c470-130">执行[sp_removedbreplication (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) 以删除所有复制设置。</span><span class="sxs-lookup"><span data-stu-id="8c470-130">Execute [sp_removedbreplication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) to remove all replication settings.</span></span>  
  
     <span data-ttu-id="8c470-131">如果需要，请重新配置复制。</span><span class="sxs-lookup"><span data-stu-id="8c470-131">Reconfigure replication if necessary.</span></span> <span data-ttu-id="8c470-132">如果您根据建议将复制拓扑编写了脚本，请使用脚本来重新配置该拓扑。</span><span class="sxs-lookup"><span data-stu-id="8c470-132">If you have scripted the replication topology as recommended, use scripts to reconfigure the topology.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c470-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8c470-133">See Also</span></span>  
 <span data-ttu-id="8c470-134">[SQL Server 数据库的备份和还原](../backup-restore/back-up-and-restore-of-sql-server-databases.md) </span><span class="sxs-lookup"><span data-stu-id="8c470-134">[Back Up and Restore of SQL Server Databases](../backup-restore/back-up-and-restore-of-sql-server-databases.md) </span></span>  
 <span data-ttu-id="8c470-135">[备份和还原复制的数据库](administration/back-up-and-restore-replicated-databases.md) </span><span class="sxs-lookup"><span data-stu-id="8c470-135">[Back Up and Restore Replicated Databases](administration/back-up-and-restore-replicated-databases.md) </span></span>  
 [<span data-ttu-id="8c470-136">错误和事件参考（复制）</span><span class="sxs-lookup"><span data-stu-id="8c470-136">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
