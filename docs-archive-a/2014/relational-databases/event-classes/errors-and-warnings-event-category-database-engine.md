---
title: “错误和警告”事件类别（数据库引擎）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Errors and Warnings event category [SQL Server]
- SQL Server event classes, Errors and Warnings event category
- event classes [SQL Server], Errors and Warnings event category
ms.assetid: 249c19b5-af68-4433-80f6-337395176641
author: stevestein
ms.author: sstein
ms.openlocfilehash: d55f37f5401f60ddfeec340af1ae6d532eb6ad01
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691190"
---
# <a name="errors-and-warnings-event-category-database-engine"></a><span data-ttu-id="58cc9-102">Errors and Warnings 事件类别（数据库引擎）</span><span class="sxs-lookup"><span data-stu-id="58cc9-102">Errors and Warnings Event Category (Database Engine)</span></span>
  <span data-ttu-id="58cc9-103">**Errors and Warnings** 事件类别包含常规错误和警告事件。</span><span class="sxs-lookup"><span data-stu-id="58cc9-103">The **Errors and Warnings** event category contains general error and warning events.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="58cc9-104">本节内容</span><span class="sxs-lookup"><span data-stu-id="58cc9-104">In This Section</span></span>  
  
|<span data-ttu-id="58cc9-105">主题</span><span class="sxs-lookup"><span data-stu-id="58cc9-105">Topic</span></span>|<span data-ttu-id="58cc9-106">说明</span><span class="sxs-lookup"><span data-stu-id="58cc9-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="58cc9-107">Attention 事件类</span><span class="sxs-lookup"><span data-stu-id="58cc9-107">Attention Event Class</span></span>](attention-event-class.md)|<span data-ttu-id="58cc9-108">指示出现了 **Attention** 事件。</span><span class="sxs-lookup"><span data-stu-id="58cc9-108">Indicates that an **Attention** event has occurred.</span></span>|  
|[<span data-ttu-id="58cc9-109">Background Job Error 事件类</span><span class="sxs-lookup"><span data-stu-id="58cc9-109">Background Job Error Event Class</span></span>](background-job-error-event-class.md)|<span data-ttu-id="58cc9-110">指示后台作业异常终止。</span><span class="sxs-lookup"><span data-stu-id="58cc9-110">Indicates that a background job has terminated abnormally.</span></span>|  
|[<span data-ttu-id="58cc9-111">Bitmap Warning 事件类</span><span class="sxs-lookup"><span data-stu-id="58cc9-111">Bitmap Warning Event Class</span></span>](bitmap-warning-event-class.md)|<span data-ttu-id="58cc9-112">指示已在查询中禁用位图筛选。</span><span class="sxs-lookup"><span data-stu-id="58cc9-112">Indicates that bitmap filtering has been disabled in a query.</span></span>|  
|[<span data-ttu-id="58cc9-113">Blocked Process Report 事件类</span><span class="sxs-lookup"><span data-stu-id="58cc9-113">Blocked Process Report Event Class</span></span>](blocked-process-report-event-class.md)|<span data-ttu-id="58cc9-114">指示任务被阻塞的时间超过了指定的时间。</span><span class="sxs-lookup"><span data-stu-id="58cc9-114">Indicates that a task has been blocked for more than a specified amount of time.</span></span>|  
|[<span data-ttu-id="58cc9-115">CPU Threshold Exceeded 事件类</span><span class="sxs-lookup"><span data-stu-id="58cc9-115">CPU Threshold Exceeded Event Class</span></span>](cpu-threshold-exceeded-event-class.md)|<span data-ttu-id="58cc9-116">指示资源调控器检测到超出指定 CPU 阈值的查询。</span><span class="sxs-lookup"><span data-stu-id="58cc9-116">Indicates that the Resource Governor detects a query that exceeds the specified CPU threshold.</span></span>|  
|[<span data-ttu-id="58cc9-117">ErrorLog 事件类</span><span class="sxs-lookup"><span data-stu-id="58cc9-117">ErrorLog Event Class</span></span>](errorlog-event-class.md)|<span data-ttu-id="58cc9-118">指示已将错误事件记录到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误日志中。</span><span class="sxs-lookup"><span data-stu-id="58cc9-118">Indicates that error events have been logged in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log.</span></span>|  
|[<span data-ttu-id="58cc9-119">EventLog 事件类</span><span class="sxs-lookup"><span data-stu-id="58cc9-119">EventLog Event Class</span></span>](eventlog-event-class.md)|<span data-ttu-id="58cc9-120">指示已将事件记录到 Windows 事件日志中。</span><span class="sxs-lookup"><span data-stu-id="58cc9-120">Indicates that events have been logged in the Windows event log.</span></span>|  
|[<span data-ttu-id="58cc9-121">Exception 事件类</span><span class="sxs-lookup"><span data-stu-id="58cc9-121">Exception Event Class</span></span>](exception-event-class.md)|<span data-ttu-id="58cc9-122">指示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中出现了异常。</span><span class="sxs-lookup"><span data-stu-id="58cc9-122">Indicates that an exception has occurred in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="58cc9-123">Exchange Spill 事件类</span><span class="sxs-lookup"><span data-stu-id="58cc9-123">Exchange Spill Event Class</span></span>](exchange-spill-event-class.md)|<span data-ttu-id="58cc9-124">指示并行查询计划中的通信缓冲区已写入 tempdb 数据库。</span><span class="sxs-lookup"><span data-stu-id="58cc9-124">Indicates that communication buffers in a parallel query plan have been written to the tempdb database.</span></span>|  
|[<span data-ttu-id="58cc9-125">Execution Warnings 事件类</span><span class="sxs-lookup"><span data-stu-id="58cc9-125">Execution Warnings Event Class</span></span>](execution-warnings-event-class.md)|<span data-ttu-id="58cc9-126">指示在执行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 语句或存储过程期间出现了内存授予警告。</span><span class="sxs-lookup"><span data-stu-id="58cc9-126">Indicates that memory grant warnings occurred during the execution of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] statement or stored procedure.</span></span>|  
|[<span data-ttu-id="58cc9-127">Hash Warning 事件类</span><span class="sxs-lookup"><span data-stu-id="58cc9-127">Hash Warning Event Class</span></span>](hash-warning-event-class.md)|<span data-ttu-id="58cc9-128">指示在哈希操作过程中发生哈希递归或哈希援助。</span><span class="sxs-lookup"><span data-stu-id="58cc9-128">Indicates that a hash recursion or hash bailout has occurred during a hashing operation.</span></span>|  
|[<span data-ttu-id="58cc9-129">Missing Column Statistics 事件类</span><span class="sxs-lookup"><span data-stu-id="58cc9-129">Missing Column Statistics Event Class</span></span>](missing-column-statistics-event-class.md)|<span data-ttu-id="58cc9-130">指示缺少可能对优化器有用的列统计信息。</span><span class="sxs-lookup"><span data-stu-id="58cc9-130">Indicates that column statistics that could have been useful for the optimizer are not available.</span></span>|  
|[<span data-ttu-id="58cc9-131">Missing Join Predicate 事件类</span><span class="sxs-lookup"><span data-stu-id="58cc9-131">Missing Join Predicate Event Class</span></span>](missing-join-predicate-event-class.md)|<span data-ttu-id="58cc9-132">指示正在执行没有联接谓词的查询。</span><span class="sxs-lookup"><span data-stu-id="58cc9-132">Indicates that a query is being executed that has no join predicate.</span></span>|  
|[<span data-ttu-id="58cc9-133">Sort Warnings 事件类</span><span class="sxs-lookup"><span data-stu-id="58cc9-133">Sort Warnings Event Class</span></span>](sort-warnings-event-class.md)|<span data-ttu-id="58cc9-134">指示不适合内存的排序操作。</span><span class="sxs-lookup"><span data-stu-id="58cc9-134">Indicates that sort operations do not fit into memory.</span></span>|  
|[<span data-ttu-id="58cc9-135">User Error Message 事件类</span><span class="sxs-lookup"><span data-stu-id="58cc9-135">User Error Message Event Class</span></span>](user-error-message-event-class.md)|<span data-ttu-id="58cc9-136">显示用户可见的错误消息。</span><span class="sxs-lookup"><span data-stu-id="58cc9-136">Displays error messages that are seen by the user.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="58cc9-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="58cc9-137">See Also</span></span>  
 [<span data-ttu-id="58cc9-138">sp_trace_setevent (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="58cc9-138">sp_trace_setevent &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  
