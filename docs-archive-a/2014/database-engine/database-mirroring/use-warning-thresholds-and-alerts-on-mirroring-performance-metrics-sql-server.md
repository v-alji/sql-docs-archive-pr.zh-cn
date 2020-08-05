---
title: 对镜像性能指标使用警告阈值和警报 (SQL Server) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- monitoring database mirroring [SQL Server]
- thresholds [SQL Server]
- database mirroring [SQL Server], managing in SQL Server Management Studio
- alerts [SQL Server], database mirroring
- database mirroring [SQL Server], monitoring
- warnings [database mirroring]
ms.assetid: 8cdd1515-0bd7-4f8c-a7fc-a33b575e20f6
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 908b234143bc7e2140fe1c98d85ba150ea69b28d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580867"
---
# <a name="use-warning-thresholds-and-alerts-on-mirroring-performance-metrics-sql-server"></a><span data-ttu-id="4c9a8-102">使用镜像性能度量的警告阈值和警报 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="4c9a8-102">Use Warning Thresholds and Alerts on Mirroring Performance Metrics (SQL Server)</span></span>
  <span data-ttu-id="4c9a8-103">本主题包含有关一些 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 事件的信息，可以为这些事件配置和管理用于数据库镜像的警告阈值。</span><span class="sxs-lookup"><span data-stu-id="4c9a8-103">This topic contains information about the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] events for which warning thresholds can be configured and managed for database mirroring.</span></span> <span data-ttu-id="4c9a8-104">可以使用数据库镜像监视器或 **sp_dbmmonitorchangealert**、 **sp_dbmmonitorhelpalert**和 **sp_dbmmonitordropalert** 存储过程。</span><span class="sxs-lookup"><span data-stu-id="4c9a8-104">You can use the  Database Mirroring Monitor or the **sp_dbmmonitorchangealert**, **sp_dbmmonitorhelpalert**, and **sp_dbmmonitordropalert** stored procedures.</span></span> <span data-ttu-id="4c9a8-105">本主题还包含有关对数据库镜像事件配置警报的信息。</span><span class="sxs-lookup"><span data-stu-id="4c9a8-105">This topic also contains information about configuring alerts on database mirroring events.</span></span>  
  
 <span data-ttu-id="4c9a8-106">针对镜像数据库建立监视之后，系统管理员可以为多个关键绩效指标配置警告阈值。</span><span class="sxs-lookup"><span data-stu-id="4c9a8-106">After monitoring is established for a mirrored database, a system administrator can configure warning thresholds on several key performance metrics.</span></span> <span data-ttu-id="4c9a8-107">同时，管理员还可以为这些数据库镜像事件和其他数据库镜像事件配置警报。</span><span class="sxs-lookup"><span data-stu-id="4c9a8-107">Also, an administrator can configure alerts on these and other database mirroring events.</span></span>  
  
 <span data-ttu-id="4c9a8-108">**本主题内容：**</span><span class="sxs-lookup"><span data-stu-id="4c9a8-108">**In This Topic:**</span></span>  
  
-   [<span data-ttu-id="4c9a8-109">性能指标和警告阈值</span><span class="sxs-lookup"><span data-stu-id="4c9a8-109">Performance Metrics and Warning Thresholds</span></span>](#PerfMetricsAndWarningThresholds)  
  
-   [<span data-ttu-id="4c9a8-110">设置和管理警告阈值</span><span class="sxs-lookup"><span data-stu-id="4c9a8-110">Setting Up and Managing Warning Thresholds</span></span>](#SetUpManageWarningThresholds)  
  
-   [<span data-ttu-id="4c9a8-111">将警报用于镜像数据库</span><span class="sxs-lookup"><span data-stu-id="4c9a8-111">Using Alerts for a Mirrored Database</span></span>](#UseAlerts)  
  
-   [<span data-ttu-id="4c9a8-112">相关任务</span><span class="sxs-lookup"><span data-stu-id="4c9a8-112">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="performance-metrics-and-warning-thresholds"></a><a name="PerfMetricsAndWarningThresholds"></a> <span data-ttu-id="4c9a8-113">性能指标和警告阈值</span><span class="sxs-lookup"><span data-stu-id="4c9a8-113">Performance Metrics and Warning Thresholds</span></span>  
 <span data-ttu-id="4c9a8-114">下表列出可为其配置警告的性能指标，说明相应的警告阈值并列出相应的数据库镜像监视器标签。</span><span class="sxs-lookup"><span data-stu-id="4c9a8-114">The following table lists the performance metrics for which warnings can be configured, describes the corresponding warning threshold, and lists the corresponding Database Mirroring Monitor label.</span></span>  
  
|<span data-ttu-id="4c9a8-115">性能指标</span><span class="sxs-lookup"><span data-stu-id="4c9a8-115">Performance metric</span></span>|<span data-ttu-id="4c9a8-116">警告阈值</span><span class="sxs-lookup"><span data-stu-id="4c9a8-116">Warning threshold</span></span>|<span data-ttu-id="4c9a8-117">数据库镜像监视器标签</span><span class="sxs-lookup"><span data-stu-id="4c9a8-117">Database Mirroring Monitor label</span></span>|  
|------------------------|-----------------------|--------------------------------------|  
|<span data-ttu-id="4c9a8-118">未发送日志</span><span class="sxs-lookup"><span data-stu-id="4c9a8-118">Unsent log</span></span>|<span data-ttu-id="4c9a8-119">指定未发送日志达到多少 KB 后，在主体服务器实例上生成一个警告。</span><span class="sxs-lookup"><span data-stu-id="4c9a8-119">Specifies how many kilobytes (KB) of unsent log generate a warning on the principal server instance.</span></span> <span data-ttu-id="4c9a8-120">此警告有助于根据 KB 度量数据丢失的可能性，尤其与高性能模式相关。</span><span class="sxs-lookup"><span data-stu-id="4c9a8-120">This warning helps measure the potential for data loss in terms of KB and is especially relevant for high-performance mode.</span></span> <span data-ttu-id="4c9a8-121">但是，当镜像因伙伴断开连接而暂停或挂起时，该警告也适用于高安全模式。</span><span class="sxs-lookup"><span data-stu-id="4c9a8-121">However, the warning is also relevant for high-safety mode when mirroring is paused or suspended because the partners become disconnected.</span></span>|<span data-ttu-id="4c9a8-122">**如果未发送日志超出了阈值，则发出警告**</span><span class="sxs-lookup"><span data-stu-id="4c9a8-122">**Warn if the unsent log exceeds the threshold**</span></span>|  
|<span data-ttu-id="4c9a8-123">未还原日志</span><span class="sxs-lookup"><span data-stu-id="4c9a8-123">Unrestored log</span></span>|<span data-ttu-id="4c9a8-124">指定未还原日志达到多少 KB 后，会在镜像服务器实例上生成一个警告。</span><span class="sxs-lookup"><span data-stu-id="4c9a8-124">Specifies how many KB of unrestored log generate a warning on the mirror server instance.</span></span> <span data-ttu-id="4c9a8-125">此警告可以帮助度量故障转移时间。</span><span class="sxs-lookup"><span data-stu-id="4c9a8-125">This warning helps measure failover time.</span></span> <span data-ttu-id="4c9a8-126">“故障转移时间 ”主要包括前一个镜像服务器前滚其重做队列中剩余的任意日志所需的时间，以及一小段额外时间。</span><span class="sxs-lookup"><span data-stu-id="4c9a8-126">*Failover time* consists mainly of the time that the former mirror server requires to roll forward any log remaining in its redo queue, plus a short additional time.</span></span><br /><br /> <span data-ttu-id="4c9a8-127">注意：对于自动故障转移，系统识别错误所需的时间与故障转移时间无关。</span><span class="sxs-lookup"><span data-stu-id="4c9a8-127">Note: For an automatic failover, the time for the system to notice the error is independent of the failover time.</span></span><br /><br /> <span data-ttu-id="4c9a8-128">有关详细信息，请参阅 [估计在角色切换期间服务的中断（数据库镜像）](estimate-the-interruption-of-service-during-role-switching-database-mirroring.md)。</span><span class="sxs-lookup"><span data-stu-id="4c9a8-128">For more information, see [Estimate the Interruption of Service During Role Switching &#40;Database Mirroring&#41;](estimate-the-interruption-of-service-during-role-switching-database-mirroring.md).</span></span>|<span data-ttu-id="4c9a8-129">**如果未还原日志超出了阈值，则发出警告**</span><span class="sxs-lookup"><span data-stu-id="4c9a8-129">**Warn if the unrestored log exceeds the threshold**</span></span>|  
|<span data-ttu-id="4c9a8-130">最早的未发送事务</span><span class="sxs-lookup"><span data-stu-id="4c9a8-130">Oldest unsent transaction</span></span>|<span data-ttu-id="4c9a8-131">指定在主体服务器实例上生成警告之前，发送队列中可以累积的事务的分钟数。</span><span class="sxs-lookup"><span data-stu-id="4c9a8-131">Specifies the number of minutes worth of transactions that can accumulate in the send queue before a warning is generated on the principal server instance.</span></span> <span data-ttu-id="4c9a8-132">此警告有助于根据时间度量数据丢失的可能性，尤其与高性能模式相关。</span><span class="sxs-lookup"><span data-stu-id="4c9a8-132">This warning helps measure the potential for data loss in terms of time and is especially relevant for high-performance mode.</span></span> <span data-ttu-id="4c9a8-133">但是，当镜像因伙伴断开连接而暂停或挂起时，该警告也适用于高安全模式。</span><span class="sxs-lookup"><span data-stu-id="4c9a8-133">However, the warning is also relevant for high-safety mode when mirroring is paused or suspended because the partners become disconnected.</span></span>|<span data-ttu-id="4c9a8-134">**如果最早的未发送事务的保留时间超出了阈值，则发出警告**</span><span class="sxs-lookup"><span data-stu-id="4c9a8-134">**Warn if the age of the oldest unsent transaction exceeds the threshold**</span></span>|  
|<span data-ttu-id="4c9a8-135">镜像提交开销</span><span class="sxs-lookup"><span data-stu-id="4c9a8-135">Mirror commit overhead</span></span>|<span data-ttu-id="4c9a8-136">指定在主体服务器上生成警告之前，每个事务可允许的平均延迟的毫秒数。</span><span class="sxs-lookup"><span data-stu-id="4c9a8-136">Specifies the number of milliseconds of average delay per transaction that are tolerated before a warning is generated on the principal server.</span></span> <span data-ttu-id="4c9a8-137">此延迟是主体服务器实例等待镜像服务器实例将事务日志记录写入重做队列时，所发生的开销量。</span><span class="sxs-lookup"><span data-stu-id="4c9a8-137">This delay is the amount of overhead incurred while the principal server instance waits for the mirror server instance to write the transaction's log record into the redo queue.</span></span> <span data-ttu-id="4c9a8-138">该值只适用于高安全模式。</span><span class="sxs-lookup"><span data-stu-id="4c9a8-138">This value is relevant only in high-safety mode.</span></span>|<span data-ttu-id="4c9a8-139">**如果镜像提交开销超过了阈值则发出警告**</span><span class="sxs-lookup"><span data-stu-id="4c9a8-139">**Warn if the mirror commit overhead exceeds the threshold**</span></span>|  
  
 <span data-ttu-id="4c9a8-140">对于上述任何一个性能指标，系统管理员都可以指定镜像数据库的阈值。</span><span class="sxs-lookup"><span data-stu-id="4c9a8-140">For any one of these performance metrics, a system administrator can specify a threshold on a mirrored database.</span></span> <span data-ttu-id="4c9a8-141">有关详细信息，请参阅本主题后面的 [设置和管理警告阈值](#SetUpManageWarningThresholds)。</span><span class="sxs-lookup"><span data-stu-id="4c9a8-141">For more information, see [Setting Up and Managing Warning Thresholds](#SetUpManageWarningThresholds), later in this topic.</span></span>  
  
##  <a name="setting-up-and-managing-warning-thresholds"></a><a name="SetUpManageWarningThresholds"></a> <span data-ttu-id="4c9a8-142">设置和管理警告阈值</span><span class="sxs-lookup"><span data-stu-id="4c9a8-142">Setting Up and Managing Warning Thresholds</span></span>  
 <span data-ttu-id="4c9a8-143">系统管理员可以为关键镜像性能指标配置一个或多个警告阈值。</span><span class="sxs-lookup"><span data-stu-id="4c9a8-143">A system administrator can configure one or more warning thresholds for the key mirroring performance metrics.</span></span> <span data-ttu-id="4c9a8-144">我们建议为伙伴双方都设置给定警告的阈值，以确保即使出现数据库故障转移的情况，警告也会一直保留。</span><span class="sxs-lookup"><span data-stu-id="4c9a8-144">We recommend setting a threshold for a given warning on both partners to make sure that the warning persists if the database fails over.</span></span> <span data-ttu-id="4c9a8-145">每个伙伴的适当阈值都取决于该伙伴系统的性能。</span><span class="sxs-lookup"><span data-stu-id="4c9a8-145">The appropriate threshold on each partner depends on the performance capabilities of that partner's system.</span></span>  
  
 <span data-ttu-id="4c9a8-146">可以使用下列任意一项配置和管理警告阈值：</span><span class="sxs-lookup"><span data-stu-id="4c9a8-146">Warning thresholds can be configured and managed by using either of the following:</span></span>  
  
-   <span data-ttu-id="4c9a8-147">数据库镜像监视器</span><span class="sxs-lookup"><span data-stu-id="4c9a8-147">Database Mirroring Monitor</span></span>  
  
     <span data-ttu-id="4c9a8-148">在数据库镜像监视器中，管理员可以通过选择 **“警告”** 选项卡式页面，同时查看主体服务器实例和镜像服务器实例上选定数据库的当前警告配置。</span><span class="sxs-lookup"><span data-stu-id="4c9a8-148">In Database Mirroring Monitor, the administrator can view the current configuration of warnings for a selected database at both the principal and mirror server instances at the same time by selecting the **Warnings** tabbed page.</span></span> <span data-ttu-id="4c9a8-149">在此页上，管理员可以打开 **“设置警告阈值”** 对话框以启用和配置一个或多个警告阈值。</span><span class="sxs-lookup"><span data-stu-id="4c9a8-149">From there, the administrator can open the **Set Warning Thresholds** dialog box to enable and configure one or more warning thresholds.</span></span>  
  
     <span data-ttu-id="4c9a8-150">有关数据库镜像监视器界面的介绍，请参阅 [Database Mirroring Monitor Overview](database-mirroring-monitor-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="4c9a8-150">For an introduction to the Database Mirroring Monitor interface, see [Database Mirroring Monitor Overview](database-mirroring-monitor-overview.md).</span></span> <span data-ttu-id="4c9a8-151">有关启动数据库镜像监视器的信息，请参阅 [启动数据库镜像监视器 (SQL Server Management Studio)](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="4c9a8-151">For information about launching Database Mirroring Monitor, see [Start Database Mirroring Monitor &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md).</span></span>  
  
-   <span data-ttu-id="4c9a8-152">系统存储过程</span><span class="sxs-lookup"><span data-stu-id="4c9a8-152">System stored procedures</span></span>  
  
     <span data-ttu-id="4c9a8-153">管理员可以使用下面一组系统存储过程，针对伙伴双方的镜像数据库，分别设置和管理警告阈值。</span><span class="sxs-lookup"><span data-stu-id="4c9a8-153">The following set of system stored procedures enable an administrator to set up and manage warning thresholds on mirrored databases of one partner at a time.</span></span>  
  
    |<span data-ttu-id="4c9a8-154">过程</span><span class="sxs-lookup"><span data-stu-id="4c9a8-154">Procedure</span></span>|<span data-ttu-id="4c9a8-155">说明</span><span class="sxs-lookup"><span data-stu-id="4c9a8-155">Description</span></span>|  
    |---------------|-----------------|  
    |[<span data-ttu-id="4c9a8-156">sp_dbmmonitorchangealert (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4c9a8-156">sp_dbmmonitorchangealert &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dbmmonitorchangealert-transact-sql)|<span data-ttu-id="4c9a8-157">添加或更改指定镜像性能指标的警告阈值。</span><span class="sxs-lookup"><span data-stu-id="4c9a8-157">Adds or changes warning threshold for a specified mirroring performance metric.</span></span>|  
    |[<span data-ttu-id="4c9a8-158">sp_dbmmonitorhelpalert (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4c9a8-158">sp_dbmmonitorhelpalert &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dbmmonitorhelpalert-transact-sql)|<span data-ttu-id="4c9a8-159">返回若干个关键数据库镜像监视器性能指标中的一个或所有指标的警告阈值信息。</span><span class="sxs-lookup"><span data-stu-id="4c9a8-159">Returns information about warning thresholds on one or all of several key database mirroring monitor performance metrics.</span></span>|  
    |[<span data-ttu-id="4c9a8-160">sp_dbmmonitordropalert (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4c9a8-160">sp_dbmmonitordropalert &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dbmmonitordropalert-transact-sql)|<span data-ttu-id="4c9a8-161">删除指定性能指标的警告。</span><span class="sxs-lookup"><span data-stu-id="4c9a8-161">Drops the warning for a specified performance metric.</span></span>|  
  
## <a name="performance-threshold-events-sent-to-the-windows-event-log"></a><span data-ttu-id="4c9a8-162">发送到 Windows 事件日志的性能阈值事件</span><span class="sxs-lookup"><span data-stu-id="4c9a8-162">Performance-Threshold Events Sent to the Windows Event Log</span></span>  
 <span data-ttu-id="4c9a8-163">如果为性能指标定义了警告阈值，则在更新状态表时，将针对阈值计算最新的值。</span><span class="sxs-lookup"><span data-stu-id="4c9a8-163">If warning thresholdis defined for a performance metric, when the status table is updated, the latest value is evaluated against the threshold.</span></span> <span data-ttu-id="4c9a8-164">如果已达到阈值，则更新过程**sp_dbmmonitorupdate**将为指标生成一个信息事件-*性能阈值事件*，并将事件写入 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 事件日志。</span><span class="sxs-lookup"><span data-stu-id="4c9a8-164">If the threshold has been reached, the update procedure, **sp_dbmmonitorupdate**, generates an informational event-a *performance-threshold event*- for the metric and writes the event to the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows event log.</span></span> <span data-ttu-id="4c9a8-165">下表列出性能阈值事件的 ID。</span><span class="sxs-lookup"><span data-stu-id="4c9a8-165">The following table lists the event IDs of the performance-threshold events.</span></span>  
  
|<span data-ttu-id="4c9a8-166">性能指标</span><span class="sxs-lookup"><span data-stu-id="4c9a8-166">Performance metric</span></span>|<span data-ttu-id="4c9a8-167">事件 ID</span><span class="sxs-lookup"><span data-stu-id="4c9a8-167">Event ID</span></span>|  
|------------------------|--------------|  
|<span data-ttu-id="4c9a8-168">未发送日志</span><span class="sxs-lookup"><span data-stu-id="4c9a8-168">Unsent log</span></span>|<span data-ttu-id="4c9a8-169">32042</span><span class="sxs-lookup"><span data-stu-id="4c9a8-169">32042</span></span>|  
|<span data-ttu-id="4c9a8-170">未还原日志</span><span class="sxs-lookup"><span data-stu-id="4c9a8-170">Unrestored log</span></span>|<span data-ttu-id="4c9a8-171">32043</span><span class="sxs-lookup"><span data-stu-id="4c9a8-171">32043</span></span>|  
|<span data-ttu-id="4c9a8-172">最早的未发送事务</span><span class="sxs-lookup"><span data-stu-id="4c9a8-172">Oldest unsent transaction</span></span>|<span data-ttu-id="4c9a8-173">32040</span><span class="sxs-lookup"><span data-stu-id="4c9a8-173">32040</span></span>|  
|<span data-ttu-id="4c9a8-174">镜像提交开销</span><span class="sxs-lookup"><span data-stu-id="4c9a8-174">Mirror commit overhead</span></span>|<span data-ttu-id="4c9a8-175">32044</span><span class="sxs-lookup"><span data-stu-id="4c9a8-175">32044</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="4c9a8-176">管理员可以针对这些事件中的任何一个或多个定义警报。</span><span class="sxs-lookup"><span data-stu-id="4c9a8-176">An administrator can define alerts on any one or more of these events.</span></span> <span data-ttu-id="4c9a8-177">有关详细信息，请参阅本主题后面的 [将警报用于镜像数据库](#UseAlerts)</span><span class="sxs-lookup"><span data-stu-id="4c9a8-177">For more information, see [Using Alerts for a Mirrored Database](#UseAlerts), later in this</span></span>  
>   
>  <span data-ttu-id="4c9a8-178">。</span><span class="sxs-lookup"><span data-stu-id="4c9a8-178">topic.</span></span>  
  
##  <a name="using-alerts-for-a-mirrored-database"></a><a name="UseAlerts"></a><span data-ttu-id="4c9a8-179">使用镜像数据库的警报</span><span class="sxs-lookup"><span data-stu-id="4c9a8-179">Using Alerts for a Mirrored Database</span></span>  
 <span data-ttu-id="4c9a8-180">监视镜像数据库的一个重要组成部分就是针对重要的数据库镜像事件配置警报。</span><span class="sxs-lookup"><span data-stu-id="4c9a8-180">An important part of monitoring a mirrored database is configuring alerts on significant database mirro events.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="4c9a8-181">可生成下列数据库镜像事件类型：</span><span class="sxs-lookup"><span data-stu-id="4c9a8-181">generates the following types of database mirroring events:</span></span>  
  
-   <span data-ttu-id="4c9a8-182">性能阈值事件</span><span class="sxs-lookup"><span data-stu-id="4c9a8-182">Performance threshold events</span></span>  
  
     <span data-ttu-id="4c9a8-183">有关详细信息，请参阅本主题前面的“发送到 Windows 事件日志的性能阈值事件”。</span><span class="sxs-lookup"><span data-stu-id="4c9a8-183">For more information, see "Performance-Threshold Events Sent to the Windows Event Log" earlier in this topic.</span></span>  
  
-   <span data-ttu-id="4c9a8-184">状态更改事件</span><span class="sxs-lookup"><span data-stu-id="4c9a8-184">State-change events</span></span>  
  
     <span data-ttu-id="4c9a8-185">这些事件为 Windows Management Instrumentation (WMI) 事件，在数据库镜像会话的内部状态发生更改时生成。</span><span class="sxs-lookup"><span data-stu-id="4c9a8-185">These are Windows Management Instrumentation (WMI) events that are generated when changes occur in the internal state of a database mirroring session.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4c9a8-186">有关详细信息，请参阅 [WMI Provider for Server Events 的概念](../../relational-databases/wmi-provider-server-events/wmi-provider-for-server-events-concepts.md)。</span><span class="sxs-lookup"><span data-stu-id="4c9a8-186">For more information, see [WMI Provider for Server Events Concepts](../../relational-databases/wmi-provider-server-events/wmi-provider-for-server-events-concepts.md).</span></span>  
  
 <span data-ttu-id="4c9a8-187">系统管理员可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理或其他应用程序（例如 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Operations Manager）针对这些事件配置警报。</span><span class="sxs-lookup"><span data-stu-id="4c9a8-187">A system administrator can configure alerts on these by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent or other applications, such as [!INCLUDE[msCoName](../../includes/msconame-md.md)] Operations Manager.</span></span>  
  
 <span data-ttu-id="4c9a8-188">当针对数据库镜像事件定义警报时，我们建议在伙伴双方服务器实例上同时定义警告阈值和警报。</span><span class="sxs-lookup"><span data-stu-id="4c9a8-188">When you define alerts on database mirroring events, we recommend that you define warning thresholds and alerts at both partner server instances.</span></span> <span data-ttu-id="4c9a8-189">可以在主体服务器或镜像服务器上生成单独的事件，但是每个伙伴都可以随时执行其中任意一种角色。</span><span class="sxs-lookup"><span data-stu-id="4c9a8-189">Individual events are generated at either the principal server or the mirror server, but each partner can perform either role at any time.</span></span> <span data-ttu-id="4c9a8-190">为了确保警报在故障转移后继续有效，必须同时在伙伴双方上定义警报。</span><span class="sxs-lookup"><span data-stu-id="4c9a8-190">To make sure that an alert continues to operate after a failover, the alert must be defined at both partners.</span></span>  
  
 <span data-ttu-id="4c9a8-191">有关详细信息，请参阅此 [SQL Server 网站](../../database-engine/database-mirroring/use-warning-thresholds-and-alerts-on-mirroring-performance-metrics-sql-server.md)上有关数据库镜像事件警报的白皮书。</span><span class="sxs-lookup"><span data-stu-id="4c9a8-191">For more information, see the white paper about alerting on database mirroring events at this [SQL Server Web site](../../database-engine/database-mirroring/use-warning-thresholds-and-alerts-on-mirroring-performance-metrics-sql-server.md).</span></span> <span data-ttu-id="4c9a8-192">此白皮书包含有关如何使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理、数据库镜像 WMI 事件以及示例脚本配置警报的信息。</span><span class="sxs-lookup"><span data-stu-id="4c9a8-192">This white paper contains information about how to configure alerts using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, the database mirroring WMI events, and sample scripts.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="4c9a8-193">对于所有镜像会话，我们极力建议您将数据库配置为针对任意状态更改事件发送警报。</span><span class="sxs-lookup"><span data-stu-id="4c9a8-193">For all mirroring sessions, we strongly recommend that you configure the database to send an alert on any state-change events.</span></span> <span data-ttu-id="4c9a8-194">除非专门通过手动配置更改来实现状态更改，否则会出现危及数据安全的情况。</span><span class="sxs-lookup"><span data-stu-id="4c9a8-194">Unless a state change is expected as the result of a manual configuration change, something has occurred that could compromise your data.</span></span> <span data-ttu-id="4c9a8-195">为了帮助保护数据，请找出状态发生意外更改的原因并予以纠正。</span><span class="sxs-lookup"><span data-stu-id="4c9a8-195">To help protect your data, identify and fix the cause of an unexpected state change.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="4c9a8-196">相关任务</span><span class="sxs-lookup"><span data-stu-id="4c9a8-196">Related Tasks</span></span>  
 <span data-ttu-id="4c9a8-197">**使用 SQL Server Management Studio 创建警报**</span><span class="sxs-lookup"><span data-stu-id="4c9a8-197">**To create an alert using SQL Server Management Studio**</span></span>  
  
-   [<span data-ttu-id="4c9a8-198">使用错误号创建警报</span><span class="sxs-lookup"><span data-stu-id="4c9a8-198">Create an Alert Using an Error Number</span></span>](../../ssms/agent/create-an-alert-using-an-error-number.md)  
  
-   [<span data-ttu-id="4c9a8-199">创建 WMI 事件警报</span><span class="sxs-lookup"><span data-stu-id="4c9a8-199">Create a WMI Event Alert</span></span>](../../ssms/agent/create-a-wmi-event-alert.md)  
  
 <span data-ttu-id="4c9a8-200">**监视数据库镜像**</span><span class="sxs-lookup"><span data-stu-id="4c9a8-200">**To monitor database mirroring**</span></span>  
  
-   [<span data-ttu-id="4c9a8-201">启动数据库镜像监视器 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="4c9a8-201">Start Database Mirroring Monitor &#40;SQL Server Management Studio&#41;</span></span>](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="4c9a8-202">sp_dbmmonitoraddmonitoring (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4c9a8-202">sp_dbmmonitoraddmonitoring &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dbmmonitoraddmonitoring-transact-sql)  
  
-   [<span data-ttu-id="4c9a8-203">sp_dbmmonitorchangealert (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4c9a8-203">sp_dbmmonitorchangealert &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dbmmonitorchangealert-transact-sql)  
  
-   [<span data-ttu-id="4c9a8-204">sp_dbmmonitorchangemonitoring (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4c9a8-204">sp_dbmmonitorchangemonitoring &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dbmmonitorchangemonitoring-transact-sql)  
  
-   [<span data-ttu-id="4c9a8-205">sp_dbmmonitordropalert (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4c9a8-205">sp_dbmmonitordropalert &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dbmmonitordropalert-transact-sql)  
  
-   [<span data-ttu-id="4c9a8-206">sp_dbmmonitordropmonitoring (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4c9a8-206">sp_dbmmonitordropmonitoring &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dbmmonitordropmonitoring-transact-sql)  
  
-   [<span data-ttu-id="4c9a8-207">sp_dbmmonitorhelpalert (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4c9a8-207">sp_dbmmonitorhelpalert &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dbmmonitorhelpalert-transact-sql)  
  
-   [<span data-ttu-id="4c9a8-208">sp_dbmmonitorhelpmonitoring (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4c9a8-208">sp_dbmmonitorhelpmonitoring &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dbmmonitorhelpmonitoring-transact-sql)  
  
-   [<span data-ttu-id="4c9a8-209">sp_dbmmonitorresults (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4c9a8-209">sp_dbmmonitorresults &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dbmmonitorresults-transact-sql)  
  
-   [<span data-ttu-id="4c9a8-210">sp_dbmmonitorupdate (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4c9a8-210">sp_dbmmonitorupdate &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dbmmonitorupdate-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="4c9a8-211">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4c9a8-211">See Also</span></span>  
 <span data-ttu-id="4c9a8-212">[数据库镜像 (SQL Server)](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="4c9a8-212">[Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="4c9a8-213">监视数据库镜像 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="4c9a8-213">Monitoring Database Mirroring &#40;SQL Server&#41;</span></span>](monitoring-database-mirroring-sql-server.md)  
  
  
