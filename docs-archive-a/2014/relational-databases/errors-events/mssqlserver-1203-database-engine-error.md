---
title: MSSQLSERVER_1203 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1203 (Database Engine error)
ms.assetid: 33a35f00-98c8-46c6-b432-544b326b6117
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3cea816a60ccd1b90d849194766edebd2d64d0b4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589137"
---
# <a name="mssqlserver_1203"></a><span data-ttu-id="9acbb-102">MSSQLSERVER_1203</span><span class="sxs-lookup"><span data-stu-id="9acbb-102">MSSQLSERVER_1203</span></span>
    
## <a name="details"></a><span data-ttu-id="9acbb-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="9acbb-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9acbb-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="9acbb-104">Product Name</span></span>|<span data-ttu-id="9acbb-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="9acbb-105">SQL Server</span></span>|  
|<span data-ttu-id="9acbb-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="9acbb-106">Event ID</span></span>|<span data-ttu-id="9acbb-107">1203</span><span class="sxs-lookup"><span data-stu-id="9acbb-107">1203</span></span>|  
|<span data-ttu-id="9acbb-108">事件源</span><span class="sxs-lookup"><span data-stu-id="9acbb-108">Event Source</span></span>|<span data-ttu-id="9acbb-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="9acbb-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="9acbb-110">组件</span><span class="sxs-lookup"><span data-stu-id="9acbb-110">Component</span></span>|<span data-ttu-id="9acbb-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="9acbb-111">SQLEngine</span></span>|  
|<span data-ttu-id="9acbb-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="9acbb-112">Symbolic Name</span></span>|<span data-ttu-id="9acbb-113">LK_NOT</span><span class="sxs-lookup"><span data-stu-id="9acbb-113">LK_NOT</span></span>|  
|<span data-ttu-id="9acbb-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="9acbb-114">Message Text</span></span>|<span data-ttu-id="9acbb-115">进程 ID %d 尝试对不归它所有的资源进行解锁: %.\*ls。</span><span class="sxs-lookup"><span data-stu-id="9acbb-115">Process ID %d attempted to unlock a resource it does not own: %.\*ls.</span></span> <span data-ttu-id="9acbb-116">请重试该事务，因为此错误可能是计时条件导致的。</span><span class="sxs-lookup"><span data-stu-id="9acbb-116">Retry the transaction, because this error may be caused by a timing condition.</span></span> <span data-ttu-id="9acbb-117">如果该问题仍然存在，请与数据库管理员联系。</span><span class="sxs-lookup"><span data-stu-id="9acbb-117">If the problem persists, contact the database administrator.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="9acbb-118">说明</span><span class="sxs-lookup"><span data-stu-id="9acbb-118">Explanation</span></span>  
 <span data-ttu-id="9acbb-119">当 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 执行的活动不是普通的后处理清除活动，并且发现它试图解锁的特定页已经解锁时，将产生此错误。</span><span class="sxs-lookup"><span data-stu-id="9acbb-119">This error occurs when [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is engaged in some activity other than ordinary post-processing cleanup and it finds that a particular page that it is trying to unlock is already unlocked.</span></span>  
  
### <a name="possible-causes"></a><span data-ttu-id="9acbb-120">可能的原因</span><span class="sxs-lookup"><span data-stu-id="9acbb-120">Possible Causes</span></span>  
 <span data-ttu-id="9acbb-121">此错误的基本原因可能与受影响数据库中存在结构问题相关。</span><span class="sxs-lookup"><span data-stu-id="9acbb-121">The underlying cause of this error may be related to structural problems within the affected database.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="9acbb-122">可以通过管理页的获取和释放维护多用户环境中的并发控制。</span><span class="sxs-lookup"><span data-stu-id="9acbb-122">manages the acquisition and release of pages to maintain concurrency control in the multiuser environment.</span></span> <span data-ttu-id="9acbb-123">此机制的维护是通过使用各种内部锁结构来实现的，这些内部锁结构标识了当前的页和当前的锁类型。</span><span class="sxs-lookup"><span data-stu-id="9acbb-123">This mechanism is maintained by using various internal lock structures that identify the page and the type of lock present.</span></span> <span data-ttu-id="9acbb-124">处理受影响页时获取锁，处理完成后则释放锁。</span><span class="sxs-lookup"><span data-stu-id="9acbb-124">Locks are acquired for processing of affected pages and released when the processing is finished.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="9acbb-125">用户操作</span><span class="sxs-lookup"><span data-stu-id="9acbb-125">User Action</span></span>  
 <span data-ttu-id="9acbb-126">对对象所属数据库执行 DBCC CHECKDB。</span><span class="sxs-lookup"><span data-stu-id="9acbb-126">Execute DBCC CHECKDB against the database in which the object belongs.</span></span> <span data-ttu-id="9acbb-127">如果 DBCC CHECKDB 未报告错误，则尝试重新建立连接并执行此命令。</span><span class="sxs-lookup"><span data-stu-id="9acbb-127">If DBCC CHECKDB reports no errors, try to reestablish the connection and execute the command.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="9acbb-128">如果执行 DBCC CHECKDB 时有一个 REPAIR 子句未更正索引问题，或者如果不确定执行具有 REPAIR 子句的 DBCC CHECKDB 会对数据有何影响，请与主要支持提供商联系。</span><span class="sxs-lookup"><span data-stu-id="9acbb-128">If you are executing DBCC CHECKDB with one of the REPAIR clauses does not correct the index problem, or if you are not sure what effect DBCC CHECKDB with a REPAIR clause has on your data, contact your primary support provider.</span></span>  
  
  
