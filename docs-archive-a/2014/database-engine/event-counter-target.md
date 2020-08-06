---
title: 事件计数器目标 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- synchronous event counter target [SQL Server extended events]
- targets [SQL Server extended events], synchronous event counter target
ms.assetid: 342e08d1-dcca-4a71-ae64-cb61b55b85bc
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: f540f39176ec638cdc9236b315e306ecebfdcb1b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690049"
---
# <a name="event-counter-target"></a><span data-ttu-id="a68d2-102">事件计数器目标</span><span class="sxs-lookup"><span data-stu-id="a68d2-102">Event Counter Target</span></span>
  <span data-ttu-id="a68d2-103">事件计数器目标将计算在扩展事件会话过程中发生的所有事件数目。</span><span class="sxs-lookup"><span data-stu-id="a68d2-103">The event counter target counts all events that occur during an Extended Events session.</span></span> <span data-ttu-id="a68d2-104">通过使用事件计数器目标，您可以获得有关工作负荷特征的信息，而不必因进行完整的事件收集而增加系统开销。</span><span class="sxs-lookup"><span data-stu-id="a68d2-104">By using the event counter target, you can obtain information about workload characteristics without adding the overhead of full event collection.</span></span> <span data-ttu-id="a68d2-105">此目标不包含任何可自定义的参数。</span><span class="sxs-lookup"><span data-stu-id="a68d2-105">This target has no customizable parameters.</span></span>  
  
## <a name="adding-the-target-to-a-session"></a><span data-ttu-id="a68d2-106">将目标添加到会话</span><span class="sxs-lookup"><span data-stu-id="a68d2-106">Adding the Target to a Session</span></span>  
 <span data-ttu-id="a68d2-107">若要将事件计数器目标添加到扩展事件会话，您必须在创建或更改事件会话时包括下面的语句：</span><span class="sxs-lookup"><span data-stu-id="a68d2-107">To add the event counter target to an Extended Events session, you must include the following statement when you create or alter an event session:</span></span>  
  
```  
ADD TARGET package0.event_counter  
```  
  
## <a name="reviewing-the-target-output"></a><span data-ttu-id="a68d2-108">查看目标输出</span><span class="sxs-lookup"><span data-stu-id="a68d2-108">Reviewing the Target Output</span></span>  
 <span data-ttu-id="a68d2-109">若要查看事件计数器目标的输出，你可以使用下面的查询，将 *session_name* 替换为事件会话的名称：</span><span class="sxs-lookup"><span data-stu-id="a68d2-109">To review the output from the event counter target, you can use the following query, replacing *session_name* with the name of the event session:</span></span>  
  
```  
SELECT name, target_name, CAST(xet.target_data AS xml)  
FROM sys.dm_xe_session_targets AS xet  
JOIN sys.dm_xe_sessions AS xe  
   ON (xe.address = xet.event_session_address)  
WHERE xe.name = 'session_name'  
```  
  
 <span data-ttu-id="a68d2-110">下面的示例演示了事件计数器目标输出的格式。</span><span class="sxs-lookup"><span data-stu-id="a68d2-110">The following example shows the event counter target output format.</span></span>  
  
```  
<CounterTarget truncated = "0">  
  <Packages>  
    <Package name = "[package name]">  
      <Event name = "[event name]" count = "[number]" />  
    </Package>  
  </Packages>  
</CounterTarget>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a68d2-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a68d2-111">See Also</span></span>  
 <span data-ttu-id="a68d2-112">[SQL Server 扩展事件目标](../../2014/database-engine/sql-server-extended-events-targets.md) </span><span class="sxs-lookup"><span data-stu-id="a68d2-112">[SQL Server Extended Events Targets](../../2014/database-engine/sql-server-extended-events-targets.md) </span></span>  
 <span data-ttu-id="a68d2-113">[sys.dm_xe_session_targets (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-targets-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a68d2-113">[sys.dm_xe_session_targets &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-targets-transact-sql) </span></span>  
 <span data-ttu-id="a68d2-114">[CREATE EVENT SESSION (Transact-SQL)](/sql/t-sql/statements/create-event-session-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a68d2-114">[CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql) </span></span>  
 [<span data-ttu-id="a68d2-115">ALTER EVENT SESSION (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="a68d2-115">ALTER EVENT SESSION &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-event-session-transact-sql)  
  
  
