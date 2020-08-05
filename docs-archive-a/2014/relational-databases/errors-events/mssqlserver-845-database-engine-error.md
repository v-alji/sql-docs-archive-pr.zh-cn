---
title: MSSQLSERVER_845 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 845 (Database Engine error)
ms.assetid: 8fff6ad4-234c-44be-b123-e25d5e1cd63e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 24bfb8b3758d0656dad96e4af4ed3b94aa51e07f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580762"
---
# <a name="mssqlserver_845"></a><span data-ttu-id="aec98-102">MSSQLSERVER_845</span><span class="sxs-lookup"><span data-stu-id="aec98-102">MSSQLSERVER_845</span></span>
    
## <a name="details"></a><span data-ttu-id="aec98-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="aec98-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="aec98-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="aec98-104">Product Name</span></span>|<span data-ttu-id="aec98-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="aec98-105">SQL Server</span></span>|  
|<span data-ttu-id="aec98-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="aec98-106">Event ID</span></span>|<span data-ttu-id="aec98-107">845</span><span class="sxs-lookup"><span data-stu-id="aec98-107">845</span></span>|  
|<span data-ttu-id="aec98-108">事件源</span><span class="sxs-lookup"><span data-stu-id="aec98-108">Event Source</span></span>|<span data-ttu-id="aec98-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="aec98-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="aec98-110">组件</span><span class="sxs-lookup"><span data-stu-id="aec98-110">Component</span></span>|<span data-ttu-id="aec98-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="aec98-111">SQLEngine</span></span>|  
|<span data-ttu-id="aec98-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="aec98-112">Symbolic Name</span></span>|<span data-ttu-id="aec98-113">BUFLATCH_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="aec98-113">BUFLATCH_TIMEOUT</span></span>|  
|<span data-ttu-id="aec98-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="aec98-114">Message Text</span></span>|<span data-ttu-id="aec98-115">等待用于页 %S_PGID，数据库 ID %d 的缓冲区闩锁类型 %d 时发生超时。</span><span class="sxs-lookup"><span data-stu-id="aec98-115">Time-out occurred while waiting for buffer latch type %d for page %S_PGID, database ID %d.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="aec98-116">说明</span><span class="sxs-lookup"><span data-stu-id="aec98-116">Explanation</span></span>  
 <span data-ttu-id="aec98-117">进程要等待获取闩锁，但进程等到时限过期后也未能获得闩锁。</span><span class="sxs-lookup"><span data-stu-id="aec98-117">A process was waiting to acquire a latch, but the process waited until the time limit expired and failed to acquire one.</span></span> <span data-ttu-id="aec98-118">其他任务阻塞系统进程时，通常会导致完成 I/O 操作的时间过长，这时则可能发生此错误。</span><span class="sxs-lookup"><span data-stu-id="aec98-118">This can occur if an I/O operation takes too long to complete, usually as a result of other tasks blocking system processes.</span></span> <span data-ttu-id="aec98-119">在一些实例中，此错误可能是硬件故障引起的。</span><span class="sxs-lookup"><span data-stu-id="aec98-119">In some instances, this error may be the result of hardware failure.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="aec98-120">用户操作</span><span class="sxs-lookup"><span data-stu-id="aec98-120">User Action</span></span>  
 <span data-ttu-id="aec98-121">执行下列任务可能可以防止此错误：</span><span class="sxs-lookup"><span data-stu-id="aec98-121">Performing the following tasks may prevent this error:</span></span>  
  
-   <span data-ttu-id="aec98-122">减少工作负荷。</span><span class="sxs-lookup"><span data-stu-id="aec98-122">Reduce the workload.</span></span>  
  
-   <span data-ttu-id="aec98-123">检查错误日志或事件日志中是否存在相关联的 I/O 故障。</span><span class="sxs-lookup"><span data-stu-id="aec98-123">Verify whether there are associated I/O failures in the error log or event log.</span></span> <span data-ttu-id="aec98-124">I/O 故障通常是由磁盘故障引起的。</span><span class="sxs-lookup"><span data-stu-id="aec98-124">I/O failures are typically caused by disk malfunction.</span></span>  
  
-   <span data-ttu-id="aec98-125">检查错误日志中是否存在非生成任务和其他严重错误。</span><span class="sxs-lookup"><span data-stu-id="aec98-125">Check error log for non-yielding tasks and other critical errors.</span></span>  
  
-   <span data-ttu-id="aec98-126">如果频繁出现诸如断定之类的错误，请解决这些问题。</span><span class="sxs-lookup"><span data-stu-id="aec98-126">If critical errors such as asserts frequently occur, resolve these problems.</span></span>  
  
 <span data-ttu-id="aec98-127">如果错误仍存在，请与 Microsoft 客户服务与支持部门联系。</span><span class="sxs-lookup"><span data-stu-id="aec98-127">If the error persists, contact Microsoft Customer Service and Support.</span></span>  
  
  
