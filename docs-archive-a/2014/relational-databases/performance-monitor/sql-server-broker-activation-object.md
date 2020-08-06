---
title: SQL Server - Broker Activation 对象 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:Broker Activation
- Broker Activation object
ms.assetid: cd9b6880-c924-42c7-b333-09c303317c0b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4048c2baecaeb4bde7a1e215a15e8c51a60a01bd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689351"
---
# <a name="sql-server-broker-activation-object"></a><span data-ttu-id="f446b-102">SQL Server Broker Activation 对象</span><span class="sxs-lookup"><span data-stu-id="f446b-102">SQL Server, Broker Activation Object</span></span>
  <span data-ttu-id="f446b-103">**SQLServer:BrokerActivation** 性能对象包含一些性能计数器，这些计数器报告有关存储过程激活的信息。</span><span class="sxs-lookup"><span data-stu-id="f446b-103">The **SQLServer:BrokerActivation** performance object contains performance counters that report information on stored procedure activation.</span></span> <span data-ttu-id="f446b-104">下表列出了此对象包含的计数器。</span><span class="sxs-lookup"><span data-stu-id="f446b-104">The table below lists the counters that this object contains.</span></span>  
  
|<span data-ttu-id="f446b-105">SQL Server Broker Activation 计数器</span><span class="sxs-lookup"><span data-stu-id="f446b-105">SQL Server Broker Activation counters</span></span>|<span data-ttu-id="f446b-106">说明</span><span class="sxs-lookup"><span data-stu-id="f446b-106">Description</span></span>|  
|-------------------------------------------|-----------------|  
|<span data-ttu-id="f446b-107">**Stored Procedures Invoked/sec**</span><span class="sxs-lookup"><span data-stu-id="f446b-107">**Stored Procedures Invoked/sec**</span></span>|<span data-ttu-id="f446b-108">此计数器报告每秒内实例中所有队列监视器调用的激活存储过程的总数。</span><span class="sxs-lookup"><span data-stu-id="f446b-108">This counter reports the total number of activation stored procedures invoked by all queue monitors in the instance per second.</span></span>|  
|<span data-ttu-id="f446b-109">**Task Limit Reached**</span><span class="sxs-lookup"><span data-stu-id="f446b-109">**Task Limit Reached**</span></span>|<span data-ttu-id="f446b-110">此计数器报告队列监视器本应启动新任务但由于已在运行的队列任务数达到最大值而并未启动的总次数。</span><span class="sxs-lookup"><span data-stu-id="f446b-110">This counter reports the total number of times that a queue monitor would have started a new task, but did not because the maximum number of tasks for the queue is already running.</span></span>|  
|<span data-ttu-id="f446b-111">**Task Limit Reached/sec**</span><span class="sxs-lookup"><span data-stu-id="f446b-111">**Task Limit Reached/sec**</span></span>|<span data-ttu-id="f446b-112">此计数器报告每秒内队列监视器本应启动新任务但由于已在运行的队列任务数达到最大值而并未启动的次数。</span><span class="sxs-lookup"><span data-stu-id="f446b-112">This counter reports the number of times per second that a queue monitor would have started a new task, but did not because the maximum number of tasks for the queue is already running.</span></span>|  
|<span data-ttu-id="f446b-113">**Tasks Aborted/sec**</span><span class="sxs-lookup"><span data-stu-id="f446b-113">**Tasks Aborted/sec**</span></span>|<span data-ttu-id="f446b-114">此计数器报告以错误结束或由队列监视器因无法接收消息而中止的激活存储过程任务数。</span><span class="sxs-lookup"><span data-stu-id="f446b-114">This counter reports the number of activation stored procedure tasks that end with an error, or are aborted by a queue monitor for failing to receive messages.</span></span>|  
|<span data-ttu-id="f446b-115">**Tasks Running**</span><span class="sxs-lookup"><span data-stu-id="f446b-115">**Tasks Running**</span></span>|<span data-ttu-id="f446b-116">此计数器报告当前运行的激活存储过程数。</span><span class="sxs-lookup"><span data-stu-id="f446b-116">This counter reports the number of activation stored procedures that are currently running.</span></span>|  
|<span data-ttu-id="f446b-117">**Tasks Started/sec**</span><span class="sxs-lookup"><span data-stu-id="f446b-117">**Tasks Started/sec**</span></span>|<span data-ttu-id="f446b-118">此计数器报告每秒内实例中所有队列监视器启动的激活存储过程数。</span><span class="sxs-lookup"><span data-stu-id="f446b-118">This counter reports the number of activation stored procedures started per second by all queue monitors in the instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f446b-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f446b-119">See Also</span></span>  
 <span data-ttu-id="f446b-120">[sys.dm_broker_activated_tasks (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-broker-activated-tasks-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f446b-120">[sys.dm_broker_activated_tasks &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-broker-activated-tasks-transact-sql) </span></span>  
 <span data-ttu-id="f446b-121">[sys.dm_broker_queue_monitors (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-broker-queue-monitors-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f446b-121">[sys.dm_broker_queue_monitors &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-broker-queue-monitors-transact-sql) </span></span>  
 [<span data-ttu-id="f446b-122">监视资源使用情况（系统监视器）</span><span class="sxs-lookup"><span data-stu-id="f446b-122">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](monitor-resource-usage-system-monitor.md)  
  
  
