---
title: 将现有 SQL 跟踪脚本转换为扩展事件会话 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xevents
ms.topic: conceptual
helpviewer_keywords:
- SQL Trace, convert script to extended events
- extended events [SQL Server], convert SQL Trace script
ms.assetid: 4c8f29e6-0a37-490f-88b3-33493871b3f9
author: rothja
ms.author: jroth
ms.openlocfilehash: 1e5b0d0e20fbf4fd55398c130abf6cfff128ebe8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589101"
---
# <a name="convert-an-existing-sql-trace-script-to-an-extended-events-session"></a><span data-ttu-id="7f3e5-102">将现有 SQL 跟踪脚本转换为扩展事件会话</span><span class="sxs-lookup"><span data-stu-id="7f3e5-102">Convert an Existing SQL Trace Script to an Extended Events Session</span></span>
  <span data-ttu-id="7f3e5-103">如果您具有想要转换为扩展事件会话的现有 SQL 跟踪脚本，则可以使用本主题中的过程创建等效的扩展事件会话。</span><span class="sxs-lookup"><span data-stu-id="7f3e5-103">If you have an existing SQL Trace script that you want to convert to an Extended Events session, you can use the procedures in this topic to create an equivalent Extended Events session.</span></span> <span data-ttu-id="7f3e5-104">通过使用 trace_xe_action_map 和 trace_xe_event_map 系统表中的信息，你可以收集进行转换所必需的信息。</span><span class="sxs-lookup"><span data-stu-id="7f3e5-104">By using the information in the trace_xe_action_map and trace_xe_event_map system tables, you can collect the information that you must have to do the conversion.</span></span>  
  
 <span data-ttu-id="7f3e5-105">这些步骤包括以下内容：</span><span class="sxs-lookup"><span data-stu-id="7f3e5-105">The steps include the following:</span></span>  
  
1.  <span data-ttu-id="7f3e5-106">执行现有脚本以便创建一个 SQL 跟踪会话，然后获取该跟踪的 ID。</span><span class="sxs-lookup"><span data-stu-id="7f3e5-106">Execute the existing script to create a SQL Trace session, and then obtain the ID of the trace.</span></span>  
  
2.  <span data-ttu-id="7f3e5-107">运行一个查询，该查询使用 fn_trace_geteventinfo 函数来为每个 SQL 跟踪事件类及其关联列找到等效的扩展事件的事件和操作。</span><span class="sxs-lookup"><span data-stu-id="7f3e5-107">Run a query that uses the fn_trace_geteventinfo function to find the equivalent Extended Events events and actions for each SQL Trace event class and its associated columns.</span></span>  
  
3.  <span data-ttu-id="7f3e5-108">使用 fn_trace_getfilterinfo 函数列出要使用的筛选器和等效的扩展事件操作。</span><span class="sxs-lookup"><span data-stu-id="7f3e5-108">Use the fn_trace_getfilterinfo function to list the filters and the equivalent Extended Events actions to use.</span></span>  
  
4.  <span data-ttu-id="7f3e5-109">手动创建扩展事件会话，并且使用等效的扩展事件的事件、操作和谓词（筛选器）。</span><span class="sxs-lookup"><span data-stu-id="7f3e5-109">Manually create an Extended Events session, using the equivalent Extended Events events, actions, and predicates (filters).</span></span>  
  
## <a name="to-obtain-the-trace-id"></a><span data-ttu-id="7f3e5-110">获取跟踪 ID</span><span class="sxs-lookup"><span data-stu-id="7f3e5-110">To obtain the trace ID</span></span>  
  
1.  <span data-ttu-id="7f3e5-111">在查询编辑器中打开 SQL 跟踪脚本，然后执行该脚本以便创建跟踪会话。</span><span class="sxs-lookup"><span data-stu-id="7f3e5-111">Open the SQL Trace script in Query Editor, and then execute the script to create the trace session.</span></span> <span data-ttu-id="7f3e5-112">请注意，无需运行该跟踪会话即可完成此过程。</span><span class="sxs-lookup"><span data-stu-id="7f3e5-112">Note that the trace session does not need to be running to complete this procedure.</span></span>  
  
2.  <span data-ttu-id="7f3e5-113">获取跟踪的 ID。</span><span class="sxs-lookup"><span data-stu-id="7f3e5-113">Obtain the ID of the trace.</span></span> <span data-ttu-id="7f3e5-114">为此，请使用以下查询：</span><span class="sxs-lookup"><span data-stu-id="7f3e5-114">To do this, use the following query:</span></span>  
  
    ```sql
    SELECT * FROM sys.traces;  
    GO  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="7f3e5-115">跟踪 ID 1 通常指示默认跟踪。</span><span class="sxs-lookup"><span data-stu-id="7f3e5-115">Trace ID 1 typically indicates the default trace.</span></span>  
  
## <a name="to-determine-the-extended-events-equivalents"></a><span data-ttu-id="7f3e5-116">确定等效的扩展事件</span><span class="sxs-lookup"><span data-stu-id="7f3e5-116">To determine the Extended Events equivalents</span></span>  
  
1.  <span data-ttu-id="7f3e5-117">若要确定等效的扩展事件的事件和操作，请运行以下查询，其中，将 *trace_id* 设置为你在之前过程中获取的跟踪 ID 的值。</span><span class="sxs-lookup"><span data-stu-id="7f3e5-117">To determine the equivalent Extended Events events and actions, run the following query, where *trace_id* is set to the value of the trace ID that you obtained in the previous procedure.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7f3e5-118">在这个示例中，使用默认跟踪 (1) 的跟踪 ID。</span><span class="sxs-lookup"><span data-stu-id="7f3e5-118">In this example, the trace ID for the default trace (1) is used.</span></span>  
  
    ```sql
    USE MASTER;  
    GO  
    DECLARE @trace_id int;  
    SET @trace_id = 1;  
    SELECT DISTINCT el.eventid, em.package_name, em.xe_event_name AS 'event'  
       , el.columnid, ec.xe_action_name AS 'action'  
    FROM (sys.fn_trace_geteventinfo(@trace_id) AS el  
       LEFT OUTER JOIN sys.trace_xe_event_map AS em  
          ON el.eventid = em.trace_event_id)  
    LEFT OUTER JOIN sys.trace_xe_action_map AS ec  
       ON el.columnid = ec.trace_column_id  
    WHERE em.xe_event_name IS NOT NULL AND ec.xe_action_name IS NOT NULL;  
    ```  
  
     <span data-ttu-id="7f3e5-119">将返回等效的扩展事件的事件 ID、包名称、事件名称、列 ID 和操作名称。</span><span class="sxs-lookup"><span data-stu-id="7f3e5-119">The equivalent Extended Events event ID, package name, event name, column ID and action name are returned.</span></span> <span data-ttu-id="7f3e5-120">您将在本主题后面的“创建扩展事件会话”过程中使用此输出。</span><span class="sxs-lookup"><span data-stu-id="7f3e5-120">You will use this output in the procedure "To create the Extended Events session" later in this topic.</span></span>  
  
     <span data-ttu-id="7f3e5-121">在某些情况下，筛选列将映射到默认在扩展事件的事件中包括的事件数据字段。</span><span class="sxs-lookup"><span data-stu-id="7f3e5-121">In some cases, the filtered column maps to an event data field that is included by default in the Extended Events event.</span></span> <span data-ttu-id="7f3e5-122">因此，“Extended_Events_action_name”列将为 NULL。</span><span class="sxs-lookup"><span data-stu-id="7f3e5-122">Therefore, the "Extended_Events_action_name" column will be NULL.</span></span> <span data-ttu-id="7f3e5-123">如果发生此情况，您必须执行以下操作以便确定哪一数据字段等效于筛选列：</span><span class="sxs-lookup"><span data-stu-id="7f3e5-123">If this occurs, you must do the following to determine which data field is equivalent to the filtered column:</span></span>  
  
    1.  <span data-ttu-id="7f3e5-124">对于返回 NULL 的操作，标识脚本中哪些 SQL 跟踪事件类包含要筛选的列。</span><span class="sxs-lookup"><span data-stu-id="7f3e5-124">For the actions that return NULL, identify which SQL Trace event classes in the script contain the column that is being filtered.</span></span>  
  
         <span data-ttu-id="7f3e5-125">例如，你可能使用了 SP:StmtCompleted 事件类，并且对 Duration 跟踪列名（SQL 跟踪事件类 ID 45 和 SQL 跟踪列 ID 13）指定了一个筛选器。</span><span class="sxs-lookup"><span data-stu-id="7f3e5-125">For example, you may have used the SP:StmtCompleted event class, and specified a filter on the Duration trace column name (SQL Trace event class ID 45, and SQL Trace column ID 13).</span></span> <span data-ttu-id="7f3e5-126">在此情况下，该操作名称将以 NULL 的形式出现在查询结果中。</span><span class="sxs-lookup"><span data-stu-id="7f3e5-126">In this case, the action name will appear as NULL in the query results.</span></span>  
  
    2.  <span data-ttu-id="7f3e5-127">对于您在前一步骤中标识的每个 SQL 跟踪事件类，找到等效的扩展事件的事件名称。</span><span class="sxs-lookup"><span data-stu-id="7f3e5-127">For each SQL Trace event class that you identified in the previous step, find the equivalent Extended Events event name.</span></span> <span data-ttu-id="7f3e5-128">（如果你不确定等效的事件名称，请使用 [查看与 SQL 跟踪事件类等效的扩展事件](view-the-extended-events-equivalents-to-sql-trace-event-classes.md)主题中的查询。）</span><span class="sxs-lookup"><span data-stu-id="7f3e5-128">(If you are not sure of the equivalent event name, use the query in the topic [View the Extended Events Equivalents to SQL Trace Event Classes](view-the-extended-events-equivalents-to-sql-trace-event-classes.md).)</span></span>  
  
    3.  <span data-ttu-id="7f3e5-129">使用下面的查询可以标识要用于您在前一步骤中标识的事件的正确的数据字段。</span><span class="sxs-lookup"><span data-stu-id="7f3e5-129">Use the following query to identify the correct data fields to use for the events that you identified in the previous step.</span></span> <span data-ttu-id="7f3e5-130">该查询将在“事件字段”列中显示扩展事件数据字段。</span><span class="sxs-lookup"><span data-stu-id="7f3e5-130">The query shows the Extended Events data fields in the "event_field" column.</span></span> <span data-ttu-id="7f3e5-131">在该查询中，用前一步骤中指定的事件名称替换 *<event_name>*。</span><span class="sxs-lookup"><span data-stu-id="7f3e5-131">In the query, replace *<event_name>* with the name of an event that you specified in the previous step.</span></span>  
  
        ```sql
        SELECT xp.name package_name, xe.name event_name  
           ,xc.name event_field, xc.description  
        FROM sys.trace_xe_event_map AS em  
        INNER JOIN sys.dm_xe_objects AS xe  
           ON em.xe_event_name = xe.name  
        INNER JOIN sys.dm_xe_packages AS xp  
           ON xe.package_guid = xp.guid AND em.package_name = xp.name  
        INNER JOIN sys.dm_xe_object_columns AS xc  
           ON xe.name = xc.object_name  
        WHERE xe.object_type = 'event' AND xc.column_type <> 'readonly'  
           AND em.xe_event_name = '<event_name>';  
        ```  
  
         <span data-ttu-id="7f3e5-132">例如，SP:StmtCompleted 事件类映射到 sp_statement_completed 扩展事件的事件。</span><span class="sxs-lookup"><span data-stu-id="7f3e5-132">For example, the SP:StmtCompleted event class maps to the sp_statement_completed Extended Events event.</span></span> <span data-ttu-id="7f3e5-133">如果你在查询中将 sp_statement_completed 指定为事件名称，则“event_field”列将显示随该事件默认包括的字段。</span><span class="sxs-lookup"><span data-stu-id="7f3e5-133">If you specify sp_statement_completed as the event name in the query, the "event_field" column shows the fields that are included by default with the event.</span></span> <span data-ttu-id="7f3e5-134">在查看这些字段时，您会看到有一个“duration”字段。</span><span class="sxs-lookup"><span data-stu-id="7f3e5-134">Looking at the fields, you can see that there is a "duration" field.</span></span> <span data-ttu-id="7f3e5-135">若要在等效的扩展事件会话中创建筛选器，你需要添加一个谓词，例如“WHERE duration > 0”。</span><span class="sxs-lookup"><span data-stu-id="7f3e5-135">To create the filter in the equivalent Extended Events session, you would add a predicate such as "WHERE duration > 0".</span></span> <span data-ttu-id="7f3e5-136">有关示例，请参阅本主题中的“创建扩展事件会话”过程。</span><span class="sxs-lookup"><span data-stu-id="7f3e5-136">For an example, see the "To create the Extended Events session" procedure in this topic.</span></span>  
  
## <a name="to-create-the-extended-events-session"></a><span data-ttu-id="7f3e5-137">创建扩展事件会话</span><span class="sxs-lookup"><span data-stu-id="7f3e5-137">To create the Extended Events session</span></span>  
 <span data-ttu-id="7f3e5-138">使用查询编辑器可以创建扩展事件会话，并且将输出写入某一文件目标。</span><span class="sxs-lookup"><span data-stu-id="7f3e5-138">Use Query Editor to create the Extended Events session, and to write the output to a file target.</span></span> <span data-ttu-id="7f3e5-139">下面的步骤描述单个查询，并且提供介绍如何生成查询的说明。</span><span class="sxs-lookup"><span data-stu-id="7f3e5-139">The following steps describe a single query, with explanations to show you how to build the query.</span></span> <span data-ttu-id="7f3e5-140">有关完整查询示例，请参阅本主题的“示例”部分。</span><span class="sxs-lookup"><span data-stu-id="7f3e5-140">For the full query example, see the "Example" section of this topic.</span></span>  
  
1.  <span data-ttu-id="7f3e5-141">添加语句以创建事件会话，并且使用要用于扩展事件会话的名称替换*session_name* 。</span><span class="sxs-lookup"><span data-stu-id="7f3e5-141">Add statements to create the event session, replacing s*ession_name* with the name that you want to use for the Extended Events session.</span></span>  
  
    ```sql
    IF EXISTS(SELECT * FROM sys.server_event_sessions WHERE name='session_name')  
       DROP EVENT SESSION [Session_Name] ON SERVER;  
    CREATE EVENT SESSION [Session_Name]  
    ON SERVER;  
    ```  
  
2.  <span data-ttu-id="7f3e5-142">添加在“确定等效的扩展事件”过程中作为输出返回的扩展事件的事件和操作，并且添加在“确定在脚本中使用的筛选器”过程中标识的谓词（筛选器）。</span><span class="sxs-lookup"><span data-stu-id="7f3e5-142">Add the Extended Events events and actions that were returned as output in the procedure "Determine the Extended Events equivalents", and add the predicates (filters) that you identified in the procedure "To determine the filters that were used in the script".</span></span>  
  
     <span data-ttu-id="7f3e5-143">下面的示例使用一个 SQL 跟踪脚本，该脚本包括 SQL:StmtStarting 和 SP:StmtCompleted 事件类，以及用于会话 ID 和持续时间的筛选器。</span><span class="sxs-lookup"><span data-stu-id="7f3e5-143">The following example uses a SQL Trace script that includes the SQL:StmtStarting and SP:StmtCompleted event classes, with filters for session ID and duration.</span></span> <span data-ttu-id="7f3e5-144">“确定等效的扩展事件”过程中查询的示例输出返回了以下结果集：</span><span class="sxs-lookup"><span data-stu-id="7f3e5-144">Sample output for the query in the "Determine the Extended Events equivalents" procedure returned the following result set:</span></span>  
  
    ```  
    Eventid  package_name  event                   columnid  action  
    44       sqlserver     sp_statement_starting   6         nt_username  
    44       sqlserver     sp_statement_starting   9         client_pid  
    44       sqlserver     sp_statement_starting   10        client_app_name  
    44       sqlserver     sp_statement_starting   11        server_principal_name  
    44       sqlserver     sp_statement_starting   12        session_id  
    45       sqlserver     sp_statement_completed  6         nt_username  
    45       sqlserver     sp_statement_completed  9         client_pid  
    45       sqlserver     sp_statement_completed  10        client_app_name  
    45       sqlserver     sp_statement_completed  11        server_principal_name  
    45       sqlserver     sp_statement_completed  12        session_id  
    ```  
  
     <span data-ttu-id="7f3e5-145">为了将其转换为等效的扩展事件，添加了 sqlserver.sp_statement_starting 和 sqlserver.sp_statement_completed 事件以及操作列表。</span><span class="sxs-lookup"><span data-stu-id="7f3e5-145">To convert this to the Extended Events equivalent, the sqlserver.sp_statement_starting and the sqlserver.sp_statement_completed events are added, with a list of actions.</span></span> <span data-ttu-id="7f3e5-146">谓词语句作为 WHERE 子句包括。</span><span class="sxs-lookup"><span data-stu-id="7f3e5-146">Predicate statements are included as WHERE clauses.</span></span>  
  
    ```sql
    ADD EVENT sqlserver.sp_statement_starting  
       (ACTION  
          (  
          sqlserver.nt_username,  
          sqlserver.client_pid,  
          sqlserver.client_app_name,  
          sqlserver.server_principal_name,  
          sqlserver.session_id  
          )  
       WHERE sqlserver.session_id = 59   
       ),  
  
    ADD EVENT sqlserver.sp_statement_completed  
       (ACTION  
          (  
          sqlserver.nt_username,  
          sqlserver.client_pid,  
          sqlserver.client_app_name,  
          sqlserver.server_principal_name,  
          sqlserver.session_id  
          )  
       WHERE sqlserver.session_id = 59 AND duration > 0  
       )  
    ```  
  
3.  <span data-ttu-id="7f3e5-147">添加异步文件目标，并且使用要用来保存输出的位置替换文件路径。</span><span class="sxs-lookup"><span data-stu-id="7f3e5-147">Add the asynchronous file target, replacing the file paths with the location where you want to save the output.</span></span> <span data-ttu-id="7f3e5-148">在指定文件目标时，必须包括日志文件和元数据文件路径文件。</span><span class="sxs-lookup"><span data-stu-id="7f3e5-148">When specifying the file target, you must include a log file and metadata file path file.</span></span>  
  
    ```sql
    ADD TARGET package0.asynchronous_file_target(  
       SET filename='c:\temp\ExtendedEventsStoredProcs.xel', metadatafile='c:\temp\ExtendedEventsStoredProcs.xem');  
    ```  
  
## <a name="to-view-the-results"></a><span data-ttu-id="7f3e5-149">查看结果</span><span class="sxs-lookup"><span data-stu-id="7f3e5-149">To view the results</span></span>  
  
1.  <span data-ttu-id="7f3e5-150">可使用 sys.fn_xe_file_target_read_file 函数查看输出。</span><span class="sxs-lookup"><span data-stu-id="7f3e5-150">You can use the sys.fn_xe_file_target_read_file function to view the output.</span></span> <span data-ttu-id="7f3e5-151">为此，运行以下查询，并且使用您指定的路径替换文件路径：</span><span class="sxs-lookup"><span data-stu-id="7f3e5-151">To do this, run the following query, replacing the file paths with the paths that you specified:</span></span>  
  
    ```sql
    SELECT *, CAST(event_data as XML) AS 'event_data_XML'  
    FROM sys.fn_xe_file_target_read_file('c:\temp\ExtendedEventsStoredProcs*.xel', 'c:\temp\ExtendedEventsStoredProcs*.xem', NULL, NULL);  
  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="7f3e5-152">将事件数据转换为 XML 是可选的。</span><span class="sxs-lookup"><span data-stu-id="7f3e5-152">Casting the event data as XML is optional.</span></span>  
  
     <span data-ttu-id="7f3e5-153">有关 sys.fn_xe_file_target_read_file 函数的详细信息，请参阅 [sys.fn_xe_file_target_read_file (Transact-SQL)](/sql/relational-databases/system-functions/sys-fn-xe-file-target-read-file-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="7f3e5-153">For more information about the sys.fn_xe_file_target_read_file function, see [sys.fn_xe_file_target_read_file &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-xe-file-target-read-file-transact-sql).</span></span>  
  
    ```sql
    IF EXISTS(SELECT * FROM sys.server_event_sessions WHERE name='session_name')  
       DROP EVENT SESSION [session_name] ON SERVER;  
    CREATE EVENT SESSION [session_name]  
    ON SERVER  
  
    ADD EVENT sqlserver.sp_statement_starting  
       (ACTION  
       (  
          sqlserver.nt_username,  
          sqlserver.client_pid,  
          sqlserver.client_app_name,  
          sqlserver.server_principal_name,  
          sqlserver.session_id  
       )  
       WHERE sqlserver.session_id = 59   
       ),  
  
    ADD EVENT sqlserver.sp_statement_completed  
       (ACTION  
       (  
          sqlserver.nt_username,  
          sqlserver.client_pid,  
          sqlserver.client_app_name,  
          sqlserver.server_principal_name,  
          sqlserver.session_id  
       )  
       WHERE sqlserver.session_id = 59 AND duration > 0  
       );  
  
    ADD TARGET package0.asynchronous_file_target  
       (SET filename='c:\temp\ExtendedEventsStoredProcs.xel', metadatafile='c:\temp\ExtendedEventsStoredProcs.xem');  
    ```  
  
## <a name="example"></a><span data-ttu-id="7f3e5-154">示例</span><span class="sxs-lookup"><span data-stu-id="7f3e5-154">Example</span></span>  
  
```sql
IF EXISTS(SELECT * FROM sys.server_event_sessions WHERE name='session_name')  
   DROP EVENT SESSION [session_name] ON SERVER;  
CREATE EVENT SESSION [session_name]  
ON SERVER  
  
ADD EVENT sqlserver.sp_statement_starting  
   (ACTION  
   (  
      sqlserver.nt_username,  
      sqlserver.client_pid,  
      sqlserver.client_app_name,  
      sqlserver.server_principal_name,  
      sqlserver.session_id  
   )  
   WHERE sqlserver.session_id = 59   
   ),  
  
ADD EVENT sqlserver.sp_statement_completed  
   (ACTION  
   (  
      sqlserver.nt_username,  
      sqlserver.client_pid,  
      sqlserver.client_app_name,  
      sqlserver.server_principal_name,  
      sqlserver.session_id  
   )  
   WHERE sqlserver.session_id = 59 AND duration > 0  
   )  
  
ADD TARGET package0.asynchronous_file_target  
   (SET filename='c:\temp\ExtendedEventsStoredProcs.xel', metadatafile='c:\temp\ExtendedEventsStoredProcs.xem');  
```  
  
## <a name="see-also"></a><span data-ttu-id="7f3e5-155">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7f3e5-155">See Also</span></span>  
 [<span data-ttu-id="7f3e5-156">查看与 SQL 跟踪事件类等效的扩展事件</span><span class="sxs-lookup"><span data-stu-id="7f3e5-156">View the Extended Events Equivalents to SQL Trace Event Classes</span></span>](view-the-extended-events-equivalents-to-sql-trace-event-classes.md)  
  
  
