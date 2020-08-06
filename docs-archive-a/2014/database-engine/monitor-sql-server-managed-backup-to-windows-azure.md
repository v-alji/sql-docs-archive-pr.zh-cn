---
title: 监视 SQL Server 托管备份到 Azure |Microsoft Docs
description: 本文介绍可用于确定使用 SQL Server 托管备份到 Azure 的总体运行状况并标识错误的工具。
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: cfb9e431-7d4c-457c-b090-6f2528b2f315
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: baec99e63c70befde0cfce76e42dd6202ebc0bad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590368"
---
# <a name="monitor-sql-server-managed-backup-to-azure"></a><span data-ttu-id="66e49-103">监视针对 Azure 的 SQL Server 托管备份</span><span class="sxs-lookup"><span data-stu-id="66e49-103">Monitor SQL Server Managed Backup to Azure</span></span>
  [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]<span data-ttu-id="66e49-104">内置多种措施，可在备份过程中找出问题和错误，如有可能，再通过纠正措施纠正这些问题。</span><span class="sxs-lookup"><span data-stu-id="66e49-104">has built-in measures to identify problems and errors during backup processes and remedy with corrective action when possible.</span></span>  <span data-ttu-id="66e49-105">但是，有一些需要用户干预的情况。</span><span class="sxs-lookup"><span data-stu-id="66e49-105">However there are certain situations where user intervention is required.</span></span> <span data-ttu-id="66e49-106">本主题介绍可用于确定备份的整体运行状况和标识需解决的任何错误的工具。</span><span class="sxs-lookup"><span data-stu-id="66e49-106">This topic describes the tools that you can use to determine the overall health status of backups, and identify any errors that need to be addressed.</span></span>  
  
## <a name="overview-of-ss_smartbackup-built-in-debugging"></a><span data-ttu-id="66e49-107">[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]的内置调试概述</span><span class="sxs-lookup"><span data-stu-id="66e49-107">Overview of [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] Built-in Debugging</span></span>  
 <span data-ttu-id="66e49-108">[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]定期检查计划的备份并尝试重新安排任何失败的备份。</span><span class="sxs-lookup"><span data-stu-id="66e49-108">The [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] periodically reviews scheduled backups and attempts to reschedule any failed backups.</span></span> <span data-ttu-id="66e49-109">它定期轮询存储帐户以找出日志链中影响数据库可恢复性的中断情况，并且相应地安排新备份。</span><span class="sxs-lookup"><span data-stu-id="66e49-109">It polls the storage account periodically to identify breaks in log chains affecting recoverability of the database, and schedules new backups accordingly.</span></span> <span data-ttu-id="66e49-110">它还将考虑 Azure 限制策略，并提供管理多个数据库备份的机制。</span><span class="sxs-lookup"><span data-stu-id="66e49-110">It also takes into account Azure throttling policies, and has mechanisms in place to manage multiple database backups.</span></span> [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]<span data-ttu-id="66e49-111">使用扩展事件跟踪所有活动。</span><span class="sxs-lookup"><span data-stu-id="66e49-111">uses extended events to track all activity.</span></span> <span data-ttu-id="66e49-112">[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]代理使用的扩展事件通道包括管理、操作、分析和调试。</span><span class="sxs-lookup"><span data-stu-id="66e49-112">The Extended Event channels used by [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] agent include, Admin, Operational, Analytical, and Debug.</span></span> <span data-ttu-id="66e49-113">属于管理类别的事件通常与错误相关且要求用户干预，并且默认情况下是启用的。</span><span class="sxs-lookup"><span data-stu-id="66e49-113">Events that fall under the Admin category usually are related to errors and require user intervention and are enabled by default.</span></span> <span data-ttu-id="66e49-114">分析事件默认情况下也启用，但通常与要求用户干预的错误无关。</span><span class="sxs-lookup"><span data-stu-id="66e49-114">Analytical events are also turned on by default, but usually are not related to errors that require user intervention.</span></span> <span data-ttu-id="66e49-115">操作事件通常是信息性的。</span><span class="sxs-lookup"><span data-stu-id="66e49-115">Operation events are typically informational.</span></span> <span data-ttu-id="66e49-116">例如，操作事件包括计划备份、成功完成备份等。调试是最详细的，在内部使用，用于 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 确定问题并在需要时对其进行更正。</span><span class="sxs-lookup"><span data-stu-id="66e49-116">For example, operational events include scheduling a backup, a successful completion of backup, etc. The Debug is the most verbose and is used internally by [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] to determine issues and correct them if required.</span></span>  
  
### <a name="configure-monitoring-parameters-for-ss_smartbackup"></a><span data-ttu-id="66e49-117">为[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]配置监视参数</span><span class="sxs-lookup"><span data-stu-id="66e49-117">Configure Monitoring Parameters for [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]</span></span>  
 <span data-ttu-id="66e49-118">**Smart_admin sp_set_parameter**系统存储过程允许您指定监视设置。</span><span class="sxs-lookup"><span data-stu-id="66e49-118">The **smart_admin.sp_set_parameter** system stored procedure allows you to specify monitoring settings.</span></span> <span data-ttu-id="66e49-119">以下部分演练启用扩展事件以及针对错误和警告启用电子邮件通知的过程。</span><span class="sxs-lookup"><span data-stu-id="66e49-119">The following sections walks through the process of enabling Extended Events,  and enabling email notification for errors and warnings.</span></span>  
  
 <span data-ttu-id="66e49-120">**Smart_admin fn_get_parameter**函数可用于获取特定参数或所有已配置参数的当前设置。</span><span class="sxs-lookup"><span data-stu-id="66e49-120">The **smart_admin.fn_get_parameter** function can be used to get the current setting for a specific parameter or all configured parameters.</span></span> <span data-ttu-id="66e49-121">如果从未配置参数，则此函数不返回任何值。</span><span class="sxs-lookup"><span data-stu-id="66e49-121">If the parameters have never been configured, the function does not return any values.</span></span>  
  
1.  <span data-ttu-id="66e49-122">连接到 [!INCLUDE[ssDE](../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="66e49-122">Connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="66e49-123">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="66e49-123">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="66e49-124">将以下示例复制并粘贴到查询窗口中，然后单击 **“执行”** 。</span><span class="sxs-lookup"><span data-stu-id="66e49-124">Copy and paste the following example into the query window and then click **Execute**.</span></span> <span data-ttu-id="66e49-125">这将返回扩展事件的当前配置和电子邮件通知。</span><span class="sxs-lookup"><span data-stu-id="66e49-125">This will return the current configuration for Extended Events, and e-mail notifications.</span></span>  
  
```sql
Use msdb  
Go  
SELECT * FROM smart_admin.fn_get_parameter (NULL)  
GO  
```  
  
 <span data-ttu-id="66e49-126">有关详细信息，请参阅[smart_admin fn_get_parameter &#40;transact-sql&#41;](/sql/relational-databases/system-functions/managed-backup-fn-get-parameter-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="66e49-126">For more information, see [smart_admin.fn_get_parameter &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/managed-backup-fn-get-parameter-transact-sql)</span></span>  
  
### <a name="extended-events-for-monitoring"></a><span data-ttu-id="66e49-127">用于监视的扩展事件</span><span class="sxs-lookup"><span data-stu-id="66e49-127">Extended Events for Monitoring</span></span>  
 <span data-ttu-id="66e49-128">默认情况下，启用管理、操作和分析事件。</span><span class="sxs-lookup"><span data-stu-id="66e49-128">By default, Admin, Operational and Analytical events are turned on.</span></span> <span data-ttu-id="66e49-129">管理事件最严重，在找出需要手动干预才能解决问题的错误时很有用。</span><span class="sxs-lookup"><span data-stu-id="66e49-129">Admin events are most critical, useful when identifying errors that require manual intervention to solve the problem.</span></span> <span data-ttu-id="66e49-130">可能要开启操作和调试事件，但要考虑到这些事件为详细事件，可能需要进行一些筛选。</span><span class="sxs-lookup"><span data-stu-id="66e49-130">You may want to turn on the operational and debug events but consider that these events are verbose and may require some filtering.</span></span> <span data-ttu-id="66e49-131">以下过程描述如何监视通过扩展事件记录的事件。</span><span class="sxs-lookup"><span data-stu-id="66e49-131">The following procedures describe how to monitor events logged through Extended Events.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="66e49-132">与 SQL 引擎的扩展事件不同，[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]不支持扩展事件会话概念。</span><span class="sxs-lookup"><span data-stu-id="66e49-132">Unlike Extended Events for SQL Engine, [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] does not support Extended Event session concepts.</span></span> <span data-ttu-id="66e49-133">系统存储过程和函数是用于与扩展事件交互的工具。</span><span class="sxs-lookup"><span data-stu-id="66e49-133">System stored procedures and functions are the tools used to interact with extended events.</span></span> <span data-ttu-id="66e49-134">您还可以从日志目录查看扩展事件日志。</span><span class="sxs-lookup"><span data-stu-id="66e49-134">You can also view the extended event log from the log directory.</span></span>  
  
##### <a name="to-configure-and-view-extended-events"></a><span data-ttu-id="66e49-135">配置和查看扩展事件</span><span class="sxs-lookup"><span data-stu-id="66e49-135">To Configure and View Extended Events</span></span>  
  
1.  <span data-ttu-id="66e49-136">通过运行以下查询查看可用的扩展事件通道及其当前状态：</span><span class="sxs-lookup"><span data-stu-id="66e49-136">To view available Extended Event channels and their current status by running the following query:</span></span>  
  
    ```sql
    SELECT * FROM smart_admin.fn_get_current_xevent_settings()  
    ```  
  
     <span data-ttu-id="66e49-137">此查询的输出将显示 event_name，无论它是否可配置以及当前是否启用。</span><span class="sxs-lookup"><span data-stu-id="66e49-137">The output from this query will display the event_name, whether it is configurable or not, and whether it is currently enabled.</span></span>  <span data-ttu-id="66e49-138">有关详细信息，请参阅[smart_admin fn_get_current_xevent_settings &#40;transact-sql&#41;](/sql/relational-databases/system-functions/managed-backup-fn-get-current-xevent-settings-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="66e49-138">For more information, see [smart_admin.fn_get_current_xevent_settings &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/managed-backup-fn-get-current-xevent-settings-transact-sql).</span></span>  
  
2.  <span data-ttu-id="66e49-139">若要启用调试事件，请运行以下查询：</span><span class="sxs-lookup"><span data-stu-id="66e49-139">To enable debug events, run the following query:</span></span>  
  
    ```sql
    --  to enable debug events  
    Use msdb;  
    GO 
    EXEC smart_admin.sp_set_parameter 'FileRetentionDebugXevent', 'True'  
    ```  
  
     <span data-ttu-id="66e49-140">有关存储过程的详细信息，请参阅[smart_admin sp_set_parameter &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/managed-backup-sp-set-parameter-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="66e49-140">For more information about the stored procedure, see [smart_admin.sp_set_parameter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/managed-backup-sp-set-parameter-transact-sql).</span></span>  
  
3.  <span data-ttu-id="66e49-141">若要查看记入日志的事件，请使用以下查询：</span><span class="sxs-lookup"><span data-stu-id="66e49-141">To view the logged events run the following query:</span></span>  
  
    ```sql
    --  View all events in the current week  
    Use msdb;  
    Go  
    DECLARE @startofweek datetime  
    DECLARE @endofweek datetime  
    SET @startofweek = DATEADD(Day, 1-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)
    SET @endofweek = DATEADD(Day, 7-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)  
  
    EXEC smart_admin.sp_get_backup_diagnostics @begin_time = @startofweek, @end_time = @endofweek;
    ```  
  
    ```sql
    --  view all admin events  
    Use msdb;  
    Go  
    DECLARE @startofweek datetime  
    DECLARE @endofweek datetime  
    SET @startofweek = DATEADD(Day, 1-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)   
    SET @endofweek = DATEADD(Day, 7-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)  
  
    DECLARE @eventresult TABLE  
    (event_type nvarchar(512),  
    event nvarchar (512),  
    timestamp datetime  
    )  
  
    INSERT INTO @eventresult  
  
    EXEC smart_admin.sp_get_backup_diagnostics @begin_time = @startofweek, @end_time = @endofweek  
  
    SELECT * from @eventresult  
    WHERE event_type LIKE '%admin%'
    ```  
  
### <a name="aggregated-error-countshealth-status"></a><span data-ttu-id="66e49-142">聚合的错误计数/运行状态</span><span class="sxs-lookup"><span data-stu-id="66e49-142">Aggregated Error Counts/Health Status</span></span>  
 <span data-ttu-id="66e49-143">**Smart_admin fn_get_health_status**函数返回一个表，其中列出了可用于监视的运行状况的每个类别的聚合错误计数 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="66e49-143">The **smart_admin.fn_get_health_status** function returns a table of aggregated error counts for each category that can be used to monitor the health status of [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)].</span></span> <span data-ttu-id="66e49-144">本主题中后面介绍的系统配置的电子邮件通知机制也使用这个相同的函数。</span><span class="sxs-lookup"><span data-stu-id="66e49-144">This same function is also used by the system configured e-mail notification mechanism described later in this topic.</span></span>   
<span data-ttu-id="66e49-145">这些聚合的计数可用于监视系统运行状况。</span><span class="sxs-lookup"><span data-stu-id="66e49-145">These aggregated counts can be used to monitor system health.</span></span> <span data-ttu-id="66e49-146">例如，如果 number_ of_retention_loops 列在 30 分钟内为 0，则可能保持管理占用较长时间，或者甚至未正确工作。</span><span class="sxs-lookup"><span data-stu-id="66e49-146">For example, if the number_ of_retention_loops column is 0 in 30 minutes, it is possible that retention management is taking long time or even not working correctly.</span></span> <span data-ttu-id="66e49-147">非零错误列可能指示问题，并且应查看扩展事件日志以便发现问题。</span><span class="sxs-lookup"><span data-stu-id="66e49-147">Non-zero error columns may indicate problems and Extended Events logs should be checked to discover the problem.</span></span> <span data-ttu-id="66e49-148">或者，调用**smart_admin sp_get_backup_diagnostics**存储过程以查找错误的详细信息。</span><span class="sxs-lookup"><span data-stu-id="66e49-148">Alternatively, call **smart_admin.sp_get_backup_diagnostics** stored procedure to find the details of the error.</span></span>  
  
### <a name="using-agent-notification-for-assessing-backup-status-and-health"></a><span data-ttu-id="66e49-149">使用代理通知以便评估备份状态和运行状况</span><span class="sxs-lookup"><span data-stu-id="66e49-149">Using Agent Notification for Assessing Backup Status and Health</span></span>  
 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]<span data-ttu-id="66e49-150">包括一个通知机制，后者基于 SQL Server 基于策略的管理策略。</span><span class="sxs-lookup"><span data-stu-id="66e49-150">includes a notification mechanism that is based on SQL Server policy based management policies.</span></span>  
  
 <span data-ttu-id="66e49-151">**先决条件：**</span><span class="sxs-lookup"><span data-stu-id="66e49-151">**Prerequisites:**</span></span>  
  
-   <span data-ttu-id="66e49-152">使用此功能需要数据库邮件。</span><span class="sxs-lookup"><span data-stu-id="66e49-152">Database Mail is required to use this functionality.</span></span> <span data-ttu-id="66e49-153">有关如何为 SQL Server 实例启用 DB 邮件的详细信息，请参阅[Configure 数据库邮件](../relational-databases/database-mail/configure-database-mail.md)。</span><span class="sxs-lookup"><span data-stu-id="66e49-153">For more information, about how to enable DB Mail for the instance of SQL Server, see [Configure Database Mail](../relational-databases/database-mail/configure-database-mail.md).</span></span>  
  
-   <span data-ttu-id="66e49-154">SQL Server 代理警报系统属性应设置为使用数据库邮件。</span><span class="sxs-lookup"><span data-stu-id="66e49-154">SQL Server Agent Alert System properties should be set to use Database Mail.</span></span>  
  
 <span data-ttu-id="66e49-155">**通知体系结构：**</span><span class="sxs-lookup"><span data-stu-id="66e49-155">**Notification Architecture:**</span></span>  
  
-   <span data-ttu-id="66e49-156">**基于策略的管理：** 设置了两个策略来监视备份运行状况：**智能管理系统运行状况策略**和**智能管理用户操作运行状况策略**。</span><span class="sxs-lookup"><span data-stu-id="66e49-156">**Policy Based Management:** Two policies are set to monitor backup health: **Smart Admin System Health Policy**, and the **Smart Admin User Action Health Policy**.</span></span> <span data-ttu-id="66e49-157">智能管理系统运行状况策略评估严重错误（例如 SQL 凭据无效或缺少 SQL 凭据、连接错误），并且报告系统的运行状况。</span><span class="sxs-lookup"><span data-stu-id="66e49-157">The Smart Admin System Health Policy evaluates critical errors like lack of or invalid SQL Credentials, connectivity errors and reports the health of the system.</span></span> <span data-ttu-id="66e49-158">这些问题通常要求手动操作以便纠正基本问题。</span><span class="sxs-lookup"><span data-stu-id="66e49-158">These typically require a manual action to correct the underlying issue.</span></span> <span data-ttu-id="66e49-159">智能管理用户操作运行状况策略评估警告，例如损坏的备份等。</span><span class="sxs-lookup"><span data-stu-id="66e49-159">The Smart Admin User Action Health Policy evaluates warnings such as corrupted backups, and such.</span></span>  <span data-ttu-id="66e49-160">这些问题可能无需任何操作，只是对某一事件的警告。</span><span class="sxs-lookup"><span data-stu-id="66e49-160">These may not require any action but just a warning of an event.</span></span> <span data-ttu-id="66e49-161">此类问题应该由[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]代理自动负责处理。</span><span class="sxs-lookup"><span data-stu-id="66e49-161">It is expected that such issues will be automatically taken care of by [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] agent.</span></span>  
  
-   <span data-ttu-id="66e49-162">**SQL Server 代理**作业：使用包含三个作业步骤的 SQL Server 代理作业来执行通知。</span><span class="sxs-lookup"><span data-stu-id="66e49-162">**SQL Server Agent** Job: The notification is performed using a SQL Server Agent job that has three job steps.</span></span> <span data-ttu-id="66e49-163">在第一个作业步骤中，它将进行检测以便查看[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]是为数据库还是实例配置的。</span><span class="sxs-lookup"><span data-stu-id="66e49-163">In the first job step it detects to see whether [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] is configured for a database or instance.</span></span> <span data-ttu-id="66e49-164">如果它发现启用并配置了[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]，则它执行第二步：执行一个 PowerShell cmdlet，后者通过评估 SQL Server 基于策略的管理策略，评估运行状况。</span><span class="sxs-lookup"><span data-stu-id="66e49-164">If it finds [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] enabled and configured, it executes the second step: executes a PowerShell cmdlet that assess the health status by evaluating the SQL Server policy based management policies.</span></span> <span data-ttu-id="66e49-165">如果它发现错误或警告，则它将失败，而这将触发第三步：第三步发出一个电子邮件通知，其中含有错误/警告报表。</span><span class="sxs-lookup"><span data-stu-id="66e49-165">If it finds either an error or warning, it fails which then triggers the third step: The third step sends out an e-mail notification with the error/warning report.</span></span>  <span data-ttu-id="66e49-166">但是，默认情况下不启用此 SQL Server 代理作业。</span><span class="sxs-lookup"><span data-stu-id="66e49-166">However this SQL Server Agent job is not enabled by default.</span></span> <span data-ttu-id="66e49-167">若要启用电子邮件通知作业，请使用**smart_admin sp_set_backup_parameter**系统存储过程。</span><span class="sxs-lookup"><span data-stu-id="66e49-167">To enable the e-mail notification job, use the **smart_admin.sp_set_backup_parameter** system stored procedure.</span></span>  <span data-ttu-id="66e49-168">下面的过程更详细地说明了这些步骤：</span><span class="sxs-lookup"><span data-stu-id="66e49-168">The following procedure describes the steps in more detail:</span></span>  
  
##### <a name="enabling-email-notification"></a><span data-ttu-id="66e49-169">启用通知电子邮件</span><span class="sxs-lookup"><span data-stu-id="66e49-169">Enabling Email Notification</span></span>  
  
1.  <span data-ttu-id="66e49-170">如果尚未配置数据库邮件，请使用[配置数据库邮件](../relational-databases/database-mail/configure-database-mail.md)中所述的步骤。</span><span class="sxs-lookup"><span data-stu-id="66e49-170">If Database Mail is not already configured, use the steps described in [Configure Database Mail](../relational-databases/database-mail/configure-database-mail.md).</span></span>  
  
2.  <span data-ttu-id="66e49-171">将数据库设置为 SQL Server 警报系统的邮件系统：右键单击**SQL Server 代理**，选择 "**警报系统**"，选中 "**启用邮件配置文件**" 框，选择**数据库邮件**作为**邮件系统**，然后选择以前创建的邮件配置文件。</span><span class="sxs-lookup"><span data-stu-id="66e49-171">Set database as the Mail System for SQL Server Alert System: Right Click on **SQL Server Agent**, select **Alert System**, check the **Enable mail profile** box, Select **Database Mail** as the **Mail System**, and select a previously created Mail profile.</span></span>  
  
3.  <span data-ttu-id="66e49-172">在查询窗口中运行以下查询并提供要将通知发送到的电子邮件地址：</span><span class="sxs-lookup"><span data-stu-id="66e49-172">Run the following query in a query window and provide the e-mail address where you want the notification to be sent to:</span></span>  
  
    ```sql
    Use msdb  
    Go  
    EXEC smart_admin.sp_set_parameter @parameter_name = 'SSMBackup2WANotificationEmailIds', @parameter_value = '<email address>'
    ```  
  
     <span data-ttu-id="66e49-173">这将创建一个 SQL Server 代理作业，它用于收集运行状态并且在没有与备份有关的错误或问题时发送通知。</span><span class="sxs-lookup"><span data-stu-id="66e49-173">This creates a SQL Server Agent job that is used to gather health status and send notifications when there is an error or an issue with backups.</span></span>  
  
 <span data-ttu-id="66e49-174">下面是一个示例脚本，它通过 SQL Server 代理作业启用数据库邮件和设置电子邮件通知</span><span class="sxs-lookup"><span data-stu-id="66e49-174">Following is a sample script  to enable DB Mail and set up the e-mail notification through SQL Server Agent Job</span></span>  
  
```sql
-- Prereq: Make sure that SQL Server service runs in a service account that has  
--  access to SMTP Server   
-- set SQL Server service account as domain account   
  
EXEC sp_configure 'show advanced', 1  
RECONFIGURE  
GO  
  
-- Enable DBMail  
EXEC sp_configure 'Database Mail XPs',1  
GO  
RECONFIGURE  
GO  
  
-- Configure DBMail  
DECLARE @emailid NVARCHAR(255)  
-- Note: change this email to your own email id  
SET @emailid = N'emailalias@mycompany.com'  
  
DECLARE @smtpserver NVARCHAR(255)  
SET @smtpserver = N'smtphost.domainname.com'  
  
DECLARE @mailprofile NVARCHAR(255)  
SET @mailprofile = N'my_profile'  
  
EXEC msdb.dbo.sysmail_add_account_sp @account_name=N'myaccount',  
                @email_address = @emailid,  
                @replyto_address = @emailid,  
                @mailserver_name = @smtpserver,  
                @use_default_credentials = 1  
  
EXEC msdb.dbo.sysmail_add_profile_sp @profile_name=@mailprofile  
EXEC msdb.dbo.sysmail_add_profileaccount_sp @profile_name=@mailprofile, @account_name=N'myaccount', @sequence_number=1  
  
-- Set SQL Agent to use DBMail profile  
EXEC msdb.dbo.sp_set_sqlagent_properties @databasemail_profile = @mailprofile  
  
-- Configure Notifications   
EXEC msdb.smart_admin.sp_set_parameter  
@parameter_name = 'SSMBackup2WANotificationEmailIds',  
@parameter_value = @emailid  
  
-- To test is you are receiving notifications  
-- delete few backup files from your storage container, Wait for 15 minutes & see if you get any email notification
```  
  
### <a name="using-powershell-to-setup-custom-health-monitoring"></a><span data-ttu-id="66e49-175">使用 PowerShell 设置自定义运行状况监视</span><span class="sxs-lookup"><span data-stu-id="66e49-175">Using PowerShell to Setup Custom Health Monitoring</span></span>  
 <span data-ttu-id="66e49-176">**Get-sqlsmartadmin** cmdlet 可用于创建自定义运行状况监视。</span><span class="sxs-lookup"><span data-stu-id="66e49-176">The **Test-SqlSmartAdmin** cmdlet can be used to create custom health monitoring.</span></span> <span data-ttu-id="66e49-177">例如，可在实例级别配置前一部分中所述的通知选项。</span><span class="sxs-lookup"><span data-stu-id="66e49-177">For example, the notification option described in the previous section can be configured at the instance level.</span></span>  <span data-ttu-id="66e49-178">如果将若干 SQL Server 实例配置为使用[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]，则可使用 PowerShell cmdlet 创建脚本，为所有实例收集备份的状态和运行状况。</span><span class="sxs-lookup"><span data-stu-id="66e49-178">If you have several instances of SQL Server configured to use [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)], the PowerShell cmdlet can be used to create scripts in gather the status and health of backups for all the instances.</span></span>  
  
 <span data-ttu-id="66e49-179">**Get-sqlsmartadmin** cmdlet 将评估 SQL Server 基于策略的管理策略返回的错误和警告，并报告汇总的状态。</span><span class="sxs-lookup"><span data-stu-id="66e49-179">The **Test-SqlSmartAdmin** cmdlet assesses the errors and warnings returned by the SQL Server Policy Based Management policies and reports out a rolled up status.</span></span>  <span data-ttu-id="66e49-180">默认情况下，此 cmdlet 使用系统策略。</span><span class="sxs-lookup"><span data-stu-id="66e49-180">By default this cmdlet uses the system policies.</span></span> <span data-ttu-id="66e49-181">若要包括任何自定义策略，请使用 `-AllowUserPolicies` 参数。</span><span class="sxs-lookup"><span data-stu-id="66e49-181">To include any custom policy use the `-AllowUserPolicies` parameter.</span></span>  
  
 <span data-ttu-id="66e49-182">下面是一个示例 PowerShell 脚本，它基于系统策略以及任何创建的用户策略返回错误和警告的报告：</span><span class="sxs-lookup"><span data-stu-id="66e49-182">Following is a sample PowerShell script that returns a report of errors and warnings based on the system policies and any user policies created:</span></span>  
  
```powershell
$policyResults = Get-SqlSmartAdmin | Test-SqlSmartAdmin -AllowUserPolicies  
$policyResults.PolicyEvaluationDetails | Select Name, Category, Expression, Result, Exception | fl
```  
  
 <span data-ttu-id="66e49-183">下面的脚本将返回默认实例 () 的错误和警告的详细报告 `\SQL\COMPUTER\DEFAULT` ：</span><span class="sxs-lookup"><span data-stu-id="66e49-183">The following script returns a detailed report of the errors and warnings for the default instance (`\SQL\COMPUTER\DEFAULT`):</span></span>  
  
```powershell
(Get-SqlSmartAdmin ).EnumHealthStatus()  
```  
  
### <a name="objects-in-msdb-database"></a><span data-ttu-id="66e49-184">MSDB 数据库中的对象</span><span class="sxs-lookup"><span data-stu-id="66e49-184">Objects in MSDB database</span></span>  
 <span data-ttu-id="66e49-185">为实现功能，安装了一些对象。</span><span class="sxs-lookup"><span data-stu-id="66e49-185">There are objects that are installed to implement the functionality.</span></span> <span data-ttu-id="66e49-186">这些对象仅供内部使用。</span><span class="sxs-lookup"><span data-stu-id="66e49-186">These objects are reserved for internal use.</span></span> <span data-ttu-id="66e49-187">但是，有一个系统表对于监视备份状态可能很有用：smart_backup_files。</span><span class="sxs-lookup"><span data-stu-id="66e49-187">However, there is one system table that can be useful in monitoring the backup status: smart_backup_files.</span></span> <span data-ttu-id="66e49-188">此表中存储的与监视（如备份类型、数据库名称、第一个 lsn 和最后一个 lsn）相关的大部分信息都是通过 system 函数[smart_admin fn_available_backups&#41;&#40;。 ](/sql/relational-databases/system-functions/managed-backup-fn-available-backups-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="66e49-188">Most of the Information   stored in this table relevant to monitoring like the type of backup, database name, first and last lsn, backup expiry dates are exposed through the system function [smart_admin.fn_available_backups &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/managed-backup-fn-available-backups-transact-sql).</span></span> <span data-ttu-id="66e49-189">但是，使用该函数时无法使用 smart_backup_files 表中指示备份文件状态的 status 列。</span><span class="sxs-lookup"><span data-stu-id="66e49-189">However the status column in the smart_backup_files table which indicates the status of the backup file is not available using the function.</span></span> <span data-ttu-id="66e49-190">下面是一个示例查询，可使用它从系统表检索某些信息（包括状态）：</span><span class="sxs-lookup"><span data-stu-id="66e49-190">Following is a sample query you can use to retrieve the some information including the status from the system table:</span></span>  
  
```sql
USE msdb  
GO  
SELECT  
 database_name AS [Database Name] ,backup_path AS [Backup Destination and File]  
,[Backup Type] =  
CASE backup_type  
WHEN 1 THEN 'FULL'  
WHEN 2 THEN 'LOG'  
END  
,[Backup Status] =  
CASE [status]  
WHEN 'A' THEN 'Available'  
WHEN 'B' THEN 'Copy In Progress'  
WHEN 'C' THEN 'Corrupted'  
WHEN 'D' THEN 'Deleted'  
WHEN 'F' THEN 'Copy Failed'  
WHEN 'U' THEN 'Unknown'  
END  
,first_lsn AS [First LSN]  
,last_lsn AS [Last LSN]  
,backup_start_date AS [Backup Start Time]  
,backup_finish_date AS [Backup Completion Time]  
,expiration_date AS [Backup Expiry Date/Time]  
FROM  
smart_backup_files;
```  
  
 <span data-ttu-id="66e49-191">以下详细介绍返回的不同状态：</span><span class="sxs-lookup"><span data-stu-id="66e49-191">Following is a detailed explanation of the different status returned:</span></span>  
  
-   <span data-ttu-id="66e49-192">**可用-A：** 这是一个正常的备份文件。</span><span class="sxs-lookup"><span data-stu-id="66e49-192">**Available - A:** This is a normal backup file.</span></span> <span data-ttu-id="66e49-193">备份已完成，并且还验证它在 Azure 存储中可用。</span><span class="sxs-lookup"><span data-stu-id="66e49-193">The backup has been completed, and also verified that it is available in the Azure storage.</span></span>  
  
-   <span data-ttu-id="66e49-194">**正在进行复制-B：** 此状态专门用于可用性组数据库。</span><span class="sxs-lookup"><span data-stu-id="66e49-194">**Copy in Progress -B:** This status is specifically for Availability Group databases.</span></span> <span data-ttu-id="66e49-195">如果 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 检测到备份日志链中断，则它将首先尝试找出可能导致备份链中断的备份。</span><span class="sxs-lookup"><span data-stu-id="66e49-195">If [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] detects a break in the backup log chain, it will first attempt identify the  backup that might have caused the break in backup chain.</span></span> <span data-ttu-id="66e49-196">查找备份文件时，它会尝试将文件复制到 Azure 存储。</span><span class="sxs-lookup"><span data-stu-id="66e49-196">On finding the backup file it attempts to copy the file to Azure storage.</span></span> <span data-ttu-id="66e49-197">在进行复制过程时，它将显示此状态。</span><span class="sxs-lookup"><span data-stu-id="66e49-197">When the copying process is in progress it will display this status.</span></span>  
  
-   <span data-ttu-id="66e49-198">**复制失败-F：** 类似于正在进行复制，这是特定的 t 可用性组数据库。</span><span class="sxs-lookup"><span data-stu-id="66e49-198">**Copy Failed - F:** Similar to Copy In Progress, this is specific t Availability Group databases.</span></span> <span data-ttu-id="66e49-199">如果复制过程失败，则将状态标为 F。</span><span class="sxs-lookup"><span data-stu-id="66e49-199">If the copy process fails, the status is marked as F.</span></span>  
  
-   <span data-ttu-id="66e49-200">**损坏-C：** 如果在 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 多次尝试后仍无法通过执行还原 HEADER_ONLY 命令来验证存储中的备份文件，则会将此文件标记为已损坏。</span><span class="sxs-lookup"><span data-stu-id="66e49-200">**Corrupted - C:** If [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] is unable to verify the backup file in the storage by performing a RESTORE HEADER_ONLY command even after multiple attempts, it marks this file as corrupted.</span></span> [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] <span data-ttu-id="66e49-201">将安排一次备份以确保损坏的文件不会导致备份链中断。</span><span class="sxs-lookup"><span data-stu-id="66e49-201">will schedule a backup to ensure that the corrupted file does not result in a break of the backup chain.</span></span>  
  
-   <span data-ttu-id="66e49-202">**已删除-D：** 在 Azure 存储中找不到相应的文件。</span><span class="sxs-lookup"><span data-stu-id="66e49-202">**Deleted - D:** The corresponding file cannot be found in the Azure storage.</span></span> <span data-ttu-id="66e49-203">如果删除的文件导致备份链中断，则 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 将安排一次备份。</span><span class="sxs-lookup"><span data-stu-id="66e49-203">[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] will schedule a backup if the deleted file results in a break in the backup chain.</span></span>  
  
-   <span data-ttu-id="66e49-204">**未知-U：** 此状态表明，尚未 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 能够验证 Azure 存储中是否存在文件和其属性。</span><span class="sxs-lookup"><span data-stu-id="66e49-204">**Unknown - U:** This status indicated that [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] has not yet been able to verify file existence and its properties in the Azure storage.</span></span> <span data-ttu-id="66e49-205">下次运行此过程时（大约每 15 分钟一次），将更新此状态。</span><span class="sxs-lookup"><span data-stu-id="66e49-205">The next time the process runs, which is approximately every 15 minutes, this status will be updated.</span></span>  
