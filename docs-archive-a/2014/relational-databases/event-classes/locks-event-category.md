---
title: “锁定”事件类别 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Locks event category [SQL Server]
- SQL Server event classes, Locks event category
- event classes [SQL Server], Locks event category
- lock escalation [SQL Server], locks event category
ms.assetid: 27d6afa2-7dab-4fe7-a1ad-064b879dc654
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3a202279021e3e6c7c3c44a167792bb9439567aa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578889"
---
# <a name="locks-event-category"></a><span data-ttu-id="2bbdf-102">Locks 事件类别</span><span class="sxs-lookup"><span data-stu-id="2bbdf-102">Locks Event Category</span></span>
  <span data-ttu-id="2bbdf-103">使用 Locks 事件类别中的事件类可监视   实例中的锁定活动[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2bbdf-103">Use the event classes in the **Locks** event category to monitor locking activity in an instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span> <span data-ttu-id="2bbdf-104">这些事件类有助于调查由于多个用户同时读取和修改数据而引起的锁定问题。</span><span class="sxs-lookup"><span data-stu-id="2bbdf-104">These event classes can help you investigate locking problems caused by multiple users reading and modifying data concurrently.</span></span>  
  
 <span data-ttu-id="2bbdf-105">由于 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 通常会处理很多锁，因此在跟踪期间捕获 **Locks** 事件类别会带来很大的开销并生成大型跟踪文件或表。</span><span class="sxs-lookup"><span data-stu-id="2bbdf-105">Because the [!INCLUDE[ssDE](../../includes/ssde-md.md)] often processes many locks, capturing the **Locks** event classes during a trace can incur significant overhead and result in large trace files or tables.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2bbdf-106">本节内容</span><span class="sxs-lookup"><span data-stu-id="2bbdf-106">In This Section</span></span>  
  
|<span data-ttu-id="2bbdf-107">主题</span><span class="sxs-lookup"><span data-stu-id="2bbdf-107">Topic</span></span>|<span data-ttu-id="2bbdf-108">说明</span><span class="sxs-lookup"><span data-stu-id="2bbdf-108">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="2bbdf-109">Deadlock Graph 事件类</span><span class="sxs-lookup"><span data-stu-id="2bbdf-109">Deadlock Graph Event Class</span></span>](deadlock-graph-event-class.md)|<span data-ttu-id="2bbdf-110">提供死锁的 XML 说明。</span><span class="sxs-lookup"><span data-stu-id="2bbdf-110">Provides an XML description of a deadlock.</span></span>|  
|[<span data-ttu-id="2bbdf-111">Lock:Acquired 事件类</span><span class="sxs-lookup"><span data-stu-id="2bbdf-111">Lock:Acquired Event Class</span></span>](lock-acquired-event-class.md)|<span data-ttu-id="2bbdf-112">指示已获取资源（例如表中的行）的锁。</span><span class="sxs-lookup"><span data-stu-id="2bbdf-112">Indicates that a lock has been acquired on a resource, such as a row in a table.</span></span>|  
|[<span data-ttu-id="2bbdf-113">Lock:Cancel 事件类</span><span class="sxs-lookup"><span data-stu-id="2bbdf-113">Lock:Cancel Event Class</span></span>](lock-cancel-event-class.md)|<span data-ttu-id="2bbdf-114">跟踪在获取锁之前取消的锁请求（例如，为防止死锁）。</span><span class="sxs-lookup"><span data-stu-id="2bbdf-114">Tracks requests for locks that were canceled before the lock was acquired (for example, to prevent a deadlock).</span></span>|  
|[<span data-ttu-id="2bbdf-115">Lock:Deadlock Chain 事件类</span><span class="sxs-lookup"><span data-stu-id="2bbdf-115">Lock:Deadlock Chain Event Class</span></span>](lock-deadlock-chain-event-class.md)|<span data-ttu-id="2bbdf-116">监视出现死锁条件的时间和涉及的对象。</span><span class="sxs-lookup"><span data-stu-id="2bbdf-116">Monitors when deadlock conditions occur and which objects are involved.</span></span>|  
|[<span data-ttu-id="2bbdf-117">Lock:Deadlock 事件类</span><span class="sxs-lookup"><span data-stu-id="2bbdf-117">Lock:Deadlock Event Class</span></span>](lock-deadlock-event-class.md)|<span data-ttu-id="2bbdf-118">跟踪事务何时针对已由另一个事务锁定（导致死锁）的资源请求锁。</span><span class="sxs-lookup"><span data-stu-id="2bbdf-118">Tracks when a transaction has requested a lock on a resource already locked by another transaction, resulting in a deadlock.</span></span>|  
|[<span data-ttu-id="2bbdf-119">Lock:Escalation 事件类</span><span class="sxs-lookup"><span data-stu-id="2bbdf-119">Lock:Escalation Event Class</span></span>](lock-escalation-event-class.md)|<span data-ttu-id="2bbdf-120">指示较细粒度的锁已转换为较粗粒度的锁。</span><span class="sxs-lookup"><span data-stu-id="2bbdf-120">Indicates that a finer-grained lock has been converted to a coarser-grained lock.</span></span>|  
|[<span data-ttu-id="2bbdf-121">Lock:Released 事件类</span><span class="sxs-lookup"><span data-stu-id="2bbdf-121">Lock:Released Event Class</span></span>](lock-released-event-class.md)|<span data-ttu-id="2bbdf-122">跟踪何时释放锁。</span><span class="sxs-lookup"><span data-stu-id="2bbdf-122">Tracks when a lock is released.</span></span>|  
|[<span data-ttu-id="2bbdf-123">Lock:Timeout (timeout > 0) 事件类</span><span class="sxs-lookup"><span data-stu-id="2bbdf-123">Lock:Timeout &#40;timeout &#62; 0&#41; Event Class</span></span>](lock-timeout-timeout-0-event-class.md)|<span data-ttu-id="2bbdf-124">由于另一个事务持有所需资源的阻塞锁而使锁请求无法完成时，跟踪该锁请求。</span><span class="sxs-lookup"><span data-stu-id="2bbdf-124">Tracks when lock requests cannot be completed because another transaction has a blocking lock on the requested resource.</span></span> <span data-ttu-id="2bbdf-125">仅在锁超时值大于零的情况下才会发生此类事件。</span><span class="sxs-lookup"><span data-stu-id="2bbdf-125">This event occurs only in situations where the lock time-out value is greater than zero.</span></span>|  
|[<span data-ttu-id="2bbdf-126">Lock:Timeout 事件类</span><span class="sxs-lookup"><span data-stu-id="2bbdf-126">Lock:Timeout Event Class</span></span>](lock-timeout-event-class.md)|<span data-ttu-id="2bbdf-127">由于另一个事务持有所需资源的阻塞锁而使锁请求无法完成时，跟踪该锁请求。</span><span class="sxs-lookup"><span data-stu-id="2bbdf-127">Tracks when lock requests cannot be completed because another transaction has a blocking lock on the requested resource.</span></span>|  
  
  
