---
title: MSSQL_REPL020011 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_REPL020011 error
ms.assetid: f72072d7-bbb6-48ad-ac88-afa74aeb4d58
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 646f25740ebb007f8d04a89690d3b712781efcc8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691678"
---
# <a name="mssql_repl020011"></a><span data-ttu-id="e1088-102">MSSQL_REPL020011</span><span class="sxs-lookup"><span data-stu-id="e1088-102">MSSQL_REPL020011</span></span>
    
## <a name="message-details"></a><span data-ttu-id="e1088-103">消息详细信息</span><span class="sxs-lookup"><span data-stu-id="e1088-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e1088-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="e1088-104">Product Name</span></span>|<span data-ttu-id="e1088-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="e1088-105">SQL Server</span></span>|  
|<span data-ttu-id="e1088-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="e1088-106">Event ID</span></span>|<span data-ttu-id="e1088-107">20011</span><span class="sxs-lookup"><span data-stu-id="e1088-107">20011</span></span>|  
|<span data-ttu-id="e1088-108">事件源</span><span class="sxs-lookup"><span data-stu-id="e1088-108">Event Source</span></span>|<span data-ttu-id="e1088-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="e1088-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="e1088-110">组件</span><span class="sxs-lookup"><span data-stu-id="e1088-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="e1088-111">符号名称</span><span class="sxs-lookup"><span data-stu-id="e1088-111">Symbolic Name</span></span>||  
|<span data-ttu-id="e1088-112">消息正文</span><span class="sxs-lookup"><span data-stu-id="e1088-112">Message Text</span></span>|<span data-ttu-id="e1088-113">进程无法在“%2”上执行“%1”。</span><span class="sxs-lookup"><span data-stu-id="e1088-113">The process could not execute '%1' on '%2'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="e1088-114">说明</span><span class="sxs-lookup"><span data-stu-id="e1088-114">Explanation</span></span>  
 <span data-ttu-id="e1088-115">事务复制处理过程中的许多情况都可能引发此错误，例如日志读取器代理执行 **sp_replcmds**（此过程无法在 \<ServerName> 上执行“sp_replcmds”）或 **sp_repldone**（此过程无法在 \<ServerName> 上执行“sp_repldone”）时。</span><span class="sxs-lookup"><span data-stu-id="e1088-115">This error can be raised in a number of circumstances during transactional replication processing, such as when the Log Reader Agent executes **sp_replcmds** (The process could not execute 'sp_replcmds' on \<ServerName>) or **sp_repldone** (The process could not execute 'sp_repldone' on \<ServerName>).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e1088-116">用户操作</span><span class="sxs-lookup"><span data-stu-id="e1088-116">User Action</span></span>  
 <span data-ttu-id="e1088-117">如果在您刚刚从备份中还原的数据库中出现此错误，请确保遵守了备份和还原文档中列出的步骤，包括在适合时执行 **sp_replrestart** 。</span><span class="sxs-lookup"><span data-stu-id="e1088-117">If this error is raised in a database that you have just restored from a backup, ensure you have followed the steps outlined in the backup and restore documentation, including executing **sp_replrestart** if appropriate.</span></span> <span data-ttu-id="e1088-118">有关详细信息，请参阅 [快照复制和事务复制的备份和还原策略](administration/strategies-for-backing-up-and-restoring-snapshot-and-transactional-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="e1088-118">For more information, see [Strategies for Backing Up and Restoring Snapshot and Transactional Replication](administration/strategies-for-backing-up-and-restoring-snapshot-and-transactional-replication.md).</span></span>  
  
 <span data-ttu-id="e1088-119">此错误是一个内部处理错误，如果在还原之外的环境中出现此错误，则通常表示必须删除或重新配置复制。</span><span class="sxs-lookup"><span data-stu-id="e1088-119">This error is an internal processing error and if it is raised in circumstances other than a restore, it typically indicates that replication must be removed and reconfigured.</span></span> <span data-ttu-id="e1088-120">如果无法删除复制，请与客户支持部门联系以获取帮助。</span><span class="sxs-lookup"><span data-stu-id="e1088-120">If you cannot remove replication, contact customer support for assistance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1088-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e1088-121">See Also</span></span>  
 <span data-ttu-id="e1088-122">[错误和事件参考（复制）](errors-and-events-reference-replication.md) </span><span class="sxs-lookup"><span data-stu-id="e1088-122">[Errors and Events Reference &#40;Replication&#41;](errors-and-events-reference-replication.md) </span></span>  
 <span data-ttu-id="e1088-123">[sp_replcmds (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-replcmds-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e1088-123">[sp_replcmds &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replcmds-transact-sql) </span></span>  
 [<span data-ttu-id="e1088-124">sp_repldone (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="e1088-124">sp_repldone &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-repldone-transact-sql)  
  
  
