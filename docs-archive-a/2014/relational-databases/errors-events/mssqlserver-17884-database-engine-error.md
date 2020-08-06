---
title: MSSQLSERVER_17884 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17884 (Database Engine error)
ms.assetid: 8d05ba05-3f71-4dc3-bd81-2ea5ac9fe843
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: bd5beca2a7dfd20afbf9eff196d89452ef3533d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690629"
---
# <a name="mssqlserver_17884"></a><span data-ttu-id="b2fe2-102">MSSQLSERVER_17884</span><span class="sxs-lookup"><span data-stu-id="b2fe2-102">MSSQLSERVER_17884</span></span>
    
## <a name="details"></a><span data-ttu-id="b2fe2-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="b2fe2-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b2fe2-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="b2fe2-104">Product Name</span></span>|<span data-ttu-id="b2fe2-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="b2fe2-105">SQL Server</span></span>|  
|<span data-ttu-id="b2fe2-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="b2fe2-106">Event ID</span></span>|<span data-ttu-id="b2fe2-107">17884</span><span class="sxs-lookup"><span data-stu-id="b2fe2-107">17884</span></span>|  
|<span data-ttu-id="b2fe2-108">事件源</span><span class="sxs-lookup"><span data-stu-id="b2fe2-108">Event Source</span></span>|<span data-ttu-id="b2fe2-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="b2fe2-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="b2fe2-110">组件</span><span class="sxs-lookup"><span data-stu-id="b2fe2-110">Component</span></span>|<span data-ttu-id="b2fe2-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="b2fe2-111">SQLEngine</span></span>|  
|<span data-ttu-id="b2fe2-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="b2fe2-112">Symbolic Name</span></span>|<span data-ttu-id="b2fe2-113">SRV_SCHEDULER_DEADLOCK</span><span class="sxs-lookup"><span data-stu-id="b2fe2-113">SRV_SCHEDULER_DEADLOCK</span></span>|  
|<span data-ttu-id="b2fe2-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="b2fe2-114">Message Text</span></span>|<span data-ttu-id="b2fe2-115">在最后 %d 秒内，没有一个工作线程拾取了分配给节点 %d 上的进程的新查询。</span><span class="sxs-lookup"><span data-stu-id="b2fe2-115">New queries assigned to process on Node %d have not been picked  up by a worker thread in the last %d seconds.</span></span> <span data-ttu-id="b2fe2-116">查询被阻塞或长时间运行可能导致出现此情况，并且可能会延长客户端响应时间。</span><span class="sxs-lookup"><span data-stu-id="b2fe2-116">Blocking or long-running queries can contribute to this condition, and may degrade client response time.</span></span> <span data-ttu-id="b2fe2-117">请使用 "最大工作线程数(max worker threads)" 配置选项增加允许的线程数，或者优化当前正运行的查询。</span><span class="sxs-lookup"><span data-stu-id="b2fe2-117">Use the "max worker threads" configuration option to increase number  of allowable threads, or optimize current running queries.</span></span>  <span data-ttu-id="b2fe2-118">SQL 进程使用率: %d%%。</span><span class="sxs-lookup"><span data-stu-id="b2fe2-118">SQL Process Utilization: %d%%.</span></span> <span data-ttu-id="b2fe2-119">系统空闲率：%d%%。</span><span class="sxs-lookup"><span data-stu-id="b2fe2-119">System Idle: %d%%.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="b2fe2-120">说明</span><span class="sxs-lookup"><span data-stu-id="b2fe2-120">Explanation</span></span>  
 <span data-ttu-id="b2fe2-121">每个计划程序都没有向前运行的迹象，这可能是由死锁造成的：每个线程都无法向前运行和/或无法提取并处理新的工作。</span><span class="sxs-lookup"><span data-stu-id="b2fe2-121">There is no sign of progress in each of the schedulers and could be caused by deadlocks where none of the threads can advance and/or no new work can be picked up and processed.</span></span> <span data-ttu-id="b2fe2-122">如果进程使用率较低，计算机上的其他进程可能导致服务器进程 CPU 不足。</span><span class="sxs-lookup"><span data-stu-id="b2fe2-122">If process utilization is low then other processes on the machine may be causing the server process CPU starvation.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b2fe2-123">用户操作</span><span class="sxs-lookup"><span data-stu-id="b2fe2-123">User Action</span></span>  
 <span data-ttu-id="b2fe2-124">确定发生阻塞而无法向前运行的原因，并相应地解决这些问题。</span><span class="sxs-lookup"><span data-stu-id="b2fe2-124">Determine why there is blocking and no progress being made and resolve situation accordingly.</span></span> <span data-ttu-id="b2fe2-125">如果进程使用率较低，请检查系统上其他进程产生的负载。</span><span class="sxs-lookup"><span data-stu-id="b2fe2-125">If process utilization is low check the load on the system caused by other processes.</span></span>  
  
  
