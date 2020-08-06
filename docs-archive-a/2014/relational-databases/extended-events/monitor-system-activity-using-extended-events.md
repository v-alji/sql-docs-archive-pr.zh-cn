---
title: 使用扩展事件监视系统活动 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xevents
ms.topic: conceptual
helpviewer_keywords:
- xe
- extended events [SQL Server], monitoring system activity
ms.assetid: d83ad88f-818c-49fe-a9a9-299f704fca53
author: rothja
ms.author: jroth
ms.openlocfilehash: d847d156d8244ede533e684c9e6b753d7d7b5047
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577658"
---
# <a name="monitor-system-activity-using-extended-events"></a><span data-ttu-id="bb2eb-102">使用扩展事件监视系统活动</span><span class="sxs-lookup"><span data-stu-id="bb2eb-102">Monitor System Activity Using Extended Events</span></span>
  <span data-ttu-id="bb2eb-103">此过程说明如何将扩展事件和 Windows 事件跟踪 (ETW) 配合使用来监视系统活动。</span><span class="sxs-lookup"><span data-stu-id="bb2eb-103">This procedure illustrates how Extended Events can be used with Event Tracing for Windows (ETW) to monitor system activity.</span></span> <span data-ttu-id="bb2eb-104">此过程还说明如何使用 CREATE EVENT SESSION、ALTER EVENT SESSION 和 DROP EVENT SESSION 语句。</span><span class="sxs-lookup"><span data-stu-id="bb2eb-104">The procedure also shows how the CREATE EVENT SESSION, ALTER EVENT SESSION, and DROP EVENT SESSION statements are used.</span></span>  
  
 <span data-ttu-id="bb2eb-105">若要完成这些任务，需使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中的查询编辑器执行以下过程。</span><span class="sxs-lookup"><span data-stu-id="bb2eb-105">Accomplishing these tasks involves using Query Editor in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to carry out the following procedure.</span></span> <span data-ttu-id="bb2eb-106">此过程还要求使用命令提示符运行 ETW 命令。</span><span class="sxs-lookup"><span data-stu-id="bb2eb-106">The procedure also requires using the command prompt to run ETW commands.</span></span>  
  
### <a name="to-monitor-system-activity-using-extended-events"></a><span data-ttu-id="bb2eb-107">使用扩展事件监视系统活动</span><span class="sxs-lookup"><span data-stu-id="bb2eb-107">To monitor system activity using Extended Events</span></span>  
  
1.  <span data-ttu-id="bb2eb-108">在查询编辑器中，发出下列语句创建事件会话并添加两个事件。</span><span class="sxs-lookup"><span data-stu-id="bb2eb-108">In Query Editor, issue the following statements to create an event session and add two events.</span></span> <span data-ttu-id="bb2eb-109">checkpoint_begin 和 checkpoint_end 事件在数据库检查点开始和结束时激发。</span><span class="sxs-lookup"><span data-stu-id="bb2eb-109">These events, checkpoint_begin and checkpoint_end, fire at the beginning and end of a database checkpoint.</span></span>  
  
    ```  
    CREATE EVENT SESSION test0  
    ON SERVER  
    ADD EVENT sqlserver.checkpoint_begin,  
    ADD EVENT sqlserver.checkpoint_end  
    WITH (MAX_DISPATCH_LATENCY = 1 SECONDS)  
    go  
    ```  
  
2.  <span data-ttu-id="bb2eb-110">添加具有 32 个存储桶的存储桶存储目标，以根据数据库 ID 对检查点数目进行计数。</span><span class="sxs-lookup"><span data-stu-id="bb2eb-110">Add the bucketing target with 32 buckets to count the number of checkpoints based on the database ID.</span></span>  
  
    ```  
    ALTER EVENT SESSION test0  
    ON SERVER  
    ADD TARGET package0.histogram  
    (  
          SET slots = 32, filtering_event_name = 'sqlserver.checkpoint_end', source_type = 0, source = 'database_id'  
    )  
    go  
    ```  
  
3.  <span data-ttu-id="bb2eb-111">发出下列语句添加 ETW 目标。</span><span class="sxs-lookup"><span data-stu-id="bb2eb-111">Issue the following statements to add the ETW target.</span></span> <span data-ttu-id="bb2eb-112">这样便能查看开始和结束事件，这些事件用于确定检查点的长度。</span><span class="sxs-lookup"><span data-stu-id="bb2eb-112">This will enable you to see the begin and end events, which is used to determine how long the checkpoint takes.</span></span>  
  
    ```  
    ALTER EVENT SESSION test0  
    ON SERVER  
    ADD TARGET package0.etw_classic_sync_target  
    go  
    ```  
  
4.  <span data-ttu-id="bb2eb-113">发出下列语句启动会话并开始事件收集。</span><span class="sxs-lookup"><span data-stu-id="bb2eb-113">Issue the following statements to start the session and begin event collection.</span></span>  
  
    ```  
    ALTER EVENT SESSION test0  
    ON SERVER  
    STATE = start  
    go  
    ```  
  
5.  <span data-ttu-id="bb2eb-114">发出下列语句激发三个事件。</span><span class="sxs-lookup"><span data-stu-id="bb2eb-114">Issue the following statements to cause three events to fire.</span></span>  
  
    ```  
    USE tempdb  
          checkpoint  
    go  
    USE master  
          checkpoint  
          checkpoint  
    go  
    ```  
  
6.  <span data-ttu-id="bb2eb-115">发出下列语句查看事件计数。</span><span class="sxs-lookup"><span data-stu-id="bb2eb-115">Issue the following statements to view the event counts.</span></span>  
  
    ```  
    SELECT CAST(xest.target_data AS xml) Bucketizer_Target_Data_in_XML  
    FROM sys.dm_xe_session_targets xest  
    JOIN sys.dm_xe_sessions xes ON xes.address = xest.event_session_address  
    JOIN sys.server_event_sessions ses ON xes.name = ses.name  
    WHERE xest.target_name = 'histogram' AND xes.name = 'test0'  
    go  
    ```  
  
7.  <span data-ttu-id="bb2eb-116">在命令提示符下，发出下列命令查看 ETW 数据。</span><span class="sxs-lookup"><span data-stu-id="bb2eb-116">At the command prompt, issue the following commands to view the ETW data.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="bb2eb-117"> 若要获得 **tracerpt** 命令的帮助，请在命令提示符下输入 `tracerpt /?`。</span><span class="sxs-lookup"><span data-stu-id="bb2eb-117">To get help for the **tracerpt** command, at the command prompt, enter `tracerpt /?`.</span></span>  
  
    ```  
    logman query -ets --- List the ETW sessions. This is optional.  
    logman update XE_DEFAULT_ETW_SESSION -fd -ets --- Flush the ETW log.  
    tracerpt %temp%\xeetw.etl -o xeetw.txt --- Dump the events so they can be seen.  
    ```  
  
8.  <span data-ttu-id="bb2eb-118">发出下列语句停止事件会话并将其从服务器上删除。</span><span class="sxs-lookup"><span data-stu-id="bb2eb-118">Issue the following statements to stop the event session and remove it from the server.</span></span>  
  
    ```  
    ALTER EVENT SESSION test0  
    ON SERVER  
    STATE = STOP  
    go  
  
    DROP EVENT SESSION test0  
    ON SERVER  
    go  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="bb2eb-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bb2eb-119">See Also</span></span>  
 <span data-ttu-id="bb2eb-120">[CREATE EVENT SESSION (Transact-SQL)](/sql/t-sql/statements/create-event-session-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="bb2eb-120">[CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql) </span></span>  
 <span data-ttu-id="bb2eb-121">[ALTER EVENT SESSION &#40;Transact-sql&#41;](/sql/t-sql/statements/alter-event-session-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="bb2eb-121">[ALTER EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-event-session-transact-sql) </span></span>  
 <span data-ttu-id="bb2eb-122">[DROP EVENT SESSION (Transact-SQL)](/sql/t-sql/statements/drop-event-session-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="bb2eb-122">[DROP EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-event-session-transact-sql) </span></span>  
 [<span data-ttu-id="bb2eb-123">扩展事件目录视图 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="bb2eb-123">Extended Events Catalog Views &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/extended-events-catalog-views-transact-sql)  
 <span data-ttu-id="bb2eb-124">[扩展事件动态管理视图](../views/views.md) </span><span class="sxs-lookup"><span data-stu-id="bb2eb-124">[Extended Events Dynamic Management Views](../views/views.md) </span></span>  
 [<span data-ttu-id="bb2eb-125">SQL Server 扩展事件目标</span><span class="sxs-lookup"><span data-stu-id="bb2eb-125">SQL Server Extended Events Targets</span></span>](../../database-engine/sql-server-extended-events-targets.md)  
  
  
