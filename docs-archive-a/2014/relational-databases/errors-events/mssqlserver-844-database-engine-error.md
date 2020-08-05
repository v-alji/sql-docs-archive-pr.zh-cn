---
title: MSSQLSERVER_844 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 844 (Database Engine error)
ms.assetid: 2060c886-1226-4066-bc0c-de90a1cfb82b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c4870d6e43ec12b49033ea3b5f88fa0d0cdd597a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580766"
---
# <a name="mssqlserver_844"></a><span data-ttu-id="333fe-102">MSSQLSERVER_844</span><span class="sxs-lookup"><span data-stu-id="333fe-102">MSSQLSERVER_844</span></span>
    
## <a name="details"></a><span data-ttu-id="333fe-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="333fe-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="333fe-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="333fe-104">Product Name</span></span>|<span data-ttu-id="333fe-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="333fe-105">SQL Server</span></span>|  
|<span data-ttu-id="333fe-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="333fe-106">Event ID</span></span>|<span data-ttu-id="333fe-107">844</span><span class="sxs-lookup"><span data-stu-id="333fe-107">844</span></span>|  
|<span data-ttu-id="333fe-108">事件源</span><span class="sxs-lookup"><span data-stu-id="333fe-108">Event Source</span></span>|<span data-ttu-id="333fe-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="333fe-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="333fe-110">组件</span><span class="sxs-lookup"><span data-stu-id="333fe-110">Component</span></span>|<span data-ttu-id="333fe-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="333fe-111">SQLEngine</span></span>|  
|<span data-ttu-id="333fe-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="333fe-112">Symbolic Name</span></span>|<span data-ttu-id="333fe-113">BUFLATCH_TIMEOUT_CONTINUE</span><span class="sxs-lookup"><span data-stu-id="333fe-113">BUFLATCH_TIMEOUT_CONTINUE</span></span>|  
|<span data-ttu-id="333fe-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="333fe-114">Message Text</span></span>|<span data-ttu-id="333fe-115">等待缓冲区闩锁时出现超时 - 类型 %d，bp %p，页 %d:%d，stat %#x，数据库 ID: %d，分配单元 ID: %I64d%ls，任务 0x%p : %d，等待时间 %d，标志 0x%I64x，所属任务 0x%p。</span><span class="sxs-lookup"><span data-stu-id="333fe-115">Time-out occurred while waiting for buffer latch -- type %d, bp %p, page %d:%d, stat %#x, database id: %d, allocation unit id: %I64d%ls, task 0x%p : %d, waittime %d, flags 0x%I64x, owning task 0x%p.</span></span>  <span data-ttu-id="333fe-116">将继续等待。</span><span class="sxs-lookup"><span data-stu-id="333fe-116">Continuing to wait.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="333fe-117">说明</span><span class="sxs-lookup"><span data-stu-id="333fe-117">Explanation</span></span>  
 <span data-ttu-id="333fe-118">进程正在等待获取闩锁。</span><span class="sxs-lookup"><span data-stu-id="333fe-118">A process is waiting to acquire a latch.</span></span> <span data-ttu-id="333fe-119">此问题可能是由所用时间太长而无法完成的 I/O 操作导致的。</span><span class="sxs-lookup"><span data-stu-id="333fe-119">This problem can be caused by an I/O operation taking too long to complete.</span></span> <span data-ttu-id="333fe-120">通常，此类型的错误是其他任务阻塞系统进程的结果。</span><span class="sxs-lookup"><span data-stu-id="333fe-120">Typically this type of error is the result of other tasks blocking system processes.</span></span> <span data-ttu-id="333fe-121">在一些实例中，此错误可能是硬件故障引起的。</span><span class="sxs-lookup"><span data-stu-id="333fe-121">In some instances, this error may be the result of hardware failure.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="333fe-122">用户操作</span><span class="sxs-lookup"><span data-stu-id="333fe-122">User Action</span></span>  
 <span data-ttu-id="333fe-123">尝试执行以下操作以防止出现此错误：</span><span class="sxs-lookup"><span data-stu-id="333fe-123">Try the following to prevent this error from occurring:</span></span>  
  
-   <span data-ttu-id="333fe-124">减少工作负荷。</span><span class="sxs-lookup"><span data-stu-id="333fe-124">Reduce workload.</span></span>  
  
-   <span data-ttu-id="333fe-125">在错误日志或事件日志中检查关联的 I/O 故障。</span><span class="sxs-lookup"><span data-stu-id="333fe-125">Check for associated I/O failures in error log or event log.</span></span> <span data-ttu-id="333fe-126">I/O 故障通常是指磁盘故障。</span><span class="sxs-lookup"><span data-stu-id="333fe-126">I/O failures typically point to a disk malfunction.</span></span>  
  
-   <span data-ttu-id="333fe-127">检查错误日志以查找非生成任务和其他错误。</span><span class="sxs-lookup"><span data-stu-id="333fe-127">Check the error log for non-yielding tasks and other critical errors.</span></span>  
  
-   <span data-ttu-id="333fe-128">如果频繁出现诸如断定之类的错误，请解决这些问题。</span><span class="sxs-lookup"><span data-stu-id="333fe-128">If critical errors such as asserts frequently occur, resolve these problems.</span></span>  
  
 <span data-ttu-id="333fe-129">如果错误仍存在，请与 Microsoft 客户服务与支持部门联系。</span><span class="sxs-lookup"><span data-stu-id="333fe-129">If the error persists, contact Microsoft Customer Service and Support.</span></span>  
  
  
