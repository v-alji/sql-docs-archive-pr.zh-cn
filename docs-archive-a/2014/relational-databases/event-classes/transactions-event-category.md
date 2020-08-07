---
title: “事务”事件类别 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- SQL Server event classes, Transactions event category
- event classes [SQL Server], Transactions event category
- Transactions event category [SQL Server]
ms.assetid: bfc75c5b-7115-49d8-9148-a0c84ee66a9a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3b68a91fb166797c220cb0c4f5cf2607ca267538
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589109"
---
# <a name="transactions-event-category"></a><span data-ttu-id="deabf-102">Transactions 事件类别</span><span class="sxs-lookup"><span data-stu-id="deabf-102">Transactions Event Category</span></span>
  <span data-ttu-id="deabf-103">**Transactions** 事件类可用于监视事务的状态。</span><span class="sxs-lookup"><span data-stu-id="deabf-103">The **Transactions** event classes can be used to monitor the status of transactions.</span></span> <span data-ttu-id="deabf-104">带有 **TM:** 前缀的事件类名称可用于跟踪通过事务管理界面发送的、与事务相关的操作。</span><span class="sxs-lookup"><span data-stu-id="deabf-104">The event class names that are prefixed with **TM:** are used to track the transaction-related operations that are sent through the transaction management interface.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="deabf-105">本节内容</span><span class="sxs-lookup"><span data-stu-id="deabf-105">In This Section</span></span>  
  
|<span data-ttu-id="deabf-106">主题</span><span class="sxs-lookup"><span data-stu-id="deabf-106">Topic</span></span>|<span data-ttu-id="deabf-107">说明</span><span class="sxs-lookup"><span data-stu-id="deabf-107">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="deabf-108">DTCTransaction 事件类</span><span class="sxs-lookup"><span data-stu-id="deabf-108">DTCTransaction Event Class</span></span>](dtctransaction-event-class.md)|<span data-ttu-id="deabf-109">跟踪由 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 分布式事务处理协调器 (MS DTC) 协调的事务。</span><span class="sxs-lookup"><span data-stu-id="deabf-109">Tracks transactions coordinated by the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator (MS DTC).</span></span> <span data-ttu-id="deabf-110">这些是在 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]的两个或两个以上的数据库或实例之间分布的事务。</span><span class="sxs-lookup"><span data-stu-id="deabf-110">These are transactions distributed between two or more databases or instances of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span>|  
|[<span data-ttu-id="deabf-111">SQLTransaction 事件类</span><span class="sxs-lookup"><span data-stu-id="deabf-111">SQLTransaction Event Class</span></span>](sqltransaction-event-class.md)|<span data-ttu-id="deabf-112">跟踪 [!INCLUDE[tsql](../../includes/tsql-md.md)] BEGIN TRAN、COMMIT TRAN、SAVE TRAN 和 ROLLBACK TRAN 语句。</span><span class="sxs-lookup"><span data-stu-id="deabf-112">Tracks [!INCLUDE[tsql](../../includes/tsql-md.md)] BEGIN TRAN, COMMIT TRAN, SAVE TRAN, and ROLLBACK TRAN statements.</span></span>|  
|[<span data-ttu-id="deabf-113">TM: Begin Tran Completed 事件类</span><span class="sxs-lookup"><span data-stu-id="deabf-113">TM: Begin Tran Completed Event Class</span></span>](tm-begin-tran-completed-event-class.md)|<span data-ttu-id="deabf-114">指明已完成 BEGIN TRANSACTION 请求。</span><span class="sxs-lookup"><span data-stu-id="deabf-114">Indicates that a BEGIN TRANSACTION request has completed.</span></span>|  
|[<span data-ttu-id="deabf-115">TM: Begin Tran Starting 事件类</span><span class="sxs-lookup"><span data-stu-id="deabf-115">TM: Begin Tran Starting Event Class</span></span>](tm-begin-tran-starting-event-class.md)|<span data-ttu-id="deabf-116">指明正在启动 BEGIN TRANSACTION 请求。</span><span class="sxs-lookup"><span data-stu-id="deabf-116">Indicates that a BEGIN TRANSACTION request is starting.</span></span>|  
|[<span data-ttu-id="deabf-117">TM: Commit Tran Completed 事件类</span><span class="sxs-lookup"><span data-stu-id="deabf-117">TM: Commit Tran Completed Event Class</span></span>](tm-commit-tran-completed-event-class.md)|<span data-ttu-id="deabf-118">指明已完成 COMMIT TRANSACTION 请求。</span><span class="sxs-lookup"><span data-stu-id="deabf-118">Indicates that a COMMIT TRANSACTION request has completed.</span></span>|  
|[<span data-ttu-id="deabf-119">TM: Commit Tran Starting 事件类</span><span class="sxs-lookup"><span data-stu-id="deabf-119">TM: Commit Tran Starting Event Class</span></span>](tm-commit-tran-starting-event-class.md)|<span data-ttu-id="deabf-120">指明正在启动 COMMIT TRANSACTION 请求。</span><span class="sxs-lookup"><span data-stu-id="deabf-120">Indicates that a COMMIT TRANSACTION request is starting.</span></span>|  
|[<span data-ttu-id="deabf-121">TM: Promote Tran Completed 事件类</span><span class="sxs-lookup"><span data-stu-id="deabf-121">TM: Promote Tran Completed Event Class</span></span>](tm-promote-tran-completed-event-class.md)|<span data-ttu-id="deabf-122">指明已完成 PROMOTE TRANSACTION 请求。</span><span class="sxs-lookup"><span data-stu-id="deabf-122">Indicates that a PROMOTE TRANSACTION request has completed.</span></span>|  
|[<span data-ttu-id="deabf-123">TM: Promote Tran Starting 事件类</span><span class="sxs-lookup"><span data-stu-id="deabf-123">TM: Promote Tran Starting Event Class</span></span>](tm-promote-tran-starting-event-class.md)|<span data-ttu-id="deabf-124">指明正在启动 PROMOTE TRANSACTION 请求。</span><span class="sxs-lookup"><span data-stu-id="deabf-124">Indicates that a PROMOTE TRANSACTION request is starting.</span></span>|  
|[<span data-ttu-id="deabf-125">TM: Rollback Tran Completed 事件类</span><span class="sxs-lookup"><span data-stu-id="deabf-125">TM: Rollback Tran Completed Event Class</span></span>](tm-rollback-tran-completed-event-class.md)|<span data-ttu-id="deabf-126">指明已完成 ROLLBACK TRANSACTION 请求。</span><span class="sxs-lookup"><span data-stu-id="deabf-126">Indicates that a ROLLBACK TRANSACTION request has completed.</span></span>|  
|[<span data-ttu-id="deabf-127">TM: Rollback Tran Starting 事件类</span><span class="sxs-lookup"><span data-stu-id="deabf-127">TM: Rollback Tran Starting Event Class</span></span>](tm-rollback-tran-starting-event-class.md)|<span data-ttu-id="deabf-128">指明正在启动 ROLLBACK TRANSACTION 请求。</span><span class="sxs-lookup"><span data-stu-id="deabf-128">Indicates that a ROLLBACK TRANSACTION request is starting.</span></span>|  
|[<span data-ttu-id="deabf-129">TM: Save Tran Completed 事件类</span><span class="sxs-lookup"><span data-stu-id="deabf-129">TM: Save Tran Completed Event Class</span></span>](tm-save-tran-completed-event-class.md)|<span data-ttu-id="deabf-130">指明已完成 SAVE TRANSACTION 请求。</span><span class="sxs-lookup"><span data-stu-id="deabf-130">Indicates that a SAVE TRANSACTION request has completed.</span></span>|  
|[<span data-ttu-id="deabf-131">TM: Save Tran Starting 事件类</span><span class="sxs-lookup"><span data-stu-id="deabf-131">TM: Save Tran Starting Event Class</span></span>](tm-save-tran-starting-event-class.md)|<span data-ttu-id="deabf-132">指明正在启动 SAVE TRANSACTION 请求。</span><span class="sxs-lookup"><span data-stu-id="deabf-132">Indicates that a SAVE TRANSACTION request is starting.</span></span>|  
|[<span data-ttu-id="deabf-133">TransactionLog 事件类</span><span class="sxs-lookup"><span data-stu-id="deabf-133">TransactionLog Event Class</span></span>](transactionlog-event-class.md)|<span data-ttu-id="deabf-134">跟踪事务何时写入数据库事务日志。</span><span class="sxs-lookup"><span data-stu-id="deabf-134">Tracks when transactions are written to a database transaction log.</span></span>|  
  
  
