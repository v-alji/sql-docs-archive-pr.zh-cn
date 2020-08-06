---
title: Windows 事件跟踪目标 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xevents
ms.topic: conceptual
helpviewer_keywords:
- event tracing for windows target
- ETW target
- targets [SQL Server extended events], event tracing for windows target
ms.assetid: ca2bb295-b7f6-49c3-91ed-0ad4c39f89d5
author: rothja
ms.author: jroth
ms.openlocfilehash: 55f247af30b5278f614b6505a94266cc07ec6c54
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578216"
---
# <a name="event-tracing-for-windows-target"></a><span data-ttu-id="6be87-102">Windows 事件跟踪目标</span><span class="sxs-lookup"><span data-stu-id="6be87-102">Event Tracing for Windows Target</span></span>
  <span data-ttu-id="6be87-103">在将 Windows 事件跟踪 (ETW) 作为目标使用前，建议您先掌握 ETW 的相关使用知识。</span><span class="sxs-lookup"><span data-stu-id="6be87-103">Before you use Event Tracing for Windows (ETW) as a target, we recommend that you have a working knowledge of ETW.</span></span> <span data-ttu-id="6be87-104">ETW 跟踪或者与扩展事件结合使用，或者用作扩展事件的事件使用者。</span><span class="sxs-lookup"><span data-stu-id="6be87-104">ETW tracing is either used together with Extended Events or as an Extended Events event consumer.</span></span> <span data-ttu-id="6be87-105">您可以从以下外部链接入手，获取有关 ETW 的背景信息：</span><span class="sxs-lookup"><span data-stu-id="6be87-105">The following external links provide a starting point for obtaining background information about ETW:</span></span>  
  
-   [<span data-ttu-id="6be87-106">Windows 事件</span><span class="sxs-lookup"><span data-stu-id="6be87-106">Windows Events</span></span>](https://go.microsoft.com/fwlink/?LinkId=92380)  
  
-   [<span data-ttu-id="6be87-107">使用 ETW 改善调试和性能优化</span><span class="sxs-lookup"><span data-stu-id="6be87-107">Improve Debugging And Performance Tuning With ETW</span></span>](https://go.microsoft.com/fwlink/?LinkId=92381)  
  
 <span data-ttu-id="6be87-108">ETW 目标是单独目标，尽管该目标可以被添加到多个会话中。</span><span class="sxs-lookup"><span data-stu-id="6be87-108">The ETW target is a singleton target, although the target can be added to many sessions.</span></span> <span data-ttu-id="6be87-109">如果某事件在多个会话中被引发，则该事件在每次发生事件时仅被传播给 ETW 目标一次。</span><span class="sxs-lookup"><span data-stu-id="6be87-109">If an event is raised on many sessions, the event will only be propagated to the ETW target one time per event occurrence.</span></span> <span data-ttu-id="6be87-110">每个进程仅限一个扩展事件引擎实例。</span><span class="sxs-lookup"><span data-stu-id="6be87-110">The Extended Events engine is limited to a single instance per process.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="6be87-111">为使 ETW 目标能够工作， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务启动帐户必须是性能日志用户组的成员。</span><span class="sxs-lookup"><span data-stu-id="6be87-111">For the ETW target to work, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Service startup account must be a member of the Performance Log Users group.</span></span>  
  
 <span data-ttu-id="6be87-112">对于 ETW 会话中存在的事件，其配置由承载扩展事件引擎的进程来控制。</span><span class="sxs-lookup"><span data-stu-id="6be87-112">The configuration of the events present in an ETW session is controlled by the process that hosts the Extended Events engine.</span></span> <span data-ttu-id="6be87-113">该引擎控制着引发哪些事件，以及必须满足哪些条件才能引发事件。</span><span class="sxs-lookup"><span data-stu-id="6be87-113">The engine controls which events to raise and what conditions must be met for an event to occur.</span></span>  
  
 <span data-ttu-id="6be87-114">在绑定到扩展事件会话之后，即在进程的生存期中首次附加 ETW 目标之后，ETW 目标会在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 访问接口上打开一个单独的 ETW 会话。</span><span class="sxs-lookup"><span data-stu-id="6be87-114">After binding to an Extended Events session, which attaches the ETW target for the first time during the lifetime of a process, the ETW target opens a single ETW session on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider.</span></span> <span data-ttu-id="6be87-115">如果已经存在 ETW 会话，ETW 目标将获取对现有会话的引用。</span><span class="sxs-lookup"><span data-stu-id="6be87-115">If an ETW session already exists, the ETW target obtains a reference to the existing session.</span></span> <span data-ttu-id="6be87-116">此 ETW 会话由给定计算机上的所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例共享，</span><span class="sxs-lookup"><span data-stu-id="6be87-116">This ETW session is shared across all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances on a given computer.</span></span> <span data-ttu-id="6be87-117">并从具有此 ETW 目标的会话接收所有事件。</span><span class="sxs-lookup"><span data-stu-id="6be87-117">This ETW session receives all the events from sessions that have the ETW target.</span></span>  
  
 <span data-ttu-id="6be87-118">由于 ETW 需要启用访问接口才能使用事件并将事件发送给 ETW 会话，因而对此会话启用所有扩展事件包。</span><span class="sxs-lookup"><span data-stu-id="6be87-118">Because ETW needs providers to be enabled to consume events and flow them down to the ETW, all Extended Events packages are enabled on the session.</span></span> <span data-ttu-id="6be87-119">激发事件后，ETW 目标将事件发送给对其启用了事件访问接口的会话。</span><span class="sxs-lookup"><span data-stu-id="6be87-119">When an event is fired, the ETW target sends the event to the session on which the provider for the event is enabled.</span></span>  
  
 <span data-ttu-id="6be87-120">ETW 目标支持对引发事件的线程同步发布事件。</span><span class="sxs-lookup"><span data-stu-id="6be87-120">The ETW target supports synchronous publishing of events on the thread that raises the event.</span></span> <span data-ttu-id="6be87-121">但是，ETW 目标不支持异步事件发布。</span><span class="sxs-lookup"><span data-stu-id="6be87-121">However, the ETW target does not support asynchronous event publishing.</span></span>  
  
 <span data-ttu-id="6be87-122">ETW 目标不支持来自外部 ETW 控制器（例如 Logman.exe）的控制。</span><span class="sxs-lookup"><span data-stu-id="6be87-122">The ETW target does not support control from external ETW controllers such as Logman.exe.</span></span> <span data-ttu-id="6be87-123">若要生成 ETW 跟踪，必须使用 ETW 目标创建事件会话。</span><span class="sxs-lookup"><span data-stu-id="6be87-123">To produce ETW traces, an event session must be created with the ETW target.</span></span> <span data-ttu-id="6be87-124">有关详细信息，请参阅 [CREATE EVENT SESSION (Transact-SQL)](/sql/t-sql/statements/create-event-session-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="6be87-124">For more information, see [CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6be87-125">启用 ETW 目标将创建一个名为 XE_DEFAULT_ETW_SESSION 的 ETW 会话。</span><span class="sxs-lookup"><span data-stu-id="6be87-125">Enabling the ETW target creates an ETW session that is named XE_DEFAULT_ETW_SESSION.</span></span> <span data-ttu-id="6be87-126">如果名为 XE_DEFAULT_ETW_SESSION 的会话已经存在，则使用该会话而不修改现有会话的任何属性。</span><span class="sxs-lookup"><span data-stu-id="6be87-126">If a session with the name XE_DEFAULT_ETW_SESSION already exists, it is used without modifying any properties of the existing session.</span></span> <span data-ttu-id="6be87-127">XE_DEFAULT_ETW_SESSION 由所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例共享。</span><span class="sxs-lookup"><span data-stu-id="6be87-127">The XE_DEFAULT_ETW_SESSION is shared between all instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="6be87-128">启动了 XE_DEFAULT_ETW_SESSION 后，必须使用 ETW 控制器（如 Logman 工具）停止它。</span><span class="sxs-lookup"><span data-stu-id="6be87-128">After you start the XE_DEFAULT_ETW_SESSION, you must stop it by using an ETW controller, such as the Logman tool.</span></span> <span data-ttu-id="6be87-129">例如，可在命令提示符下运行以下命令：`logman stop XE_DEFAULT_ETW_SESSION -ets`。</span><span class="sxs-lookup"><span data-stu-id="6be87-129">For example, you can run the following command at the command prompt: `logman stop XE_DEFAULT_ETW_SESSION -ets`.</span></span>  
  
 <span data-ttu-id="6be87-130">下表介绍了配置 ETW 目标时可用的选项。</span><span class="sxs-lookup"><span data-stu-id="6be87-130">The following table describes the available options for configuring the ETW target.</span></span>  
  
|<span data-ttu-id="6be87-131">选项</span><span class="sxs-lookup"><span data-stu-id="6be87-131">Option</span></span>|<span data-ttu-id="6be87-132">允许的值</span><span class="sxs-lookup"><span data-stu-id="6be87-132">Allowed values</span></span>|<span data-ttu-id="6be87-133">说明</span><span class="sxs-lookup"><span data-stu-id="6be87-133">Description</span></span>|  
|------------|--------------------|-----------------|  
|<span data-ttu-id="6be87-134">default_xe_session_name</span><span class="sxs-lookup"><span data-stu-id="6be87-134">default_xe_session_name</span></span>|<span data-ttu-id="6be87-135">任何不超过 256 个字符的字符串。</span><span class="sxs-lookup"><span data-stu-id="6be87-135">Any string up to 256 characters.</span></span> <span data-ttu-id="6be87-136">此值是可选的。</span><span class="sxs-lookup"><span data-stu-id="6be87-136">This value is optional.</span></span>|<span data-ttu-id="6be87-137">扩展事件会话名称。</span><span class="sxs-lookup"><span data-stu-id="6be87-137">The Extended Events session name.</span></span> <span data-ttu-id="6be87-138">默认情况下为 XE_DEFAULT_ETW_SESSION。</span><span class="sxs-lookup"><span data-stu-id="6be87-138">By default, this is XE_DEFAULT_ETW_SESSION.</span></span>|  
|<span data-ttu-id="6be87-139">default_etw_session_logfile_path</span><span class="sxs-lookup"><span data-stu-id="6be87-139">default_etw_session_logfile_path</span></span>|<span data-ttu-id="6be87-140">任何不超过 256 个字符的字符串。</span><span class="sxs-lookup"><span data-stu-id="6be87-140">Any string up to 256 characters.</span></span> <span data-ttu-id="6be87-141">此值是可选的。</span><span class="sxs-lookup"><span data-stu-id="6be87-141">This value is optional.</span></span>|<span data-ttu-id="6be87-142">扩展事件会话日志文件的路径。</span><span class="sxs-lookup"><span data-stu-id="6be87-142">The path of the log file for the Extended Events session.</span></span> <span data-ttu-id="6be87-143">默认情况下为 %TEMP%\ XEEtw.etl。</span><span class="sxs-lookup"><span data-stu-id="6be87-143">By default, this is %TEMP%\ XEEtw.etl.</span></span>|  
|<span data-ttu-id="6be87-144">default_etw_session_logfile_size_mb</span><span class="sxs-lookup"><span data-stu-id="6be87-144">default_etw_session_logfile_size_mb</span></span>|<span data-ttu-id="6be87-145">任何无符号整数。</span><span class="sxs-lookup"><span data-stu-id="6be87-145">Any unsigned integer.</span></span> <span data-ttu-id="6be87-146">此值是可选的。</span><span class="sxs-lookup"><span data-stu-id="6be87-146">This value is optional.</span></span>|<span data-ttu-id="6be87-147">扩展事件会话日志文件的大小 (MB)。</span><span class="sxs-lookup"><span data-stu-id="6be87-147">The log file size, in megabytes (MB), for the Extended Events session.</span></span> <span data-ttu-id="6be87-148">默认值为 20 MB。</span><span class="sxs-lookup"><span data-stu-id="6be87-148">The default is 20 MB.</span></span>|  
|<span data-ttu-id="6be87-149">default_etw_session_buffer_size_kb</span><span class="sxs-lookup"><span data-stu-id="6be87-149">default_etw_session_buffer_size_kb</span></span>|<span data-ttu-id="6be87-150">任何无符号整数。</span><span class="sxs-lookup"><span data-stu-id="6be87-150">Any unsigned integer.</span></span> <span data-ttu-id="6be87-151">此值是可选的。</span><span class="sxs-lookup"><span data-stu-id="6be87-151">This value is optional.</span></span>|<span data-ttu-id="6be87-152">扩展事件会话内存缓冲区的大小 (KB)。</span><span class="sxs-lookup"><span data-stu-id="6be87-152">The in-memory buffer size, in kilobytes (KB), for the Extended Events session.</span></span> <span data-ttu-id="6be87-153">默认值为 128 KB。</span><span class="sxs-lookup"><span data-stu-id="6be87-153">The default is 128 KB.</span></span>|  
|<span data-ttu-id="6be87-154">retries</span><span class="sxs-lookup"><span data-stu-id="6be87-154">retries</span></span>|<span data-ttu-id="6be87-155">任何无符号整数。</span><span class="sxs-lookup"><span data-stu-id="6be87-155">Any unsigned integer.</span></span>|<span data-ttu-id="6be87-156">尝试将事件发布给 ETW 子系统的重试次数，在此次数之后将删除该事件。</span><span class="sxs-lookup"><span data-stu-id="6be87-156">The number of times to retry publishing the event to the ETW subsystem before dropping the event.</span></span> <span data-ttu-id="6be87-157">默认值为 0。</span><span class="sxs-lookup"><span data-stu-id="6be87-157">The default is 0.</span></span>|  
  
 <span data-ttu-id="6be87-158">这些设置的配置是可选的。</span><span class="sxs-lookup"><span data-stu-id="6be87-158">Configuring these settings is optional.</span></span> <span data-ttu-id="6be87-159">ETW 目标使用这些设置的默认值。</span><span class="sxs-lookup"><span data-stu-id="6be87-159">The ETW target uses default values for these settings.</span></span>  
  
 <span data-ttu-id="6be87-160">ETW 目标负责下列操作：</span><span class="sxs-lookup"><span data-stu-id="6be87-160">The ETW target is responsible for:</span></span>  
  
-   <span data-ttu-id="6be87-161">创建默认的 ETW 会话。</span><span class="sxs-lookup"><span data-stu-id="6be87-161">Creating the default ETW session.</span></span>  
  
-   <span data-ttu-id="6be87-162">向 ETW 注册所有扩展事件包。</span><span class="sxs-lookup"><span data-stu-id="6be87-162">Registering all Extended Events packages with ETW.</span></span> <span data-ttu-id="6be87-163">这样可以确保 ETW 不会删除事件。</span><span class="sxs-lookup"><span data-stu-id="6be87-163">This ensures that events are not dropped by ETW.</span></span>  
  
-   <span data-ttu-id="6be87-164">管理事件向 ETW 的发送。</span><span class="sxs-lookup"><span data-stu-id="6be87-164">Managing the flow of events to ETW.</span></span> <span data-ttu-id="6be87-165">ETW 目标使用扩展事件数据创建 ETW 事件并将其发送给相应的 ETW 会话。</span><span class="sxs-lookup"><span data-stu-id="6be87-165">The ETW target creates an ETW event with Extended Events data and sends it to the appropriate ETW session.</span></span> <span data-ttu-id="6be87-166">如果事件的大小超过缓冲区的大小，或数据无法容纳到一个 ETW 事件中，则 ETW 将把事件拆分成几个片段。</span><span class="sxs-lookup"><span data-stu-id="6be87-166">If the event is larger than the buffer size, or data cannot fit in one ETW event, ETW splits the event into fragments.</span></span>  
  
-   <span data-ttu-id="6be87-167">使扩展事件包在任何时候均保持为启用状态。</span><span class="sxs-lookup"><span data-stu-id="6be87-167">Keeping Extended Events packages enabled at all times.</span></span>  
  
 <span data-ttu-id="6be87-168">ETW 使用以下默认文件位置：</span><span class="sxs-lookup"><span data-stu-id="6be87-168">The following default file locations are used by ETW:</span></span>  
  
-   <span data-ttu-id="6be87-169">ETW 输出文件的格式为 %TEMP%\XEEtw.etl。</span><span class="sxs-lookup"><span data-stu-id="6be87-169">The ETW output file is in %TEMP%\XEEtw.etl.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="6be87-170">当第一个会话启动后不能再更改该文件路径。</span><span class="sxs-lookup"><span data-stu-id="6be87-170">The file path cannot be changed after the first session starts.</span></span>  
  
-   <span data-ttu-id="6be87-171">托管对象格式 (MOF) 文件位于 \<your install path>\Microsoft SQL Server\Shared。</span><span class="sxs-lookup"><span data-stu-id="6be87-171">Managed Object Format (MOF) files are in *\<your install path>* \Microsoft SQL Server\Shared.</span></span> <span data-ttu-id="6be87-172">有关详细信息，请参阅 MSDN 上的 [托管对象格式](https://go.microsoft.com/fwlink/?LinkId=92851) 。</span><span class="sxs-lookup"><span data-stu-id="6be87-172">For more information, see [Managed Object Format](https://go.microsoft.com/fwlink/?LinkId=92851) on MSDN.</span></span>  
  
## <a name="adding-the-target-to-a-session"></a><span data-ttu-id="6be87-173">将目标添加到会话</span><span class="sxs-lookup"><span data-stu-id="6be87-173">Adding the Target to a Session</span></span>  
 <span data-ttu-id="6be87-174">若要将 ETW 目标添加到扩展事件会话中，您必须在创建或更改事件会话时包括下面的语句：</span><span class="sxs-lookup"><span data-stu-id="6be87-174">To add the ETW target to an Extended Events session, you must include the following statement when you create or alter an event session:</span></span>  
  
```  
ADD TARGET package0.etw_classic_sync_target  
```  
  
 <span data-ttu-id="6be87-175">有关说明如何使用 ETW 目标的完整示例的详细信息（包括如何查看数据），请参阅 [使用扩展事件监视系统活动](monitor-system-activity-using-extended-events.md)。</span><span class="sxs-lookup"><span data-stu-id="6be87-175">For more information about a full example that shows how to use the ETW target, including how to view the data, see [Monitor System Activity Using Extended Events](monitor-system-activity-using-extended-events.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6be87-176">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6be87-176">See Also</span></span>  
 <span data-ttu-id="6be87-177">[SQL Server 扩展事件目标](../../database-engine/sql-server-extended-events-targets.md) </span><span class="sxs-lookup"><span data-stu-id="6be87-177">[SQL Server Extended Events Targets](../../database-engine/sql-server-extended-events-targets.md) </span></span>  
 <span data-ttu-id="6be87-178">[sys.dm_xe_session_targets (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-targets-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6be87-178">[sys.dm_xe_session_targets &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-targets-transact-sql) </span></span>  
 <span data-ttu-id="6be87-179">[CREATE EVENT SESSION (Transact-SQL)](/sql/t-sql/statements/create-event-session-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6be87-179">[CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql) </span></span>  
 [<span data-ttu-id="6be87-180">ALTER EVENT SESSION (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="6be87-180">ALTER EVENT SESSION &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-event-session-transact-sql)  
  
  
