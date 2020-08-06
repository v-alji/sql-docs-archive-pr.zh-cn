---
title: 创建计划并将计划附加到作业 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server]
- scheduling jobs [SQL Server]
- jobs [SQL Server], scheduling
- CPU [SQL Server], idle conditions
- automatic job processing
- SQL Server Agent jobs, scheduling
- idle time [SQL Server]
ms.assetid: 079c2984-0052-4a37-a2b8-4ece56e6b6b5
author: stevestein
ms.author: sstein
ms.openlocfilehash: ced47013b6552725e6350b113a3722b066016a6b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689264"
---
# <a name="create-and-attach-schedules-to-jobs"></a><span data-ttu-id="13bed-102">创建计划并将计划附加到作业</span><span class="sxs-lookup"><span data-stu-id="13bed-102">Create and Attach Schedules to Jobs</span></span>
  <span data-ttu-id="13bed-103">计划 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业就是定义使作业在没有用户交互的情况下开始运行的条件。</span><span class="sxs-lookup"><span data-stu-id="13bed-103">Scheduling [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs means defining the condition or conditions that cause the job to begin running without user interaction.</span></span> <span data-ttu-id="13bed-104">通过为作业创建新计划或将现有计划附加到作业可以将作业计划为自动运行。</span><span class="sxs-lookup"><span data-stu-id="13bed-104">You can schedule a job to run automatically by creating a new schedule for the job, or by attaching an existing schedule to the job.</span></span>  
  
 <span data-ttu-id="13bed-105">以下是两种用来创建计划的方法：</span><span class="sxs-lookup"><span data-stu-id="13bed-105">There are two ways to create a schedule:</span></span>  
  
-   <span data-ttu-id="13bed-106">在创建作业的时候创建计划。</span><span class="sxs-lookup"><span data-stu-id="13bed-106">Create the schedule while you are creating a job.</span></span>  
  
-   <span data-ttu-id="13bed-107">在对象资源管理器中创建计划。</span><span class="sxs-lookup"><span data-stu-id="13bed-107">Create the schedule in Object Explorer.</span></span>  
  
 <span data-ttu-id="13bed-108">创建计划后，可将该计划附加到多个作业，即使该计划是为特定作业创建的也是如此。</span><span class="sxs-lookup"><span data-stu-id="13bed-108">After a schedule has been created, you can attach that schedule to multiple jobs, even if the schedule was created for a specific job.</span></span> <span data-ttu-id="13bed-109">还可以从作业分离计划。</span><span class="sxs-lookup"><span data-stu-id="13bed-109">You can also detach schedules from jobs.</span></span>  
  
 <span data-ttu-id="13bed-110">计划可以基于时间，也可以基于事件。</span><span class="sxs-lookup"><span data-stu-id="13bed-110">A schedule can be based upon time or an event.</span></span> <span data-ttu-id="13bed-111">例如，可以计划在以下时间运行作业：</span><span class="sxs-lookup"><span data-stu-id="13bed-111">For example, you can schedule a job to run at the following times:</span></span>  
  
-   <span data-ttu-id="13bed-112">每当 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理启动时。</span><span class="sxs-lookup"><span data-stu-id="13bed-112">Whenever [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent starts.</span></span>  
  
-   <span data-ttu-id="13bed-113">每当计算机的 CPU 使用率处于定义的空闲状态水平时。</span><span class="sxs-lookup"><span data-stu-id="13bed-113">Whenever CPU utilization of the computer is at a level you have defined as idle.</span></span>  
  
-   <span data-ttu-id="13bed-114">在特定日期和时间运行一次。</span><span class="sxs-lookup"><span data-stu-id="13bed-114">One time, at a specific date and time.</span></span>  
  
-   <span data-ttu-id="13bed-115">按重复的计划运行。</span><span class="sxs-lookup"><span data-stu-id="13bed-115">On a recurring schedule.</span></span>  
  
 <span data-ttu-id="13bed-116">除了创建作业计划之外，还可以创建警报，通过运行作业来响应事件。</span><span class="sxs-lookup"><span data-stu-id="13bed-116">As an alternative to job schedules, you can also create an alert that responds to an event by running a job.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="13bed-117">一次只能运行一个作业实例。</span><span class="sxs-lookup"><span data-stu-id="13bed-117">Only one instance of the job can be run at a time.</span></span> <span data-ttu-id="13bed-118">如果在作业按计划运行时尝试手动运行该作业， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理将拒绝该请求。</span><span class="sxs-lookup"><span data-stu-id="13bed-118">If you try to run a job manually while it is running as scheduled, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent refuses the request.</span></span>  
  
 <span data-ttu-id="13bed-119">若要阻止已计划的作业运行，必须执行以下操作之一：</span><span class="sxs-lookup"><span data-stu-id="13bed-119">To prevent a scheduled job from running, you must do one of the following:</span></span>  
  
-   <span data-ttu-id="13bed-120">禁用计划。</span><span class="sxs-lookup"><span data-stu-id="13bed-120">Disable the schedule.</span></span>  
  
-   <span data-ttu-id="13bed-121">禁用作业。</span><span class="sxs-lookup"><span data-stu-id="13bed-121">Disable the job.</span></span>  
  
-   <span data-ttu-id="13bed-122">从作业分离计划。</span><span class="sxs-lookup"><span data-stu-id="13bed-122">Detach the schedule from the job.</span></span>  
  
-   <span data-ttu-id="13bed-123">停止 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服务。</span><span class="sxs-lookup"><span data-stu-id="13bed-123">Stop the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service.</span></span>  
  
-   <span data-ttu-id="13bed-124">删除计划。</span><span class="sxs-lookup"><span data-stu-id="13bed-124">Delete the schedule.</span></span>  
  
 <span data-ttu-id="13bed-125">即使计划未启用，作业仍可以为响应警报而运行，或者由用户手动运行。</span><span class="sxs-lookup"><span data-stu-id="13bed-125">If the schedule is not enabled, the job can still run in response to an alert or when a user runs the job manually.</span></span> <span data-ttu-id="13bed-126">如果作业计划未启用，则任何使用该计划的作业都不会启用该计划。</span><span class="sxs-lookup"><span data-stu-id="13bed-126">When a job schedule is not enabled, the schedule is not enabled for any job that uses the schedule.</span></span>  
  
 <span data-ttu-id="13bed-127">必须显式重新启用已禁用的计划。</span><span class="sxs-lookup"><span data-stu-id="13bed-127">You must explicitly re-enable a schedule that has been disabled.</span></span> <span data-ttu-id="13bed-128">编辑计划不会自动重新启用计划。</span><span class="sxs-lookup"><span data-stu-id="13bed-128">Editing the schedule does not automatically re-enable the schedule.</span></span>  
  
## <a name="scheduling-start-dates"></a><span data-ttu-id="13bed-129">计划开始日期</span><span class="sxs-lookup"><span data-stu-id="13bed-129">Scheduling Start Dates</span></span>  
 <span data-ttu-id="13bed-130">计划的开始日期必须不早于 19900101。</span><span class="sxs-lookup"><span data-stu-id="13bed-130">The start date of a schedule must be greater than or equal to 19900101.</span></span>  
  
 <span data-ttu-id="13bed-131">将计划附加到作业时，应查看计划用于首次运行作业的开始日期。</span><span class="sxs-lookup"><span data-stu-id="13bed-131">When you are attaching a schedule to a job, you should review the start date that the schedule uses to run the job for the first time.</span></span> <span data-ttu-id="13bed-132">开始日期取决于将计划附加到作业时的日期和时间。</span><span class="sxs-lookup"><span data-stu-id="13bed-132">The start date depends upon the day and time when you attach the schedule to the job.</span></span> <span data-ttu-id="13bed-133">例如，创建的计划为星期一的上午 8:00 运行，并且隔周运行。</span><span class="sxs-lookup"><span data-stu-id="13bed-133">For example, you create a schedule that runs every other Monday at 8:00 A.M.</span></span> <span data-ttu-id="13bed-134">如果您在 2008 年 3 月 3 日星期一上午 10:00 创建一个作业，</span><span class="sxs-lookup"><span data-stu-id="13bed-134">If you create a job at 10:00 A.M.</span></span> <span data-ttu-id="13bed-135">则计划开始日期是 2008 年 3 月 17 日星期一。</span><span class="sxs-lookup"><span data-stu-id="13bed-135">on Monday, March 3, 2008, the schedule start date is Monday, March 17, 2008.</span></span> <span data-ttu-id="13bed-136">如果您在 2008 年 3 月 4 日星期二创建另一个作业，则计划开始日期是 2008 年 3 月 10 日星期一。</span><span class="sxs-lookup"><span data-stu-id="13bed-136">If you create another job on Tuesday, March 4, 2008, the schedule start date is Monday, March 10, 2008.</span></span>  
  
 <span data-ttu-id="13bed-137">在将计划附加到作业后可更改计划的开始日期。</span><span class="sxs-lookup"><span data-stu-id="13bed-137">You can change the schedule start date after you attach the schedule to a job.</span></span>  
  
## <a name="cpu-idle-schedules"></a><span data-ttu-id="13bed-138">CPU 空闲计划</span><span class="sxs-lookup"><span data-stu-id="13bed-138">CPU Idle Schedules</span></span>  
 <span data-ttu-id="13bed-139">若要最大限度地利用 CPU 资源，可以为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理定义一个 CPU 空闲条件。</span><span class="sxs-lookup"><span data-stu-id="13bed-139">To maximize CPU resources, you can define a CPU idle condition for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="13bed-140">代理使用 CPU 空闲条件设置来确定运行作业的最佳时间。</span><span class="sxs-lookup"><span data-stu-id="13bed-140">Agent uses the CPU idle condition setting to determine the best time to run jobs.</span></span> <span data-ttu-id="13bed-141">例如，可计划作业，使其在 CPU 空闲时间和业务量较低时重新生成索引。</span><span class="sxs-lookup"><span data-stu-id="13bed-141">For example, you can schedule a job to rebuild indexes during CPU idle time and slow production periods.</span></span>  
  
 <span data-ttu-id="13bed-142">将作业定义为在 CPU 空闲时间运行之前，应确定正常处理过程中 CPU 的负荷。</span><span class="sxs-lookup"><span data-stu-id="13bed-142">Before you define jobs to run during CPU idle time, determine the load on the CPU during normal processing.</span></span> <span data-ttu-id="13bed-143">若要执行此操作，请使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 或性能监视器来监视服务器流量并收集统计信息。</span><span class="sxs-lookup"><span data-stu-id="13bed-143">To do this, use [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] or Performance Monitor to monitor server traffic and collect statistics.</span></span> <span data-ttu-id="13bed-144">然后，利用收集到的信息设置 CPU 空闲时间百分比和持续时间。</span><span class="sxs-lookup"><span data-stu-id="13bed-144">You can then use the information you gather to set the CPU idle time percentage and duration.</span></span>  
  
 <span data-ttu-id="13bed-145">将 CPU 空闲条件定义为一个百分比，在该百分比以下，CPU 使用率必须持续指定的时间。</span><span class="sxs-lookup"><span data-stu-id="13bed-145">Define the CPU idle condition as a percentage below which CPU usage must remain for a specified time.</span></span> <span data-ttu-id="13bed-146">然后，设置持续时间长度。</span><span class="sxs-lookup"><span data-stu-id="13bed-146">Next, set the amount of time.</span></span> <span data-ttu-id="13bed-147">如果 CPU 使用率在指定时间内低于指定的百分比，则 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理将启动具有 CPU 空闲时间计划的所有作业。</span><span class="sxs-lookup"><span data-stu-id="13bed-147">When the CPU usage is below the specified percentage for the specified amount of time, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent starts all jobs that have a CPU idle time schedule.</span></span> <span data-ttu-id="13bed-148">有关使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 或性能监视器来监视 cpu 使用率的详细信息，请参阅[监视 Cpu 使用情况](../../relational-databases/performance-monitor/monitor-cpu-usage.md)。</span><span class="sxs-lookup"><span data-stu-id="13bed-148">For more information on using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] or Performance Monitor to monitor CPU usage, see [Monitor CPU Usage](../../relational-databases/performance-monitor/monitor-cpu-usage.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="13bed-149">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="13bed-149">Related Tasks</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="13bed-150">**说明**</span><span class="sxs-lookup"><span data-stu-id="13bed-150">**Description**</span></span>|<span data-ttu-id="13bed-151">**主题**</span><span class="sxs-lookup"><span data-stu-id="13bed-151">**Topic**</span></span>|  
|<span data-ttu-id="13bed-152">介绍如何为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业创建计划。</span><span class="sxs-lookup"><span data-stu-id="13bed-152">Describes how to create a schedule for a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job.</span></span>|[<span data-ttu-id="13bed-153">创建计划</span><span class="sxs-lookup"><span data-stu-id="13bed-153">Create a Schedule</span></span>](create-a-schedule.md)|  
|<span data-ttu-id="13bed-154">介绍如何安排 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业计划。</span><span class="sxs-lookup"><span data-stu-id="13bed-154">Describes how to schedule a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job.</span></span>|[<span data-ttu-id="13bed-155">安排作业计划</span><span class="sxs-lookup"><span data-stu-id="13bed-155">Schedule a Job</span></span>](schedule-a-job.md)|  
|<span data-ttu-id="13bed-156">说明如何定义服务器的 CPU 空闲条件。</span><span class="sxs-lookup"><span data-stu-id="13bed-156">Explains how to define the CPU idle condition for your server.</span></span>|[<span data-ttu-id="13bed-157">设置 CPU 空闲时间和持续时间 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="13bed-157">Set CPU Idle Time and Duration &#40;SQL Server Management Studio&#41;</span></span>](set-cpu-idle-time-and-duration-sql-server-management-studio.md)|  
  
## <a name="see-also"></a><span data-ttu-id="13bed-158">另请参阅</span><span class="sxs-lookup"><span data-stu-id="13bed-158">See Also</span></span>  
 <span data-ttu-id="13bed-159">[sp_help_jobschedule &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-help-jobschedule-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="13bed-159">[sp_help_jobschedule &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-jobschedule-transact-sql) </span></span>  
 [<span data-ttu-id="13bed-160">dbo.sysjobschedules &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="13bed-160">dbo.sysjobschedules &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-tables/dbo-sysjobschedules-transact-sql)  
  
  
