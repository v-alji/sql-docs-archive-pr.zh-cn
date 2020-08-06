---
title: 事件配对目标 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- pairing target [SQL Server extended events]
- event pairing target
- targets [SQL Server extended events], pairing target
ms.assetid: 3c87dcfb-543a-4bd8-a73d-1390bdf4ffa3
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: a1a6beb1c6996e6e12f16c4555fd9dfcab97617d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690045"
---
# <a name="event-pairing-target"></a><span data-ttu-id="e5c89-102">事件配对目标</span><span class="sxs-lookup"><span data-stu-id="e5c89-102">Event Pairing Target</span></span>
  <span data-ttu-id="e5c89-103">事件配对目标使用两个事件中存在的一列或多列数据来对这两个事件进行匹配。</span><span class="sxs-lookup"><span data-stu-id="e5c89-103">The event pairing target matches two events using one or more columns of data that are present in each event.</span></span> <span data-ttu-id="e5c89-104">许多事件是成对的，例如，锁获取和锁释放。</span><span class="sxs-lookup"><span data-stu-id="e5c89-104">Many events come in pairs, for example, lock acquires and lock releases.</span></span> <span data-ttu-id="e5c89-105">对某个事件序列配对完毕，便会放弃这两个事件。</span><span class="sxs-lookup"><span data-stu-id="e5c89-105">After an event sequence is paired, both events are discarded.</span></span> <span data-ttu-id="e5c89-106">放弃匹配完毕的事件便于检测哪些获取的锁尚未释放。</span><span class="sxs-lookup"><span data-stu-id="e5c89-106">Discarding matched sets allows for easy detection of lock acquisitions that have not been released.</span></span>  
  
 <span data-ttu-id="e5c89-107">通过使用事件级别筛选器，可以使用配对目标仅捕获那些与预设条件不匹配的事件。</span><span class="sxs-lookup"><span data-stu-id="e5c89-107">By using event-level filters, the pairing target can be used to only capture events that do not match pre-set criteria.</span></span>  
  
 <span data-ttu-id="e5c89-108">使用事件配对目标时，可以选择两个要匹配的事件和一个序列，此序列由要对其进行匹配的列构成。</span><span class="sxs-lookup"><span data-stu-id="e5c89-108">When you use the event pairing target, you can choose two events that will be matched, together with a sequence of columns to perform the matching on.</span></span> <span data-ttu-id="e5c89-109">此序列中的所有列必须属于同一类型。</span><span class="sxs-lookup"><span data-stu-id="e5c89-109">All the columns in this sequence must be of the same type.</span></span>  
  
 <span data-ttu-id="e5c89-110">下表描述了配置事件配对时可用的选项。</span><span class="sxs-lookup"><span data-stu-id="e5c89-110">The following table describes the available options for configuring event pairing.</span></span>  
  
|<span data-ttu-id="e5c89-111">选项</span><span class="sxs-lookup"><span data-stu-id="e5c89-111">Option</span></span>|<span data-ttu-id="e5c89-112">允许的值</span><span class="sxs-lookup"><span data-stu-id="e5c89-112">Allowed values</span></span>|<span data-ttu-id="e5c89-113">说明</span><span class="sxs-lookup"><span data-stu-id="e5c89-113">Description</span></span>|  
|------------|--------------------|-----------------|  
|<span data-ttu-id="e5c89-114">begin_event</span><span class="sxs-lookup"><span data-stu-id="e5c89-114">begin_event</span></span>|<span data-ttu-id="e5c89-115">当前会话中存在的任何一个事件的名称。</span><span class="sxs-lookup"><span data-stu-id="e5c89-115">Any event name that is present in the current session.</span></span>|<span data-ttu-id="e5c89-116">用于指定成对序列中开始事件的事件名称。</span><span class="sxs-lookup"><span data-stu-id="e5c89-116">The event name specifying the beginning event in a paired sequence.</span></span>|  
|<span data-ttu-id="e5c89-117">end_event</span><span class="sxs-lookup"><span data-stu-id="e5c89-117">end_event</span></span>|<span data-ttu-id="e5c89-118">当前会话中存在的任何一个事件的名称。</span><span class="sxs-lookup"><span data-stu-id="e5c89-118">Any event name that is present in the current session.</span></span>|<span data-ttu-id="e5c89-119">用于指定成对序列中结束事件的事件名称。</span><span class="sxs-lookup"><span data-stu-id="e5c89-119">The event name specifying the ending event in a paired sequence.</span></span>|  
|<span data-ttu-id="e5c89-120">begin_matching_columns</span><span class="sxs-lookup"><span data-stu-id="e5c89-120">begin_matching_columns</span></span>|<span data-ttu-id="e5c89-121">一个以逗号分隔的列名称排序列表。</span><span class="sxs-lookup"><span data-stu-id="e5c89-121">A comma-delimited, ordered list of column names.</span></span>|<span data-ttu-id="e5c89-122">要对其执行匹配的列。</span><span class="sxs-lookup"><span data-stu-id="e5c89-122">The columns to perform matching on.</span></span>|  
|<span data-ttu-id="e5c89-123">end_matching_columns</span><span class="sxs-lookup"><span data-stu-id="e5c89-123">end_matching_columns</span></span>|<span data-ttu-id="e5c89-124">一个以逗号分隔的列名称排序列表。</span><span class="sxs-lookup"><span data-stu-id="e5c89-124">A comma-delimited, ordered list of column names.</span></span>|<span data-ttu-id="e5c89-125">要对其执行匹配的列。</span><span class="sxs-lookup"><span data-stu-id="e5c89-125">The columns to perform matching on.</span></span>|  
|<span data-ttu-id="e5c89-126">begin_matching_actions</span><span class="sxs-lookup"><span data-stu-id="e5c89-126">begin_matching_actions</span></span>|<span data-ttu-id="e5c89-127">一个以逗号分隔的操作排序列表。</span><span class="sxs-lookup"><span data-stu-id="e5c89-127">A comma-delimited, ordered list of actions.</span></span>|<span data-ttu-id="e5c89-128">要对其执行匹配的操作。</span><span class="sxs-lookup"><span data-stu-id="e5c89-128">The actions to perform matching on.</span></span>|  
|<span data-ttu-id="e5c89-129">end_matching_actions</span><span class="sxs-lookup"><span data-stu-id="e5c89-129">end_matching_actions</span></span>|<span data-ttu-id="e5c89-130">一个以逗号分隔的操作排序列表。</span><span class="sxs-lookup"><span data-stu-id="e5c89-130">A comma-delimited, ordered list of actions.</span></span>|<span data-ttu-id="e5c89-131">要对其执行匹配的操作。</span><span class="sxs-lookup"><span data-stu-id="e5c89-131">The actions to perform matching on.</span></span>|  
|<span data-ttu-id="e5c89-132">respond_to_memory_pressure</span><span class="sxs-lookup"><span data-stu-id="e5c89-132">respond_to_memory_pressure</span></span>|<span data-ttu-id="e5c89-133">以下值之一：</span><span class="sxs-lookup"><span data-stu-id="e5c89-133">One of the following values:</span></span><br /><br /> <span data-ttu-id="e5c89-134">0 = 不响应。</span><span class="sxs-lookup"><span data-stu-id="e5c89-134">0 = Do not respond.</span></span><br /><br /> <span data-ttu-id="e5c89-135">1 = 内存不足时停止向列表添加新的孤立项。</span><span class="sxs-lookup"><span data-stu-id="e5c89-135">1 = Stop adding new orphans to the list when there is memory pressure.</span></span>|<span data-ttu-id="e5c89-136">目标对内存事件予以响应。</span><span class="sxs-lookup"><span data-stu-id="e5c89-136">The target response to memory events.</span></span> <span data-ttu-id="e5c89-137">如果设为 1，则服务器内存不足时，将删除保留的不成对信息。</span><span class="sxs-lookup"><span data-stu-id="e5c89-137">If set to 1 and the server is low on memory, unpaired information that is being maintained is removed.</span></span>|  
|<span data-ttu-id="e5c89-138">max_orphans</span><span class="sxs-lookup"><span data-stu-id="e5c89-138">max_orphans</span></span>||<span data-ttu-id="e5c89-139">指定将在目标中收集的不成对事件的总数。</span><span class="sxs-lookup"><span data-stu-id="e5c89-139">Specifies the total number of unpaired events that will be collected in the target.</span></span> <span data-ttu-id="e5c89-140">一旦达到此限制，将在先入先出 (FIFO) 的基础上删除不成对事件。</span><span class="sxs-lookup"><span data-stu-id="e5c89-140">Once the limit is reached, unpaired events are removed on a first-in, first-out (FIFO) basis.</span></span> <span data-ttu-id="e5c89-141">默认值 = 10,000。</span><span class="sxs-lookup"><span data-stu-id="e5c89-141">Default = 10,000.</span></span>|  
  
 <span data-ttu-id="e5c89-142">系统将捕获并存储与某个事件相关联的所有数据，以供将来配对之用。</span><span class="sxs-lookup"><span data-stu-id="e5c89-142">All the data associated with an event is captured and stored for future pairing.</span></span> <span data-ttu-id="e5c89-143">此外，还将收集由操作添加的数据。</span><span class="sxs-lookup"><span data-stu-id="e5c89-143">In addition, data added by actions is also collected.</span></span> <span data-ttu-id="e5c89-144">收集的事件数据存储在内存中，因此会有一定的限制。</span><span class="sxs-lookup"><span data-stu-id="e5c89-144">The collected event data is stored in memory, and therefore has a finite limit.</span></span> <span data-ttu-id="e5c89-145">此限制基于系统容量和活动。</span><span class="sxs-lookup"><span data-stu-id="e5c89-145">This limit is based on system capacity and activity.</span></span> <span data-ttu-id="e5c89-146">所用内存量将根据可用系统资源来决定，而不是以最大内存量作为限定因素。</span><span class="sxs-lookup"><span data-stu-id="e5c89-146">Instead of taking the maximum amount of memory to be used as a parameter, the amount of memory used will be based on available system resources.</span></span> <span data-ttu-id="e5c89-147">内存不足时，将删除已经保留的不成对事件。</span><span class="sxs-lookup"><span data-stu-id="e5c89-147">When these are not available, unpaired events that have been retained will be dropped.</span></span> <span data-ttu-id="e5c89-148">如果某事件尚未成对便被删除，则与之匹配的事件将作为不成对事件出现。</span><span class="sxs-lookup"><span data-stu-id="e5c89-148">If an event has not been paired and is dropped, the matching event will appear as an unpaired event.</span></span>  
  
 <span data-ttu-id="e5c89-149">配对目标会将不成对事件序列化为 XML 格式。</span><span class="sxs-lookup"><span data-stu-id="e5c89-149">The pairing target serializes unpaired events to an XML format.</span></span> <span data-ttu-id="e5c89-150">此格式不遵从任何架构，</span><span class="sxs-lookup"><span data-stu-id="e5c89-150">This format does not conform to any schema.</span></span> <span data-ttu-id="e5c89-151">只包含两种元素类型。</span><span class="sxs-lookup"><span data-stu-id="e5c89-151">The format only contains two element types.</span></span> <span data-ttu-id="e5c89-152">**\<unpaired>** 元素为根，后跟一个。</span><span class="sxs-lookup"><span data-stu-id="e5c89-152">The **\<unpaired>** element is the root, followed by one.</span></span> <span data-ttu-id="e5c89-153">**\<event>** 元素，用于当前正在跟踪的每个不成对事件。</span><span class="sxs-lookup"><span data-stu-id="e5c89-153">**\<event>** element for each unpaired event that is currently being tracked.</span></span> <span data-ttu-id="e5c89-154">**\<event>** 元素包含一个属性，其中包含不成对事件的名称。</span><span class="sxs-lookup"><span data-stu-id="e5c89-154">The **\<event>** element contains one attribute that contains the name of the unpaired event.</span></span>  
  
## <a name="adding-the-target-to-a-session"></a><span data-ttu-id="e5c89-155">将目标添加到会话</span><span class="sxs-lookup"><span data-stu-id="e5c89-155">Adding the Target to a Session</span></span>  
 <span data-ttu-id="e5c89-156">若要将配对目标添加到扩展事件会话，您必须在创建或更改事件会话时包括下面的语句：</span><span class="sxs-lookup"><span data-stu-id="e5c89-156">To add the pair matching target to an Extended Events session, you must include the following statement when you create or alter an event session:</span></span>  
  
```  
ADD TARGET package0.pair_matching   
```  
  
 <span data-ttu-id="e5c89-157">紧接着可以使用一个 SET 语句，以定义开始和结束事件，以及要匹配的操作或列。</span><span class="sxs-lookup"><span data-stu-id="e5c89-157">You would follow this with a SET statement, to define the beginning and ending events, and which actions or columns to match.</span></span> <span data-ttu-id="e5c89-158">下面的示例演示对匹配的 sqlserver.lock_acquired 和 sqlserver.lock_released 事件的示例语法。</span><span class="sxs-lookup"><span data-stu-id="e5c89-158">The following example shows sample syntax for pair matching the sqlserver.lock_acquired and sqlserver.lock_released events.</span></span>  
  
```  
   ( SET begin_event = 'sqlserver.lock_acquired',  
      begin_matching_columns = 'database_id, resource_0, resource_1, resource_2, transaction_id, mode',  
      end_event = 'sqlserver.lock_released',  
      end_matching_columns = 'database_id, resource_0, resource_1, resource_2, transaction_id, mode',  
   respond_to_memory_pressure = 1)  
```  
  
 <span data-ttu-id="e5c89-159">有关详细信息，请参阅 [确定持有锁的查询](../relational-databases/extended-events/determine-which-queries-are-holding-locks.md)。</span><span class="sxs-lookup"><span data-stu-id="e5c89-159">For more information, see [Determine Which Queries Are Holding Locks](../relational-databases/extended-events/determine-which-queries-are-holding-locks.md).</span></span>  
  
## <a name="reviewing-the-target-output"></a><span data-ttu-id="e5c89-160">查看目标输出</span><span class="sxs-lookup"><span data-stu-id="e5c89-160">Reviewing the Target Output</span></span>  
 <span data-ttu-id="e5c89-161">若要查看成对匹配目标的输出，你可以使用下面的查询，将 *session_name* 替换为事件会话的名称。</span><span class="sxs-lookup"><span data-stu-id="e5c89-161">To review the output for the pair matching target, you can use the following query, replacing *session_name* with the name of the event session.</span></span>  
  
```  
SELECT name, target_name, CAST(xet.target_data AS xml)  
FROM sys.dm_xe_session_targets AS xet  
JOIN sys.dm_xe_sessions AS xe  
   ON (xe.address = xet.event_session_address)  
WHERE xe.name = 'session_name'  
```  
  
 <span data-ttu-id="e5c89-162">下面的示例演示了配对目标输出格式。</span><span class="sxs-lookup"><span data-stu-id="e5c89-162">The following example shows the pairing target output format.</span></span>  
  
```  
<unpaired truncated = "0" matchedCount = "[matched count]" memoryPressureDroppedCount = " [lost count]">  
    <event name  = "[event name]" package = "[package]" id= "[event ID value]" version = "[event version]">  
    <data name = "[column name]">   
    <type name = "[column type]" package = "[type package]" />   
    <value>[column value]</value>  
    <text value>[text value]</text>>  
        </data>  
    </event>  
</unpaired>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e5c89-163">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e5c89-163">See Also</span></span>  
 <span data-ttu-id="e5c89-164">[SQL Server 扩展事件目标](../../2014/database-engine/sql-server-extended-events-targets.md) </span><span class="sxs-lookup"><span data-stu-id="e5c89-164">[SQL Server Extended Events Targets](../../2014/database-engine/sql-server-extended-events-targets.md) </span></span>  
 <span data-ttu-id="e5c89-165">[sys.dm_xe_session_targets (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-targets-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e5c89-165">[sys.dm_xe_session_targets &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-targets-transact-sql) </span></span>  
 <span data-ttu-id="e5c89-166">[CREATE EVENT SESSION (Transact-SQL)](/sql/t-sql/statements/create-event-session-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e5c89-166">[CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql) </span></span>  
 [<span data-ttu-id="e5c89-167">ALTER EVENT SESSION (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="e5c89-167">ALTER EVENT SESSION &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-event-session-transact-sql)  
  
  
