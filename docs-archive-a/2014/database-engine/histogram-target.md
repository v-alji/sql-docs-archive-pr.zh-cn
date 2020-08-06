---
title: 直方图目标 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- bucketing target [SQL Server extended events]
- event bucketing target
- targets [SQL Server extended events], bucketing
ms.assetid: 2ea39141-7eb0-4c74-abf8-114c2c106a19
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: acb124ef949849561a6bca0ba4016b40c1343384
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689579"
---
# <a name="histogram-target"></a><span data-ttu-id="2bec6-102">直方图目标</span><span class="sxs-lookup"><span data-stu-id="2bec6-102">Histogram Target</span></span>
  <span data-ttu-id="2bec6-103">直方图目标基于事件数据对发生的特定事件类型进行分组。</span><span class="sxs-lookup"><span data-stu-id="2bec6-103">The histogram target groups occurrences of a specific event type based on event data.</span></span> <span data-ttu-id="2bec6-104">事件的分组是基于指定的事件列或操作进行计数的。</span><span class="sxs-lookup"><span data-stu-id="2bec6-104">The groupings of events are counted based on a specified event column or action.</span></span> <span data-ttu-id="2bec6-105">您可以使用直方图目标来排除性能问题。</span><span class="sxs-lookup"><span data-stu-id="2bec6-105">You can use the histogram target to troubleshoot performance issues.</span></span> <span data-ttu-id="2bec6-106">通过标识哪些事件发生的频率最高，您就可以找到可能引起性能问题的“作用点”。</span><span class="sxs-lookup"><span data-stu-id="2bec6-106">By identifying which events are occurring most frequently, you can find "hotspots" that indicate a potential cause of a performance problem.</span></span>  
  
 <span data-ttu-id="2bec6-107">下表描述了可用于配置直方图目标的选项。</span><span class="sxs-lookup"><span data-stu-id="2bec6-107">The following table describes the options that can be used to configure the histogram target.</span></span>  
  
|<span data-ttu-id="2bec6-108">选项</span><span class="sxs-lookup"><span data-stu-id="2bec6-108">Option</span></span>|<span data-ttu-id="2bec6-109">允许的值</span><span class="sxs-lookup"><span data-stu-id="2bec6-109">Allowed values</span></span>|<span data-ttu-id="2bec6-110">说明</span><span class="sxs-lookup"><span data-stu-id="2bec6-110">Description</span></span>|  
|------------|--------------------|-----------------|  
|<span data-ttu-id="2bec6-111">slots</span><span class="sxs-lookup"><span data-stu-id="2bec6-111">slots</span></span>|<span data-ttu-id="2bec6-112">任何整数值。</span><span class="sxs-lookup"><span data-stu-id="2bec6-112">Any integer value.</span></span> <span data-ttu-id="2bec6-113">此值是可选的。</span><span class="sxs-lookup"><span data-stu-id="2bec6-113">This value is optional.</span></span>|<span data-ttu-id="2bec6-114">用户指定值，指示要保留的分组的最大数目。</span><span class="sxs-lookup"><span data-stu-id="2bec6-114">A user-specified value indicating the maximum number of groupings to retain.</span></span> <span data-ttu-id="2bec6-115">达到此值后，将忽略那些不属于现有组的新事件。</span><span class="sxs-lookup"><span data-stu-id="2bec6-115">When this value is reached, new events that do not belong to the existing groups are ignored.</span></span><br /><br /> <span data-ttu-id="2bec6-116">请注意，为了提高性能，槽号将向上舍入到最近的 2 次幂。</span><span class="sxs-lookup"><span data-stu-id="2bec6-116">Note that to improve performance, the slot number is rounded up to the next power of 2.</span></span>|  
|<span data-ttu-id="2bec6-117">filtering_event_name</span><span class="sxs-lookup"><span data-stu-id="2bec6-117">filtering_event_name</span></span>|<span data-ttu-id="2bec6-118">扩展事件会话中存在的任何事件。</span><span class="sxs-lookup"><span data-stu-id="2bec6-118">Any event present in the Extended Events session.</span></span> <span data-ttu-id="2bec6-119">此值是可选的。</span><span class="sxs-lookup"><span data-stu-id="2bec6-119">This value is optional.</span></span>|<span data-ttu-id="2bec6-120">用于标识事件类的用户指定值。</span><span class="sxs-lookup"><span data-stu-id="2bec6-120">A user-specified value that is used to identify a class of events.</span></span> <span data-ttu-id="2bec6-121">只有指定事件实例才会存储在桶中。</span><span class="sxs-lookup"><span data-stu-id="2bec6-121">Only instances of the specified event are bucketed.</span></span> <span data-ttu-id="2bec6-122">所有其他事件都被忽略。</span><span class="sxs-lookup"><span data-stu-id="2bec6-122">All other events are ignored.</span></span><br /><br /> <span data-ttu-id="2bec6-123">如果指定此值，则必须使用以下格式： *package_name*.*event_name*，例如 `'sqlserver.checkpoint_end'`。</span><span class="sxs-lookup"><span data-stu-id="2bec6-123">If you specify this value, you must use the format: *package_name*.*event_name*, for example `'sqlserver.checkpoint_end'`.</span></span> <span data-ttu-id="2bec6-124">使用以下查询可以标识包名称：</span><span class="sxs-lookup"><span data-stu-id="2bec6-124">You can identify the package name by using the following query:</span></span><br /><br /> <span data-ttu-id="2bec6-125">选择 p.name event_name</span><span class="sxs-lookup"><span data-stu-id="2bec6-125">SELECT p.name, se.event_name</span></span><br /><span data-ttu-id="2bec6-126">从 sys.databases dm_xe_session_events se</span><span class="sxs-lookup"><span data-stu-id="2bec6-126">FROM sys.dm_xe_session_events se</span></span><br /><span data-ttu-id="2bec6-127">联接 sys.databases dm_xe_packages p</span><span class="sxs-lookup"><span data-stu-id="2bec6-127">JOIN sys.dm_xe_packages p</span></span><br /><span data-ttu-id="2bec6-128">在 se_event_package_guid = p. guid</span><span class="sxs-lookup"><span data-stu-id="2bec6-128">ON se_event_package_guid = p.guid</span></span><br /><span data-ttu-id="2bec6-129">ORDER BY p.name，event_name</span><span class="sxs-lookup"><span data-stu-id="2bec6-129">ORDER BY p.name, se.event_name</span></span><br /><br /> <br /><br /> <span data-ttu-id="2bec6-130">如果不指定 filtering_event_name 值，则必须将 source_type 设为 1（默认值）。</span><span class="sxs-lookup"><span data-stu-id="2bec6-130">If you do not specify the filtering_event_name value, source_type must be set to 1 (the default).</span></span>|  
|<span data-ttu-id="2bec6-131">source_type</span><span class="sxs-lookup"><span data-stu-id="2bec6-131">source_type</span></span>|<span data-ttu-id="2bec6-132">存储桶基于的对象的类型。</span><span class="sxs-lookup"><span data-stu-id="2bec6-132">The type of object that the bucket is based on.</span></span> <span data-ttu-id="2bec6-133">该值是可选的，如果未指定值，则使用默认值 1。</span><span class="sxs-lookup"><span data-stu-id="2bec6-133">This value is optional and if not specified has a default value of 1.</span></span>|<span data-ttu-id="2bec6-134">可以是下列值之一：</span><span class="sxs-lookup"><span data-stu-id="2bec6-134">Can have one of the following values:</span></span><br /><br /> <span data-ttu-id="2bec6-135">0 = 事件</span><span class="sxs-lookup"><span data-stu-id="2bec6-135">0 for an event</span></span><br /><br /> <span data-ttu-id="2bec6-136">1 = 操作</span><span class="sxs-lookup"><span data-stu-id="2bec6-136">1 for an action</span></span>|  
|<span data-ttu-id="2bec6-137">source</span><span class="sxs-lookup"><span data-stu-id="2bec6-137">source</span></span>|<span data-ttu-id="2bec6-138">事件列或操作名称。</span><span class="sxs-lookup"><span data-stu-id="2bec6-138">Event column or action name.</span></span>|<span data-ttu-id="2bec6-139">用作数据源的事件列或操作名称。</span><span class="sxs-lookup"><span data-stu-id="2bec6-139">The event column or action name that is used as the data source.</span></span><br /><br /> <span data-ttu-id="2bec6-140">当为源指定事件列时，必须从用作 filtering_event_name 值的事件中指定列。</span><span class="sxs-lookup"><span data-stu-id="2bec6-140">When you specify an event column for source, you must specify a column from the event that is used for the filtering_event_name value.</span></span> <span data-ttu-id="2bec6-141">使用以下查询可以标识潜在列：</span><span class="sxs-lookup"><span data-stu-id="2bec6-141">You can identify the potential columns by using the following query:</span></span><br /><br /> <span data-ttu-id="2bec6-142">从 sys.databases 中选择 name。 dm_xe_object_columns</span><span class="sxs-lookup"><span data-stu-id="2bec6-142">SELECT name FROM sys.dm_xe_object_columns</span></span><br /><span data-ttu-id="2bec6-143">WHERE object_name = ' \<eventname> '</span><span class="sxs-lookup"><span data-stu-id="2bec6-143">WHERE object_name = '\<eventname>'</span></span><br /><span data-ttu-id="2bec6-144">和 column_type！ = ' readonly '</span><span class="sxs-lookup"><span data-stu-id="2bec6-144">AND column_type != 'readonly'</span></span><br /><br /> <span data-ttu-id="2bec6-145">当为源指定事件列时，不一定要在源值中包括包名称。</span><span class="sxs-lookup"><span data-stu-id="2bec6-145">When you specify an event column for source, you do not have to include the package name in the source value.</span></span><br /><br /> <span data-ttu-id="2bec6-146">当为源指定操作名称时，必须使用在此目标所用于的事件会话中为收集配置的一个操作。</span><span class="sxs-lookup"><span data-stu-id="2bec6-146">When you specify an action name for source, you must use one of the actions that is configured for collection in the event session for which this target is being used.</span></span> <span data-ttu-id="2bec6-147">若要查找操作名称的潜在值，可以查询 sys.dm_xe_sesssion_event_actions 视图的 action_name 列。</span><span class="sxs-lookup"><span data-stu-id="2bec6-147">To find potential values for the action name, you can query the action_name column of the sys.dm_xe_sesssion_event_actions view.</span></span><br /><br /> <span data-ttu-id="2bec6-148">如果将操作名称作为数据源使用，则必须使用以下格式指定源值： *package_name*.*action_name*。</span><span class="sxs-lookup"><span data-stu-id="2bec6-148">If you are using an action name as the data source, you must specify the source value by using the format: *package_name*.*action_name*.</span></span>|  
  
 <span data-ttu-id="2bec6-149">以下示例演示了直方图目标如何在高级别收集数据。</span><span class="sxs-lookup"><span data-stu-id="2bec6-149">The following example illustrates at a high level how the histogram target collects data.</span></span> <span data-ttu-id="2bec6-150">在此示例中，您希望使用直方图目标来计算每种等待类型中发生的等待数。</span><span class="sxs-lookup"><span data-stu-id="2bec6-150">In this example, you want to use the histogram target to count how many waits of each wait type occurred.</span></span> <span data-ttu-id="2bec6-151">为此，您将会在定义直方图目标时指定以下选项：</span><span class="sxs-lookup"><span data-stu-id="2bec6-151">To do this, you would specify the following options when you define the histogram target:</span></span>  
  
-   <span data-ttu-id="2bec6-152">filtering_event_name = 'wait_info'</span><span class="sxs-lookup"><span data-stu-id="2bec6-152">filtering_event_name = 'wait_info'</span></span>  
  
-   <span data-ttu-id="2bec6-153">source = 'wait_type'</span><span class="sxs-lookup"><span data-stu-id="2bec6-153">source = 'wait_type'</span></span>  
  
-   <span data-ttu-id="2bec6-154">source_type = 0（因为 wait_type 是个事件列）</span><span class="sxs-lookup"><span data-stu-id="2bec6-154">source_type = 0 (because wait_type is an event column)</span></span>  
  
 <span data-ttu-id="2bec6-155">在此示例方案中，针对 wait_type 源记录了以下数据。</span><span class="sxs-lookup"><span data-stu-id="2bec6-155">In the example scenario, the following data is recorded for the wait_type source.</span></span>  
  
|<span data-ttu-id="2bec6-156">筛选事件名称</span><span class="sxs-lookup"><span data-stu-id="2bec6-156">Filtering event name</span></span>|<span data-ttu-id="2bec6-157">源列值</span><span class="sxs-lookup"><span data-stu-id="2bec6-157">Source column value</span></span>|  
|--------------------------|-------------------------|  
|<span data-ttu-id="2bec6-158">wait_info</span><span class="sxs-lookup"><span data-stu-id="2bec6-158">wait_info</span></span>|<span data-ttu-id="2bec6-159">file_io</span><span class="sxs-lookup"><span data-stu-id="2bec6-159">file_io</span></span>|  
|<span data-ttu-id="2bec6-160">wait_info</span><span class="sxs-lookup"><span data-stu-id="2bec6-160">wait_info</span></span>|<span data-ttu-id="2bec6-161">file_io</span><span class="sxs-lookup"><span data-stu-id="2bec6-161">file_io</span></span>|  
|<span data-ttu-id="2bec6-162">wait_info</span><span class="sxs-lookup"><span data-stu-id="2bec6-162">wait_info</span></span>|<span data-ttu-id="2bec6-163">network</span><span class="sxs-lookup"><span data-stu-id="2bec6-163">network</span></span>|  
|<span data-ttu-id="2bec6-164">wait_info</span><span class="sxs-lookup"><span data-stu-id="2bec6-164">wait_info</span></span>|<span data-ttu-id="2bec6-165">network</span><span class="sxs-lookup"><span data-stu-id="2bec6-165">network</span></span>|  
|<span data-ttu-id="2bec6-166">wait_info</span><span class="sxs-lookup"><span data-stu-id="2bec6-166">wait_info</span></span>|<span data-ttu-id="2bec6-167">sleep</span><span class="sxs-lookup"><span data-stu-id="2bec6-167">sleep</span></span>|  
  
 <span data-ttu-id="2bec6-168">等待类型值可以划分为三个槽，具有以下值和槽计数：</span><span class="sxs-lookup"><span data-stu-id="2bec6-168">The wait type values would be categorized into three slots, with the following values and slot counts:</span></span>  
  
|<span data-ttu-id="2bec6-169">值</span><span class="sxs-lookup"><span data-stu-id="2bec6-169">Value</span></span>|<span data-ttu-id="2bec6-170">槽计数</span><span class="sxs-lookup"><span data-stu-id="2bec6-170">Slot count</span></span>|  
|-----------|----------------|  
|<span data-ttu-id="2bec6-171">file_io</span><span class="sxs-lookup"><span data-stu-id="2bec6-171">file_io</span></span>|<span data-ttu-id="2bec6-172">2</span><span class="sxs-lookup"><span data-stu-id="2bec6-172">2</span></span>|  
|<span data-ttu-id="2bec6-173">network</span><span class="sxs-lookup"><span data-stu-id="2bec6-173">network</span></span>|<span data-ttu-id="2bec6-174">2</span><span class="sxs-lookup"><span data-stu-id="2bec6-174">2</span></span>|  
|<span data-ttu-id="2bec6-175">sleep</span><span class="sxs-lookup"><span data-stu-id="2bec6-175">sleep</span></span>|<span data-ttu-id="2bec6-176">1</span><span class="sxs-lookup"><span data-stu-id="2bec6-176">1</span></span>|  
  
 <span data-ttu-id="2bec6-177">直方图目标只保留指定源的事件数据。</span><span class="sxs-lookup"><span data-stu-id="2bec6-177">The histogram target only retains event data for the specified source.</span></span> <span data-ttu-id="2bec6-178">某些情况下，事件数据可能太大而无法完全保留，这时便会截断数据。</span><span class="sxs-lookup"><span data-stu-id="2bec6-178">In some cases the event data may be too large to retain completely, in which case the data is truncated.</span></span> <span data-ttu-id="2bec6-179">截断事件数据后，将记录字节数并以 XML 输出方式显示出来。</span><span class="sxs-lookup"><span data-stu-id="2bec6-179">When event data is truncated, the number of bytes is recorded and displayed as XML output.</span></span>  
  
## <a name="adding-the-target-to-a-session"></a><span data-ttu-id="2bec6-180">将目标添加到会话</span><span class="sxs-lookup"><span data-stu-id="2bec6-180">Adding the Target to a Session</span></span>  
 <span data-ttu-id="2bec6-181">若要将直方图目标添加到扩展事件会话，在创建或更改事件会话时，您必须根据所需目标类型包括下面任一语句：</span><span class="sxs-lookup"><span data-stu-id="2bec6-181">To add the histogram target to an Extended Events session, you must include either of the following statements when you create or alter an event session, depending on the desired target type:</span></span>  
  
```  
ADD TARGET package0.histogram  
```  
  
 <span data-ttu-id="2bec6-182">可以使用 SET 语句设置各种选项。</span><span class="sxs-lookup"><span data-stu-id="2bec6-182">You can use the SET statement to set the various options.</span></span> <span data-ttu-id="2bec6-183">下面的示例演示了直方图目标的添加方式，将在该目标中收集 sqlserver.checkpoint_end 事件的数据。</span><span class="sxs-lookup"><span data-stu-id="2bec6-183">The following example shows the addition of the histogram target, where data for the sqlserver.checkpoint_end event is collected.</span></span>  
  
```  
ADD TARGET package0.histogram  
(SET slots = 32, filtering_event_name = 'sqlserver.checkpoint_end', source_type = 0, source = 'database_id')  
```  
  
 <span data-ttu-id="2bec6-184">有关详细信息，请参阅 [查找具有最多锁定的对象](../relational-databases/extended-events/find-the-objects-that-have-the-most-locks-taken-on-them.md)和 [使用扩展事件监视系统活动](../relational-databases/extended-events/monitor-system-activity-using-extended-events.md)。</span><span class="sxs-lookup"><span data-stu-id="2bec6-184">For more information, see [Find the Objects That Have the Most Locks Taken on Them](../relational-databases/extended-events/find-the-objects-that-have-the-most-locks-taken-on-them.md), and [Monitor System Activity Using Extended Events](../relational-databases/extended-events/monitor-system-activity-using-extended-events.md).</span></span>  
  
## <a name="reviewing-the-target-output"></a><span data-ttu-id="2bec6-185">查看目标输出</span><span class="sxs-lookup"><span data-stu-id="2bec6-185">Reviewing the Target Output</span></span>  
 <span data-ttu-id="2bec6-186">直方图目标将数据以 XML 格式序列化到一个调用程序或过程中。</span><span class="sxs-lookup"><span data-stu-id="2bec6-186">The histogram target serializes data to a calling program or procedure in XML format.</span></span> <span data-ttu-id="2bec6-187">目标输出不遵从任何架构。</span><span class="sxs-lookup"><span data-stu-id="2bec6-187">The target output does not conform to any schema.</span></span>  
  
 <span data-ttu-id="2bec6-188">若要查看直方图目标的输出，你可以使用下面的查询，并将 *session_name* 替换为事件会话的名称。</span><span class="sxs-lookup"><span data-stu-id="2bec6-188">To review the output from the histogram target, you can use the following query, replacing *session_name* with the name of the event session.</span></span>  
  
```  
SELECT name, target_name, CAST(xet.target_data AS xml)  
FROM sys.dm_xe_session_targets AS xet  
JOIN sys.dm_xe_sessions AS xe  
   ON (xe.address = xet.event_session_address)  
WHERE xe.name = 'session_name'  
```  
  
 <span data-ttu-id="2bec6-189">以下示例演示了直方图目标的输出格式。</span><span class="sxs-lookup"><span data-stu-id="2bec6-189">The following example illustrates histogram target output format.</span></span>  
  
```  
<Slots truncated = "0" buckets=[count]>  
    <Slot count=[count] trunc=[truncated bytes]>  
        <value>  
        </value>  
    </Slot>  
</Slots>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2bec6-190">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2bec6-190">See Also</span></span>  
 <span data-ttu-id="2bec6-191">[SQL Server 扩展事件目标](../../2014/database-engine/sql-server-extended-events-targets.md) </span><span class="sxs-lookup"><span data-stu-id="2bec6-191">[SQL Server Extended Events Targets](../../2014/database-engine/sql-server-extended-events-targets.md) </span></span>  
 <span data-ttu-id="2bec6-192">[sys.dm_xe_session_targets (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-targets-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2bec6-192">[sys.dm_xe_session_targets &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-targets-transact-sql) </span></span>  
 <span data-ttu-id="2bec6-193">[CREATE EVENT SESSION (Transact-SQL)](/sql/t-sql/statements/create-event-session-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2bec6-193">[CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql) </span></span>  
 [<span data-ttu-id="2bec6-194">ALTER EVENT SESSION (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="2bec6-194">ALTER EVENT SESSION &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-event-session-transact-sql)  
  
  
