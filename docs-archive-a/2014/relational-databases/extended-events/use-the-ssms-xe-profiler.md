---
title: 使用 system_health 会话 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xevents
ms.topic: conceptual
helpviewer_keywords:
- extended events [SQL Server], system health session
- extended events [SQL Server], system_health session
- system_health session [SQL Server extended events]
- system health session [SQL Server extended events]
ms.assetid: 1e1fad43-d747-4775-ac0d-c50648e56d78
author: yualan
ms.author: alayu
ms.openlocfilehash: 86c3221fb4c0ea0690b369888ac8f2f9f82d6ef9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577646"
---
# <a name="use-the-system_health-session"></a><span data-ttu-id="c849d-102">使用 system_health 会话</span><span class="sxs-lookup"><span data-stu-id="c849d-102">Use the system_health Session</span></span>
  <span data-ttu-id="c849d-103">system_health 会话是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]默认包含的扩展事件会话。</span><span class="sxs-lookup"><span data-stu-id="c849d-103">The system_health session is an Extended Events session that is included by default with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c849d-104">该会话在 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 启动时自动启动，并且运行时不会对性能造成任何明显影响。</span><span class="sxs-lookup"><span data-stu-id="c849d-104">This session starts automatically when the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] starts, and runs without any noticeable performance effects.</span></span> <span data-ttu-id="c849d-105">该会话收集的系统数据可用于帮助对 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的性能问题进行故障排除。</span><span class="sxs-lookup"><span data-stu-id="c849d-105">The session collects system data that you can use to help troubleshoot performance issues in the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="c849d-106">因此，我们建议您不要停止或删除该会话。</span><span class="sxs-lookup"><span data-stu-id="c849d-106">Therefore, we recommend that you do not stop or delete the session.</span></span>  
  
 <span data-ttu-id="c849d-107">该会话收集的信息包括：</span><span class="sxs-lookup"><span data-stu-id="c849d-107">The session collects information that includes the following:</span></span>  
  
-   <span data-ttu-id="c849d-108">发生严重性 >=20 的错误的任何会话的 sql_text 和 session_id 。</span><span class="sxs-lookup"><span data-stu-id="c849d-108">The sql_text and session_id for any sessions that encounter an error that has a severity >=20.</span></span>  
  
-   <span data-ttu-id="c849d-109">发生内存相关错误的任何会话的 sql_text 和 session_id 。</span><span class="sxs-lookup"><span data-stu-id="c849d-109">The sql_text and session_id for any sessions that encounter a memory-related error.</span></span> <span data-ttu-id="c849d-110">这些错误包括 17803、701、802、8645、8651、8657 和 8902。</span><span class="sxs-lookup"><span data-stu-id="c849d-110">The errors include 17803, 701, 802, 8645, 8651, 8657 and 8902.</span></span>  
  
-   <span data-ttu-id="c849d-111">任何无法完成的计划程序问题的记录。</span><span class="sxs-lookup"><span data-stu-id="c849d-111">A record of any non-yielding scheduler problems.</span></span> <span data-ttu-id="c849d-112">（这些问题在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误日志中显示为错误 17883。）</span><span class="sxs-lookup"><span data-stu-id="c849d-112">(These appear in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log as error 17883.)</span></span>  
  
-   <span data-ttu-id="c849d-113">检测到的任何死锁。</span><span class="sxs-lookup"><span data-stu-id="c849d-113">Any deadlocks that are detected.</span></span>  
  
-   <span data-ttu-id="c849d-114">等待闩锁（或其他相关资源）时间 > 15 秒的任何会话的 callstack、sql_text 和 session_id。</span><span class="sxs-lookup"><span data-stu-id="c849d-114">The callstack, sql_text, and session_id for any sessions that have waited on latches (or other interesting resources) for > 15 seconds.</span></span>  
  
-   <span data-ttu-id="c849d-115">等待锁（或其他相关资源）时间 > 30 秒的任何会话的 callstack、sql_text 和 session_id。</span><span class="sxs-lookup"><span data-stu-id="c849d-115">The callstack, sql_text, and session_id for any sessions that have waited on locks for > 30 seconds.</span></span>  
  
-   <span data-ttu-id="c849d-116">为获得“抢先等待”（或其他相关资源）而等待时间很长的任何会话的 callstack、sql_text 和 session_id。</span><span class="sxs-lookup"><span data-stu-id="c849d-116">The callstack, sql_text, and session_id for any sessions that have waited for a long time for preemptive waits.</span></span> <span data-ttu-id="c849d-117">持续时间因等待类型而异。</span><span class="sxs-lookup"><span data-stu-id="c849d-117">The duration varies by wait type.</span></span> <span data-ttu-id="c849d-118">在抢先等待中， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 等待的是外部 API 调用。</span><span class="sxs-lookup"><span data-stu-id="c849d-118">A preemptive wait is where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is waiting for external API calls.</span></span>  
  
-   <span data-ttu-id="c849d-119">CLR 分配失败和虚拟分配失败的调用堆栈和 session_id。</span><span class="sxs-lookup"><span data-stu-id="c849d-119">The callstack and session_id for CLR allocation and virtual allocation failures.</span></span>  
  
-   <span data-ttu-id="c849d-120">有关内存 Broker、计划程序监视、内存节点 OOM、安全性和连接的 ring_buffer 事件。</span><span class="sxs-lookup"><span data-stu-id="c849d-120">The ring_buffer events for the memory broker, scheduler monitor, memory node OOM, security, and connectivity.</span></span>  
  
-   <span data-ttu-id="c849d-121">sp_server_diagnostics 中的系统组件结果。</span><span class="sxs-lookup"><span data-stu-id="c849d-121">System component results from sp_server_diagnostics.</span></span>  
  
-   <span data-ttu-id="c849d-122">scheduler_monitor_system_health_ring_buffer_recorded 收集的实例运行状况。</span><span class="sxs-lookup"><span data-stu-id="c849d-122">Instance health collected by scheduler_monitor_system_health_ring_buffer_recorded.</span></span>  
  
-   <span data-ttu-id="c849d-123">CLR 分配失败。</span><span class="sxs-lookup"><span data-stu-id="c849d-123">CLR Allocation failures.</span></span>  
  
-   <span data-ttu-id="c849d-124">使用 connectivity_ring_buffer_recorded 时的连接错误。</span><span class="sxs-lookup"><span data-stu-id="c849d-124">Connectivity errors using connectivity_ring_buffer_recorded.</span></span>  
  
-   <span data-ttu-id="c849d-125">使用 security_error_ring_buffer_recorded 时的安全错误。</span><span class="sxs-lookup"><span data-stu-id="c849d-125">Security errors using security_error_ring_buffer_recorded.</span></span>  
  
## <a name="viewing-the-session-data"></a><span data-ttu-id="c849d-126">查看会话数据</span><span class="sxs-lookup"><span data-stu-id="c849d-126">Viewing the Session Data</span></span>  
 <span data-ttu-id="c849d-127">会话使用环形缓冲区目标存储数据。</span><span class="sxs-lookup"><span data-stu-id="c849d-127">The session uses the ring buffer target to store the data.</span></span> <span data-ttu-id="c849d-128">若要查看会话数据，请使用下面的查询：</span><span class="sxs-lookup"><span data-stu-id="c849d-128">To view the session data, use the following query:</span></span>  
  
```  
SELECT CAST(xet.target_data as xml) FROM sys.dm_xe_session_targets xet  
JOIN sys.dm_xe_sessions xe  
ON (xe.address = xet.event_session_address)  
WHERE xe.name = 'system_health'  
```  
  
 <span data-ttu-id="c849d-129">若要查看事件文件中的会话数据，请使用 Management Studio 中提供的扩展事件用户界面。</span><span class="sxs-lookup"><span data-stu-id="c849d-129">To view the session data from the event file, use the Extended Events user interface available in Management Studio.</span></span> <span data-ttu-id="c849d-130">有关详细信息，请参阅 [View Event Session Data](../../database-engine/view-event-session-data.md) 。</span><span class="sxs-lookup"><span data-stu-id="c849d-130">See [View Event Session Data](../../database-engine/view-event-session-data.md) for more information.</span></span>  
  
## <a name="restoring-the-system_health-session"></a><span data-ttu-id="c849d-131">还原 system_health 会话</span><span class="sxs-lookup"><span data-stu-id="c849d-131">Restoring the system_health Session</span></span>  
 <span data-ttu-id="c849d-132">如果删除 system_health 会话，则可以通过在查询编辑器中执行 **u_tables.sql** 文件来还原该会话。</span><span class="sxs-lookup"><span data-stu-id="c849d-132">If you delete the system_health session, you can restore it by executing the **u_tables.sql** file in Query Editor.</span></span> <span data-ttu-id="c849d-133">该文件位于下面的文件夹中，其中 C: 表示您安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 程序文件的驱动器：</span><span class="sxs-lookup"><span data-stu-id="c849d-133">This file is located in the following folder, where C: represents the drive where you installed the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] program files:</span></span>  
  
 <span data-ttu-id="c849d-134">C:\Program Files\Microsoft SQL Server\MSSQL12. \<*instanceid*>\MSSQL\Install</span><span class="sxs-lookup"><span data-stu-id="c849d-134">C:\Program Files\Microsoft SQL Server\MSSQL12.\<*instanceid*>\MSSQL\Install</span></span>  
  
 <span data-ttu-id="c849d-135">请注意，在还原该会话后，必须使用 ALTER EVENT SESSION 语句或使用对象资源管理器中的 **“扩展事件”** 节点启动会话。</span><span class="sxs-lookup"><span data-stu-id="c849d-135">Be aware that after you restore the session, you must start the session by using the ALTER EVENT SESSION statement or by using the **Extended Events** node in Object Explorer.</span></span> <span data-ttu-id="c849d-136">否则，该会话会在您下次重新启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务时自动启动。</span><span class="sxs-lookup"><span data-stu-id="c849d-136">Otherwise, the session starts automatically the next time that you restart the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c849d-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c849d-137">See Also</span></span>  
 [<span data-ttu-id="c849d-138">扩展事件工具</span><span class="sxs-lookup"><span data-stu-id="c849d-138">Extended Events Tools</span></span>](extended-events-tools.md)  
  
  
