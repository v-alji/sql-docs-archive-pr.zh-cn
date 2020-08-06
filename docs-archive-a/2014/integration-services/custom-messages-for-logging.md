---
title: 日志记录的自定义消息 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- logs [Integration Services], custom
- writing log entries
- SSIS packages, logs
- custom messages for logging [Integration Services]
ms.assetid: 3c74bba9-02b7-4bf5-bad5-19278b680730
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2b9f450c74ef6d46876adfde45729c71b3262449
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586909"
---
# <a name="custom-messages-for-logging"></a><span data-ttu-id="e2117-102">日志记录的自定义消息</span><span class="sxs-lookup"><span data-stu-id="e2117-102">Custom Messages for Logging</span></span>
  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="e2117-103">提供了一组丰富的自定义事件，可以用来写入包和很多任务的日志项。</span><span class="sxs-lookup"><span data-stu-id="e2117-103">provides a rich set of custom events for writing log entries for packages and many tasks.</span></span> <span data-ttu-id="e2117-104">使用这些项可以记录预定义的事件或用户定义的消息，供随后分析时使用，从而将有关执行进度、结果和问题的详细信息保存下来。</span><span class="sxs-lookup"><span data-stu-id="e2117-104">You can use these entries to save detailed information about execution progress, results, and problems by recording predefined events or user-defined messages for later analysis.</span></span> <span data-ttu-id="e2117-105">例如，可以记录大容量插入的开始和结束时间，从而找出包运行时的性能问题。</span><span class="sxs-lookup"><span data-stu-id="e2117-105">For example, you can record when a bulk insert begins and ends to identify performance issues when the package runs.</span></span>  
  
 <span data-ttu-id="e2117-106">与对包和所有容器及任务可用的标准日志记录事件集相比，自定义日志项是一组不同的项。</span><span class="sxs-lookup"><span data-stu-id="e2117-106">The custom log entries are a different set of entries than the set of standard logging events that are available for packages and all containers and tasks.</span></span> <span data-ttu-id="e2117-107">您可以根据需要使用自定义日志项来捕获有关包中特定任务的有用信息。</span><span class="sxs-lookup"><span data-stu-id="e2117-107">The custom log entries are tailored to capture useful information about a specific task in a package.</span></span> <span data-ttu-id="e2117-108">例如，执行 SQL 任务的一个自定义日志项可以在日志中记录该任务所执行的 SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="e2117-108">For example, one of the custom log entries for the Execute SQL task records the SQL statement that the task executes in the log.</span></span>  
  
 <span data-ttu-id="e2117-109">所有日志项都包括日期和时间信息，包括在包开始和完成时自动写入的日志项。</span><span class="sxs-lookup"><span data-stu-id="e2117-109">All log entries include date and time information, including the log entries that are automatically written when a package begins and finishes.</span></span> <span data-ttu-id="e2117-110">很多日志事件都会在日志中写入多个项。</span><span class="sxs-lookup"><span data-stu-id="e2117-110">Many of the log events write multiple entries to the log.</span></span> <span data-ttu-id="e2117-111">这通常发生在事件有不同阶段时。</span><span class="sxs-lookup"><span data-stu-id="e2117-111">This typically occurs when the event has different phases.</span></span> <span data-ttu-id="e2117-112">例如，`ExecuteSQLExecutingQuery` 日志事件写入三项：在任务获得与数据库的连接之后写入一项，在任务开始准备 SQL 语句之后写入另一项，并在执行完 SQL 语句之后再写入一项。</span><span class="sxs-lookup"><span data-stu-id="e2117-112">For example, the `ExecuteSQLExecutingQuery` log event writes three entries: one entry after the task acquires a connection to the database, another after the task starts to prepare the SQL statement, and one more after the execution of the SQL statement is completed.</span></span>  
  
 <span data-ttu-id="e2117-113">以下 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 对象有自定义日志项：</span><span class="sxs-lookup"><span data-stu-id="e2117-113">The following [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] objects have custom log entries:</span></span>  
  
 [<span data-ttu-id="e2117-114">包</span><span class="sxs-lookup"><span data-stu-id="e2117-114">Package</span></span>](#Package)  
  
 [<span data-ttu-id="e2117-115">大容量插入任务</span><span class="sxs-lookup"><span data-stu-id="e2117-115">Bulk Insert Task</span></span>](#BulkInsert)  
  
 [<span data-ttu-id="e2117-116">数据流任务</span><span class="sxs-lookup"><span data-stu-id="e2117-116">Data Flow Task</span></span>](#DataFlow)  
  
 [<span data-ttu-id="e2117-117">执行 DTS 2000 任务</span><span class="sxs-lookup"><span data-stu-id="e2117-117">Execute DTS 2000 Task</span></span>](#ExecuteDTS200)  
  
 [<span data-ttu-id="e2117-118">执行进程任务</span><span class="sxs-lookup"><span data-stu-id="e2117-118">Execute Process Task</span></span>](#ExecuteProcess)  
  
 [<span data-ttu-id="e2117-119">执行 SQL 任务</span><span class="sxs-lookup"><span data-stu-id="e2117-119">Execute SQL Task</span></span>](#ExecuteSQL)  
  
 [<span data-ttu-id="e2117-120">文件系统任务</span><span class="sxs-lookup"><span data-stu-id="e2117-120">File System Task</span></span>](#FileSystem)  
  
 [<span data-ttu-id="e2117-121">FTP 任务</span><span class="sxs-lookup"><span data-stu-id="e2117-121">FTP Task</span></span>](#FTP)  
  
 [<span data-ttu-id="e2117-122">消息队列任务</span><span class="sxs-lookup"><span data-stu-id="e2117-122">Message Queue Task</span></span>](#MessageQueue)  
  
 [<span data-ttu-id="e2117-123">脚本任务</span><span class="sxs-lookup"><span data-stu-id="e2117-123">Script Task</span></span>](#Script)  
  
 [<span data-ttu-id="e2117-124">发送邮件任务</span><span class="sxs-lookup"><span data-stu-id="e2117-124">Send Mail Task</span></span>](#SendMail)  
  
 [<span data-ttu-id="e2117-125">传输数据库任务</span><span class="sxs-lookup"><span data-stu-id="e2117-125">Transfer Database Task</span></span>](#TransferDatabase)  
  
 [<span data-ttu-id="e2117-126">传输错误消息任务</span><span class="sxs-lookup"><span data-stu-id="e2117-126">Transfer Error Messages Task</span></span>](#TransferErrorMessages)  
  
 [<span data-ttu-id="e2117-127">传输作业任务</span><span class="sxs-lookup"><span data-stu-id="e2117-127">Transfer Jobs Task</span></span>](#TransferJobs)  
  
 [<span data-ttu-id="e2117-128">传输登录名任务</span><span class="sxs-lookup"><span data-stu-id="e2117-128">Transfer Logins Task</span></span>](#TransferLogins)  
  
 [<span data-ttu-id="e2117-129">传输主存储过程任务</span><span class="sxs-lookup"><span data-stu-id="e2117-129">Transfer Master Stored Procedures Task</span></span>](#TransferMasterStoredProcedures)  
  
 [<span data-ttu-id="e2117-130">传输 SQL Server 对象任务</span><span class="sxs-lookup"><span data-stu-id="e2117-130">Transfer SQL Server Objects Task</span></span>](#TransferSQLServerObjects)  
  
 [<span data-ttu-id="e2117-131">Web 服务任务</span><span class="sxs-lookup"><span data-stu-id="e2117-131">Web Services Task</span></span>](#WebServices)  
  
 [<span data-ttu-id="e2117-132">WMI 数据读取器任务</span><span class="sxs-lookup"><span data-stu-id="e2117-132">WMI Data Reader Task</span></span>](#WMIDataReader)  
  
 [<span data-ttu-id="e2117-133">WMI 事件观察器任务</span><span class="sxs-lookup"><span data-stu-id="e2117-133">WMI Event Watcher Task</span></span>](#WMIEventWatcher)  
  
 [<span data-ttu-id="e2117-134">XML 任务</span><span class="sxs-lookup"><span data-stu-id="e2117-134">XML Task</span></span>](#XML)  
  
## <a name="log-entries"></a><span data-ttu-id="e2117-135">日志项</span><span class="sxs-lookup"><span data-stu-id="e2117-135">Log Entries</span></span>  
  
###  <a name="package"></a><a name="Package"></a> <span data-ttu-id="e2117-136">“包”</span><span class="sxs-lookup"><span data-stu-id="e2117-136">Package</span></span>  
 <span data-ttu-id="e2117-137">下表列出了包的自定义日志项。</span><span class="sxs-lookup"><span data-stu-id="e2117-137">The following table lists the custom log entries for packages.</span></span>  
  
|<span data-ttu-id="e2117-138">日志项</span><span class="sxs-lookup"><span data-stu-id="e2117-138">Log entry</span></span>|<span data-ttu-id="e2117-139">说明</span><span class="sxs-lookup"><span data-stu-id="e2117-139">Description</span></span>|  
|---------------|-----------------|  
|`PackageStart`|<span data-ttu-id="e2117-140">指示包开始运行。</span><span class="sxs-lookup"><span data-stu-id="e2117-140">Indicates that the package began to run.</span></span><br /><br /> <span data-ttu-id="e2117-141">注意：此日志项自动写入日志。</span><span class="sxs-lookup"><span data-stu-id="e2117-141">Note: This log entry is automatically written to the log.</span></span> <span data-ttu-id="e2117-142">无法排除它。</span><span class="sxs-lookup"><span data-stu-id="e2117-142">You cannot exclude it.</span></span>|  
|`PackageEnd`|<span data-ttu-id="e2117-143">指示包已完成。</span><span class="sxs-lookup"><span data-stu-id="e2117-143">Indicates that the package completed.</span></span><br /><br /> <span data-ttu-id="e2117-144">注意：此日志项自动写入日志。</span><span class="sxs-lookup"><span data-stu-id="e2117-144">Note: This log entry is automatically written to the log.</span></span> <span data-ttu-id="e2117-145">无法排除它。</span><span class="sxs-lookup"><span data-stu-id="e2117-145">You cannot exclude it.</span></span>|  
|`Diagnostic`|<span data-ttu-id="e2117-146">提供影响包执行的系统配置的相关信息，例如，可并发运行的可执行文件数。</span><span class="sxs-lookup"><span data-stu-id="e2117-146">Provides information about the system configuration that affects package execution such as the number executables that can be run concurrently.</span></span><br /><br /> <span data-ttu-id="e2117-147">`Diagnostic` 日志项还包括调用外部数据访问接口之前和之后的项。</span><span class="sxs-lookup"><span data-stu-id="e2117-147">The `Diagnostic` log entry also includes before and after entries for calls to external data providers.</span></span> <span data-ttu-id="e2117-148">有关详细信息，请参阅 [对包连接进行故障排除的工具](troubleshooting/troubleshooting-tools-for-package-connectivity.md)。</span><span class="sxs-lookup"><span data-stu-id="e2117-148">For more information, see [Troubleshooting Tools Package Connectivity](troubleshooting/troubleshooting-tools-for-package-connectivity.md).</span></span>|  
  
###  <a name="bulk-insert-task"></a><a name="BulkInsert"></a> <span data-ttu-id="e2117-149">大容量插入任务</span><span class="sxs-lookup"><span data-stu-id="e2117-149">Bulk Insert Task</span></span>  
 <span data-ttu-id="e2117-150">下表列出了大容量插入任务的自定义日志项。</span><span class="sxs-lookup"><span data-stu-id="e2117-150">The following table lists the custom log entries for the Bulk Insert task.</span></span>  
  
|<span data-ttu-id="e2117-151">日志项</span><span class="sxs-lookup"><span data-stu-id="e2117-151">Log entry</span></span>|<span data-ttu-id="e2117-152">说明</span><span class="sxs-lookup"><span data-stu-id="e2117-152">Description</span></span>|  
|---------------|-----------------|  
|`DTSBulkInsertTaskBegin`|<span data-ttu-id="e2117-153">指示大容量插入开始。</span><span class="sxs-lookup"><span data-stu-id="e2117-153">Indicates that the bulk insert began.</span></span>|  
|`DTSBulkInsertTaskEnd`|<span data-ttu-id="e2117-154">指示大容量插入完成。</span><span class="sxs-lookup"><span data-stu-id="e2117-154">Indicates that the bulk insert finished.</span></span>|  
|`DTSBulkInsertTaskInfos`|<span data-ttu-id="e2117-155">提供有关任务的说明性信息。</span><span class="sxs-lookup"><span data-stu-id="e2117-155">Provides descriptive information about the task.</span></span>|  
  
###  <a name="data-flow-task"></a><a name="DataFlow"></a> <span data-ttu-id="e2117-156">Data Flow Task</span><span class="sxs-lookup"><span data-stu-id="e2117-156">Data Flow Task</span></span>  
 <span data-ttu-id="e2117-157">下表列出了数据流任务的自定义日志项。</span><span class="sxs-lookup"><span data-stu-id="e2117-157">The following table lists the custom log entries for the Data Flow task.</span></span>  
  
|<span data-ttu-id="e2117-158">日志项</span><span class="sxs-lookup"><span data-stu-id="e2117-158">Log entry</span></span>|<span data-ttu-id="e2117-159">说明</span><span class="sxs-lookup"><span data-stu-id="e2117-159">Description</span></span>|  
|---------------|-----------------|  
|`BufferSizeTuning`|<span data-ttu-id="e2117-160">指示数据流任务更改了缓冲区的大小。</span><span class="sxs-lookup"><span data-stu-id="e2117-160">Indicates that the Data Flow task changed the size of the buffer.</span></span> <span data-ttu-id="e2117-161">日志条目描述了大小更改的原因，并列出了临时的新缓冲区大小。</span><span class="sxs-lookup"><span data-stu-id="e2117-161">The log entry describes the reasons for the size change and lists the temporary new buffer size.</span></span>|  
|`OnPipelinePostEndOfRowset`|<span data-ttu-id="e2117-162">表示组件已经给出它的行集结束信号，该信号由对 `ProcessInput` 方法的最后调用设置。</span><span class="sxs-lookup"><span data-stu-id="e2117-162">Denotes that a component has been given its end-of-rowset signal, which is set by the last call of the `ProcessInput` method.</span></span> <span data-ttu-id="e2117-163">对于数据流中处理输入的每个组件，都会写入一项。</span><span class="sxs-lookup"><span data-stu-id="e2117-163">An entry is written for each component in the data flow that processes input.</span></span> <span data-ttu-id="e2117-164">该项包括组件的名称。</span><span class="sxs-lookup"><span data-stu-id="e2117-164">The entry includes the name of the component.</span></span>|  
|`OnPipelinePostPrimeOutput`|<span data-ttu-id="e2117-165">指示组件已经完成它对 `PrimeOutput` 方法的最后一次调用。</span><span class="sxs-lookup"><span data-stu-id="e2117-165">Indicates that the component has completed its last call to the `PrimeOutput` method.</span></span> <span data-ttu-id="e2117-166">取决于数据流，可能写入多个日志条目。</span><span class="sxs-lookup"><span data-stu-id="e2117-166">Depending on the data flow, multiple log entries may be written.</span></span> <span data-ttu-id="e2117-167">如果组件是源组件，这意味着该组件已经完成对行的处理。</span><span class="sxs-lookup"><span data-stu-id="e2117-167">If the component is a source, this means that the component has finished processing rows.</span></span>|  
|`OnPipelinePreEndOfRowset`|<span data-ttu-id="e2117-168">指示组件将要接收它的行集结束信号，该信号由对 `ProcessInput` 方法的最后一次调用设置。</span><span class="sxs-lookup"><span data-stu-id="e2117-168">Indicates that a component is about to receive its end-of-rowset signal, which is set by the last call of the `ProcessInput` method.</span></span> <span data-ttu-id="e2117-169">对于数据流中处理输入的每个组件，都会写入一项。</span><span class="sxs-lookup"><span data-stu-id="e2117-169">An entry is written for each component in the data flow that processes input.</span></span> <span data-ttu-id="e2117-170">该项包括组件的名称。</span><span class="sxs-lookup"><span data-stu-id="e2117-170">The entry includes the name of the component.</span></span>|  
|`OnPipelinePrePrimeOutput`|<span data-ttu-id="e2117-171">指示组件将从 `PrimeOutput` 方法接收它的调用。</span><span class="sxs-lookup"><span data-stu-id="e2117-171">Indicates that the component is about to receive its call from the `PrimeOutput` method.</span></span> <span data-ttu-id="e2117-172">取决于数据流，可能写入多个日志条目。</span><span class="sxs-lookup"><span data-stu-id="e2117-172">Depending on the data flow, multiple log entries may be written.</span></span>|  
|`OnPipelineRowsSent`|<span data-ttu-id="e2117-173">报告对 `ProcessInput` 方法的调用为组件输入所提供的行数。</span><span class="sxs-lookup"><span data-stu-id="e2117-173">Reports the number of rows provided to a component input by a call to the `ProcessInput` method.</span></span> <span data-ttu-id="e2117-174">此日志条目包括组件名。</span><span class="sxs-lookup"><span data-stu-id="e2117-174">The log entry includes the component name.</span></span>|  
|`PipelineBufferLeak`|<span data-ttu-id="e2117-175">提供在缓冲区管理器退出之后使缓冲区保持活动状态的任何组件的相关信息。</span><span class="sxs-lookup"><span data-stu-id="e2117-175">Provides information about any component that kept buffers alive after the buffer manager goes away.</span></span> <span data-ttu-id="e2117-176">这意味着缓冲区资源未释放，并且可能导致内存泄漏。</span><span class="sxs-lookup"><span data-stu-id="e2117-176">This means that buffers resources were not released and may cause memory leaks.</span></span> <span data-ttu-id="e2117-177">日志条目提供组件的名称和缓冲区的 ID。</span><span class="sxs-lookup"><span data-stu-id="e2117-177">The log entry provides the name of the component and the ID of the buffer.</span></span>|  
|`PipelineExecutionPlan`|<span data-ttu-id="e2117-178">报告数据流的执行计划。</span><span class="sxs-lookup"><span data-stu-id="e2117-178">Reports the execution plan of the data flow.</span></span> <span data-ttu-id="e2117-179">它提供有关缓冲区将如何发送到组件的信息。</span><span class="sxs-lookup"><span data-stu-id="e2117-179">It provides information about how buffers will be sent to components.</span></span> <span data-ttu-id="e2117-180">此信息与 PipelineExecutionTrees 项组合，一起描述在任务中所发生的事情。</span><span class="sxs-lookup"><span data-stu-id="e2117-180">This information, in combination with the PipelineExecutionTrees entry, describes what is occurring in the task.</span></span>|  
|`PipelineExecutionTrees`|<span data-ttu-id="e2117-181">报告数据流中的布局的执行树。</span><span class="sxs-lookup"><span data-stu-id="e2117-181">Reports the execution trees of the layout in the data flow.</span></span> <span data-ttu-id="e2117-182">数据流引擎的计划程序使用这些树生成数据流的执行计划。</span><span class="sxs-lookup"><span data-stu-id="e2117-182">The scheduler of the data flow engine use the trees to build the execution plan of the data flow.</span></span>|  
|`PipelineInitialization`|<span data-ttu-id="e2117-183">提供有关任务的初始化信息。</span><span class="sxs-lookup"><span data-stu-id="e2117-183">Provides initialization information about the task.</span></span> <span data-ttu-id="e2117-184">此信息包括要用来临时存储 BLOB 数据、默认缓冲区大小和缓冲区行数的目录。</span><span class="sxs-lookup"><span data-stu-id="e2117-184">This information includes the directories to use for temporary storage of BLOB data, the default buffer size, and the number of rows in a buffer.</span></span> <span data-ttu-id="e2117-185">取决于数据流任务的配置，可能写入多个日志条目。</span><span class="sxs-lookup"><span data-stu-id="e2117-185">Depending on the configuration of the Data Flow task, multiple log entries may be written.</span></span>|  
  
###  <a name="execute-dts-2000-task"></a><a name="ExecuteDTS200"></a> <span data-ttu-id="e2117-186">执行 DTS 2000 任务</span><span class="sxs-lookup"><span data-stu-id="e2117-186">Execute DTS 2000 Task</span></span>  
 <span data-ttu-id="e2117-187">下表列出了执行 DTS 2000 任务的自定义日志项。</span><span class="sxs-lookup"><span data-stu-id="e2117-187">The following table lists the custom log entries for the Execute DTS 2000 task.</span></span>  
  
|<span data-ttu-id="e2117-188">日志项</span><span class="sxs-lookup"><span data-stu-id="e2117-188">Log entry</span></span>|<span data-ttu-id="e2117-189">说明</span><span class="sxs-lookup"><span data-stu-id="e2117-189">Description</span></span>|  
|---------------|-----------------|  
|`ExecuteDTS80PackageTaskBegin`|<span data-ttu-id="e2117-190">指示任务开始运行 DTS 2000 包。</span><span class="sxs-lookup"><span data-stu-id="e2117-190">Indicates that the task began to run a DTS 2000 package.</span></span>|  
|`ExecuteDTS80PackageTaskEnd`|<span data-ttu-id="e2117-191">指示任务已完成。</span><span class="sxs-lookup"><span data-stu-id="e2117-191">Indicates that the task finished.</span></span><br /><br /> <span data-ttu-id="e2117-192">注意：任务结束之后，DTS 2000 包可能继续运行。</span><span class="sxs-lookup"><span data-stu-id="e2117-192">Note: The DTS 2000 package may continue to run after the task ends.</span></span>|  
|`ExecuteDTS80PackageTaskTaskInfo`|<span data-ttu-id="e2117-193">提供有关任务的说明性信息。</span><span class="sxs-lookup"><span data-stu-id="e2117-193">Provides descriptive information about the task.</span></span>|  
|`ExecuteDTS80PackageTaskTaskResult`|<span data-ttu-id="e2117-194">报告该任务所运行的 DTS 2000 包的执行结果。</span><span class="sxs-lookup"><span data-stu-id="e2117-194">Reports the execution result of the DTS 2000 package that the task ran.</span></span>|  
  
###  <a name="execute-process-task"></a><a name="ExecuteProcess"></a> <span data-ttu-id="e2117-195">执行进程任务</span><span class="sxs-lookup"><span data-stu-id="e2117-195">Execute Process Task</span></span>  
 <span data-ttu-id="e2117-196">下表列出了执行进程任务的自定义日志项。</span><span class="sxs-lookup"><span data-stu-id="e2117-196">The following table lists the custom log entries for the Execute Process task.</span></span>  
  
|<span data-ttu-id="e2117-197">日志项</span><span class="sxs-lookup"><span data-stu-id="e2117-197">Log entry</span></span>|<span data-ttu-id="e2117-198">说明</span><span class="sxs-lookup"><span data-stu-id="e2117-198">Description</span></span>|  
|---------------|-----------------|  
|`ExecuteProcessExecutingProcess`|<span data-ttu-id="e2117-199">提供有关进程的信息，该进程运行此任务按配置要求要运行的可执行文件。</span><span class="sxs-lookup"><span data-stu-id="e2117-199">Provides information about the process of running the executable that the task is configured to run.</span></span><br /><br /> <span data-ttu-id="e2117-200">写入两个日志条目。</span><span class="sxs-lookup"><span data-stu-id="e2117-200">Two log entries are written.</span></span> <span data-ttu-id="e2117-201">一个日志项包含有关任务所运行的可执行文件的名称和位置的信息，另一个则记录从可执行文件退出的信息。</span><span class="sxs-lookup"><span data-stu-id="e2117-201">One contains information about the name and location of the executable that the task runs, and the other records the exit from the executable.</span></span>|  
|`ExecuteProcessVariableRouting`|<span data-ttu-id="e2117-202">提供有关哪些变量被路由到可执行文件的输入和输出的信息。</span><span class="sxs-lookup"><span data-stu-id="e2117-202">Provides information about which variables are routed to the input and outputs of the executable.</span></span> <span data-ttu-id="e2117-203">将为 stdin（输入）、stdout（输出）和 stderr（错误输出）写入日志条目。</span><span class="sxs-lookup"><span data-stu-id="e2117-203">Log entries are written for stdin (the input), stdout (the output), and stderr (the error output).</span></span>|  
  
###  <a name="execute-sql-task"></a><a name="ExecuteSQL"></a> <span data-ttu-id="e2117-204">执行 SQL 任务</span><span class="sxs-lookup"><span data-stu-id="e2117-204">Execute SQL Task</span></span>  
 <span data-ttu-id="e2117-205">下表介绍了执行 SQL 任务的自定义日志项。</span><span class="sxs-lookup"><span data-stu-id="e2117-205">The following table describes the custom log entry for the Execute SQL task.</span></span>  
  
|<span data-ttu-id="e2117-206">日志项</span><span class="sxs-lookup"><span data-stu-id="e2117-206">Log entry</span></span>|<span data-ttu-id="e2117-207">说明</span><span class="sxs-lookup"><span data-stu-id="e2117-207">Description</span></span>|  
|---------------|-----------------|  
|`ExecuteSQLExecutingQuery`|<span data-ttu-id="e2117-208">提供有关 SQL 语句的执行阶段的信息。</span><span class="sxs-lookup"><span data-stu-id="e2117-208">Provides information about the execution phases of the SQL statement.</span></span> <span data-ttu-id="e2117-209">在任务获得与数据库的连接时、任务开始准备 SQL 语句时以及执行完 SQL 语句之后写入日志项。</span><span class="sxs-lookup"><span data-stu-id="e2117-209">Log entries are written when the task acquires connection to the database, when the task starts to prepare the SQL statement, and after the execution of the SQL statement is completed.</span></span> <span data-ttu-id="e2117-210">准备阶段的日志条目包括任务所使用的 SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="e2117-210">The log entry for the prepare phase includes the SQL statement that the task uses.</span></span>|  
  
###  <a name="file-system-task"></a><a name="FileSystem"></a> <span data-ttu-id="e2117-211">文件系统任务</span><span class="sxs-lookup"><span data-stu-id="e2117-211">File System Task</span></span>  
 <span data-ttu-id="e2117-212">下表介绍了文件系统任务的自定义日志项。</span><span class="sxs-lookup"><span data-stu-id="e2117-212">The following table describes the custom log entry for the File System task.</span></span>  
  
|<span data-ttu-id="e2117-213">日志项</span><span class="sxs-lookup"><span data-stu-id="e2117-213">Log entry</span></span>|<span data-ttu-id="e2117-214">说明</span><span class="sxs-lookup"><span data-stu-id="e2117-214">Description</span></span>|  
|---------------|-----------------|  
|`FileSystemOperation`|<span data-ttu-id="e2117-215">报告任务所执行的操作。</span><span class="sxs-lookup"><span data-stu-id="e2117-215">Reports the operation that the task performs.</span></span> <span data-ttu-id="e2117-216">在文件系统操作开始时写入日志项，日志项包括有关源和目标的信息。</span><span class="sxs-lookup"><span data-stu-id="e2117-216">The log entry is written when the file system operation starts and includes information about the source and destination.</span></span>|  
  
###  <a name="ftp-task"></a><a name="FTP"></a> <span data-ttu-id="e2117-217">FTP 任务</span><span class="sxs-lookup"><span data-stu-id="e2117-217">FTP Task</span></span>  
 <span data-ttu-id="e2117-218">下表列出了 FTP 任务的自定义日志项。</span><span class="sxs-lookup"><span data-stu-id="e2117-218">The following table lists the custom log entries for the FTP task.</span></span>  
  
|<span data-ttu-id="e2117-219">日志项</span><span class="sxs-lookup"><span data-stu-id="e2117-219">Log entry</span></span>|<span data-ttu-id="e2117-220">说明</span><span class="sxs-lookup"><span data-stu-id="e2117-220">Description</span></span>|  
|---------------|-----------------|  
|`FTPConnectingToServer`|<span data-ttu-id="e2117-221">指示任务已启动与 FTP 服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="e2117-221">Indicates that the task initiated a connection to the FTP server.</span></span>|  
|`FTPOperation`|<span data-ttu-id="e2117-222">报告任务所执行的 FTP 操作的开始及其类型。</span><span class="sxs-lookup"><span data-stu-id="e2117-222">Reports the beginning of and the type of FTP operation that the task performs.</span></span>|  
  
###  <a name="message-queue-task"></a><a name="MessageQueue"></a> <span data-ttu-id="e2117-223">消息队列任务</span><span class="sxs-lookup"><span data-stu-id="e2117-223">Message Queue Task</span></span>  
 <span data-ttu-id="e2117-224">下表列出了消息队列任务的自定义日志项。</span><span class="sxs-lookup"><span data-stu-id="e2117-224">The following table lists the custom log entries for the Message Queue task.</span></span>  
  
|<span data-ttu-id="e2117-225">日志项</span><span class="sxs-lookup"><span data-stu-id="e2117-225">Log entry</span></span>|<span data-ttu-id="e2117-226">说明</span><span class="sxs-lookup"><span data-stu-id="e2117-226">Description</span></span>|  
|---------------|-----------------|  
|`MSMQAfterOpen`|<span data-ttu-id="e2117-227">指示任务已完成打开消息队列的操作。</span><span class="sxs-lookup"><span data-stu-id="e2117-227">Indicates that the task finished opening the message queue.</span></span>|  
|`MSMQBeforeOpen`|<span data-ttu-id="e2117-228">指示任务开始打开消息队列。</span><span class="sxs-lookup"><span data-stu-id="e2117-228">Indicates that the task began to open the message queue.</span></span>|  
|`MSMQBeginReceive`|<span data-ttu-id="e2117-229">指示任务开始接收消息。</span><span class="sxs-lookup"><span data-stu-id="e2117-229">Indicates that the task began to receive a message.</span></span>|  
|`MSMQBeginSend`|<span data-ttu-id="e2117-230">指示任务开始发送消息。</span><span class="sxs-lookup"><span data-stu-id="e2117-230">Indicates that the task began to send a message.</span></span>|  
|`MSMQEndReceive`|<span data-ttu-id="e2117-231">指示任务完成接收消息。</span><span class="sxs-lookup"><span data-stu-id="e2117-231">Indicates that the task finished receiving a message.</span></span>|  
|`MSMQEndSend`|<span data-ttu-id="e2117-232">指示任务完成发送消息的操作。</span><span class="sxs-lookup"><span data-stu-id="e2117-232">Indicates that the task finished sending a message</span></span>|  
|`MSMQTaskInfo`|<span data-ttu-id="e2117-233">提供有关任务的说明性信息。</span><span class="sxs-lookup"><span data-stu-id="e2117-233">Provides descriptive information about the task.</span></span>|  
|`MSMQTaskTimeOut`|<span data-ttu-id="e2117-234">指示任务已超时。</span><span class="sxs-lookup"><span data-stu-id="e2117-234">Indicates that the task timed out.</span></span>|  
  
###  <a name="script-task"></a><a name="Script"></a> <span data-ttu-id="e2117-235">脚本任务</span><span class="sxs-lookup"><span data-stu-id="e2117-235">Script Task</span></span>  
 <span data-ttu-id="e2117-236">下表介绍了脚本任务的自定义日志项。</span><span class="sxs-lookup"><span data-stu-id="e2117-236">The following table describes the custom log entry for the Script task.</span></span>  
  
|<span data-ttu-id="e2117-237">日志项</span><span class="sxs-lookup"><span data-stu-id="e2117-237">Log entry</span></span>|<span data-ttu-id="e2117-238">说明</span><span class="sxs-lookup"><span data-stu-id="e2117-238">Description</span></span>|  
|---------------|-----------------|  
|`ScriptTaskLogEntry`|<span data-ttu-id="e2117-239">报告在脚本中实现日志记录的结果。</span><span class="sxs-lookup"><span data-stu-id="e2117-239">Reports the results of implementing logging in the script.</span></span> <span data-ttu-id="e2117-240">在每次调用 `Log` 对象的 `Dts` 方法时将写入日志项。</span><span class="sxs-lookup"><span data-stu-id="e2117-240">A log entry is written for each call to the `Log` method of the `Dts` object.</span></span> <span data-ttu-id="e2117-241">代码运行时将写入日志项。</span><span class="sxs-lookup"><span data-stu-id="e2117-241">The entry is written when the code is run.</span></span> <span data-ttu-id="e2117-242">有关详细信息，请参阅 [Logging in the Script Task](extending-packages-scripting/task/logging-in-the-script-task.md)。</span><span class="sxs-lookup"><span data-stu-id="e2117-242">For more information, see [Logging in the Script Task](extending-packages-scripting/task/logging-in-the-script-task.md).</span></span>|  
  
###  <a name="send-mail-task"></a><a name="SendMail"></a> <span data-ttu-id="e2117-243">发送邮件任务</span><span class="sxs-lookup"><span data-stu-id="e2117-243">Send Mail Task</span></span>  
 <span data-ttu-id="e2117-244">下表列出了发送邮件任务的自定义日志项。</span><span class="sxs-lookup"><span data-stu-id="e2117-244">The following table lists the custom log entries for the Send Mail task.</span></span>  
  
|<span data-ttu-id="e2117-245">日志项</span><span class="sxs-lookup"><span data-stu-id="e2117-245">Log entry</span></span>|<span data-ttu-id="e2117-246">说明</span><span class="sxs-lookup"><span data-stu-id="e2117-246">Description</span></span>|  
|---------------|-----------------|  
|`SendMailTaskBegin`|<span data-ttu-id="e2117-247">指示任务开始发送电子邮件。</span><span class="sxs-lookup"><span data-stu-id="e2117-247">Indicates that the task began to send an e-mail message.</span></span>|  
|`SendMailTaskEnd`|<span data-ttu-id="e2117-248">指示任务已发送完电子邮件。</span><span class="sxs-lookup"><span data-stu-id="e2117-248">Indicates that the task finished sending an e-mail message.</span></span>|  
|`SendMailTaskInfo`|<span data-ttu-id="e2117-249">提供有关任务的说明性信息。</span><span class="sxs-lookup"><span data-stu-id="e2117-249">Provides descriptive information about the task.</span></span>|  
  
###  <a name="transfer-database-task"></a><a name="TransferDatabase"></a> <span data-ttu-id="e2117-250">传输数据库任务</span><span class="sxs-lookup"><span data-stu-id="e2117-250">Transfer Database Task</span></span>  
 <span data-ttu-id="e2117-251">下表列出了传输数据库任务的自定义日志项。</span><span class="sxs-lookup"><span data-stu-id="e2117-251">The following table lists the custom log entries for the Transfer Database task.</span></span>  
  
|<span data-ttu-id="e2117-252">日志项</span><span class="sxs-lookup"><span data-stu-id="e2117-252">Log entry</span></span>|<span data-ttu-id="e2117-253">说明</span><span class="sxs-lookup"><span data-stu-id="e2117-253">Description</span></span>|  
|---------------|-----------------|  
|`SourceDB`|<span data-ttu-id="e2117-254">指定任务所复制的数据库。</span><span class="sxs-lookup"><span data-stu-id="e2117-254">Specifies the database that the task copied.</span></span>|  
|`SourceSQLServer`|<span data-ttu-id="e2117-255">指定从中复制数据库的计算机。</span><span class="sxs-lookup"><span data-stu-id="e2117-255">Specifies the computer from which the database was copied.</span></span>|  
  
###  <a name="transfer-error-messages-task"></a><a name="TransferErrorMessages"></a> <span data-ttu-id="e2117-256">传输错误消息任务</span><span class="sxs-lookup"><span data-stu-id="e2117-256">Transfer Error Messages Task</span></span>  
 <span data-ttu-id="e2117-257">下表列出了传输错误消息任务的自定义日志项。</span><span class="sxs-lookup"><span data-stu-id="e2117-257">The following table lists the custom log entries for the Transfer Error Messages task.</span></span>  
  
|<span data-ttu-id="e2117-258">日志项</span><span class="sxs-lookup"><span data-stu-id="e2117-258">Log entry</span></span>|<span data-ttu-id="e2117-259">说明</span><span class="sxs-lookup"><span data-stu-id="e2117-259">Description</span></span>|  
|---------------|-----------------|  
|`TransferErrorMessagesTaskFinishedTransferringObjects`|<span data-ttu-id="e2117-260">指示任务已完成传输错误消息的操作。</span><span class="sxs-lookup"><span data-stu-id="e2117-260">Indicates that the task finished transferring error messages.</span></span>|  
|`TransferErrorMessagesTaskStartTransferringObjects`|<span data-ttu-id="e2117-261">指示任务已开始传输错误消息。</span><span class="sxs-lookup"><span data-stu-id="e2117-261">Indicates that the task started to transfer error messages.</span></span>|  
  
###  <a name="transfer-jobs-task"></a><a name="TransferJobs"></a> <span data-ttu-id="e2117-262">传输作业任务</span><span class="sxs-lookup"><span data-stu-id="e2117-262">Transfer Jobs Task</span></span>  
 <span data-ttu-id="e2117-263">下表列出传输作业任务的自定义日志项。</span><span class="sxs-lookup"><span data-stu-id="e2117-263">The following table lists the custom log entries for the Transfer Jobs task.</span></span>  
  
|<span data-ttu-id="e2117-264">日志项</span><span class="sxs-lookup"><span data-stu-id="e2117-264">Log entry</span></span>|<span data-ttu-id="e2117-265">说明</span><span class="sxs-lookup"><span data-stu-id="e2117-265">Description</span></span>|  
|---------------|-----------------|  
|`TransferJobsTaskFinishedTransferringObjects`|<span data-ttu-id="e2117-266">指示任务已完成传输 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 代理作业。</span><span class="sxs-lookup"><span data-stu-id="e2117-266">Indicates that the task finished transferring [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent jobs.</span></span>|  
|`TransferJobsTaskStartTransferringObjects`|<span data-ttu-id="e2117-267">指示任务已开始传输 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 代理作业。</span><span class="sxs-lookup"><span data-stu-id="e2117-267">Indicates that the task started to transfer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent jobs.</span></span>|  
  
###  <a name="transfer-logins-task"></a><a name="TransferLogins"></a> <span data-ttu-id="e2117-268">传输登录名任务</span><span class="sxs-lookup"><span data-stu-id="e2117-268">Transfer Logins Task</span></span>  
 <span data-ttu-id="e2117-269">下表列出了传输登录名任务的自定义日志项。</span><span class="sxs-lookup"><span data-stu-id="e2117-269">The following table lists the custom log entries for the Transfer Logins task.</span></span>  
  
|<span data-ttu-id="e2117-270">日志项</span><span class="sxs-lookup"><span data-stu-id="e2117-270">Log entry</span></span>|<span data-ttu-id="e2117-271">说明</span><span class="sxs-lookup"><span data-stu-id="e2117-271">Description</span></span>|  
|---------------|-----------------|  
|`TransferLoginsTaskFinishedTransferringObjects`|<span data-ttu-id="e2117-272">指示任务已传输完登录名。</span><span class="sxs-lookup"><span data-stu-id="e2117-272">Indicates that the task finished transferring logins.</span></span>|  
|`TransferLoginsTaskStartTransferringObjects`|<span data-ttu-id="e2117-273">指示任务已开始传输登录名。</span><span class="sxs-lookup"><span data-stu-id="e2117-273">Indicates that the task started to transfer logins.</span></span>|  
  
###  <a name="transfer-master-stored-procedures-task"></a><a name="TransferMasterStoredProcedures"></a> <span data-ttu-id="e2117-274">传输主存储过程任务</span><span class="sxs-lookup"><span data-stu-id="e2117-274">Transfer Master Stored Procedures Task</span></span>  
 <span data-ttu-id="e2117-275">下表列出可传输主存储过程任务的自定义日志项。</span><span class="sxs-lookup"><span data-stu-id="e2117-275">The following table lists the custom log entries for the Transfer Master Stored Procedures task.</span></span>  
  
|<span data-ttu-id="e2117-276">日志项</span><span class="sxs-lookup"><span data-stu-id="e2117-276">Log entry</span></span>|<span data-ttu-id="e2117-277">说明</span><span class="sxs-lookup"><span data-stu-id="e2117-277">Description</span></span>|  
|---------------|-----------------|  
|`TransferStoredProceduresTaskFinishedTransferringObjects`|<span data-ttu-id="e2117-278">指示任务已传输完在 **master** 数据库中存储的用户定义的存储过程。</span><span class="sxs-lookup"><span data-stu-id="e2117-278">Indicates that the task finished transferring user-defined stored procedures that are stored in the **master** database.</span></span>|  
|`TransferStoredProceduresTaskStartTransferringObjects`|<span data-ttu-id="e2117-279">指示任务已开始传输 **master** 数据库中存储的用户定义的存储过程。</span><span class="sxs-lookup"><span data-stu-id="e2117-279">Indicates that the task started to transfer user-defined stored procedures that are stored in the **master** database.</span></span>|  
  
###  <a name="transfer-sql-server-objects-task"></a><a name="TransferSQLServerObjects"></a> <span data-ttu-id="e2117-280">传输 SQL Server 对象任务</span><span class="sxs-lookup"><span data-stu-id="e2117-280">Transfer SQL Server Objects Task</span></span>  
 <span data-ttu-id="e2117-281">下表列出了传输 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 对象任务的自定义日志项。</span><span class="sxs-lookup"><span data-stu-id="e2117-281">The following table lists the custom log entries for the Transfer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Objects task.</span></span>  
  
|<span data-ttu-id="e2117-282">日志项</span><span class="sxs-lookup"><span data-stu-id="e2117-282">Log entry</span></span>|<span data-ttu-id="e2117-283">说明</span><span class="sxs-lookup"><span data-stu-id="e2117-283">Description</span></span>|  
|---------------|-----------------|  
|`TransferSqlServerObjectsTaskFinishedTransferringObjects`|<span data-ttu-id="e2117-284">指示任务已完成传输 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 数据库对象。</span><span class="sxs-lookup"><span data-stu-id="e2117-284">Indicates that the task finished transferring [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database objects.</span></span>|  
|`TransferSqlServerObjectsTaskStartTransferringObjects`|<span data-ttu-id="e2117-285">指示任务已开始传输 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 数据库对象。</span><span class="sxs-lookup"><span data-stu-id="e2117-285">Indicates that the task started to transfer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database objects.</span></span>|  
  
###  <a name="web-services-task"></a><a name="WebServices"></a> <span data-ttu-id="e2117-286">Web 服务任务</span><span class="sxs-lookup"><span data-stu-id="e2117-286">Web Services Task</span></span>  
 <span data-ttu-id="e2117-287">下表列出了可以为 Web 服务任务启用的自定义日志项。</span><span class="sxs-lookup"><span data-stu-id="e2117-287">The following table lists the custom log entries that you can enable for the Web Services task.</span></span>  
  
|<span data-ttu-id="e2117-288">日志项</span><span class="sxs-lookup"><span data-stu-id="e2117-288">Log entry</span></span>|<span data-ttu-id="e2117-289">说明</span><span class="sxs-lookup"><span data-stu-id="e2117-289">Description</span></span>|  
|---------------|-----------------|  
|`WSTaskBegin`|<span data-ttu-id="e2117-290">任务已开始访问 Web 服务。</span><span class="sxs-lookup"><span data-stu-id="e2117-290">The task began to access a Web service.</span></span>|  
|`WSTaskEnd`|<span data-ttu-id="e2117-291">任务已完成 Web 服务方法。</span><span class="sxs-lookup"><span data-stu-id="e2117-291">The task completed a Web service method.</span></span>|  
|`WSTaskInfo`|<span data-ttu-id="e2117-292">有关任务的说明性信息。</span><span class="sxs-lookup"><span data-stu-id="e2117-292">Descriptive information about the task.</span></span>|  
  
###  <a name="wmi-data-reader-task"></a><a name="WMIDataReader"></a> <span data-ttu-id="e2117-293">WMI 数据读取器任务</span><span class="sxs-lookup"><span data-stu-id="e2117-293">WMI Data Reader Task</span></span>  
 <span data-ttu-id="e2117-294">下表列出了 WMI 数据读取器任务的自定义日志项。</span><span class="sxs-lookup"><span data-stu-id="e2117-294">The following table lists the custom log entries for the WMI Data Reader task.</span></span>  
  
|<span data-ttu-id="e2117-295">日志项</span><span class="sxs-lookup"><span data-stu-id="e2117-295">Log entry</span></span>|<span data-ttu-id="e2117-296">说明</span><span class="sxs-lookup"><span data-stu-id="e2117-296">Description</span></span>|  
|---------------|-----------------|  
|`WMIDataReaderGettingWMIData`|<span data-ttu-id="e2117-297">指示任务已开始读取 WMI 数据。</span><span class="sxs-lookup"><span data-stu-id="e2117-297">Indicates that the task began to read WMI data.</span></span>|  
|`WMIDataReaderOperation`|<span data-ttu-id="e2117-298">报告任务所运行的 WQL 查询。</span><span class="sxs-lookup"><span data-stu-id="e2117-298">Reports the WQL query that the task ran.</span></span>|  
  
###  <a name="wmi-event-watcher-task"></a><a name="WMIEventWatcher"></a> <span data-ttu-id="e2117-299">WMI 事件观察器任务</span><span class="sxs-lookup"><span data-stu-id="e2117-299">WMI Event Watcher Task</span></span>  
 <span data-ttu-id="e2117-300">下表列出了 WMI 事件观察器任务的自定义日志项。</span><span class="sxs-lookup"><span data-stu-id="e2117-300">The following table lists the custom log entries for the WMI Event Watcher task.</span></span>  
  
|<span data-ttu-id="e2117-301">日志项</span><span class="sxs-lookup"><span data-stu-id="e2117-301">Log entry</span></span>|<span data-ttu-id="e2117-302">说明</span><span class="sxs-lookup"><span data-stu-id="e2117-302">Description</span></span>|  
|---------------|-----------------|  
|`WMIEventWatcherEventOccurred`|<span data-ttu-id="e2117-303">表示发生了任务正在监视的事件。</span><span class="sxs-lookup"><span data-stu-id="e2117-303">Denotes that the event occurred that the task was monitoring.</span></span>|  
|`WMIEventWatcherTimedout`|<span data-ttu-id="e2117-304">指示任务已超时。</span><span class="sxs-lookup"><span data-stu-id="e2117-304">Indicates that the task timed out.</span></span>|  
|`WMIEventWatcherWatchingForWMIEvents`|<span data-ttu-id="e2117-305">指示任务已开始执行 WQL 查询。</span><span class="sxs-lookup"><span data-stu-id="e2117-305">Indicates that the task began to execute the WQL query.</span></span> <span data-ttu-id="e2117-306">日志项包括查询。</span><span class="sxs-lookup"><span data-stu-id="e2117-306">The entry includes the query.</span></span>|  
  
###  <a name="xml-task"></a><a name="XML"></a> <span data-ttu-id="e2117-307">XML 任务</span><span class="sxs-lookup"><span data-stu-id="e2117-307">XML Task</span></span>  
 <span data-ttu-id="e2117-308">下表介绍了 XML 任务的自定义日志项。</span><span class="sxs-lookup"><span data-stu-id="e2117-308">The following table describes the custom log entry for the XML task.</span></span>  
  
|<span data-ttu-id="e2117-309">日志项</span><span class="sxs-lookup"><span data-stu-id="e2117-309">Log entry</span></span>|<span data-ttu-id="e2117-310">说明</span><span class="sxs-lookup"><span data-stu-id="e2117-310">Description</span></span>|  
|---------------|-----------------|  
|`XMLOperation`|<span data-ttu-id="e2117-311">提供任务所执行的操作的相关信息</span><span class="sxs-lookup"><span data-stu-id="e2117-311">Provides information about the operation that the task performs</span></span>|   
  
## <a name="see-also"></a><span data-ttu-id="e2117-312">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e2117-312">See Also</span></span>  
 [<span data-ttu-id="e2117-313">Integration Services (SSIS) 日志记录</span><span class="sxs-lookup"><span data-stu-id="e2117-313">Integration Services &#40;SSIS&#41; Logging</span></span>](performance/integration-services-ssis-logging.md)  
  
