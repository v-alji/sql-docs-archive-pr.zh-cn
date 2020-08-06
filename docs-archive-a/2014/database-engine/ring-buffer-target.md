---
title: 环形缓冲区目标 |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- targets [SQL Server extended events], ring buffer target
- ring buffer target [SQL Server extended events]
ms.assetid: 54494e11-b56b-43b7-aa5e-c8724e56b251
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 186e847bb9f9b621543119c25510dc5d6107e274
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589854"
---
# <a name="ring-buffer-target"></a><span data-ttu-id="0f7a6-102">环形缓冲区目标</span><span class="sxs-lookup"><span data-stu-id="0f7a6-102">Ring Buffer Target</span></span>
  <span data-ttu-id="0f7a6-103">环形缓冲区目标用于在内存中暂时容纳事件数据。</span><span class="sxs-lookup"><span data-stu-id="0f7a6-103">The ring buffer target briefly holds event data in memory.</span></span> <span data-ttu-id="0f7a6-104">此目标可通过以下两种模式中的一种来管理事件。</span><span class="sxs-lookup"><span data-stu-id="0f7a6-104">This target can manage events in one of two modes.</span></span>  
  
-   <span data-ttu-id="0f7a6-105">第一种模式是严格的先进先出模式 (FIFO)，在这种模式下，当分配给目标的所有内存都用尽时，将放弃最旧的事件。</span><span class="sxs-lookup"><span data-stu-id="0f7a6-105">The first mode is strict first-in first-out (FIFO), where the oldest event is discarded when all the memory allocated to the target is used.</span></span> <span data-ttu-id="0f7a6-106">在这种模式下（默认模式），occurrence_number 选项设为 0。</span><span class="sxs-lookup"><span data-stu-id="0f7a6-106">In this mode (the default), the occurrence_number option is set to 0.</span></span>  
  
-   <span data-ttu-id="0f7a6-107">第二种模式是按事件 FIFO，在这种模式下，每种类型将保留指定数量的事件。</span><span class="sxs-lookup"><span data-stu-id="0f7a6-107">The second mode is per-event FIFO, where a specified number of events of each type is kept.</span></span> <span data-ttu-id="0f7a6-108">在此模式下，当使用分配给目标的所有内存时，将放弃每种类型的最旧事件。</span><span class="sxs-lookup"><span data-stu-id="0f7a6-108">In this mode, the oldest events of each type are discarded when all the memory allocated to the target is used.</span></span> <span data-ttu-id="0f7a6-109">您可以配置 occurrence_number 选项来指定要保留的每种类型的事件数。</span><span class="sxs-lookup"><span data-stu-id="0f7a6-109">You can configure the occurrence_number option to specify the number of events of each type to keep.</span></span>  
  
 <span data-ttu-id="0f7a6-110">下表描述了配置环形缓冲区目标时可用的选项。</span><span class="sxs-lookup"><span data-stu-id="0f7a6-110">The following table describes the available options for configuring the ring buffer target.</span></span>  
  
|<span data-ttu-id="0f7a6-111">选项</span><span class="sxs-lookup"><span data-stu-id="0f7a6-111">Option</span></span>|<span data-ttu-id="0f7a6-112">允许的值</span><span class="sxs-lookup"><span data-stu-id="0f7a6-112">Allowed values</span></span>|<span data-ttu-id="0f7a6-113">说明</span><span class="sxs-lookup"><span data-stu-id="0f7a6-113">Description</span></span>|  
|------------|--------------------|-----------------|  
|<span data-ttu-id="0f7a6-114">max_memory</span><span class="sxs-lookup"><span data-stu-id="0f7a6-114">max_memory</span></span>|<span data-ttu-id="0f7a6-115">任何32位整数。</span><span class="sxs-lookup"><span data-stu-id="0f7a6-115">Any 32-bit integer.</span></span> <span data-ttu-id="0f7a6-116">此值是可选的。</span><span class="sxs-lookup"><span data-stu-id="0f7a6-116">This value is optional.</span></span>|<span data-ttu-id="0f7a6-117">要使用的最大内存量 (KB)。</span><span class="sxs-lookup"><span data-stu-id="0f7a6-117">The maximum amount of memory in kilobytes (KB) to use.</span></span> <span data-ttu-id="0f7a6-118">将基于首先到达的限制删除现有事件：max_event_limit 或 max_memory。</span><span class="sxs-lookup"><span data-stu-id="0f7a6-118">Existing events are dropped based on the limit that is first reached: max_event_limit or max_memory.</span></span> <span data-ttu-id="0f7a6-119">最大值为 4194303 KB。</span><span class="sxs-lookup"><span data-stu-id="0f7a6-119">The maximum value is 4194303 KB.</span></span> <span data-ttu-id="0f7a6-120">在将环形缓冲区大小设置为 GB 范围限制之前应仔细考虑，因为它可能会影响 SQL Server 中的其他内存使用者</span><span class="sxs-lookup"><span data-stu-id="0f7a6-120">A careful consideration should be made before setting the ring buffer size to limits in the GB range as it may impact other memory consumers in SQL Server</span></span>|  
|<span data-ttu-id="0f7a6-121">max_event_limit</span><span class="sxs-lookup"><span data-stu-id="0f7a6-121">max_event_limit</span></span>|<span data-ttu-id="0f7a6-122">任何32位整数。</span><span class="sxs-lookup"><span data-stu-id="0f7a6-122">Any 32-bit integer.</span></span> <span data-ttu-id="0f7a6-123">此值是可选的。</span><span class="sxs-lookup"><span data-stu-id="0f7a6-123">This value is optional.</span></span>|<span data-ttu-id="0f7a6-124">保留在 ring_buffer 中的事件的最大数量。</span><span class="sxs-lookup"><span data-stu-id="0f7a6-124">The maximum number of events kept in the ring_buffer.</span></span> <span data-ttu-id="0f7a6-125">将基于首先到达的限制删除现有事件：max_event_limit 或 max_memory。</span><span class="sxs-lookup"><span data-stu-id="0f7a6-125">Existing events are dropped based on the limit that is first reached: max_event_limit or max_memory.</span></span> <span data-ttu-id="0f7a6-126">默认值 = 1000。</span><span class="sxs-lookup"><span data-stu-id="0f7a6-126">Default = 1000.</span></span>|  
|<span data-ttu-id="0f7a6-127">occurrence_number</span><span class="sxs-lookup"><span data-stu-id="0f7a6-127">occurrence_number</span></span>|<span data-ttu-id="0f7a6-128">以下值之一：</span><span class="sxs-lookup"><span data-stu-id="0f7a6-128">One of the following values:</span></span><br /><br /> <span data-ttu-id="0f7a6-129">0（默认值）= 当分配给目标的所有内存都用尽时，将放弃最旧的事件。</span><span class="sxs-lookup"><span data-stu-id="0f7a6-129">0 (the default) = Oldest event is discarded when all the memory allocated to the target is used.</span></span><br /><br /> <span data-ttu-id="0f7a6-130">任何32位整数 = 在每次事件 FIFO 上丢弃之前，要保留的每种类型的事件数。</span><span class="sxs-lookup"><span data-stu-id="0f7a6-130">Any 32-bit integer = The number of events of each type to keep before being discarded on a per-event FIFO basis.</span></span><br /><br /> <br /><br /> <span data-ttu-id="0f7a6-131">此值是可选的。</span><span class="sxs-lookup"><span data-stu-id="0f7a6-131">This value is optional.</span></span>|<span data-ttu-id="0f7a6-132">FIFO 模式使用，如果设为大于 0 的值，则为要保留在缓冲区中的每种类型的首选事件数。</span><span class="sxs-lookup"><span data-stu-id="0f7a6-132">The FIFO mode to use, and, if set to a value greater than 0, the preferred number of events of each type to keep in the buffer.</span></span>|
| &nbsp; | &nbsp; | &nbsp; |
  
## <a name="adding-the-target-to-a-session"></a><span data-ttu-id="0f7a6-133">将目标添加到会话</span><span class="sxs-lookup"><span data-stu-id="0f7a6-133">Adding the Target to a Session</span></span>  
 <span data-ttu-id="0f7a6-134">若要将环形缓冲区目标添加到扩展事件会话中，您必须在创建或更改事件会话时包括下面的语句：</span><span class="sxs-lookup"><span data-stu-id="0f7a6-134">To add the ring buffer target to an Extended Events session, you must include the following statement when you create or alter an event session:</span></span>  
  
```sql
ADD TARGET package0.ring_buffer  
```  
  
## <a name="reviewing-the-target-output"></a><span data-ttu-id="0f7a6-135">查看目标输出</span><span class="sxs-lookup"><span data-stu-id="0f7a6-135">Reviewing the Target Output</span></span>  
 <span data-ttu-id="0f7a6-136">若要查看环形缓冲区目标的输出，可以使用下面的查询，并将 *session_name* 替换为事件会话的名称。</span><span class="sxs-lookup"><span data-stu-id="0f7a6-136">To review the output from the ring buffer target, you can use the following query, replacing *session_name* with the name of the event session.</span></span>  
  
```sql
SELECT name, target_name, CAST(xet.target_data AS xml)  
FROM sys.dm_xe_session_targets AS xet  
JOIN sys.dm_xe_sessions AS xe  
   ON (xe.address = xet.event_session_address)  
WHERE xe.name = 'session_name'  
```  
  
 <span data-ttu-id="0f7a6-137">下面的示例演示了环形缓冲区目标的输出格式。</span><span class="sxs-lookup"><span data-stu-id="0f7a6-137">The following example shows the ring buffer target output format.</span></span>  
  
```  
<RingBufferTarget eventsPerSec="" processingTime="" totalEventsProcessed="" eventCount="" droppedCount="" memoryUsed="">  
 <event name="" package="" id="" version="" timestamp="">  
    <data name="">  
      <type name="" package="" />  
      <value></value>  
      <text></text>  
    </data>  
    <action name="" package="">  
      <type name="" package="" />  
      <value></value>  
      <text></text>  
    </action>  
  </event>  
</RingBufferTarget>  
```


## <a name="see-also"></a><span data-ttu-id="0f7a6-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0f7a6-138">See Also</span></span>

- [<span data-ttu-id="0f7a6-139">SQL Server 扩展事件目标</span><span class="sxs-lookup"><span data-stu-id="0f7a6-139">SQL Server Extended Events Targets</span></span>](../../2014/database-engine/sql-server-extended-events-targets.md)
- [<span data-ttu-id="0f7a6-140">sys.dm_xe_session_targets (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="0f7a6-140">sys.dm_xe_session_targets &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-targets-transact-sql?view=sql-server-2016)
- [<span data-ttu-id="0f7a6-141">CREATE EVENT SESSION (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="0f7a6-141">CREATE EVENT SESSION &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-event-session-transact-sql?view=sql-server-2016)
- [<span data-ttu-id="0f7a6-142">ALTER EVENT SESSION (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="0f7a6-142">ALTER EVENT SESSION &#40;Transact-SQL&#41;</span></span>](https://docs.microsoft.com/sql/t-sql/statements/alter-event-session-transact-sql?view=sql-server-2016)

