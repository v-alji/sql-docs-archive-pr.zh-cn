---
title: 管理和监视变更数据捕获 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- change data capture [SQL Server], monitoring
- change data capture [SQL Server], administering
- change data capture [SQL Server], jobs
ms.assetid: 23bda497-67b2-4e7b-8e4d-f1f9a2236685
author: rothja
ms.author: jroth
ms.openlocfilehash: 8d97929ead145d1b0de1a1f83becb15ade397683
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588386"
---
# <a name="administer-and-monitor-change-data-capture-sql-server"></a><span data-ttu-id="1ae30-102">管理和监视变更数据捕获 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="1ae30-102">Administer and Monitor Change Data Capture (SQL Server)</span></span>
  <span data-ttu-id="1ae30-103">本主题介绍如何管理和监视变更数据捕获。</span><span class="sxs-lookup"><span data-stu-id="1ae30-103">This topic describes how to administer and monitor change data capture.</span></span>  
  
##  <a name="capture-job"></a><a name="Capture"></a> <span data-ttu-id="1ae30-104">捕获作业</span><span class="sxs-lookup"><span data-stu-id="1ae30-104">Capture Job</span></span>  
 <span data-ttu-id="1ae30-105">捕获作业可通过运行无参数存储过程 `sp_MScdc_capture_job` 来启动。</span><span class="sxs-lookup"><span data-stu-id="1ae30-105">The capture job is initiated by running the parameterless stored procedure `sp_MScdc_capture_job`.</span></span> <span data-ttu-id="1ae30-106">此存储过程启动时，将从 msdb.dbo.cdc_jobs 中为捕获作业提取 *maxtrans*、 *maxscans*、 *continuous*和 *pollinginterval* 的配置值。</span><span class="sxs-lookup"><span data-stu-id="1ae30-106">This stored procedure starts by extracting the configured values for *maxtrans*, *maxscans*, *continuous*, and *pollinginterval* for the capture job from msdb.dbo.cdc_jobs.</span></span> <span data-ttu-id="1ae30-107">然后，这些配置值会作为参数传递到存储过程 `sp_cdc_scan`。</span><span class="sxs-lookup"><span data-stu-id="1ae30-107">These configured values are then passed as parameters to the stored procedure `sp_cdc_scan`.</span></span> <span data-ttu-id="1ae30-108">该存储过程用于调用 `sp_replcmds` 以执行日志扫描。</span><span class="sxs-lookup"><span data-stu-id="1ae30-108">This is used to invoke `sp_replcmds` to perform the log scan.</span></span>  
  
### <a name="capture-job-parameters"></a><span data-ttu-id="1ae30-109">捕获作业参数</span><span class="sxs-lookup"><span data-stu-id="1ae30-109">Capture Job Parameters</span></span>  
 <span data-ttu-id="1ae30-110">若要了解捕获作业行为，必须了解 `sp_cdc_scan` 使用可配置参数的方式。</span><span class="sxs-lookup"><span data-stu-id="1ae30-110">To understand capture job behavior, you must understand how the configurable parameters are used by `sp_cdc_scan`.</span></span>  
  
#### <a name="maxtrans-parameter"></a><span data-ttu-id="1ae30-111">maxtrans 参数</span><span class="sxs-lookup"><span data-stu-id="1ae30-111">maxtrans Parameter</span></span>  
 <span data-ttu-id="1ae30-112">*maxtrans* 参数用于指定能够在日志的单个扫描循环中处理的最大事务数。</span><span class="sxs-lookup"><span data-stu-id="1ae30-112">The *maxtrans* parameter specifies the maximum number of transactions that can be processed in a single scan cycle of the log.</span></span> <span data-ttu-id="1ae30-113">如果在该扫描期间要处理的事务数达到该限制，则当前扫描中将不包括任何其他事务。</span><span class="sxs-lookup"><span data-stu-id="1ae30-113">If, during the scan, the number of transactions to be processed reaches this limit, no additional transactions are included in the current scan.</span></span> <span data-ttu-id="1ae30-114">一个扫描循环完成后，已处理的事务数将始终小于或等于 *maxtrans*。</span><span class="sxs-lookup"><span data-stu-id="1ae30-114">After a scan cycle is complete, the number of transactions that were processed will always be less than or equal to *maxtrans*.</span></span>  
  
#### <a name="maxscans-parameter"></a><span data-ttu-id="1ae30-115">maxscans 参数</span><span class="sxs-lookup"><span data-stu-id="1ae30-115">maxscans Parameter</span></span>  
 <span data-ttu-id="1ae30-116">*maxscans* 参数用于指定在返回 (continuous = 0) 或执行 waitfor (continuous = 1) 之前为完成日志扫描可以尝试的最大扫描循环次数。</span><span class="sxs-lookup"><span data-stu-id="1ae30-116">The *maxscans* parameter specifies the maximum number of scan cycles that are attempted to drain the log before either returning (continuous = 0) or executing a waitfor (continuous = 1).</span></span>  
  
#### <a name="continuous-parameter"></a><span data-ttu-id="1ae30-117">continuous 参数</span><span class="sxs-lookup"><span data-stu-id="1ae30-117">continuous Parameter</span></span>  
 <span data-ttu-id="1ae30-118">*连续*参数用于控制是 `sp_cdc_scan` 在排出日志后还是在 (一次) 一次拍摄模式下执行扫描循环的最大数目。</span><span class="sxs-lookup"><span data-stu-id="1ae30-118">The *continuous* parameter controls whether `sp_cdc_scan` relinquishes control in after either draining the log or executing the maximum number of scan cycles (one shot mode).</span></span> <span data-ttu-id="1ae30-119">它还控制在显式停止 `sp_cdc_scan` 之前此存储过程是否继续运行（继续模式）。</span><span class="sxs-lookup"><span data-stu-id="1ae30-119">It also controles whether `sp_cdc_scan` continues to run until explicitly stopped (continuous mode).</span></span>  
  
##### <a name="one-shot-mode"></a><span data-ttu-id="1ae30-120">单次触发模式</span><span class="sxs-lookup"><span data-stu-id="1ae30-120">One Shot Mode</span></span>  
 <span data-ttu-id="1ae30-121">在一个拍摄模式下，捕获作业请求 `sp_cdc_scan` 执行最多*maxtrans*扫描，尝试排出日志并返回。</span><span class="sxs-lookup"><span data-stu-id="1ae30-121">In one shot mode, the capture job requests `sp_cdc_scan` to perform up to *maxtrans* scans to try to drain the log and return.</span></span> <span data-ttu-id="1ae30-122">日志中存在的超出 *maxtrans* 数量的任何事务将在稍后的扫描中处理。</span><span class="sxs-lookup"><span data-stu-id="1ae30-122">Any transactions in addition to *maxtrans* that are present in the log will be processed in later scans.</span></span>  
  
 <span data-ttu-id="1ae30-123">单次触发模式用于待处理事务量已知的受控测试中，优点是作业完成后将自动关闭。</span><span class="sxs-lookup"><span data-stu-id="1ae30-123">One shot mode is used in controlled tests, where the volume of transactions to be processed is known, and there are advantages to the fact that the job closes automatically on when it is finished.</span></span> <span data-ttu-id="1ae30-124">建议不要将单次触发模式用于生产。</span><span class="sxs-lookup"><span data-stu-id="1ae30-124">One shot mode is not recommended for production use.</span></span> <span data-ttu-id="1ae30-125">这是因为它依赖于作业计划来管理扫描循环的运行频率。</span><span class="sxs-lookup"><span data-stu-id="1ae30-125">This is because t relies on the job schedule to manage how frequently the scan cycle is run.</span></span>  
  
 <span data-ttu-id="1ae30-126">以单次触发模式运行时，您可以计算捕获作业的预期吞吐量的上限并以每秒的事务数来表示。其计算方法如下：</span><span class="sxs-lookup"><span data-stu-id="1ae30-126">When running in one shot mode, you can compute an upper bound on expected throughput of the capture job, expressed in transactions per second by using the following computation:</span></span>  
  
 `(maxtrans * maxscans) / number of seconds between scans`  
  
 <span data-ttu-id="1ae30-127">即使扫描日志和填充更改表所需的时间与 0 相差不多，作业的平均吞吐量也不能超过以如下方式所获得的值：即将单次扫描所允许的最大事务数乘以允许的最大扫描次数后除以日志处理间隔的秒数。</span><span class="sxs-lookup"><span data-stu-id="1ae30-127">Even if the time that is required to scan the log and populate the change tables were not significantly different from 0, the average throughput of the job could not exceed the value obtained by dividing the maximum allowed transactions for a single scan multiplied by the maximum allowed scans by the number of seconds separating log processing.</span></span>  
  
 <span data-ttu-id="1ae30-128">如果将单次触发模式用于控制日志扫描，则日志处理间隔的秒数将不得不受作业计划的控制。</span><span class="sxs-lookup"><span data-stu-id="1ae30-128">If one shot mode were to be used to regulate log scanning, the number of seconds between log processing would have to be governed by the job schedule.</span></span> <span data-ttu-id="1ae30-129">如果需要采用这种方式，则以连续模式运行捕获作业是一种管理重新计划日志扫描的更好方式。</span><span class="sxs-lookup"><span data-stu-id="1ae30-129">When this kind of behavior is desired, running the capture job in continuous mode is a better way to manage rescheduling the log scan.</span></span>  
  
##### <a name="continuous-mode-and-the-polling-interval"></a><span data-ttu-id="1ae30-130">连续模式和轮询间隔</span><span class="sxs-lookup"><span data-stu-id="1ae30-130">Continuous Mode and the Polling Interval</span></span>  
 <span data-ttu-id="1ae30-131">在连续模式下，捕获作业将请求 `sp_cdc_scan` 连续运行。</span><span class="sxs-lookup"><span data-stu-id="1ae30-131">In continuous mode, the capture job requests that `sp_cdc_scan` run continuously.</span></span> <span data-ttu-id="1ae30-132">这使得存储过程可通过提供 maxtrans 和 maxscans 值以及日志处理间隔（轮询间隔）的秒数值来管理自己的等待循环。</span><span class="sxs-lookup"><span data-stu-id="1ae30-132">This lets the stored procedure manage its own wait loop by providing not only for maxtrans and maxscans but also a value for the number of seconds between log processing (the polling interval).</span></span> <span data-ttu-id="1ae30-133">在该模式下运行，捕获作业会保持活动状态，并在日志扫描间隔内执行 `WAITFOR`。</span><span class="sxs-lookup"><span data-stu-id="1ae30-133">Running in this mode, the capture job remains active, executing a `WAITFOR` between log scanning.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1ae30-134">如果轮询间隔的值大于 0，则重复执行单次触发作业的吞吐量的同一上限也适用于连续模式下的作业操作。</span><span class="sxs-lookup"><span data-stu-id="1ae30-134">When the value of the polling interval is greater than 0, the same upper limit on throughput for the recurring one shot job also applies to the job operation in continuous mode.</span></span> <span data-ttu-id="1ae30-135">也就是说，将 (*maxtrans* \* *maxscans*) 除以非零轮询间隔即可得到捕获作业可以处理的平均事务数的上限。</span><span class="sxs-lookup"><span data-stu-id="1ae30-135">That is, (*maxtrans* \* *maxscans*) divided by a nonzero polling interval will put an upper bound on the average number of transactions that can be processed by the capture job.</span></span>  
  
### <a name="capture-job-customization"></a><span data-ttu-id="1ae30-136">捕获作业自定义</span><span class="sxs-lookup"><span data-stu-id="1ae30-136">Capture Job Customization</span></span>  
 <span data-ttu-id="1ae30-137">对于捕获作业，可以应用其他逻辑来确定是立即开始新扫描，还是在启动新扫描之前强制休眠，而非依赖于固定的轮询间隔。</span><span class="sxs-lookup"><span data-stu-id="1ae30-137">For the capture job, you can apply additional logic to determine whether a new scan begins immediately or whether a sleep is imposed before it starts a new scan instead of rely on a fixed polling interval.</span></span> <span data-ttu-id="1ae30-138">该选择可以仅基于一天中的某个时间，可以在峰值活动期间强制长时间休眠，甚至可以在一天即将结束时（此时为完成白天处理并为夜间运行做准备的关键时刻）将轮询间隔改为 0。</span><span class="sxs-lookup"><span data-stu-id="1ae30-138">The choice could be based merely on time of the day, perhaps enforcing very long sleeps during peak activity times, and even moving to a polling interval of 0 at close of day when it is important to complete the days processing and prepare for nightly runs.</span></span> <span data-ttu-id="1ae30-139">也可以监视捕获进程进度，以确定何时已对午夜提交的所有事务进行扫描并将其存放在更改表中。</span><span class="sxs-lookup"><span data-stu-id="1ae30-139">Capture process progress could also be monitored to determine when all transactions committed by mid-night had been scanned and deposited in change tables.</span></span> <span data-ttu-id="1ae30-140">这将导致捕获作业结束，该作业可由计划的每日重启来重新启动。</span><span class="sxs-lookup"><span data-stu-id="1ae30-140">This lets the capture job end, to be restarted by a scheduled daily restart.</span></span> <span data-ttu-id="1ae30-141">通过将调用 `sp_cdc_scan` 的已交付作业步骤替换为针对 `sp_cdc_scan` 的用户已编写包装的调用，只需少量的额外操作即可获得高度自定义的行为。</span><span class="sxs-lookup"><span data-stu-id="1ae30-141">By replacing the delivered job step calling `sp_cdc_scan` with a call to a user written wrapper for `sp_cdc_scan`, highly customized behavior can be obtained with little additional effort.</span></span>  
  
##  <a name="cleanup-job"></a><a name="Cleanup"></a> <span data-ttu-id="1ae30-142">清除作业</span><span class="sxs-lookup"><span data-stu-id="1ae30-142">Cleanup Job</span></span>  
 <span data-ttu-id="1ae30-143">本部分提供有关变更数据捕获清除作业工作方式的信息。</span><span class="sxs-lookup"><span data-stu-id="1ae30-143">This section provides information about how the change data capture cleanup job works.</span></span>  
  
### <a name="structure-of-the-cleanup-job"></a><span data-ttu-id="1ae30-144">清除作业的结构</span><span class="sxs-lookup"><span data-stu-id="1ae30-144">Structure of the Cleanup Job</span></span>  
 <span data-ttu-id="1ae30-145">变更数据捕获使用基于保持期的清理策略来管理更改表的大小。</span><span class="sxs-lookup"><span data-stu-id="1ae30-145">Change data capture uses a retention based cleanup strategy to manage change table size.</span></span> <span data-ttu-id="1ae30-146">清除机制包含一个在启用第一个数据库表时所创建的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理 [!INCLUDE[tsql](../../includes/tsql-md.md)] 作业。</span><span class="sxs-lookup"><span data-stu-id="1ae30-146">The cleanup mechanism consists of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent [!INCLUDE[tsql](../../includes/tsql-md.md)] job that is created when the first database table is enabled.</span></span> <span data-ttu-id="1ae30-147">单个清除作业可处理所有数据库更改表的清除工作并将相同的保持值应用到所有定义的捕获实例。</span><span class="sxs-lookup"><span data-stu-id="1ae30-147">A single cleanup job handles cleanup for all database change tables and applies the same retention value to all defined capture instances.</span></span>  
  
 <span data-ttu-id="1ae30-148">清除作业可通过运行无参数存储过程 `sp_MScdc_cleanup_job` 来启动。</span><span class="sxs-lookup"><span data-stu-id="1ae30-148">The cleanup job is initiated by running the parameterless stored procedure `sp_MScdc_cleanup_job`.</span></span> <span data-ttu-id="1ae30-149">此存储过程开始时，将从 `msdb.dbo.cdc_jobs` 中提取为清除作业配置的保持期和阈值。</span><span class="sxs-lookup"><span data-stu-id="1ae30-149">This stored procedure starts by extracting the configured retention and threshold values for the cleanup job from `msdb.dbo.cdc_jobs`.</span></span> <span data-ttu-id="1ae30-150">保持值用于计算更改表的新低水印。</span><span class="sxs-lookup"><span data-stu-id="1ae30-150">The retention value is used to compute a new low watermark for the change tables.</span></span> <span data-ttu-id="1ae30-151">从表中的最大*tran_end_time*值减去指定的分钟数 `cdc.lsn_time_mapping` ，以获取表示为日期时间值的新低水印。</span><span class="sxs-lookup"><span data-stu-id="1ae30-151">The specified number of minutes is subtracted from the maximum *tran_end_time* value from the `cdc.lsn_time_mapping` table to obtain the new low water mark expressed as a datetime value.</span></span> <span data-ttu-id="1ae30-152">然后，使用 CDC.lsn_time_mapping 表将该日期时间值转换为相应的 `lsn` 值。</span><span class="sxs-lookup"><span data-stu-id="1ae30-152">The CDC.lsn_time_mapping table is then used to convert this datetime value to a corresponding `lsn` value.</span></span> <span data-ttu-id="1ae30-153">如果表中多个项共享相同的提交时间，则会选择与具有最小 `lsn` 的项相对应的 `lsn` 作为新低水印。</span><span class="sxs-lookup"><span data-stu-id="1ae30-153">If the same commit time is shared by multiple entries in the table, the `lsn` that corresponds to the entry that has the smallest `lsn` is chosen as the new low watermark.</span></span> <span data-ttu-id="1ae30-154">该 `lsn` 值将传递到 `sp_cdc_cleanup_change_tables` 以从数据库更改表中删除更改表项。</span><span class="sxs-lookup"><span data-stu-id="1ae30-154">This `lsn` value is passed to `sp_cdc_cleanup_change_tables` to remove change table entries from the database change tables.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1ae30-155">使用最近事务的提交时间作为计算新低水印的基准的优点在于：它可使更改在更改表中保留指定的时间。</span><span class="sxs-lookup"><span data-stu-id="1ae30-155">The advantage of using the commit time of the recent transaction as the base for computing the new low watermark is that it lets the changes remain in change tables for the specified time.</span></span> <span data-ttu-id="1ae30-156">即使在捕获进程运行落后时也会出现这种情况。</span><span class="sxs-lookup"><span data-stu-id="1ae30-156">This happens even when the capture process is running behind.</span></span> <span data-ttu-id="1ae30-157">通过为实际低水印选择具有共享提交时间的最小 `lsn`，与当前低水印具有相同提交时间的所有项会继续保留在更改表中。</span><span class="sxs-lookup"><span data-stu-id="1ae30-157">All entries that have the same commit time as the current low watermark continue to be represented within the change tables by choosing the smallest `lsn` that has the shared commit time for the actual low watermark.</span></span>  
  
 <span data-ttu-id="1ae30-158">执行清除时，所有捕获实例的低水印会在单个事务中初次更新。</span><span class="sxs-lookup"><span data-stu-id="1ae30-158">When a cleanup is performed, the low watermark for all capture instances is initially updated in a single transaction.</span></span> <span data-ttu-id="1ae30-159">然后，它会尝试从更改表和 cdc.lsn_time_mapping 表中删除过时项。</span><span class="sxs-lookup"><span data-stu-id="1ae30-159">It then tries to remove obsolete entries from the change tables and the cdc.lsn_time_mapping table.</span></span> <span data-ttu-id="1ae30-160">可配置的阈值用于限制使用任何单个语句中所删除的项数。</span><span class="sxs-lookup"><span data-stu-id="1ae30-160">The configurable threshold value limits how many entries are deleted in any single statement.</span></span> <span data-ttu-id="1ae30-161">对任何单个表执行删除操作失败并不会阻止对其他表尝试执行该操作。</span><span class="sxs-lookup"><span data-stu-id="1ae30-161">Failure to perform the delete on any individual table will not prevent the operation from being attempted on the remaining tables.</span></span>  
  
### <a name="cleanup-job-customization"></a><span data-ttu-id="1ae30-162">清除作业自定义</span><span class="sxs-lookup"><span data-stu-id="1ae30-162">Cleanup Job Customization</span></span>  
 <span data-ttu-id="1ae30-163">对于清除作业，是否可以进行自定义取决于在确定要放弃哪些更改表项时所采用的策略。</span><span class="sxs-lookup"><span data-stu-id="1ae30-163">For the cleanup job, the possibility for customization is in the strategy used to determine which change table entries are to be discarded.</span></span> <span data-ttu-id="1ae30-164">传递的清除作业中唯一支持的策略是基于时间的策略。</span><span class="sxs-lookup"><span data-stu-id="1ae30-164">The only supported strategy in the delivered cleanup job is a time-based one.</span></span> <span data-ttu-id="1ae30-165">在这种情况下，新低水印是通过从处理的最后一个事务的提交时间减去允许的保持期而计算得到的。</span><span class="sxs-lookup"><span data-stu-id="1ae30-165">In that situation, the new low watermark is computed by subtracting the allowed retention period from the commit time of the last transaction processed.</span></span> <span data-ttu-id="1ae30-166">因为基础清除过程基于 `lsn` 而不是时间，所以可使用任何数量的策略来确定要保存在更改表中的最小 `lsn`。</span><span class="sxs-lookup"><span data-stu-id="1ae30-166">Because the underlying cleanup procedures are based on `lsn` instead of time, any number of strategies can be used to determine the smallest `lsn` to keep in the change tables.</span></span> <span data-ttu-id="1ae30-167">只有某些过程是严格基于时间的。</span><span class="sxs-lookup"><span data-stu-id="1ae30-167">Only some of these are strictly time-based.</span></span> <span data-ttu-id="1ae30-168">例如，如果需要访问更改表的下游进程无法运行，则可以使用有关客户端的知识来提供故障保护。</span><span class="sxs-lookup"><span data-stu-id="1ae30-168">Knowledge about the clients, for example, could be used to provide a failsafe if downstream processes that require access to the change tables cannot run.</span></span> <span data-ttu-id="1ae30-169">此外，尽管默认策略应用相同的 `lsn` 来清除所有数据库的更改表，但还可以调用基础清除过程，以在捕获实例级别上进行清除。</span><span class="sxs-lookup"><span data-stu-id="1ae30-169">Also, although the default strategy applies the same `lsn` to clean up all the databases' change tables, the underlying cleanup procedure, can also be called to clean up at the capture instance level.</span></span>  
  
##  <a name="monitor-the-change-data-capture-process"></a><a name="Monitor"></a> <span data-ttu-id="1ae30-170">监视变更数据捕获进程</span><span class="sxs-lookup"><span data-stu-id="1ae30-170">Monitor the Change Data Capture Process</span></span>  
 <span data-ttu-id="1ae30-171">通过监视变更数据捕获进程，可以确定更改是否正以合理的滞后时间正确写入更改表中。</span><span class="sxs-lookup"><span data-stu-id="1ae30-171">Monitoring the change data capture process lets you determine if changes are being written correctly and with a reasonable latency to the change tables.</span></span> <span data-ttu-id="1ae30-172">监视还可以帮助您标识可能发生的任何错误。</span><span class="sxs-lookup"><span data-stu-id="1ae30-172">Monitoring can also help you to identify any errors that might occur.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="1ae30-173">包括两个动态管理视图，用于帮助你监视变更数据捕获： [sys.dm_cdc_log_scan_sessions](../native-client-ole-db-data-source-objects/sessions.md) 和 [sys.dm_cdc_errors](../native-client-ole-db-errors/errors.md)。</span><span class="sxs-lookup"><span data-stu-id="1ae30-173">includes two dynamic management views to help you monitor change data capture: [sys.dm_cdc_log_scan_sessions](../native-client-ole-db-data-source-objects/sessions.md) and [sys.dm_cdc_errors](../native-client-ole-db-errors/errors.md).</span></span>  
  
### <a name="identify-sessions-with-empty-result-sets"></a><span data-ttu-id="1ae30-174">标识包含空结果集的会话</span><span class="sxs-lookup"><span data-stu-id="1ae30-174">Identify Sessions with Empty Result Sets</span></span>  
 <span data-ttu-id="1ae30-175">sys.dm_cdc_log_scan_sessions 中的每一行表示一个日志扫描会话（ID 为 0 的行除外）。</span><span class="sxs-lookup"><span data-stu-id="1ae30-175">Every row in sys.dm_cdc_log_scan_sessions represents a log scan session (except the row with an ID of 0).</span></span> <span data-ttu-id="1ae30-176">一个日志扫描会话等效于执行一次 [sp_cdc_scan](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-scan-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="1ae30-176">A log scan session is equivalent to one execution of [sp_cdc_scan](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-scan-transact-sql).</span></span> <span data-ttu-id="1ae30-177">在会话期间，扫描可以返回更改，也可以返回空结果。</span><span class="sxs-lookup"><span data-stu-id="1ae30-177">During a session, the scan can either return changes or return an empty result.</span></span> <span data-ttu-id="1ae30-178">如果结果集为空，则 sys.dm_cdc_log_scan_sessions 中的 empty_scan_count 列将设置为 1。</span><span class="sxs-lookup"><span data-stu-id="1ae30-178">If the result set is empty, the empty_scan_count column in sys.dm_cdc_log_scan_sessions is set to 1.</span></span> <span data-ttu-id="1ae30-179">如果有连续的空结果集（例如，当捕获作业正在连续运行时），则最后一个现有行中的 empty_scan_count 将递增。</span><span class="sxs-lookup"><span data-stu-id="1ae30-179">If there are consecutive empty result sets, such as if the capture job is running continuously, the empty_scan_count in the last existing row is incremented.</span></span> <span data-ttu-id="1ae30-180">例如，如果 sys.dm_cdc_log_scan_sessions 已经包含与返回了更改的扫描相对应的 10 行，并且存在五个连续的空结果，则该视图包含 11 行。</span><span class="sxs-lookup"><span data-stu-id="1ae30-180">For example, if sys.dm_cdc_log_scan_sessions already contains 10 rows for scans that returned changes and there are five empty results in a row, the view contains 11 rows.</span></span> <span data-ttu-id="1ae30-181">最后一行在 empty_scan_count 列的值是 5。</span><span class="sxs-lookup"><span data-stu-id="1ae30-181">The last row has a value of 5 in the empty_scan_count column.</span></span> <span data-ttu-id="1ae30-182">若要确定有空扫描的会话，请运行以下查询：</span><span class="sxs-lookup"><span data-stu-id="1ae30-182">To determine sessions that had an empty scan, run the following query:</span></span>  
  
```sql
SELECT * from sys.dm_cdc_log_scan_sessions where empty_scan_count <> 0
```
  
### <a name="determine-latency"></a><span data-ttu-id="1ae30-183">确定滞后时间</span><span class="sxs-lookup"><span data-stu-id="1ae30-183">Determine Latency</span></span>  
 <span data-ttu-id="1ae30-184">sys.dm_cdc_log_scan_sessions 管理视图包括一个用于记录每个捕获会话滞后时间的列。</span><span class="sxs-lookup"><span data-stu-id="1ae30-184">The sys.dm_cdc_log_scan_sessions management view includes a column that records the latency for each capture session.</span></span> <span data-ttu-id="1ae30-185">滞后时间是指在源表上提交的事务与在更改表上提交的最后一个捕获的事务之间所经过的时间。</span><span class="sxs-lookup"><span data-stu-id="1ae30-185">Latency is defined as the elapsed time between a transaction being committed on a source table and the last captured transaction being committed on the change table.</span></span> <span data-ttu-id="1ae30-186">只为活动会话填充滞后时间列。</span><span class="sxs-lookup"><span data-stu-id="1ae30-186">The latency column is populated only for active sessions.</span></span> <span data-ttu-id="1ae30-187">对于其 empty_scan_count 列的值大于 0 的会话，滞后时间列将设置为 0。</span><span class="sxs-lookup"><span data-stu-id="1ae30-187">For sessions with a value greater than 0 in the empty_scan_count column, the latency column is set to 0.</span></span> <span data-ttu-id="1ae30-188">以下查询返回最近进行的会话的平均滞后时间：</span><span class="sxs-lookup"><span data-stu-id="1ae30-188">The following query returns the average latency for the most recent sessions:</span></span>  
  
```sql
SELECT latency FROM sys.dm_cdc_log_scan_sessions WHERE session_id = 0
```
  
 <span data-ttu-id="1ae30-189">可以使用滞后时间数据确定捕获进程正在以多快或多慢的速度处理事务。</span><span class="sxs-lookup"><span data-stu-id="1ae30-189">You can use latency data to determine how fast or slow the capture process is processing transactions.</span></span> <span data-ttu-id="1ae30-190">当捕获进程连续运行时，该数据最有用。</span><span class="sxs-lookup"><span data-stu-id="1ae30-190">This data is most useful when the capture process is running continuously.</span></span> <span data-ttu-id="1ae30-191">如果捕获进程正在按计划运行，那么，由于在源表上提交的事务与按计划时间运行的捕获进程之间存在滞后，因此滞后时间可能会很长。</span><span class="sxs-lookup"><span data-stu-id="1ae30-191">If the capture process is running on a schedule, latency can be high because of the lag between transactions being committed on the source table and the capture process running at its scheduled time.</span></span>  
  
 <span data-ttu-id="1ae30-192">捕获进程效率的另一个重要度量值是吞吐量。</span><span class="sxs-lookup"><span data-stu-id="1ae30-192">Another important measure of capture process efficiency is throughput.</span></span> <span data-ttu-id="1ae30-193">它是在每个会话期间每秒处理的平均命令数。</span><span class="sxs-lookup"><span data-stu-id="1ae30-193">This is the average number of commands per second that are processed during each session.</span></span> <span data-ttu-id="1ae30-194">若要确定会话的吞吐量，请将 command_count 列中的值除以持续时间列中的值。</span><span class="sxs-lookup"><span data-stu-id="1ae30-194">To determine the throughput of a session, divide the value in the command_count column by the value in the duration column.</span></span> <span data-ttu-id="1ae30-195">以下查询返回最近会话的平均吞吐量：</span><span class="sxs-lookup"><span data-stu-id="1ae30-195">The following query returns the average throughput for the most recent sessions:</span></span>  
  
```sql
SELECT command_count/duration AS [Throughput] FROM sys.dm_cdc_log_scan_sessions WHERE session_id = 0
```
  
### <a name="use-data-collector-to-collect-sampling-data"></a><span data-ttu-id="1ae30-196">使用数据收集器收集抽样数据</span><span class="sxs-lookup"><span data-stu-id="1ae30-196">Use Data Collector to Collect Sampling Data</span></span>  
 <span data-ttu-id="1ae30-197">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据收集器用于从任何表或动态管理视图中收集数据的快照，并生成性能数据仓库。</span><span class="sxs-lookup"><span data-stu-id="1ae30-197">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data collector lets you collect snapshots of data from any table or dynamic management view and build a performance data warehouse.</span></span> <span data-ttu-id="1ae30-198">对数据库启用变更数据捕获时，最好按固定时间间隔取得 sys.dm_cdc_log_scan_sessions 视图和 sys.dm_cdc_errors 视图的快照，以便随后进行分析。</span><span class="sxs-lookup"><span data-stu-id="1ae30-198">When change data capture is enabled on a database, it is useful to take snapshots of the sys.dm_cdc_log_scan_sessions view and the sys.dm_cdc_errors view at regular intervals for later analysis.</span></span> <span data-ttu-id="1ae30-199">以下过程设置一个数据收集器，用于从 sys.dm_cdc_log_scan_sessions 管理视图收集示例数据。</span><span class="sxs-lookup"><span data-stu-id="1ae30-199">The following procedure sets up a data collector for collecting sample data from the sys.dm_cdc_log_scan_sessions management view.</span></span>  
  
 <span data-ttu-id="1ae30-200">**配置数据收集**</span><span class="sxs-lookup"><span data-stu-id="1ae30-200">**Configuring Data Collection**</span></span>  
  
1.  <span data-ttu-id="1ae30-201">启用数据收集器，并配置管理数据仓库。</span><span class="sxs-lookup"><span data-stu-id="1ae30-201">Enable data collector and configure a management data warehouse.</span></span> <span data-ttu-id="1ae30-202">有关详细信息，请参阅 [管理数据收集](../data-collection/data-collection.md)。</span><span class="sxs-lookup"><span data-stu-id="1ae30-202">For more information, see [Manage Data Collection](../data-collection/data-collection.md).</span></span>  
  
2.  <span data-ttu-id="1ae30-203">执行以下代码，为变更数据捕获创建自定义收集器。</span><span class="sxs-lookup"><span data-stu-id="1ae30-203">Execute the following code to create a custom collector for change data capture.</span></span>  
  
    ```sql  
    USE msdb;  
  
    DECLARE @schedule_uid uniqueidentifier;  
  
    -- Collect and upload data every 5 minutes  
    SELECT @schedule_uid = (  
    SELECT schedule_uid from sysschedules_localserver_view   
    WHERE name = N'CollectorSchedule_Every_5min')  
  
    DECLARE @collection_set_id int;  
  
    EXEC dbo.sp_syscollector_create_collection_set  
    @name = N' CDC Performance Data Collector',  
    @schedule_uid = @schedule_uid,          
    @collection_mode = 0,                   
    @days_until_expiration = 30,                
    @description = N'This collection set collects CDC metadata',  
    @collection_set_id = @collection_set_id output;  
  
    -- Create a collection item using statistics from   
    -- the change data capture dynamic management view.  
    DECLARE @parameters xml;  
    DECLARE @collection_item_id int;  
  
    SELECT @parameters = CONVERT(xml,   
        N'<TSQLQueryCollector>  
            <Query>  
              <Value>SELECT * FROM sys.dm_cdc_log_scan_sessions</Value>  
              <OutputTable>cdc_log_scan_data</OutputTable>  
            </Query>  
          </TSQLQueryCollector>');  
  
    EXEC dbo.sp_syscollector_create_collection_item  
    @collection_set_id = @collection_set_id,  
    @collector_type_uid = N'302E93D1-3424-4BE7-AA8E-84813ECF2419',  
    @name = ' CDC Performance Data Collector',  
    @frequency = 5,   
    @parameters = @parameters,  
    @collection_item_id = @collection_item_id output;  
  
    GO  
    ```  
  
3.  <span data-ttu-id="1ae30-204">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，展开 **“管理”** ，然后展开 **“数据收集”** 。</span><span class="sxs-lookup"><span data-stu-id="1ae30-204">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand **Management**, and then expand **Data Collection**.</span></span> <span data-ttu-id="1ae30-205">右键单击 **“CDC 性能数据收集器”**，然后单击 **“启动数据收集组”**。</span><span class="sxs-lookup"><span data-stu-id="1ae30-205">Right click **CDC Performance Data Collector**, and then click **Start Data Collection Set**.</span></span>  
  
4.  <span data-ttu-id="1ae30-206">在步骤 1 配置的数据仓库中，找到表 custom_snapshots.cdc_log_scan_data。</span><span class="sxs-lookup"><span data-stu-id="1ae30-206">In the data warehouse you configured in step 1, locate the table custom_snapshots.cdc_log_scan_data.</span></span> <span data-ttu-id="1ae30-207">该表提供日志扫描会话中的数据的历史快照。</span><span class="sxs-lookup"><span data-stu-id="1ae30-207">This table provides a historical snapshot of data from log scan sessions.</span></span> <span data-ttu-id="1ae30-208">此数据可以用于分析与时间有关的滞后时间、吞吐量和其他性能度量值。</span><span class="sxs-lookup"><span data-stu-id="1ae30-208">This data can be used to analyze latency, throughput, and other performance measures over time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ae30-209">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1ae30-209">See Also</span></span>  
 <span data-ttu-id="1ae30-210">[跟踪数据更改 (SQL Server)](track-data-changes-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="1ae30-210">[Track Data Changes &#40;SQL Server&#41;](track-data-changes-sql-server.md) </span></span>  
 <span data-ttu-id="1ae30-211">[关于变更数据捕获 (SQL Server)](../track-changes/about-change-data-capture-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="1ae30-211">[About Change Data Capture &#40;SQL Server&#41;](../track-changes/about-change-data-capture-sql-server.md) </span></span>  
 <span data-ttu-id="1ae30-212">[启用和禁用变更数据捕获 (SQL Server)](enable-and-disable-change-data-capture-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="1ae30-212">[Enable and Disable Change Data Capture &#40;SQL Server&#41;](enable-and-disable-change-data-capture-sql-server.md) </span></span>  
 [<span data-ttu-id="1ae30-213">处理变更数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="1ae30-213">Work with Change Data &#40;SQL Server&#41;</span></span>](work-with-change-data-sql-server.md)  
  
  
