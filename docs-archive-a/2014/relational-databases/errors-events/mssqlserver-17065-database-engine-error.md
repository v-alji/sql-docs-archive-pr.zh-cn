---
title: MSSQLSERVER_17065 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17065 (Database Engine error)
ms.assetid: 63c2ba5a-be34-461e-bee1-03c25b396cd2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 47aebfa29b60a1c2ae50c6699946312996d26e6f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589641"
---
# <a name="mssqlserver_17065"></a><span data-ttu-id="0ea6b-102">MSSQLSERVER_17065</span><span class="sxs-lookup"><span data-stu-id="0ea6b-102">MSSQLSERVER_17065</span></span>
    
## <a name="details"></a><span data-ttu-id="0ea6b-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="0ea6b-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0ea6b-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="0ea6b-104">Product Name</span></span>|<span data-ttu-id="0ea6b-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="0ea6b-105">SQL Server</span></span>|  
|<span data-ttu-id="0ea6b-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="0ea6b-106">Event ID</span></span>|<span data-ttu-id="0ea6b-107">17065</span><span class="sxs-lookup"><span data-stu-id="0ea6b-107">17065</span></span>|  
|<span data-ttu-id="0ea6b-108">事件源</span><span class="sxs-lookup"><span data-stu-id="0ea6b-108">Event Source</span></span>|<span data-ttu-id="0ea6b-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="0ea6b-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="0ea6b-110">组件</span><span class="sxs-lookup"><span data-stu-id="0ea6b-110">Component</span></span>|<span data-ttu-id="0ea6b-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="0ea6b-111">SQLEngine</span></span>|  
|<span data-ttu-id="0ea6b-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="0ea6b-112">Symbolic Name</span></span>|<span data-ttu-id="0ea6b-113">SQLASSERT_BOTH</span><span class="sxs-lookup"><span data-stu-id="0ea6b-113">SQLASSERT_BOTH</span></span>|  
|<span data-ttu-id="0ea6b-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="0ea6b-114">Message Text</span></span>|<span data-ttu-id="0ea6b-115">SQL Server 断言:文件：\<%s>，行 = %d 失败的断言 = '%s' %s。</span><span class="sxs-lookup"><span data-stu-id="0ea6b-115">SQL Server Assertion: File: \<%s>, line = %d Failed Assertion = '%s' %s.</span></span> <span data-ttu-id="0ea6b-116">此错误可能与时间有关。</span><span class="sxs-lookup"><span data-stu-id="0ea6b-116">This error may be timing-related.</span></span> <span data-ttu-id="0ea6b-117">如果重新运行该语句后错误仍然存在，请使用 DBCC CHECKDB 来检查数据库的结构是否完整，或重新启动服务器以确保内存中的数据结构未破坏。</span><span class="sxs-lookup"><span data-stu-id="0ea6b-117">If the error persists after rerunning the statement, use DBCC CHECKDB to check the database for structural integrity, or restart the server to ensure in-memory data structures are not corrupted.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="0ea6b-118">说明</span><span class="sxs-lookup"><span data-stu-id="0ea6b-118">Explanation</span></span>  
 <span data-ttu-id="0ea6b-119">与时间有关的暂时性错误或内存中或磁盘上的数据损坏均可导致此错误。</span><span class="sxs-lookup"><span data-stu-id="0ea6b-119">This error can be caused by transient, timing-related errors, or by in-memory or on-disk data corruption.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="0ea6b-120">用户操作</span><span class="sxs-lookup"><span data-stu-id="0ea6b-120">User Action</span></span>  
 <span data-ttu-id="0ea6b-121">重新运行导致激发异常的语句。</span><span class="sxs-lookup"><span data-stu-id="0ea6b-121">Rerun the statement that caused the exception to fire.</span></span> <span data-ttu-id="0ea6b-122">如果错误是由与时间有关的事件导致的，则此错误可能不会重复发生。</span><span class="sxs-lookup"><span data-stu-id="0ea6b-122">If the error was caused by a timing-related event, the error may not recur.</span></span> <span data-ttu-id="0ea6b-123">如果问题仍然存在，请运行 DBCC CHECKDB 检查磁盘上的数据是否损坏。</span><span class="sxs-lookup"><span data-stu-id="0ea6b-123">If the problem persists, run DBCC CHECKDB to check for on-disk corruption.</span></span> <span data-ttu-id="0ea6b-124">重新启动服务器以确保内存中的数据结构未损坏。</span><span class="sxs-lookup"><span data-stu-id="0ea6b-124">Restart the server to ensure the in-memory data structures are not corrupted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ea6b-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0ea6b-125">See Also</span></span>  
 [<span data-ttu-id="0ea6b-126">DBCC CHECKDB (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="0ea6b-126">DBCC CHECKDB &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)  
  
  