---
title: SQL Server 扩展事件目标 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- targets [SQL Server extended events]
- extended events [SQL Server], targets
ms.assetid: e281684c-40d1-4cf9-a0d4-7ea1ecffa384
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 010b7cc29543f266b77aaf180c50173ef9f70346
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577804"
---
# <a name="sql-server-extended-events-targets"></a><span data-ttu-id="4ca45-102">SQL Server Extended Events Targets</span><span class="sxs-lookup"><span data-stu-id="4ca45-102">SQL Server Extended Events Targets</span></span>
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="4ca45-103">扩展事件目标是事件使用者。</span><span class="sxs-lookup"><span data-stu-id="4ca45-103">Extended Events targets are event consumers.</span></span> <span data-ttu-id="4ca45-104">目标可以写入文件、在内存缓冲区中存储事件数据或聚合事件数据。</span><span class="sxs-lookup"><span data-stu-id="4ca45-104">Targets can write to a file, store event data in a memory buffer, or aggregate event data.</span></span> <span data-ttu-id="4ca45-105">目标可以同步或异步处理数据。</span><span class="sxs-lookup"><span data-stu-id="4ca45-105">Targets can process data synchronously or asynchronously.</span></span>  
  
 <span data-ttu-id="4ca45-106">扩展事件的设计确保了对于每个会话都保证目标收到并仅收到一次事件。</span><span class="sxs-lookup"><span data-stu-id="4ca45-106">The Extended Events design ensures that targets are guaranteed to receive events once and only once per session.</span></span>  
  
 <span data-ttu-id="4ca45-107">扩展事件提供以下可用于扩展事件会话的目标：</span><span class="sxs-lookup"><span data-stu-id="4ca45-107">Extended Events provide the following targets that you can use for an Extended Events session:</span></span>  
  
-   [<span data-ttu-id="4ca45-108">事件计数器</span><span class="sxs-lookup"><span data-stu-id="4ca45-108">Event counter</span></span>](../../2014/database-engine/event-counter-target.md)  
  
     <span data-ttu-id="4ca45-109">计算在扩展事件会话过程中发生的指定事件的数目。</span><span class="sxs-lookup"><span data-stu-id="4ca45-109">Counts all specified events that occur during an Extended Events session.</span></span> <span data-ttu-id="4ca45-110">用于获取有关工作负荷特征的信息，不必因进行完整的事件收集而增加系统开销。</span><span class="sxs-lookup"><span data-stu-id="4ca45-110">Use to obtain information about workload characteristics without adding the overhead of full event collection.</span></span> <span data-ttu-id="4ca45-111">此目标是同步目标。</span><span class="sxs-lookup"><span data-stu-id="4ca45-111">This is a synchronous target.</span></span>  
  
-   [<span data-ttu-id="4ca45-112">事件文件</span><span class="sxs-lookup"><span data-stu-id="4ca45-112">Event file</span></span>](../../2014/database-engine/event-file-target.md)  
  
     <span data-ttu-id="4ca45-113">用于将事件会话输出从完整内存缓冲区写入磁盘。</span><span class="sxs-lookup"><span data-stu-id="4ca45-113">Use to write event session output from complete memory buffers to disk.</span></span> <span data-ttu-id="4ca45-114">此目标是异步目标。</span><span class="sxs-lookup"><span data-stu-id="4ca45-114">This is an asynchronous target.</span></span>  
  
-   [<span data-ttu-id="4ca45-115">事件配对</span><span class="sxs-lookup"><span data-stu-id="4ca45-115">Event pairing</span></span>](../../2014/database-engine/event-pairing-target.md)  
  
     <span data-ttu-id="4ca45-116">许多类型的事件是成对发生的，例如锁获取和锁释放。</span><span class="sxs-lookup"><span data-stu-id="4ca45-116">Many kinds of events occur in pairs, such as lock acquires and lock releases.</span></span> <span data-ttu-id="4ca45-117">用于确定指定的成对的事件何时未成对发生。</span><span class="sxs-lookup"><span data-stu-id="4ca45-117">Use to determine when a specified paired event does not occur in a matched set.</span></span> <span data-ttu-id="4ca45-118">此目标是异步目标。</span><span class="sxs-lookup"><span data-stu-id="4ca45-118">This is an asynchronous target.</span></span>  
  
-   [<span data-ttu-id="4ca45-119">Windows 事件跟踪 (ETW)</span><span class="sxs-lookup"><span data-stu-id="4ca45-119">Event Tracing for Windows (ETW)</span></span>](../relational-databases/extended-events/event-tracing-for-windows-target.md)  
  
     <span data-ttu-id="4ca45-120">用于将 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 事件与 Windows 操作系统或应用程序事件数据相关联。</span><span class="sxs-lookup"><span data-stu-id="4ca45-120">Use to correlate [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] events with Windows operating system or application event data.</span></span> <span data-ttu-id="4ca45-121">此目标是同步目标。</span><span class="sxs-lookup"><span data-stu-id="4ca45-121">This is a synchronous target.</span></span>  
  
-   [<span data-ttu-id="4ca45-122">直方图</span><span class="sxs-lookup"><span data-stu-id="4ca45-122">Histogram</span></span>](../../2014/database-engine/histogram-target.md)  
  
     <span data-ttu-id="4ca45-123">用于基于指定的事件列或操作，对指定事件发生的次数进行计数。</span><span class="sxs-lookup"><span data-stu-id="4ca45-123">Use to count the number of times that a specified event occurs, based on a specified event column or action.</span></span> <span data-ttu-id="4ca45-124">此目标是异步目标。</span><span class="sxs-lookup"><span data-stu-id="4ca45-124">This is an asynchronous target.</span></span>  
  
-   [<span data-ttu-id="4ca45-125">环形缓冲区</span><span class="sxs-lookup"><span data-stu-id="4ca45-125">Ring buffer</span></span>](../../2014/database-engine/ring-buffer-target.md)  
  
     <span data-ttu-id="4ca45-126">用于在先进先出 (FIFO) 的基础上或按事件 FIFO 的基础上将事件数据保存在内存中。</span><span class="sxs-lookup"><span data-stu-id="4ca45-126">Use to hold the event data in memory on a first-in first-out (FIFO) basis, or on a per-event FIFO basis.</span></span> <span data-ttu-id="4ca45-127">此目标是异步目标。</span><span class="sxs-lookup"><span data-stu-id="4ca45-127">This is an asynchronous target.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ca45-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4ca45-128">See Also</span></span>  
 <span data-ttu-id="4ca45-129">[扩展事件](../relational-databases/extended-events/extended-events.md) </span><span class="sxs-lookup"><span data-stu-id="4ca45-129">[Extended Events](../relational-databases/extended-events/extended-events.md) </span></span>  
 <span data-ttu-id="4ca45-130">[SQL Server 扩展事件包](../relational-databases/extended-events/sql-server-extended-events-packages.md) </span><span class="sxs-lookup"><span data-stu-id="4ca45-130">[SQL Server Extended Events Packages](../relational-databases/extended-events/sql-server-extended-events-packages.md) </span></span>  
 <span data-ttu-id="4ca45-131">[SQL Server 扩展事件会话](../relational-databases/extended-events/sql-server-extended-events-sessions.md) </span><span class="sxs-lookup"><span data-stu-id="4ca45-131">[SQL Server Extended Events Sessions](../relational-databases/extended-events/sql-server-extended-events-sessions.md) </span></span>  
 [<span data-ttu-id="4ca45-132">SQL Server 扩展事件引擎</span><span class="sxs-lookup"><span data-stu-id="4ca45-132">SQL Server Extended Events Engine</span></span>](../relational-databases/extended-events/sql-server-extended-events-engine.md)  
  
  
