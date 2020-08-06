---
title: MSSQLSERVER_1222 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1222 (Database Engine error)
ms.assetid: c5b1c2f4-f591-4cc1-aa17-204636a27f29
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ac3fe9314386836633a11f17d6775c75019de93a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576804"
---
# <a name="mssqlserver_1222"></a><span data-ttu-id="41b7a-102">MSSQLSERVER_1222</span><span class="sxs-lookup"><span data-stu-id="41b7a-102">MSSQLSERVER_1222</span></span>
    
## <a name="details"></a><span data-ttu-id="41b7a-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="41b7a-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="41b7a-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="41b7a-104">Product Name</span></span>|<span data-ttu-id="41b7a-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="41b7a-105">SQL Server</span></span>|  
|<span data-ttu-id="41b7a-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="41b7a-106">Event ID</span></span>|<span data-ttu-id="41b7a-107">1222</span><span class="sxs-lookup"><span data-stu-id="41b7a-107">1222</span></span>|  
|<span data-ttu-id="41b7a-108">事件源</span><span class="sxs-lookup"><span data-stu-id="41b7a-108">Event Source</span></span>|<span data-ttu-id="41b7a-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="41b7a-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="41b7a-110">组件</span><span class="sxs-lookup"><span data-stu-id="41b7a-110">Component</span></span>|<span data-ttu-id="41b7a-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="41b7a-111">SQLEngine</span></span>|  
|<span data-ttu-id="41b7a-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="41b7a-112">Symbolic Name</span></span>|<span data-ttu-id="41b7a-113">LK_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="41b7a-113">LK_TIMEOUT</span></span>|  
|<span data-ttu-id="41b7a-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="41b7a-114">Message Text</span></span>|<span data-ttu-id="41b7a-115">已超过了锁请求超时时段。</span><span class="sxs-lookup"><span data-stu-id="41b7a-115">Lock request time out period exceeded.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="41b7a-116">说明</span><span class="sxs-lookup"><span data-stu-id="41b7a-116">Explanation</span></span>  
 <span data-ttu-id="41b7a-117">另一个事务持有必需资源的锁的时间比此查询可以等待该资源的时间长。</span><span class="sxs-lookup"><span data-stu-id="41b7a-117">Another transaction held a lock on a required resource longer than this query could wait for it.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="41b7a-118">用户操作</span><span class="sxs-lookup"><span data-stu-id="41b7a-118">User Action</span></span>  
 <span data-ttu-id="41b7a-119">执行以下任务以缓解该问题：</span><span class="sxs-lookup"><span data-stu-id="41b7a-119">Perform the following tasks to alleviate the problem:</span></span>  
  
1.  <span data-ttu-id="41b7a-120">如有可能，请找出持有必需资源的锁的事务。</span><span class="sxs-lookup"><span data-stu-id="41b7a-120">Locate the transaction that is holding the lock on the required resource, if possible.</span></span> <span data-ttu-id="41b7a-121">使用 **sys.dm_os_waiting_tasks** 和 **sys.dm_tran_locks** 动态管理视图。</span><span class="sxs-lookup"><span data-stu-id="41b7a-121">Use **sys.dm_os_waiting_tasks** and **sys.dm_tran_locks** dynamic management views.</span></span>  
  
2.  <span data-ttu-id="41b7a-122">如果事务仍持有该锁，请终止该事务（如何适合）。</span><span class="sxs-lookup"><span data-stu-id="41b7a-122">If the transaction is still holding the lock, terminate that transaction if appropriate.</span></span>  
  
3.  <span data-ttu-id="41b7a-123">重新执行查询。</span><span class="sxs-lookup"><span data-stu-id="41b7a-123">Execute the query again.</span></span>  
  
 <span data-ttu-id="41b7a-124">如果频繁出现此错误，请更改锁超时期限，或者修改有问题的事务以便它们持有锁的时间减少。</span><span class="sxs-lookup"><span data-stu-id="41b7a-124">If this error occurs frequently change the lock time-out period or modify the offending transactions so that they hold the lock for less time.</span></span>  
  
  
