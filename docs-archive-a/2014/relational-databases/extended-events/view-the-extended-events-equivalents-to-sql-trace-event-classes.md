---
title: 查看与 SQL 跟踪事件类等效的扩展事件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xevents
ms.topic: conceptual
helpviewer_keywords:
- SQL Trace, extended events equivalents
- extended events [SQL Server], SQL Trace equivalents
- extended events [SQL Server], user configurable events
ms.assetid: 7f24104c-201d-4361-9759-f78a27936011
author: rothja
ms.author: jroth
ms.openlocfilehash: 37459359f9f6cb7e3951b705c4007477ec43e36a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682831"
---
# <a name="view-the-extended-events-equivalents-to-sql-trace-event-classes"></a><span data-ttu-id="65611-102">查看与 SQL 跟踪事件类等效的扩展事件</span><span class="sxs-lookup"><span data-stu-id="65611-102">View the Extended Events Equivalents to SQL Trace Event Classes</span></span>
  <span data-ttu-id="65611-103">如果您想要使用扩展事件来收集与 SQL 跟踪事件类和列等效的事件数据，则理解 SQL 跟踪事件映射到扩展事件的事件和操作的方式将很有用。</span><span class="sxs-lookup"><span data-stu-id="65611-103">If you want to use Extended Events to collect event data that is equivalent to SQL Trace event classes and columns, it is useful to understand how the SQL Trace events map to Extended Events events and actions.</span></span>  
  
 <span data-ttu-id="65611-104">您可以使用以下过程查看与各 SQL 跟踪事件及其关联列等效的扩展事件的事件和操作。</span><span class="sxs-lookup"><span data-stu-id="65611-104">You can use the following procedure to view the Extended Events events and actions that are equivalent to each SQL Trace event and its associated columns.</span></span>  
  
## <a name="to-view-the-extended-events-equivalents-to-sql-trace-events-using-query-editor"></a><span data-ttu-id="65611-105">使用查询编辑器查看与 SQL 跟踪事件等效的扩展事件</span><span class="sxs-lookup"><span data-stu-id="65611-105">To view the Extended Events equivalents to SQL Trace events using Query Editor</span></span>  
  
-   <span data-ttu-id="65611-106">从 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]的查询编辑器中，运行以下查询：</span><span class="sxs-lookup"><span data-stu-id="65611-106">From Query Editor in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], run the following query:</span></span>  
  
    ```  
    USE MASTER;  
    GO  
    SELECT DISTINCT  
       tb.trace_event_id,  
       te.name AS 'Event Class',  
       em.package_name AS 'Package',  
       em.xe_event_name AS 'XEvent Name',  
       tb.trace_column_id,  
       tc.name AS 'SQL Trace Column',  
       am.xe_action_name as 'Extended Events action'  
    FROM (sys.trace_events te LEFT OUTER JOIN sys.trace_xe_event_map em  
       ON te.trace_event_id = em.trace_event_id) LEFT OUTER JOIN sys.trace_event_bindings tb  
       ON em.trace_event_id = tb.trace_event_id LEFT OUTER JOIN sys.trace_columns tc  
       ON tb.trace_column_id = tc.trace_column_id LEFT OUTER JOIN sys.trace_xe_action_map am  
       ON tc.trace_column_id = am.trace_column_id  
    ORDER BY te.name, tc.name  
    ```  
  
 <span data-ttu-id="65611-107">在查看结果时，请注意以下事项：</span><span class="sxs-lookup"><span data-stu-id="65611-107">When you view the results, note the following:</span></span>  
  
-   <span data-ttu-id="65611-108">如果除“事件类”列之外的所有列都返回 NULL，则表示该事件类不是从 SQL 跟踪迁移的。</span><span class="sxs-lookup"><span data-stu-id="65611-108">If all columns return NULL except for the Event Class column, this indicates that the event class was not migrated from SQL Trace.</span></span>  
  
-   <span data-ttu-id="65611-109">如果只有“扩展事件操作”列中的值为 NULL，则表示以下两个条件之一成立：</span><span class="sxs-lookup"><span data-stu-id="65611-109">If only the value in the Extended Events action column is NULL, this indicates that either of the following conditions is true:</span></span>  
  
    -   <span data-ttu-id="65611-110">SQL 跟踪列映射到与扩展事件的事件相关联的数据字段之一。</span><span class="sxs-lookup"><span data-stu-id="65611-110">The SQL Trace column maps to one of the data fields that is associated with the Extended Events event.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="65611-111">每个扩展事件的事件都具有在结果集中自动包括的数据字段的默认集合。</span><span class="sxs-lookup"><span data-stu-id="65611-111">Each Extended Events event has a default set of data fields that are automatically included in the result set.</span></span>  
  
    -   <span data-ttu-id="65611-112">操作列不具有等效的有意义的扩展事件。</span><span class="sxs-lookup"><span data-stu-id="65611-112">The action column does not have a meaningful Extended Events equivalent.</span></span> <span data-ttu-id="65611-113">与此有关的一个示例就是 SQL 跟踪中的“事件类”列。</span><span class="sxs-lookup"><span data-stu-id="65611-113">An example of this is the EventClass column in SQL Trace.</span></span> <span data-ttu-id="65611-114">该列不是扩展事件中所必需的，因为事件名称起到相同作用。</span><span class="sxs-lookup"><span data-stu-id="65611-114">This column is not needed in Extended Events because the event name serves the same purpose.</span></span>  
  
-   <span data-ttu-id="65611-115">对于用户可配置 SQL 跟踪事件类（UserConfigurable:1 到 UserConfigurable:9），扩展事件使用单个事件来代替它们。</span><span class="sxs-lookup"><span data-stu-id="65611-115">For user configurable SQL Trace event classes (UserConfigurable:1 through UserConfigurable:9), Extended Events uses a single event to replace these.</span></span> <span data-ttu-id="65611-116">该事件名为 user_event。</span><span class="sxs-lookup"><span data-stu-id="65611-116">The event is named user_event.</span></span> <span data-ttu-id="65611-117">该事件通过使用 sp_trace_generateevent 引发，与 SQL 跟踪所使用的相同的存储过程。</span><span class="sxs-lookup"><span data-stu-id="65611-117">This event is raised by using sp_trace_generateevent, which is the same stored procedure that is used by SQL Trace.</span></span> <span data-ttu-id="65611-118">无论哪一事件 ID 传递到该存储过程，都会返回 user_event 事件。</span><span class="sxs-lookup"><span data-stu-id="65611-118">The user_event event is returned regardless of which event ID is passed to the stored procedure.</span></span> <span data-ttu-id="65611-119">但是，event_id 字段作为事件数据的一部分返回。</span><span class="sxs-lookup"><span data-stu-id="65611-119">However, an event_id field is returned as part of the event data.</span></span> <span data-ttu-id="65611-120">这使您可以生成基于事件 ID 的谓词。</span><span class="sxs-lookup"><span data-stu-id="65611-120">This enables you to build a predicate that is based on the event ID.</span></span> <span data-ttu-id="65611-121">例如，如果你在代码中使用 UserConfigurable:0（事件 ID = 82），则可以将 user_event 事件添加到会话，并且指定谓词“event_id = 82”。</span><span class="sxs-lookup"><span data-stu-id="65611-121">For example, if you use UserConfigurable:0 (event ID = 82) in the code, you can add the user_event event to the session, and specify a predicate of 'event_id = 82'.</span></span> <span data-ttu-id="65611-122">因此，你不必更改代码，因为 sp_trace_generateevent 存储过程生成扩展事件 user_event 事件以及等效的 SQL 跟踪事件类。</span><span class="sxs-lookup"><span data-stu-id="65611-122">Therefore, you do not have to change the code because the sp_trace_generateevent stored procedure generates the Extended Events user_event event, and the equivalent SQL Trace event class.</span></span>  
  
-   <span data-ttu-id="65611-123">如果除“事件类”列之外的所有列都返回 NULL，则表示该事件类不是从 SQL 跟踪迁移的。</span><span class="sxs-lookup"><span data-stu-id="65611-123">If all columns return NULL except for the Event Class column, this indicates that the event class was not migrated from SQL Trace.</span></span>  
  
-   <span data-ttu-id="65611-124">如果只有“扩展事件操作”列中的值为 NULL，则表示以下两个条件之一成立：</span><span class="sxs-lookup"><span data-stu-id="65611-124">If only the value in the Extended Events action column is NULL, this indicates that either of the following conditions is true:</span></span>  
  
    -   <span data-ttu-id="65611-125">SQL 跟踪列映射到与扩展事件的事件相关联的数据字段之一。</span><span class="sxs-lookup"><span data-stu-id="65611-125">The SQL Trace column maps to one of the data fields that is associated with the Extended Events event.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="65611-126">每个扩展事件的事件都具有在结果集中自动包括的数据字段的默认集合。</span><span class="sxs-lookup"><span data-stu-id="65611-126">Each Extended Events event has a default set of data fields that are automatically included in the result set.</span></span>  
  
    -   <span data-ttu-id="65611-127">操作列不具有等效的有意义的扩展事件。</span><span class="sxs-lookup"><span data-stu-id="65611-127">The action column does not have a meaningful Extended Events equivalent.</span></span> <span data-ttu-id="65611-128">与此有关的一个示例就是 SQL 跟踪中的“事件类”列。</span><span class="sxs-lookup"><span data-stu-id="65611-128">An example of this is the EventClass column in SQL Trace.</span></span> <span data-ttu-id="65611-129">该列不是扩展事件中所必需的，因为事件名称起到相同作用。</span><span class="sxs-lookup"><span data-stu-id="65611-129">This column is not needed in Extended Events because the event name serves the same purpose.</span></span>  
  
-   <span data-ttu-id="65611-130">对于用户可配置 SQL 跟踪事件类（UserConfigurable:1 到 UserConfigurable:9），扩展事件使用单个事件来代替它们。</span><span class="sxs-lookup"><span data-stu-id="65611-130">For user configurable SQL Trace event classes (UserConfigurable:1 through UserConfigurable:9), Extended Events uses a single event to replace these.</span></span> <span data-ttu-id="65611-131">该事件名为 user_event。</span><span class="sxs-lookup"><span data-stu-id="65611-131">The event is named user_event.</span></span> <span data-ttu-id="65611-132">该事件通过使用 sp_trace_generateevent 引发，与 SQL 跟踪所使用的相同的存储过程。</span><span class="sxs-lookup"><span data-stu-id="65611-132">This event is raised by using sp_trace_generateevent, which is the same stored procedure that is used by SQL Trace.</span></span> <span data-ttu-id="65611-133">无论哪一事件 ID 传递到该存储过程，都会返回 user_event 事件。</span><span class="sxs-lookup"><span data-stu-id="65611-133">The user_event event is returned regardless of which event ID is passed to the stored procedure.</span></span> <span data-ttu-id="65611-134">但是，event_id 字段作为事件数据的一部分返回。</span><span class="sxs-lookup"><span data-stu-id="65611-134">However, an event_id field is returned as part of the event data.</span></span> <span data-ttu-id="65611-135">这使您可以生成基于事件 ID 的谓词。</span><span class="sxs-lookup"><span data-stu-id="65611-135">This enables you to build a predicate that is based on the event ID.</span></span> <span data-ttu-id="65611-136">例如，如果你在代码中使用 UserConfigurable:0（事件 ID = 82），则可以将 user_event 事件添加到会话，并且指定谓词“event_id = 82”。</span><span class="sxs-lookup"><span data-stu-id="65611-136">For example, if you use UserConfigurable:0 (event ID = 82) in the code, you can add the user_event event to the session, and specify a predicate of 'event_id = 82'.</span></span> <span data-ttu-id="65611-137">因此，你不必更改代码，因为 sp_trace_generateevent 存储过程生成扩展事件 user_event 事件以及等效的 SQL 跟踪事件类。</span><span class="sxs-lookup"><span data-stu-id="65611-137">Therefore, you do not have to change the code because the sp_trace_generateevent stored procedure generates the Extended Events user_event event, and the equivalent SQL Trace event class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65611-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="65611-138">See Also</span></span>  
 [<span data-ttu-id="65611-139">sp_trace_generateevent (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="65611-139">sp_trace_generateevent &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-generateevent-transact-sql)  
  
  
