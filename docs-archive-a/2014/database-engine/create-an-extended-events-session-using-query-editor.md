---
title: 使用查询编辑器创建扩展事件会话 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- create extended events session
- extended events [SQL Server], create session
ms.assetid: cba0e02b-b201-4863-bf1b-9164e68e5fa8
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 648370ecdd2938b6fb425955dc02da8960f884c2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586958"
---
# <a name="create-an-extended-events-session-using-query-editor"></a><span data-ttu-id="f7670-102">使用查询编辑器创建扩展事件会话</span><span class="sxs-lookup"><span data-stu-id="f7670-102">Create an Extended Events Session Using Query Editor</span></span>
  <span data-ttu-id="f7670-103">您可以使用查询编辑器创建扩展事件会话，也可以在对象资源管理器中创建会话。</span><span class="sxs-lookup"><span data-stu-id="f7670-103">You can create an Extended Events session by using the Query Editor, or you can create a session in Object Explorer.</span></span> <span data-ttu-id="f7670-104">在对象资源管理器中，扩展事件提供了两个用户界面，你可以使用它们来创建、修改和查看事件会话数据，向导将引导你完成事件会话创建过程，以及提供更高级配置选项的新会话 UI。</span><span class="sxs-lookup"><span data-stu-id="f7670-104">In Object Explorer, Extended Events provides two user interfaces you can use to create, modify, and view event session data - a wizard that guides you through the event session creation process, and a New Session UI that provides more advanced configuration options.</span></span> <span data-ttu-id="f7670-105">您可以创建扩展事件会话来诊断 SQL Server 跟踪，这样您便能解决如下问题：</span><span class="sxs-lookup"><span data-stu-id="f7670-105">You can create Extended Events sessions to diagnose SQL Server tracing, which enables you to resolve issues such as the following:</span></span>  
  
-   <span data-ttu-id="f7670-106">查找最消耗资源的查询</span><span class="sxs-lookup"><span data-stu-id="f7670-106">Find your most expensive queries</span></span>  
  
-   <span data-ttu-id="f7670-107">查找导致闩锁争用的根本原因</span><span class="sxs-lookup"><span data-stu-id="f7670-107">Find root causes of latch contention</span></span>  
  
-   <span data-ttu-id="f7670-108">查找阻止其他查询的查询</span><span class="sxs-lookup"><span data-stu-id="f7670-108">Find a query that is blocking other queries</span></span>  
  
-   <span data-ttu-id="f7670-109">解决因重新编译查询导致的 CPU 使用率过高的问题</span><span class="sxs-lookup"><span data-stu-id="f7670-109">Troubleshoot excessive CPU usage caused by query recompilation</span></span>  
  
-   <span data-ttu-id="f7670-110">排除死锁故障</span><span class="sxs-lookup"><span data-stu-id="f7670-110">Troubleshoot deadlocks</span></span>  
  
 <span data-ttu-id="f7670-111">有关如何使用新建会话向导创建扩展事件会话的信息，请参阅[使用向导（对象资源管理器）创建扩展事件会话](../ssms/object/object-explorer.md)。</span><span class="sxs-lookup"><span data-stu-id="f7670-111">For information about how to create an Extended Events session using the New Session Wizard, see [Create an Extended Events Session Using the Wizard &#40;Object Explorer&#41;](../ssms/object/object-explorer.md).</span></span> <span data-ttu-id="f7670-112">有关如何使用新建会话 UI 创建扩展事件会话的信息，请参阅[使用新建会话创建扩展事件会话](../../2014/database-engine/create-an-extended-events-session-using-the-new-session-dialog.md)。</span><span class="sxs-lookup"><span data-stu-id="f7670-112">For information about how to create an Extended Events session using the New Session UI, see [Create an Extended Events Session Using the New Session Dialog](../../2014/database-engine/create-an-extended-events-session-using-the-new-session-dialog.md).</span></span>  
  
##  <a name="permissions"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="f7670-113">权限</span><span class="sxs-lookup"><span data-stu-id="f7670-113">Permissions</span></span>  
 <span data-ttu-id="f7670-114">若要创建扩展事件会话，您必须具有 ALTER ANY EVENT SESSION 权限。</span><span class="sxs-lookup"><span data-stu-id="f7670-114">To create an Extended Events session, you must have the ALTER ANY EVENT SESSION permission.</span></span>  
  
## <a name="creating-an-extended-events-session-using-query-editor"></a><span data-ttu-id="f7670-115">使用查询编辑器创建扩展事件会话</span><span class="sxs-lookup"><span data-stu-id="f7670-115">Creating an Extended Events session using Query Editor</span></span>  
  
#### <a name="to-create-an-extended-events-session"></a><span data-ttu-id="f7670-116">创建扩展事件会话</span><span class="sxs-lookup"><span data-stu-id="f7670-116">To create an Extended Events session</span></span>  
  
1.  <span data-ttu-id="f7670-117">下面的过程说明如何通过使用 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]中的查询编辑器创建扩展事件会话。</span><span class="sxs-lookup"><span data-stu-id="f7670-117">The following procedure shows how to create an Extended Events session by using Query Editor in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
     <span data-ttu-id="f7670-118">确定要在会话中使用的事件。</span><span class="sxs-lookup"><span data-stu-id="f7670-118">Determine which events that you want to use in the session.</span></span> <span data-ttu-id="f7670-119">若要查看所有可用事件以及关键字和渠道，请使用以下查询：</span><span class="sxs-lookup"><span data-stu-id="f7670-119">To see all the events that are available, together with the keyword and channel, use the following query:</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f7670-120">有关关键字和渠道的信息，请参阅 [SQL Server 扩展事件包](../relational-databases/extended-events/sql-server-extended-events-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="f7670-120">For information about keywords and channels, see [SQL Server Extended Events Packages](../relational-databases/extended-events/sql-server-extended-events-packages.md).</span></span>  
  
    ```  
    SELECT p.name, c.event, k.keyword, c.channel, c.description FROM  
       (  
       SELECT event_package = o.package_guid, o.description,   
       event=c.object_name, channel = v.map_value  
       FROM sys.dm_xe_objects o  
       LEFT JOIN sys.dm_xe_object_columns c ON o.name = c.object_name  
       INNER JOIN sys.dm_xe_map_values v ON c.type_name = v.name   
       AND c.column_value = cast(v.map_key AS nvarchar)  
       WHERE object_type = 'event' AND (c.name = 'CHANNEL' or c.name IS NULL)  
       ) c LEFT JOIN   
       (  
       SELECT event_package = c.object_package_guid, event = c.object_name,   
       keyword = v.map_value  
       FROM sys.dm_xe_object_columns c INNER JOIN sys.dm_xe_map_values v   
       ON c.type_name = v.name AND c.column_value = v.map_key   
       AND c.type_package_guid = v.object_package_guid  
       INNER JOIN sys.dm_xe_objects o ON o.name = c.object_name   
       AND o.package_guid = c.object_package_guid  
       WHERE object_type = 'event' AND c.name = 'KEYWORD'   
       ) k  
       ON  
       k.event_package = c.event_package AND (k.event=c.event or k.event IS NULL)  
       INNER JOIN sys.dm_xe_packages p ON p.guid = c.event_package  
    ORDER BY keyword desc, channel, event  
    ```  
  
2.  <span data-ttu-id="f7670-121">在新的查询窗口中，添加以下语句以便创建一个事件会话，并且使用你要使用的会话名称替换 *session_name* ：</span><span class="sxs-lookup"><span data-stu-id="f7670-121">In a new query window, add the following statements to create an event session, replacing *session_name* with the session name that you want to use:</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="f7670-122">此过程的步骤 2 到 6 描述事件会话定义的各部分。</span><span class="sxs-lookup"><span data-stu-id="f7670-122">Steps 2 through 6 of this procedure describe each section of the event session definition.</span></span> <span data-ttu-id="f7670-123">在执行前，您要将所有语句都添加到单个查询窗口中。</span><span class="sxs-lookup"><span data-stu-id="f7670-123">You would add all the statements to a single query window before executing.</span></span> <span data-ttu-id="f7670-124">有关完整示例，请参阅本主题的“示例”部分。</span><span class="sxs-lookup"><span data-stu-id="f7670-124">For a full example, see the Example section of this topic.</span></span>  
  
    ```  
    CREATE EVENT SESSION session_name   
    ON SERVER  
    ```  
  
3.  <span data-ttu-id="f7670-125">以 *package_name*.*event_name*格式添加你要监视的事件。</span><span class="sxs-lookup"><span data-stu-id="f7670-125">Add the events that you want to monitor, in the format *package_name*.*event_name*.</span></span> <span data-ttu-id="f7670-126">对于每个事件，添加如下的一行：</span><span class="sxs-lookup"><span data-stu-id="f7670-126">For each event, add a line similar to the following:</span></span>  
  
    ```  
    ADD EVENT package_name.event_name  
    ```  
  
     <span data-ttu-id="f7670-127">例如：</span><span class="sxs-lookup"><span data-stu-id="f7670-127">For example:</span></span>  
  
    ```  
    ADD EVENT sqlserver.file_read_completed,  
    ADD EVENT sqlserver.file_write_completed  
    ```  
  
4.  <span data-ttu-id="f7670-128">（可选）在您添加一个事件后，可以添加要执行的操作。</span><span class="sxs-lookup"><span data-stu-id="f7670-128">(Optional) After you add an event, you can add actions to take.</span></span> <span data-ttu-id="f7670-129">还可以添加谓词。</span><span class="sxs-lookup"><span data-stu-id="f7670-129">You can also add predicates.</span></span> <span data-ttu-id="f7670-130">谓词用于确立目标何时应使用事件信息的条件。</span><span class="sxs-lookup"><span data-stu-id="f7670-130">Predicates are used to establish criteria for when the event information should be consumed by the target.</span></span> <span data-ttu-id="f7670-131">通过使用 ACTION 子句添加操作，并且通过使用 WHERE 子句添加谓词。</span><span class="sxs-lookup"><span data-stu-id="f7670-131">Actions are added by using an ACTION clause, and predicates are added by using a WHERE clause.</span></span> <span data-ttu-id="f7670-132">例如，若要添加为 sqlserver.file_read_completed 事件捕获 [!INCLUDE[tsql](../includes/tsql-md.md)] 文本并且文件 ID 等于 1 的操作和谓词，要包括以下语句：</span><span class="sxs-lookup"><span data-stu-id="f7670-132">For example, to add an action and predicate where the [!INCLUDE[tsql](../includes/tsql-md.md)] text is captured for the sqlserver.file_read_completed event, where the file ID equals 1, you would include the following statement:</span></span>  
  
    ```  
    ADD EVENT sqlserver.file_read_completed  
       (ACTION (sqlserver.sql_text)  
       WHERE file_id = 1),  
    ```  
  
    -   <span data-ttu-id="f7670-133">若要查看可用的操作，请使用以下查询：</span><span class="sxs-lookup"><span data-stu-id="f7670-133">To view which actions are available, use the following query:</span></span>  
  
        ```  
        SELECT p.name AS 'package_name', xo.name AS 'action_name', xo.description, xo.object_type  
        FROM sys.dm_xe_objects AS xo  
        JOIN sys.dm_xe_packages AS p  
           ON xo.package_guid = p.guid  
        WHERE xo.object_type = 'action'  
        AND (xo.capabilities & 1 = 0   
        OR xo.capabilities IS NULL)  
        ORDER BY p.name, xo.name  
        ```  
  
    -   <span data-ttu-id="f7670-134">若要查看可用于事件的谓词，请使用以下查询，并且使用你要为其添加谓词的事件名称替换 *event_name* ：</span><span class="sxs-lookup"><span data-stu-id="f7670-134">To view which predicates are available for an event, use the following query, replacing *event_name* with the name of the event for which you want to add a predicate:</span></span>  
  
        ```  
        SELECT *  
        FROM sys.dm_xe_object_columns  
        WHERE object_name = 'event_name'  
        AND column_type = 'data'  
        ```  
  
         <span data-ttu-id="f7670-135">例如：</span><span class="sxs-lookup"><span data-stu-id="f7670-135">For example:</span></span>  
  
        ```  
        SELECT *   
        FROM sys.dm_xe_object_columns   
        WHERE object_name = 'file_read_completed'  
        AND column_type = 'data'  
        ```  
  
         <span data-ttu-id="f7670-136">请注意，您还可以添加全局谓词源。</span><span class="sxs-lookup"><span data-stu-id="f7670-136">Be aware that you can also add global predicate sources.</span></span> <span data-ttu-id="f7670-137">全局谓词源可用于任何谓词表达式中。</span><span class="sxs-lookup"><span data-stu-id="f7670-137">A global predicate source can be used in any predicate expression.</span></span> <span data-ttu-id="f7670-138">若要查看可用的全局谓词源，请使用以下查询：</span><span class="sxs-lookup"><span data-stu-id="f7670-138">To view which global predicate sources are available, use the following query:</span></span>  
  
        ```  
        SELECT p.name AS package_name, xo.name AS predicate_name  
           , xo.description, xo.object_type  
        FROM sys.dm_xe_objects AS xo  
        JOIN sys.dm_xe_packages AS p  
           ON xo.package_guid = p.guid  
        WHERE xo.object_type = 'pred_source'  
        ORDER BY p.name, xo.name  
        ```  
  
         <span data-ttu-id="f7670-139">例如，您可以使用以下谓词表达式以便指定仅为前五次发生的事件收集数据。</span><span class="sxs-lookup"><span data-stu-id="f7670-139">For example, you could use the following predicate expression to specify that data should only be collected for an event the first five times that an event occurs.</span></span>  
  
        ```  
        WHERE package0.counter <= 5  
        ```  
  
5.  <span data-ttu-id="f7670-140">添加将处理和使用事件数据的预期目标。</span><span class="sxs-lookup"><span data-stu-id="f7670-140">Add the desired target, where the event data will be processed and consumed.</span></span> <span data-ttu-id="f7670-141">使用以下格式：</span><span class="sxs-lookup"><span data-stu-id="f7670-141">Use the following format:</span></span>  
  
    ```  
    ADD TARGET package_name.target_name  
    ```  
  
     <span data-ttu-id="f7670-142">以下示例添加异步文件目标：</span><span class="sxs-lookup"><span data-stu-id="f7670-142">The following example adds the asynchronous file target:</span></span>  
  
    ```  
    ADD TARGET package0.asynchronous_file_target  
       (SET filename = 'c:\temp\xelog.xel', metadatafile = 'c:\temp\xelog.xem')  
    ```  
  
     <span data-ttu-id="f7670-143">若要查看可用目标的列表，请使用以下查询：</span><span class="sxs-lookup"><span data-stu-id="f7670-143">To view the list of available targets, use the following query:</span></span>  
  
    ```  
    SELECT p.name AS 'package_name', xo.name AS 'target_name'  
       , xo.description, xo.object_type   
    FROM sys.dm_xe_objects AS xo  
    JOIN sys.dm_xe_packages AS p  
       ON xo.package_guid = p.guid  
    WHERE xo.object_type = 'target'  
    AND (xo.capabilities & 1 = 0  
    OR xo.capabilities IS NULL)  
    ORDER BY p.name, xo.name  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="f7670-144">有关不同目标类型的信息，请参阅 [SQL Server 扩展事件目标](../../2014/database-engine/sql-server-extended-events-targets.md)。</span><span class="sxs-lookup"><span data-stu-id="f7670-144">For information about the different target types, see [SQL Server Extended Events Targets](../../2014/database-engine/sql-server-extended-events-targets.md).</span></span>  
  
6.  <span data-ttu-id="f7670-145">查看和添加任何附加的配置选项。</span><span class="sxs-lookup"><span data-stu-id="f7670-145">Review and add any additional configuration options.</span></span> <span data-ttu-id="f7670-146">例如，您可以配置不同的选项，例如事件保留模式、事件在内存中缓冲的时间或者在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 启动时事件会话是否应自动启动。</span><span class="sxs-lookup"><span data-stu-id="f7670-146">For example, you can configure options such as the event retention mode, how long events are buffered in memory, or whether the event session should start automatically when [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] starts.</span></span> <span data-ttu-id="f7670-147">主题 [ALTER EVENT SESSION (Transact SQL)](/sql/t-sql/statements/alter-event-session-transact-sql) 中对这些选项进行了介绍。</span><span class="sxs-lookup"><span data-stu-id="f7670-147">The options are described in the topic [ALTER EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-event-session-transact-sql).</span></span> <span data-ttu-id="f7670-148">请注意，如果未指定这些选项，则分配默认值。</span><span class="sxs-lookup"><span data-stu-id="f7670-148">Be aware that default values are assigned if these options are not specified.</span></span>  
  
7.  <span data-ttu-id="f7670-149">启动会话。</span><span class="sxs-lookup"><span data-stu-id="f7670-149">Start the session.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f7670-150">有关如何查看会话结果的详细信息，请参阅针对在联机丛书的 [SQL Server 扩展事件目标](../../2014/database-engine/sql-server-extended-events-targets.md) 节点中使用的目标类型的相应主题。</span><span class="sxs-lookup"><span data-stu-id="f7670-150">For more information about how to view the session results, see the corresponding topic for the target type that you used in the [SQL Server Extended Events Targets](../../2014/database-engine/sql-server-extended-events-targets.md) node of Books Online.</span></span>  
  
 <span data-ttu-id="f7670-151">下面的示例创建名为 IOActivity 的扩展事件会话，该会话捕获以下信息：</span><span class="sxs-lookup"><span data-stu-id="f7670-151">The following example creates an Extended Events session named IOActivity that captures the following information:</span></span>  
  
-   <span data-ttu-id="f7670-152">已完成文件读取的事件数据，包括用于文件 ID 等于 1 的文件读取的关联 [!INCLUDE[tsql](../includes/tsql-md.md)] 文本。</span><span class="sxs-lookup"><span data-stu-id="f7670-152">Event data for completed file reads, including the associated [!INCLUDE[tsql](../includes/tsql-md.md)] text for file reads where the file ID is equal to 1.</span></span>  
  
-   <span data-ttu-id="f7670-153">已完成文件写入的事件数据。</span><span class="sxs-lookup"><span data-stu-id="f7670-153">Event data for completed file writes.</span></span>  
  
-   <span data-ttu-id="f7670-154">数据从日志缓存写入物理日志文件时的事件数据。</span><span class="sxs-lookup"><span data-stu-id="f7670-154">Event data for when data is written from the log cache to the physical log file.</span></span>  
  
 <span data-ttu-id="f7670-155">该会话将输出发送到某一文件目标。</span><span class="sxs-lookup"><span data-stu-id="f7670-155">The session sends the output to a file target.</span></span>  
  
```  
CREATE EVENT SESSION IOActivity  
ON SERVER  
  
ADD EVENT sqlserver.file_read_completed  
   (  
   ACTION (sqlserver.sql_text)  
   WHERE file_id = 1),  
ADD EVENT sqlserver.file_write_completed,  
ADD EVENT sqlserver.databases_log_flush  
  
ADD TARGET package0.asynchronous_file_target   
   (SET filename = 'c:\temp\xelog.xel', metadatafile = 'c:\temp\xelog.xem')  
```  
  
## <a name="see-also"></a><span data-ttu-id="f7670-156">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f7670-156">See Also</span></span>  
 <span data-ttu-id="f7670-157">[CREATE EVENT SESSION (Transact-SQL)](/sql/t-sql/statements/create-event-session-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f7670-157">[CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql) </span></span>  
 <span data-ttu-id="f7670-158">[SQL Server 扩展事件目标](../../2014/database-engine/sql-server-extended-events-targets.md) </span><span class="sxs-lookup"><span data-stu-id="f7670-158">[SQL Server Extended Events Targets](../../2014/database-engine/sql-server-extended-events-targets.md) </span></span>  
 [<span data-ttu-id="f7670-159">SQL Server 扩展事件包</span><span class="sxs-lookup"><span data-stu-id="f7670-159">SQL Server Extended Events Packages</span></span>](../relational-databases/extended-events/sql-server-extended-events-packages.md)  
  
  
