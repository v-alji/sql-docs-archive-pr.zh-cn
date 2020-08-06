---
title: 监视数据库镜像 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- monitoring [SQL Server], database mirroring
- database mirroring [SQL Server], monitoring
ms.assetid: a7b1b9b0-7c19-4acc-9de3-3a7c5e70694d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 92179abd47df2ee40b48be8eade7ea3e7b9267af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690132"
---
# <a name="monitoring-database-mirroring-sql-server"></a><span data-ttu-id="b5fe2-102">监视数据库镜像 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="b5fe2-102">Monitoring Database Mirroring (SQL Server)</span></span>
  <span data-ttu-id="b5fe2-103">本节介绍数据库镜像监视器和 **sp_dbmmonitor** 系统存储过程，说明数据库镜像监视的工作方式（包括“数据库镜像监视器作业”），并概括介绍可以监视的有关数据库镜像会话的信息。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-103">This section introduces Database Mirroring Monitor and the **sp_dbmmonitor** system stored procedures, explains how database mirroring monitoring works (including the **Database Mirroring Monitor Job)**, and summarizes the information that you can monitor about database mirroring sessions.</span></span> <span data-ttu-id="b5fe2-104">此外，本节还介绍如何为一组预定义数据库镜像事件定义警告阈值，以及如何设置有关任意数据库镜像事件的警报。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-104">Additionally, this section introduces how to define warning thresholds for a set of predefined database mirroring events and how to set up alerts on any database mirroring event.</span></span>  
  
 <span data-ttu-id="b5fe2-105">可以在镜像会话期间监视镜像数据库，以验证数据是否流动以及流动的情况。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-105">You can monitor a mirrored database during a mirroring session to verify whether and how well data is flowing.</span></span> <span data-ttu-id="b5fe2-106">若要对服务器实例上的一个或多个镜像数据库进行监视设置和管理，可以使用数据库镜像监视器或 **sp_dbmmonitor** 系统存储过程。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-106">To set up and manage monitoring for one or more of the mirrored databases on a server instance, you can use either Database Mirroring Monitor or the **sp_dbmmonitor** system stored procedures.</span></span>  
  
 <span data-ttu-id="b5fe2-107">数据库镜像监视作业（ **“数据库镜像监视器作业”** ）在后台独立于数据库镜像监视器运行。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-107">A database mirroring monitoring job, **Database Mirroring Monitor Job**, operates in the background, independently of Database Mirroring Monitor.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="b5fe2-108">代理定期调用 **“数据库镜像监视器作业”** ，默认为每分钟调用一次；而作业将调用更新镜像状态的存储过程。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-108">Agent calls **Database Mirroring Monitor Job** at regular intervals, the default is once a minute, and the job calls a stored procedure that updates mirroring status.</span></span> <span data-ttu-id="b5fe2-109">如果使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 启动镜像会话，将自动创建 **“数据库镜像监视器作业”** 。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-109">If you use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to start a mirroring session, **Database Mirroring Monitor Job** is created automatically.</span></span> <span data-ttu-id="b5fe2-110">但是，如果仅使用 ALTER DATABASE *<database_name>* SET PARTNER 来启动镜像，则必须通过运行存储过程来创建作业。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-110">However, if you only use ALTER DATABASE *<database_name>* SET PARTNER to start mirroring, you must create the job by running a stored procedure.</span></span>  
  
 <span data-ttu-id="b5fe2-111">**本主题内容：**</span><span class="sxs-lookup"><span data-stu-id="b5fe2-111">**In this Topic:**</span></span>  
  
-   [<span data-ttu-id="b5fe2-112">监视镜像状态</span><span class="sxs-lookup"><span data-stu-id="b5fe2-112">Monitoring Mirroring Status</span></span>](#MonitoringStatus)  
  
-   [<span data-ttu-id="b5fe2-113">有关镜像数据库的其他信息源</span><span class="sxs-lookup"><span data-stu-id="b5fe2-113">Additional Sources of Information About a Mirrored Database</span></span>](#AdditionalSources)  
  
-   [<span data-ttu-id="b5fe2-114">相关任务</span><span class="sxs-lookup"><span data-stu-id="b5fe2-114">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="monitoring-mirroring-status"></a><a name="MonitoringStatus"></a> <span data-ttu-id="b5fe2-115">监视镜像状态</span><span class="sxs-lookup"><span data-stu-id="b5fe2-115">Monitoring Mirroring Status</span></span>  
 <span data-ttu-id="b5fe2-116">若要对服务器实例上一个或多个镜像数据库进行监视设置和管理，可以使用数据库镜像监视器或 **dbmmonitor** 系统存储过程。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-116">To set up and manage monitoring for one or more of the mirrored databases on a server instance, you can use either Database Mirroring Monitor or the **dbmmonitor** system stored procedures.</span></span> <span data-ttu-id="b5fe2-117">可以在镜像会话期间监视镜像数据库，以验证数据是否流动以及流动的情况。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-117">You can monitor a mirrored database during a mirroring session to verify whether and how well data is flowing.</span></span>  
  
 <span data-ttu-id="b5fe2-118">具体而言，监视镜像数据库可以：</span><span class="sxs-lookup"><span data-stu-id="b5fe2-118">Specifically, monitoring a mirrored database enables you to:</span></span>  
  
-   <span data-ttu-id="b5fe2-119">验证镜像是否正在运行。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-119">Verify that mirroring is functioning.</span></span>  
  
     <span data-ttu-id="b5fe2-120">基本状况包括了解这两个服务器实例是否正常运行，服务器是否已连接，以及是否将日志从主体服务器移至镜像服务器。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-120">Basic status includes knowing if the two server instances are up, that the servers are connected, and that the log is being moved from the principal to the mirror.</span></span>  
  
-   <span data-ttu-id="b5fe2-121">确定镜像数据库是否与主体数据库保持同步。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-121">Determine whether the mirror database is keeping up with the principal database.</span></span>  
  
     <span data-ttu-id="b5fe2-122">在高性能模式下，主体服务器可能会积压大量仍需发送到镜像服务器的未发送日志记录。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-122">During high-performance mode, a principal server can develop a backlog of unsent log records that still need to be sent from the principal server to the mirror server.</span></span> <span data-ttu-id="b5fe2-123">而且在任意运行模式下，镜像服务器也有可能积压大量已写入日志文件但仍需在镜像数据库中进行还原的未还原日志记录。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-123">Furthermore, in any operating mode, the mirror server can develop a backlog of unrestored log records that have been written to the log file but still need to be restored on the mirror database.</span></span>  
  
-   <span data-ttu-id="b5fe2-124">确定在高性能模式下，当主体服务器实例变得不可用时所丢失的数据量。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-124">Determine how much data was lost when the principal server instance becomes unavailable during high-performance mode.</span></span>  
  
     <span data-ttu-id="b5fe2-125">可以通过查看未发送的事务日志量（如果有）以及在主体服务器上提交丢失事务的时间间隔，来确定数据的丢失量。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-125">You can determine data loss by looking at the amount of unsent transaction log (if any) and the time interval in which the lost transactions were committed at the principal.</span></span>  
  
-   <span data-ttu-id="b5fe2-126">将当前性能与过去性能进行比较。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-126">Compare current performance with past performance.</span></span>  
  
     <span data-ttu-id="b5fe2-127">出现问题时，数据库管理员可以查看镜像性能的历史记录来帮助了解当前状态。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-127">When problems are occurring, a database administrator can view a history of the mirroring performance to help in understanding the current state.</span></span> <span data-ttu-id="b5fe2-128">通过查看历史记录，用户可以检测性能走向，识别性能问题的模式（例如，一天当中网络变慢或进入日志中的命令数变得异常庞大的时间）。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-128">Looking at the history can allow the user to detect trends in performance, identify patterns of performance problems (such as times of day when the network is slow or the number of commands entering the log is very large).</span></span>  
  
-   <span data-ttu-id="b5fe2-129">解决镜像伙伴之间数据流减小的问题。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-129">Troubleshoot the cause of reduced data flow between mirroring partners.</span></span>  
  
-   <span data-ttu-id="b5fe2-130">设置关键绩效指标的警告阈值。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-130">Set warning thresholds on key performance metrics.</span></span>  
  
     <span data-ttu-id="b5fe2-131">如果新状态行中的值超过阈值，则系统便会向 Windows 事件日志发送提示性事件。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-131">If a new status row contains a value that exceeds a threshold, an informational event is sent to the Windows event log.</span></span> <span data-ttu-id="b5fe2-132">系统管理员可以随后根据这些事件手动配置警报。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-132">A system administrator can then manually configure alerts based on these events.</span></span> <span data-ttu-id="b5fe2-133">有关详细信息，请参阅 [使用镜像性能度量的警告阈值和警报 (SQL Server)](use-warning-thresholds-and-alerts-on-mirroring-performance-metrics-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-133">For more information, see [Use Warning Thresholds and Alerts on Mirroring Performance Metrics &#40;SQL Server&#41;](use-warning-thresholds-and-alerts-on-mirroring-performance-metrics-sql-server.md).</span></span>  
  
###  <a name="tools-for-monitoring-database-mirroring-status"></a><a name="tools_for_monitoring_dbm_status"></a> <span data-ttu-id="b5fe2-134">数据库镜像状态监视工具</span><span class="sxs-lookup"><span data-stu-id="b5fe2-134">Tools for Monitoring Database Mirroring Status</span></span>  
 <span data-ttu-id="b5fe2-135">可以使用数据库镜像监视器或 **sp_dbmmonitorresults** 系统存储过程来监视镜像状态。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-135">Mirroring status can be monitored using either Database Mirroring Monitor or the **sp_dbmmonitorresults** system stored procedure.</span></span> <span data-ttu-id="b5fe2-136">两个系统管理员（即 sysadmin 固定服务器角色成员以及在**msdb** 数据库中，由系统管理员添加到 **dbm_monitor** 固定数据库角色的用户）均可使用这些工具监视本地服务器实例上任何镜像数据库中的数据库镜像。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-136">These tools can be used to monitor database mirroring on any mirrored database on the local server instance by both System administrators, that is, members of the **sysadmin** fixed server role, and user who have been added to the **dbm_monitor** fixed database role in the **msdb** database by a system administrator.</span></span> <span data-ttu-id="b5fe2-137">使用上述任意一种工具时，系统管理员还可以手动刷新镜像状态。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-137">When using either tool, a system administrator can also manually refresh mirroring status.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b5fe2-138">系统管理员还可以配置并查看关键绩效指标的警告阈值。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-138">System administrators can also configure and view warning thresholds for key performance metrics.</span></span> <span data-ttu-id="b5fe2-139">有关详细信息，请参阅 [使用镜像性能度量的警告阈值和警报 (SQL Server)](use-warning-thresholds-and-alerts-on-mirroring-performance-metrics-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-139">For more information, see [Use Warning Thresholds and Alerts on Mirroring Performance Metrics &#40;SQL Server&#41;](use-warning-thresholds-and-alerts-on-mirroring-performance-metrics-sql-server.md).</span></span>  
  
-   <span data-ttu-id="b5fe2-140">数据库镜像监视器</span><span class="sxs-lookup"><span data-stu-id="b5fe2-140">Database Mirroring Monitor</span></span>  
  
     <span data-ttu-id="b5fe2-141">数据库镜像监视器是一个图形用户界面工具，系统管理员可以使用此工具查看和更新状态，配置多个关键绩效指标的警告阈值。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-141">Database Mirroring Monitor is a graphical user interface tool that enables system administrators to view and update status and to configure warning thresholds on several key performance metrics.</span></span> <span data-ttu-id="b5fe2-142">**dbm_monitor** 固定数据库角色成员还可以使用数据库镜像监视器查看镜像状态表中的最新行，但是这些成员不能更新状态表。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-142">Database Mirroring Monitor can also be used by members of the **dbm_monitor** fixed database role to view the most recent row of the mirroring status table, though they cannot update the status table.</span></span>  
  
     <span data-ttu-id="b5fe2-143">监视器显示在 **“状态”** 选项卡式页面上选择的数据库的状态（包括性能指标）。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-143">The monitor displays the status, including performance metrics, for a selected database on the **Status** tabbed page.</span></span> <span data-ttu-id="b5fe2-144">该页的内容来自主体和镜像服务器实例。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-144">The content of this page comes from both the principal and mirror server instances.</span></span> <span data-ttu-id="b5fe2-145">通过与主体服务器实例和镜像服务器实例的单独连接收集状态时，会异步填充该页。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-145">The page is filled asynchronously as status is gathered through separate connections to the principal and mirror server instances.</span></span> <span data-ttu-id="b5fe2-146">监视器每隔 30 秒便会尝试更新一次状态表。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-146">The monitor tries to update the status table at 30-second intervals.</span></span> <span data-ttu-id="b5fe2-147">只有当状态表在 15 秒内没有更新，并且用户是 **sysadmin** 固定服务器角色的成员时，更新才能成功。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-147">The update succeeds only if the table has not been updated within 15 seconds and the user is a member of the **sysadmin** fixed server role.</span></span> <span data-ttu-id="b5fe2-148">有关 **“状态”** 页中报告的信息摘要，请参阅本主题后面的“ [数据库镜像监视器显示的状态](#perf_metrics_of_dbm_monitor)”部分。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-148">For a summary of the information reported on the **Status** page, see [Status Displayed by the Database Mirroring Monitor](#perf_metrics_of_dbm_monitor), later in this topic.</span></span>  
  
     <span data-ttu-id="b5fe2-149">有关数据库镜像监视器界面的介绍，请参阅 [Database Mirroring Monitor Overview](database-mirroring-monitor-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-149">For an introduction to the Database Mirroring Monitor interface, see [Database Mirroring Monitor Overview](database-mirroring-monitor-overview.md).</span></span> <span data-ttu-id="b5fe2-150">有关启动数据库镜像监视器的信息，请参阅 [启动数据库镜像监视器 (SQL Server Management Studio)](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-150">For information on launching Database Mirroring Monitor, see [Start Database Mirroring Monitor &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md).</span></span>  
  
-   <span data-ttu-id="b5fe2-151">系统存储过程</span><span class="sxs-lookup"><span data-stu-id="b5fe2-151">System stored procedures</span></span>  
  
     <span data-ttu-id="b5fe2-152">还可以通过运行 **sp_dbmmonitorresults** 系统存储过程来检索或更新当前的状态。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-152">You can also retrieve or update the current status by running the **sp_dbmmonitorresults** system stored procedure.</span></span> <span data-ttu-id="b5fe2-153">您还可以使用其他 dbmmonitor 存储过程在服务器实例上设置监视、更改监视参数、查看当前更新持续时间以及删除监视。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-153">Other dbmmonitor stored procedures enable you to set up monitoring, change monitoring parameters, view the current update period, and drop monitoring on the server instance.</span></span>  
  
     <span data-ttu-id="b5fe2-154">下表介绍了管理和使用数据库镜像监视的存储过程，它们独立于数据库镜像监视器工作。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-154">The following table introduces the stored procedures for managing and using database mirroring monitoring independently of the Database Mirroring Monitor.</span></span>  
  
    |<span data-ttu-id="b5fe2-155">过程</span><span class="sxs-lookup"><span data-stu-id="b5fe2-155">Procedure</span></span>|<span data-ttu-id="b5fe2-156">说明</span><span class="sxs-lookup"><span data-stu-id="b5fe2-156">Description</span></span>|  
    |---------------|-----------------|  
    |[<span data-ttu-id="b5fe2-157">sp_dbmmonitoraddmonitoring</span><span class="sxs-lookup"><span data-stu-id="b5fe2-157">sp_dbmmonitoraddmonitoring</span></span>](/sql/relational-databases/system-stored-procedures/sp-dbmmonitoraddmonitoring-transact-sql)|<span data-ttu-id="b5fe2-158">创建定期更新服务器实例上每个镜像数据库的状态信息的作业。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-158">Creates a job that periodically updates the status information for every mirrored database on the server instance.</span></span>|  
    |[<span data-ttu-id="b5fe2-159">sp_dbmmonitorchangemonitoring</span><span class="sxs-lookup"><span data-stu-id="b5fe2-159">sp_dbmmonitorchangemonitoring</span></span>](/sql/relational-databases/system-stored-procedures/sp-dbmmonitorchangemonitoring-transact-sql)|<span data-ttu-id="b5fe2-160">更改数据库镜像监视参数的值。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-160">Changes the value of a database mirroring monitoring parameter.</span></span>|  
    |[<span data-ttu-id="b5fe2-161">sp_dbmmonitorhelpmonitoring</span><span class="sxs-lookup"><span data-stu-id="b5fe2-161">sp_dbmmonitorhelpmonitoring</span></span>](/sql/relational-databases/system-stored-procedures/sp-dbmmonitorhelpmonitoring-transact-sql)|<span data-ttu-id="b5fe2-162">返回当前更新持续时间。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-162">Returns the current update period.</span></span>|  
    |[<span data-ttu-id="b5fe2-163">sp_dbmmonitorresults</span><span class="sxs-lookup"><span data-stu-id="b5fe2-163">sp_dbmmonitorresults</span></span>](/sql/relational-databases/system-stored-procedures/sp-dbmmonitorresults-transact-sql)|<span data-ttu-id="b5fe2-164">返回所监视数据库的状态行，使您能够选择此过程是否预先获取最新的状态。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-164">Returns status rows for a monitored database and allows you to choose whether the procedure obtains the latest status beforehand.</span></span>|  
    |[<span data-ttu-id="b5fe2-165">sp_dbmmonitordropmonitoring</span><span class="sxs-lookup"><span data-stu-id="b5fe2-165">sp_dbmmonitordropmonitoring</span></span>](/sql/relational-databases/system-stored-procedures/sp-dbmmonitordropmonitoring-transact-sql)|<span data-ttu-id="b5fe2-166">停止并删除服务器实例上所有数据库的镜像监视器作业。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-166">Stops and deletes the mirroring monitor job for all the databases on the server instance.</span></span>|  
  
     <span data-ttu-id="b5fe2-167">**dbmmonitor** 系统存储过程可以用作数据库镜像监视器的附加补充。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-167">The **dbmmonitor** system stored procedures can be used as an adjunct to the Database Mirroring Monitor.</span></span> <span data-ttu-id="b5fe2-168">例如，即使使用 **sp_dbmmonitoraddmonitoring**配置监视，也可以使用数据库镜像监视器查看状态。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-168">For example, even if monitoring was configured using **sp_dbmmonitoraddmonitoring**, Database Mirroring Monitor can be used to view the status.</span></span>  
  
### <a name="how-monitoring-works"></a><span data-ttu-id="b5fe2-169">监视的工作原理</span><span class="sxs-lookup"><span data-stu-id="b5fe2-169">How Monitoring Works</span></span>  
 <span data-ttu-id="b5fe2-170">本部分介绍数据库镜像状态表、数据库镜像监视器作业和监视器，并介绍用户如何监视数据库镜像状态以及如何删除镜像作业。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-170">This section introduces the database mirroring status table, database mirroring monitor job and the monitor, how users can monitor database mirroring status, and how the monitoring job can be dropped.</span></span>  
  
#### <a name="database-mirroring-status-table"></a><span data-ttu-id="b5fe2-171">数据库镜像状态表</span><span class="sxs-lookup"><span data-stu-id="b5fe2-171">Database Mirroring Status Table</span></span>  
 <span data-ttu-id="b5fe2-172">数据库镜像状态存储在 **msdb** 数据库内的一个内部、未记录的数据库镜像状态表中。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-172">Database mirroring status is stored in an internal, undocumented database mirroring status table in the **msdb** database.</span></span> <span data-ttu-id="b5fe2-173">在服务器实例上首次更新镜像状态时，便会自动创建此状态表。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-173">This status table is automatically created the first time the mirroring status is updated on the server instance.</span></span>  
  
 <span data-ttu-id="b5fe2-174">状态表可以自动更新，也可以由系统管理员手动更新，但最低更新间隔为 15 秒。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-174">The status table may be updated either automatically or manually by a system administrator, with a minimum update interval of 15 seconds.</span></span> <span data-ttu-id="b5fe2-175">将最低更新间隔设置为 15 秒可以防止服务器实例因状态请求而导致重载。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-175">The 15 second minimum prevents server instances from being overloaded with status requests.</span></span>  
  
 <span data-ttu-id="b5fe2-176">状态表可以通过数据库镜像监视器和数据库镜像监视器作业（如果正在运行）进行自动更新。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-176">The status table is updated automatically by both Database Mirroring Monitor and the database mirroring monitor job, if running.</span></span> <span data-ttu-id="b5fe2-177">默认情况下，“数据库镜像监视器作业”将每分钟更新一次状态表（系统管理员可以将更新持续时间指定为 1 至 120 分钟之间的一个值）。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-177">**Database Mirroring Monitor Job** updates the table once a minute by default (a system administrator can specify an update period of 1 to 120 minutes).</span></span> <span data-ttu-id="b5fe2-178">相反，数据库镜像监视器每隔 30 秒自动更新一次状态表。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-178">Database Mirroring Monitor, in contrast, updates the table automatically every 30 seconds.</span></span> <span data-ttu-id="b5fe2-179">对于这些更新，“数据库镜像监视器作业”和数据库镜像监视器将调用 **sp_dbmmonitorupdate**。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-179">For these updates, **Database Mirroring Monitor Job** and Database Mirroring Monitor call **sp_dbmmonitorupdate**.</span></span>  
  
 <span data-ttu-id="b5fe2-180">**sp_dbmmonitorupdate** 第一次运行时，它将在 **msdb** 数据库中创建“数据库镜像状态”表和 **dbm_monitor** 固定数据库角色。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-180">The first time **sp_dbmmonitorupdate** runs, it creates the **database mirroring status** table and the **dbm_monitor** fixed database role in the **msdb** database.</span></span> <span data-ttu-id="b5fe2-181">**sp_dbmmonitorupdate** 通常通过针对服务器实例上的每个镜像数据库将新行插入状态表来更新镜像状态；有关详细信息，请参阅本主题后面的“数据库镜像状态表”。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-181">**sp_dbmmonitorupdate** usually updates the mirroring status by inserting a new row into the status table for every mirrored database on the server instance; for more information, see "Database Mirroring Status Table," later in this topic.</span></span> <span data-ttu-id="b5fe2-182">此过程还会计算新行中的性能指标并截断保留时间长于当前保持期（默认为 7 天）的行。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-182">This procedure also evaluates the performance metrics in the new rows and truncates rows older than the current retention period (the default is 7 days).</span></span> <span data-ttu-id="b5fe2-183">有关详细信息，请参阅 [sp_dbmmonitorupdate (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-dbmmonitorupdate-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-183">For more information, see [sp_dbmmonitorupdate &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dbmmonitorupdate-transact-sql).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b5fe2-184">除非数据库镜像监视器当前正在由 **sysadmin** 固定服务器角色成员使用，否则，只有在具有“数据库镜像监视器作业”并且 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理正在运行时，才能自动更新状态表。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-184">Unless Database Mirroring Monitor is currently being used by a member of the **sysadmin** fixed server role, the status table is automatically updated only if the **Database Mirroring Monitor Job** exists and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent is running.</span></span>  
  
#### <a name="database-mirroring-monitor-job"></a><span data-ttu-id="b5fe2-185">数据库镜像监视器作业</span><span class="sxs-lookup"><span data-stu-id="b5fe2-185">Database Mirroring Monitor Job</span></span>  
 <span data-ttu-id="b5fe2-186">数据库镜像监视作业（ **“数据库镜像监视器作业”** ）独立于数据库镜像监视器运行。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-186">The database mirroring monitoring job, **Database Mirroring Monitor Job**, operates independently of Database Mirroring Monitor.</span></span> <span data-ttu-id="b5fe2-187">仅当使用**启动镜像会话时，才能自动创建** “数据库镜像监视器作业” [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-187">**Database Mirroring Monitor Job** is created automatically only if [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] is used to start a mirroring session.</span></span> <span data-ttu-id="b5fe2-188">如果始终使用 ALTER DATABASE *database_name* SET PARTNER 命令开始镜像，则仅当系统管理员运行 **sp_dbmmonitoraddmonitoring** 存储过程时，该作业才存在。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-188">If ALTER DATABASE *database_name* SET PARTNER commands are always used to start mirroring, the job exists only if the system administrator runs the **sp_dbmmonitoraddmonitoring** stored procedure.</span></span>  
  
 <span data-ttu-id="b5fe2-189">创建 **“数据库镜像监视器作业”** 之后，如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理正在运行，则默认情况下，每分钟调用一次作业。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-189">After **Database Mirroring Monitor Job** is created, assuming that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent is running, the job is called once a minute, by default.</span></span> <span data-ttu-id="b5fe2-190">然后，作业会调用 **sp_dbmmonitorupdate** 系统存储过程。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-190">The job then calls the **sp_dbmmonitorupdate** system stored procedure.</span></span>  
  
 <span data-ttu-id="b5fe2-191">默认情况下，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理每分钟调用一次“数据库镜像监视器作业”，而作业随即调用 sp_dbmmonitorupdate 以更新状态表 。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-191">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent calls **Database Mirroring Monitor Job** once a minute, by default, and the job calls **sp_dbmmonitorupdate** to update the status table.</span></span> <span data-ttu-id="b5fe2-192">系统管理员可以使用 **sp_dbmmonitorchangemonitoring** 系统存储过程更改更新持续时间，他们还可以使用 **sp_dbmmonitorchangemonitoring** 系统存储过程查看当前的更新持续时间。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-192">System administrators can change the update period by using the **sp_dbmmonitorchangemonitoring** system stored procedure, and they can view the current update period by using the **sp_dbmmonitorchangemonitoring** system stored procedure.</span></span> <span data-ttu-id="b5fe2-193">有关详细信息，请参阅 [sp_dbmmonitoraddmonitoring (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-dbmmonitoraddmonitoring-transact-sql) 和 [sp_dbmmonitorchangemonitoring (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-dbmmonitorchangemonitoring-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-193">For more information, see [sp_dbmmonitoraddmonitoring &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dbmmonitoraddmonitoring-transact-sql) and [sp_dbmmonitorchangemonitoring &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dbmmonitorchangemonitoring-transact-sql).</span></span>  
  
#### <a name="monitoring-database-mirroring-status-by-system-administrators"></a><span data-ttu-id="b5fe2-194">监视数据库镜像状态（由系统管理员执行）</span><span class="sxs-lookup"><span data-stu-id="b5fe2-194">Monitoring Database Mirroring Status (by System Administrators)</span></span>  
 <span data-ttu-id="b5fe2-195">**sysadmin** 固定服务器角色成员可以查看和更新状态表。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-195">Members of the **sysadmin** fixed server role can view and update the status table</span></span>  
  
-   <span data-ttu-id="b5fe2-196">使用数据库镜像监视器</span><span class="sxs-lookup"><span data-stu-id="b5fe2-196">Using Database Mirroring Monitor</span></span>  
  
     <span data-ttu-id="b5fe2-197">系统管理员可以使用数据库镜像监视器手动刷新 **“状态”** 页、导航树或 **“历史记录”** 页。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-197">When using Database Mirroring Monitor, a system administrator can manually refresh the **Status** page, navigation tree, or **History** page.</span></span> <span data-ttu-id="b5fe2-198">如果状态表在前 15 秒内没有更新，则此操作还会更新状态表。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-198">This also updates the status table, unless it has already been updated within the previous 15 seconds.</span></span>  
  
     <span data-ttu-id="b5fe2-199">若要查看给定服务器实例上镜像状态的历史记录，系统管理员还可以针对服务器实例单击“历史记录”按钮（位于“状态”页上）。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-199">To view the history of mirroring status on a given server instance, the system administrator can also click the **History** button for a server instance (on the **Status** page).</span></span> <span data-ttu-id="b5fe2-200">将在 **“数据库镜像历史记录”** 对话框中显示历史记录。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-200">The history is displayed in the **Database Mirroring History** dialog box.</span></span> <span data-ttu-id="b5fe2-201">在此对话框中，系统管理员可以查看服务器实例状态表中的部分或全部行。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-201">There, the system administrator can view some or all of the rows in the status table of the server instance.</span></span>  
  
     <span data-ttu-id="b5fe2-202">有关 **“状态”** 页指标的信息，请参阅本主题后面的“数据库镜像监视器显示的性能指标”。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-202">For information about the **Status** page metrics, see Performance Metrics Displayed by the "Database Mirroring Monitor," later in this topic.</span></span>  
  
-   <span data-ttu-id="b5fe2-203">使用 **sp_dbmmonitorresults**</span><span class="sxs-lookup"><span data-stu-id="b5fe2-203">Using **sp_dbmmonitorresults**</span></span>  
  
     <span data-ttu-id="b5fe2-204">系统管理员可以使用 **sp_dbmmonitorresults** 系统存储过程查看状态表，如果此状态表在前 15 秒内没有更新，则还可以选择对其进行更新。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-204">System administrators can use the **sp_dbmmonitorresults** system stored procedure to view and, optionally, to update the status table, if it has not been updated within the previous 15 seconds.</span></span> <span data-ttu-id="b5fe2-205">此过程将调用 **sp_dbmmonitorupdate** 过程并返回一个或多个历史记录行，具体取决于过程调用中的请求量。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-205">This procedure calls the **sp_dbmmonitorupdate** procedure and returns one or more history rows, depending on the amount requested in the procedure call.</span></span> <span data-ttu-id="b5fe2-206">有关其结果集中状态的信息，请参阅 [sp_dbmmonitorresults (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-dbmmonitorresults-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-206">For information about the status in its results set, see [sp_dbmmonitorresults &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dbmmonitorresults-transact-sql).</span></span>  
  
#### <a name="monitoring-database-mirroring-status-by-dbm_monitor-members"></a><span data-ttu-id="b5fe2-207">监视数据库镜像状态（由 dbm_monitor 成员执行）</span><span class="sxs-lookup"><span data-stu-id="b5fe2-207">Monitoring Database Mirroring Status (by dbm_monitor Members)</span></span>  
 <span data-ttu-id="b5fe2-208">如上所述，当 **sp_dbmmonitorupdate** 首次运行时，便会在 **msdb** 数据库中创建 **dbm_monitor** 固定数据库角色。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-208">As mentioned, the first time **sp_dbmmonitorupdate** runs, it creates the **dbm_monitor** fixed database role in the **msdb** database.</span></span> <span data-ttu-id="b5fe2-209">**dbm_monitor** 固定数据库角色成员可以使用数据库镜像监视器或 **sp_dbmmonitorresults** 存储过程查看现有的镜像状态。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-209">Members of the **dbm_monitor** fixed database role can view the existing mirroring status by using either Database Mirroring Monitor or the **sp_dbmmonitorresults** stored procedure.</span></span> <span data-ttu-id="b5fe2-210">但是这些用户不能更新状态表。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-210">But these users cannot update the status table.</span></span> <span data-ttu-id="b5fe2-211">若要了解所显示的状态的保留时间，用户可以在 "**状态**" 页上的 "**主体日志 (***\<time>***) \*\* " 和 "**镜像日志 (***\<time>***) \*\*标签" 中查看时间。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-211">To learn the age of the displayed status a user can look at the times in the **Principal log (***\<time>***)** and **Mirror log (***\<time>***)** labels on the **Status** page.</span></span>  
  
 <span data-ttu-id="b5fe2-212">**dbm_monitor** 固定数据库角色成员使用“数据库镜像监视器作业”定期更新状态表。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-212">Members of the **dbm_monitor** fixed database role depend on the **Database Mirroring Monitor Job** to update the status table at regular intervals.</span></span> <span data-ttu-id="b5fe2-213">如果作业不存在，或者 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理已停止，则状态便会迅速变旧，并且不再反映镜像会话的配置。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-213">If the job does not exist or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent is stopped, the status becomes increasingly stale and may no longer reflect the configuration of the mirroring session.</span></span> <span data-ttu-id="b5fe2-214">例如，在一次故障转移之后，伙伴可能会分享相同的角色（主体或镜像）。或者，当前主体服务器可能显示为镜像，而当前的镜像服务器显示为主体。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-214">For example, after a failover, the partners might appear to share the same role-principal or mirror, or the current principal server might be shown as the mirror, while the current mirror server is shown as the principal.</span></span>  
  
#### <a name="dropping-the-database-mirroring-monitor-job"></a><span data-ttu-id="b5fe2-215">删除数据库镜像监视器作业</span><span class="sxs-lookup"><span data-stu-id="b5fe2-215">Dropping the Database Mirroring Monitor Job</span></span>  
 <span data-ttu-id="b5fe2-216">数据库镜像监视器作业（ **“数据库镜像监视器作业”** ）在删除之前将一直保留。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-216">The database mirroring monitor job, **Database Mirroring Monitor Job**, remains until it is dropped.</span></span> <span data-ttu-id="b5fe2-217">必须由系统管理员对监视作业进行管理。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-217">The monitoring job must be managed by the system administrator.</span></span> <span data-ttu-id="b5fe2-218">若要删除“数据库镜像监视器作业”，请使用 **sp_dbmmonitordropmonitoring**。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-218">To drop **Database Mirroring Monitor Job**, use **sp_dbmmonitordropmonitoring**.</span></span> <span data-ttu-id="b5fe2-219">有关详细信息，请参阅 [sp_dbmmonitordropmonitoring (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-dbmmonitordropmonitoring-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-219">For more information, see [sp_dbmmonitordropmonitoring &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dbmmonitordropmonitoring-transact-sql).</span></span>  
  
###  <a name="status-displayed-by-the-database-mirroring-monitor"></a><a name="perf_metrics_of_dbm_monitor"></a> <span data-ttu-id="b5fe2-220">数据库镜像监视器显示的状态</span><span class="sxs-lookup"><span data-stu-id="b5fe2-220">Status Displayed by the Database Mirroring Monitor</span></span>  
 <span data-ttu-id="b5fe2-221">数据库镜像监视器的 **“状态”** 页描述了镜像伙伴以及镜像会话的状态。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-221">The **Status** page of the Database Mirroring Monitor describes the partners, and also the state of the mirroring session.</span></span> <span data-ttu-id="b5fe2-222">状态信息包括性能指标（如事务日志的状态）以及在会话没有同步时，有助于当前对完成故障转移所需时间和潜在数据丢失进行评估的其他信息。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-222">The status includes performance metrics such as the state of the transaction log and other information that is intended to help currently estimate the time required to complete a failover and the potential of data loss, if the session is not synchronized.</span></span> <span data-ttu-id="b5fe2-223">此外， **“状态”** 页还概略显示有关镜像会话的状态和信息。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-223">In addition, the **Status** page displays status and information about the mirroring session in general.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b5fe2-224">有关数据库镜像监视器和“状态”页的说明，请参阅本主题前面的[数据库镜像状态监视工具](#tools_for_monitoring_dbm_status)。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-224">For an introduction to the Database Mirroring Monitor and **Status** page, see [Tools for Monitoring Database Mirroring Status](#tools_for_monitoring_dbm_status), earlier in this topic.</span></span>  
  
 <span data-ttu-id="b5fe2-225">下面将介绍上述各内容的概要。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-225">The information provided for each of these is summarized in the following sections.</span></span>  
  
#### <a name="partners"></a><span data-ttu-id="b5fe2-226">合作伙伴</span><span class="sxs-lookup"><span data-stu-id="b5fe2-226">Partners</span></span>  
 <span data-ttu-id="b5fe2-227">**“状态”** 页显示每个伙伴的下列信息：</span><span class="sxs-lookup"><span data-stu-id="b5fe2-227">The **Status** page displays the following information for each of the partners:</span></span>  
  
-   <span data-ttu-id="b5fe2-228">服务器实例</span><span class="sxs-lookup"><span data-stu-id="b5fe2-228">Server instance</span></span>  
  
     <span data-ttu-id="b5fe2-229">在 **“状态”** 行显示状态的服务器实例的名称。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-229">Name of the server instance whose status is displayed in the **Status** row.</span></span>  
  
-   <span data-ttu-id="b5fe2-230">当前角色</span><span class="sxs-lookup"><span data-stu-id="b5fe2-230">Current role</span></span>  
  
     <span data-ttu-id="b5fe2-231">服务器实例的当前角色。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-231">Current role of the server instance.</span></span> <span data-ttu-id="b5fe2-232">可能的状态包括：</span><span class="sxs-lookup"><span data-stu-id="b5fe2-232">The possible states are:</span></span>  
  
    -   <span data-ttu-id="b5fe2-233">主体</span><span class="sxs-lookup"><span data-stu-id="b5fe2-233">Principal</span></span>  
  
    -   <span data-ttu-id="b5fe2-234">镜像</span><span class="sxs-lookup"><span data-stu-id="b5fe2-234">Mirror</span></span>  
  
-   <span data-ttu-id="b5fe2-235">镜像状态</span><span class="sxs-lookup"><span data-stu-id="b5fe2-235">Mirroring state</span></span>  
  
     <span data-ttu-id="b5fe2-236">可能的状态包括：</span><span class="sxs-lookup"><span data-stu-id="b5fe2-236">The possible states are:</span></span>  
  
    -   <span data-ttu-id="b5fe2-237">未知</span><span class="sxs-lookup"><span data-stu-id="b5fe2-237">Unknown</span></span>  
  
    -   <span data-ttu-id="b5fe2-238">正在同步</span><span class="sxs-lookup"><span data-stu-id="b5fe2-238">Synchronizing</span></span>  
  
    -   <span data-ttu-id="b5fe2-239">已同步</span><span class="sxs-lookup"><span data-stu-id="b5fe2-239">Synchronized</span></span>  
  
    -   <span data-ttu-id="b5fe2-240">Suspended</span><span class="sxs-lookup"><span data-stu-id="b5fe2-240">Suspended</span></span>  
  
    -   <span data-ttu-id="b5fe2-241">已断开连接</span><span class="sxs-lookup"><span data-stu-id="b5fe2-241">Disconnected</span></span>  
  
-   <span data-ttu-id="b5fe2-242">见证服务器连接</span><span class="sxs-lookup"><span data-stu-id="b5fe2-242">Witness connection</span></span>  
  
     <span data-ttu-id="b5fe2-243">见证服务器的连接状态。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-243">Connection status of the witness.</span></span> <span data-ttu-id="b5fe2-244">可能的状态包括：</span><span class="sxs-lookup"><span data-stu-id="b5fe2-244">The possible states are:</span></span>  
  
    -   <span data-ttu-id="b5fe2-245">未知</span><span class="sxs-lookup"><span data-stu-id="b5fe2-245">Unknown</span></span>  
  
    -   <span data-ttu-id="b5fe2-246">连续</span><span class="sxs-lookup"><span data-stu-id="b5fe2-246">Connected</span></span>  
  
    -   <span data-ttu-id="b5fe2-247">已断开连接。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-247">Disconnected.</span></span>  
  
#### <a name="log-on-the-principal-server"></a><span data-ttu-id="b5fe2-248">主体服务器上的日志</span><span class="sxs-lookup"><span data-stu-id="b5fe2-248">Log on the Principal Server</span></span>  
 <span data-ttu-id="b5fe2-249">**“状态”** 页显示主体服务器上的日志自所示时间起的下列状态信息：</span><span class="sxs-lookup"><span data-stu-id="b5fe2-249">The **Status** page displays the following information about the status of the log on the principal server as of the indicated time:</span></span>  
  
-   <span data-ttu-id="b5fe2-250">未发送日志</span><span class="sxs-lookup"><span data-stu-id="b5fe2-250">Unsent log</span></span>  
  
     <span data-ttu-id="b5fe2-251">发送队列中处于等待状态的日志量 (KB)。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-251">The amount of log waiting in the send queue in kilobytes (KB).</span></span>  
  
-   <span data-ttu-id="b5fe2-252">最早的未发送事务</span><span class="sxs-lookup"><span data-stu-id="b5fe2-252">Oldest unsent transaction</span></span>  
  
     <span data-ttu-id="b5fe2-253">发送队列中最早的未发送事务的保留时间。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-253">Age of the oldest unsent transaction in the send queue.</span></span> <span data-ttu-id="b5fe2-254">事务保留时间指示在将事务发送到镜像服务器实例之前将其保留的分钟数。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-254">The age of this transaction indicates how many minutes of transactions have not yet been sent to the mirror server instance.</span></span> <span data-ttu-id="b5fe2-255">该值有助于测量数据丢失的可能性（以时间计）。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-255">This value helps measure the potential for data loss in terms of time.</span></span>  
  
-   <span data-ttu-id="b5fe2-256">发送日志所需的时间(估计值)</span><span class="sxs-lookup"><span data-stu-id="b5fe2-256">Time to send log (estimated)</span></span>  
  
     <span data-ttu-id="b5fe2-257">根据当前发送速率，估计主体服务器实例将当前位于发送队列的日志发送到镜像服务器实例所需的分钟数。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-257">Estimated number of minutes the principal server instance requires to send the log that is currently in the send queue to the mirror server instance based on the current send rate.</span></span> <span data-ttu-id="b5fe2-258">发送日志所需的实际时间将受传入事务速率的影响，而此速率的变化非常大。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-258">The actual time to send the log will be affected by the rate of incoming transactions, which can vary significantly.</span></span> <span data-ttu-id="b5fe2-259">但是，可以使用“发送日志所需的时间（估计值）”值粗略估计手动故障转移所需的时间。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-259">However, the **Time to send log (estimated)** value can be useful for roughly estimating the time required for a manual failover.</span></span>  
  
-   <span data-ttu-id="b5fe2-260">当前发送速率</span><span class="sxs-lookup"><span data-stu-id="b5fe2-260">Current send rate</span></span>  
  
     <span data-ttu-id="b5fe2-261">事务发送到镜像服务器实例的速率（以 KB/秒计）。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-261">Rate at which transactions are being sent to the mirror server instance in KB per second.</span></span>  
  
-   <span data-ttu-id="b5fe2-262">新事务的当前速率</span><span class="sxs-lookup"><span data-stu-id="b5fe2-262">Current rate of new transactions</span></span>  
  
     <span data-ttu-id="b5fe2-263">传入事务进入主体日志的速率（以 KB/秒计）。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-263">Rate at which incoming transactions are being entered into the principal's log in KB per second.</span></span> <span data-ttu-id="b5fe2-264">若要确定镜像是落后、保持同步、还是正在追赶，请将该值与 **“发送日志所需的时间(估计值)”** 值进行比较。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-264">To determine whether mirroring is falling behind, staying up, or catching up, compare this value to the **Estimated time to send log** value.</span></span>  
  
#### <a name="log-on-the-mirror-server"></a><span data-ttu-id="b5fe2-265">镜像服务器上的日志</span><span class="sxs-lookup"><span data-stu-id="b5fe2-265">Log on the Mirror Server</span></span>  
 <span data-ttu-id="b5fe2-266">**“状态”** 页显示镜像服务器上的日志自所示时间起的下列状态信息：</span><span class="sxs-lookup"><span data-stu-id="b5fe2-266">The **Status** page displays the following information about the status of the log on the mirror server as of the indicated time:</span></span>  
  
-   <span data-ttu-id="b5fe2-267">未还原日志</span><span class="sxs-lookup"><span data-stu-id="b5fe2-267">Unrestored log</span></span>  
  
     <span data-ttu-id="b5fe2-268">重做队列中处于等待状态的日志量(以 KB 计)。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-268">The amount of log waiting in the redo queue in KB.</span></span>  
  
-   <span data-ttu-id="b5fe2-269">还原日志所需的时间(估计值)</span><span class="sxs-lookup"><span data-stu-id="b5fe2-269">Time to restore log (estimated)</span></span>  
  
     <span data-ttu-id="b5fe2-270">将当前在重做队列中的日志应用于镜像数据库所需的近似分钟数。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-270">Approximate number of minutes required for the log currently in the redo queue to be applied to the mirror database.</span></span>  
  
-   <span data-ttu-id="b5fe2-271">当前还原速率</span><span class="sxs-lookup"><span data-stu-id="b5fe2-271">Current restore rate</span></span>  
  
     <span data-ttu-id="b5fe2-272">将事务还原到镜像数据库的速率（以 KB/秒计）。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-272">Rate at which transactions are being restored into the mirror database (in KB per second).</span></span>  
  
#### <a name="mirroring-session"></a><span data-ttu-id="b5fe2-273">镜像会话</span><span class="sxs-lookup"><span data-stu-id="b5fe2-273">Mirroring Session</span></span>  
 <span data-ttu-id="b5fe2-274">此外， **“状态”** 页还显示有关镜像会话的下列信息：</span><span class="sxs-lookup"><span data-stu-id="b5fe2-274">In addition, the **Status** page displays the following information about the mirroring session:</span></span>  
  
-   <span data-ttu-id="b5fe2-275">镜像提交开销</span><span class="sxs-lookup"><span data-stu-id="b5fe2-275">Mirroring commit overhead</span></span>  
  
     <span data-ttu-id="b5fe2-276">每个事务的平均延迟时间（毫秒），仅与高安全性模式相关。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-276">Average delay per transaction in milliseconds (relevant only in high-safety mode).</span></span> <span data-ttu-id="b5fe2-277">此延迟是主体服务器实例等待镜像服务器实例将事务日志记录写入重做队列时，所发生的开销量。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-277">This delay is the amount of overhead incurred while the principal server instance waits for the mirror server instance to write the transaction's log record into the redo queue.</span></span>  
  
-   <span data-ttu-id="b5fe2-278">发送和还原所有当前日志的所需时间(估计值)</span><span class="sxs-lookup"><span data-stu-id="b5fe2-278">Time to send and restore all current log (estimated)</span></span>  
  
     <span data-ttu-id="b5fe2-279">发送在主体服务器上已提交的所有未发送日志，以及还原重做队列中当前存在的所有日志所需的估计时间。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-279">Estimated time needed to send all of the unsent log that has been committed at the principal and to restore all of the log currently in the redo queue.</span></span> <span data-ttu-id="b5fe2-280">此估计时间值可能小于“发送日志所需的时间(估计值)”和“还原日志所需的时间(估计值)”这两个字段值的总和，因为发送和还原操作可以并行执行。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-280">This estimate may be less than the sum of the values of the **Time to send log (estimated)** and **Time to restore log (estimated)** fields, because sending and restoring can operate in parallel.</span></span>  
  
-   <span data-ttu-id="b5fe2-281">见证服务器地址</span><span class="sxs-lookup"><span data-stu-id="b5fe2-281">Witness address</span></span>  
  
     <span data-ttu-id="b5fe2-282">见证服务器实例的网络地址。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-282">Network address of the witness server instance.</span></span> <span data-ttu-id="b5fe2-283">有关此地址格式的信息，请参阅[指定服务器网络地址（数据库镜像）](specify-a-server-network-address-database-mirroring.md)。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-283">For information about the format of this address, see [Specify a Server Network Address &#40;Database Mirroring&#41;](specify-a-server-network-address-database-mirroring.md).</span></span>  
  
-   <span data-ttu-id="b5fe2-284">运行模式</span><span class="sxs-lookup"><span data-stu-id="b5fe2-284">Operating mode</span></span>  
  
     <span data-ttu-id="b5fe2-285">数据库镜像会话的运行模式：</span><span class="sxs-lookup"><span data-stu-id="b5fe2-285">The operating mode of the database mirroring session:</span></span>  
  
    -   <span data-ttu-id="b5fe2-286">高性能(异步)</span><span class="sxs-lookup"><span data-stu-id="b5fe2-286">High performance (asynchronous)</span></span>  
  
    -   <span data-ttu-id="b5fe2-287">不带自动故障转移功能的高安全(同步)</span><span class="sxs-lookup"><span data-stu-id="b5fe2-287">High safety without automatic failover (synchronous)</span></span>  
  
    -   <span data-ttu-id="b5fe2-288">带自动故障转移功能的高安全(同步)</span><span class="sxs-lookup"><span data-stu-id="b5fe2-288">High safety with automatic failover (synchronous)</span></span>  
  
##  <a name="additional-sources-of-information-about-a-mirrored-database"></a><a name="AdditionalSources"></a> <span data-ttu-id="b5fe2-289">有关镜像数据库的其他信息源</span><span class="sxs-lookup"><span data-stu-id="b5fe2-289">Additional Sources of Information About a Mirrored Database</span></span>  
 <span data-ttu-id="b5fe2-290">除了使用数据库镜像监视器和 dbmmonitor 存储过程监视镜像数据库并对所监视的性能变量设置警报之外， [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 还提供了用于数据库镜像的目录视图、性能计数器和事件通知。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-290">In addition to using the Database Mirroring Monitor and dbmmonitor stored procedures to monitor a mirrored database and set up alerts on monitored performance variables, [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] provides catalog views, performance counters, and event notifications for database mirroring.</span></span>  
  
 <span data-ttu-id="b5fe2-291">**本节内容：**</span><span class="sxs-lookup"><span data-stu-id="b5fe2-291">**In This Section:**</span></span>  
  
-   [<span data-ttu-id="b5fe2-292">数据库镜像元数据</span><span class="sxs-lookup"><span data-stu-id="b5fe2-292">Database Mirroring Metadata</span></span>](#DbmMetadata)  
  
-   [<span data-ttu-id="b5fe2-293">数据库镜像性能计数器</span><span class="sxs-lookup"><span data-stu-id="b5fe2-293">Database Mirroring Performance Counters</span></span>](#DbmPerfCounters)  
  
-   [<span data-ttu-id="b5fe2-294">数据库镜像事件通知</span><span class="sxs-lookup"><span data-stu-id="b5fe2-294">Database Mirroring Event Notifications</span></span>](#DbmEventNotif)  
  
###  <a name="database-mirroring-metadata"></a><a name="DbmMetadata"></a> <span data-ttu-id="b5fe2-295">数据库镜像元数据</span><span class="sxs-lookup"><span data-stu-id="b5fe2-295">Database Mirroring Metadata</span></span>  
 <span data-ttu-id="b5fe2-296">通过下列目录视图或动态管理视图公开的元数据对每个数据库镜像会话进行了说明：</span><span class="sxs-lookup"><span data-stu-id="b5fe2-296">Each database mirroring session is described in metadata that is exposed through the following catalog or dynamic management views:</span></span>  
  
-   <span data-ttu-id="b5fe2-297">**sys.database_mirroring**</span><span class="sxs-lookup"><span data-stu-id="b5fe2-297">**sys.database_mirroring**</span></span>  
  
     <span data-ttu-id="b5fe2-298">此视图显示一个服务器实例中每个镜像数据库的数据库镜像元数据。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-298">This view displays the database mirroring metadata for each mirrored database in a server instance.</span></span> <span data-ttu-id="b5fe2-299">有关详细信息，请参阅 [sys.database_mirroring (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-database-mirroring-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-299">For more information, see [sys.database_mirroring &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-transact-sql).</span></span>  
  
-   <span data-ttu-id="b5fe2-300">**sys.database_mirroring_endpoints**</span><span class="sxs-lookup"><span data-stu-id="b5fe2-300">**sys.database_mirroring_endpoints**</span></span>  
  
     <span data-ttu-id="b5fe2-301">**sys.database_mirroring_endpoints** 目录视图显示有关服务器实例的数据库镜像端点的信息。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-301">The **sys.database_mirroring_endpoints** catalog view displays information about the database mirroring endpoint of the server instance.</span></span> <span data-ttu-id="b5fe2-302">有关详细信息，请参阅 [sys.database_mirroring_endpoints (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-302">For more information, see [sys.database_mirroring_endpoints &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql).</span></span>  
  
-   <span data-ttu-id="b5fe2-303">**sys.database_mirroring_witnesses**</span><span class="sxs-lookup"><span data-stu-id="b5fe2-303">**sys.database_mirroring_witnesses**</span></span>  
  
     <span data-ttu-id="b5fe2-304">此视图显示服务器实例为见证服务器的每个会话的数据库镜像元数据。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-304">This catalog view displays the database mirroring metadata for each session in which a server instance is the witness.</span></span> <span data-ttu-id="b5fe2-305">有关详细信息，请参阅 [sys.database_mirroring_witnesses (Transact-SQL)](/sql/relational-databases/system-catalog-views/database-mirroring-witness-catalog-views-sys-database-mirroring-witnesses)。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-305">For more information, see [sys.database_mirroring_witnesses &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/database-mirroring-witness-catalog-views-sys-database-mirroring-witnesses).</span></span>  
  
-   <span data-ttu-id="b5fe2-306">**sys.dm_db_mirroring_connections**</span><span class="sxs-lookup"><span data-stu-id="b5fe2-306">**sys.dm_db_mirroring_connections**</span></span>  
  
     <span data-ttu-id="b5fe2-307">此动态管理视图为每个数据库镜像网络连接返回一行。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-307">This dynamic management view returns a row for each database mirroring network connection.</span></span>  
  
     <span data-ttu-id="b5fe2-308">有关详细信息，请参阅 [sys.dm_db_mirroring_connections (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/database-mirroring-sys-dm-db-mirroring-connections)。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-308">For more information, see [sys.dm_db_mirroring_connections &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/database-mirroring-sys-dm-db-mirroring-connections).</span></span>  
  
###  <a name="database-mirroring-performance-counters"></a><a name="DbmPerfCounters"></a> <span data-ttu-id="b5fe2-309">数据库镜像性能计数器</span><span class="sxs-lookup"><span data-stu-id="b5fe2-309">Database Mirroring Performance Counters</span></span>  
 <span data-ttu-id="b5fe2-310">使用性能计数器可以监视数据库镜像性能。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-310">Performance counters let you monitor database mirroring performance.</span></span> <span data-ttu-id="b5fe2-311">例如，可以检查 **Transaction Delay** 计数器以确定数据库镜像是否影响主体服务器的性能，可以检查 **Redo Queue** 和 **Log Send Queue** 计数器以确定镜像数据库与主体数据库之间保持同步的情况。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-311">For example, you can examine the **Transaction Delay** counter to see if database mirroring is impacting performance on the principal server, you can examine the **Redo Queue** and **Log Send Queue** counters to see how well the mirror database is keeping up with the principal database.</span></span> <span data-ttu-id="b5fe2-312">还可以检查 **Log Bytes Sent/sec** 计数器以监视每秒发送的日志量。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-312">You can examine the **Log Bytes Sent/sec** counter to monitor the amount of log sent per second.</span></span>  
  
 <span data-ttu-id="b5fe2-313">在任一伙伴的性能监视器中，性能计数器可用于数据库镜像性能对象 (**SQLServer:Database Mirroring**)。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-313">In Performance Monitor on either partner, performance counters are available in the database mirroring performance object (**SQLServer:Database Mirroring**).</span></span> <span data-ttu-id="b5fe2-314">有关详细信息，请参阅 [SQL Server, Database Mirroring Object](../../relational-databases/performance-monitor/sql-server-database-mirroring-object.md)。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-314">For more information, see [SQL Server, Database Mirroring Object](../../relational-databases/performance-monitor/sql-server-database-mirroring-object.md).</span></span>  
  
 <span data-ttu-id="b5fe2-315">**启动性能监视器**</span><span class="sxs-lookup"><span data-stu-id="b5fe2-315">**To start the performance monitor**</span></span>  
  
-   [<span data-ttu-id="b5fe2-316">启动系统监视器 (Windows)</span><span class="sxs-lookup"><span data-stu-id="b5fe2-316">Start System Monitor &#40;Windows&#41;</span></span>](../../relational-databases/performance/start-system-monitor-windows.md)  
  
###  <a name="database-mirroring-event-notifications"></a><a name="DbmEventNotif"></a> <span data-ttu-id="b5fe2-317">数据库镜像事件通知</span><span class="sxs-lookup"><span data-stu-id="b5fe2-317">Database Mirroring Event Notifications</span></span>  
 <span data-ttu-id="b5fe2-318">事件通知是特殊类型的数据库对象。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-318">Event notifications are a special kind of database object.</span></span> <span data-ttu-id="b5fe2-319">执行事件通知可响应各种 Transact-SQL 数据定义语言 (DDL) 语句和 SQL 跟踪事件，并将有关服务器事件和数据库事件的信息发送到 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 服务。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-319">Event notifications execute in response to a variety of Transact-SQL data definition language (DDL) statements and SQL Trace events and send information about server and database events to a [!INCLUDE[ssSB](../../includes/sssb-md.md)] service.</span></span>  
  
 <span data-ttu-id="b5fe2-320">下列事件可用于数据库镜像：</span><span class="sxs-lookup"><span data-stu-id="b5fe2-320">The following events are available for database mirroring:</span></span>  
  
-   <span data-ttu-id="b5fe2-321">**Database Mirroring State Change** 事件类</span><span class="sxs-lookup"><span data-stu-id="b5fe2-321">**Database Mirroring State Change** event class</span></span>  
  
     <span data-ttu-id="b5fe2-322">这指示镜像数据库镜像状态的更改时间。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-322">This indicates when the mirroring state of a mirrored database changes.</span></span> <span data-ttu-id="b5fe2-323">有关详细信息，请参阅 [Database Mirroring State Change Event Class](../../relational-databases/event-classes/database-mirroring-state-change-event-class.md)。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-323">For more information, see [Database Mirroring State Change Event Class](../../relational-databases/event-classes/database-mirroring-state-change-event-class.md).</span></span>  
  
-   <span data-ttu-id="b5fe2-324">**Audit Database Mirroring Login** 事件类</span><span class="sxs-lookup"><span data-stu-id="b5fe2-324">**Audit Database Mirroring Login** event class</span></span>  
  
     <span data-ttu-id="b5fe2-325">这报告与数据库镜像传输安全性相关的审核消息。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-325">This reports audit messages related to database mirroring transport security.</span></span> <span data-ttu-id="b5fe2-326">有关详细信息，请参阅 [Audit Database Mirroring Login Event Class](../../relational-databases/event-classes/audit-database-mirroring-login-event-class.md)。</span><span class="sxs-lookup"><span data-stu-id="b5fe2-326">For more information, see [Audit Database Mirroring Login Event Class](../../relational-databases/event-classes/audit-database-mirroring-login-event-class.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="b5fe2-327">相关任务</span><span class="sxs-lookup"><span data-stu-id="b5fe2-327">Related Tasks</span></span>  
  
-   [<span data-ttu-id="b5fe2-328">使用镜像性能度量的警告阈值和警报 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="b5fe2-328">Use Warning Thresholds and Alerts on Mirroring Performance Metrics &#40;SQL Server&#41;</span></span>](use-warning-thresholds-and-alerts-on-mirroring-performance-metrics-sql-server.md)  
  
-   [<span data-ttu-id="b5fe2-329">启动数据库镜像监视器 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="b5fe2-329">Start Database Mirroring Monitor &#40;SQL Server Management Studio&#41;</span></span>](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="b5fe2-330">查看镜像数据库的状态 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="b5fe2-330">View the State of a Mirrored Database &#40;SQL Server Management Studio&#41;</span></span>](view-the-state-of-a-mirrored-database-sql-server-management-studio.md)  
  
 <span data-ttu-id="b5fe2-331">**存储过程**</span><span class="sxs-lookup"><span data-stu-id="b5fe2-331">**Stored procedures**</span></span>  
  
-   [<span data-ttu-id="b5fe2-332">sp_dbmmonitoraddmonitoring (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b5fe2-332">sp_dbmmonitoraddmonitoring &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dbmmonitoraddmonitoring-transact-sql)  
  
-   [<span data-ttu-id="b5fe2-333">sp_dbmmonitorchangealert (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b5fe2-333">sp_dbmmonitorchangealert &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dbmmonitorchangealert-transact-sql)  
  
-   [<span data-ttu-id="b5fe2-334">sp_dbmmonitorchangemonitoring (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b5fe2-334">sp_dbmmonitorchangemonitoring &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dbmmonitorchangemonitoring-transact-sql)  
  
-   [<span data-ttu-id="b5fe2-335">sp_dbmmonitordropalert (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b5fe2-335">sp_dbmmonitordropalert &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dbmmonitordropalert-transact-sql)  
  
-   [<span data-ttu-id="b5fe2-336">sp_dbmmonitordropmonitoring (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b5fe2-336">sp_dbmmonitordropmonitoring &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dbmmonitordropmonitoring-transact-sql)  
  
-   [<span data-ttu-id="b5fe2-337">sp_dbmmonitorhelpalert (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b5fe2-337">sp_dbmmonitorhelpalert &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dbmmonitorhelpalert-transact-sql)  
  
-   [<span data-ttu-id="b5fe2-338">sp_dbmmonitorhelpmonitoring (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b5fe2-338">sp_dbmmonitorhelpmonitoring &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dbmmonitorhelpmonitoring-transact-sql)  
  
-   [<span data-ttu-id="b5fe2-339">sp_dbmmonitorresults (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b5fe2-339">sp_dbmmonitorresults &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dbmmonitorresults-transact-sql)  
  
-   [<span data-ttu-id="b5fe2-340">sp_dbmmonitorupdate (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b5fe2-340">sp_dbmmonitorupdate &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dbmmonitorupdate-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="b5fe2-341">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b5fe2-341">See Also</span></span>  
 <span data-ttu-id="b5fe2-342">[数据库镜像 (SQL Server)](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="b5fe2-342">[Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="b5fe2-343">WMI Provider for Server Events 的概念</span><span class="sxs-lookup"><span data-stu-id="b5fe2-343">WMI Provider for Server Events Concepts</span></span>](../../relational-databases/wmi-provider-server-events/wmi-provider-for-server-events-concepts.md)  
  
  
