---
title: 创建 SQL Server 代理主作业 | Microsoft Docs
ms.custom: ''
ms.date: 04/26/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], master jobs
- jobs [SQL Server Agent], creating
- master SQL Server Agent job [SQL Server]
ms.assetid: c12ab23f-d7ee-43a5-8cd2-0a9121292bcd
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8a6503caec3f153878e360ee29ce09a5c099ade5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689699"
---
# <a name="create-a-sql-server-agent-master-job"></a><span data-ttu-id="1aca9-102">创建 SQL Server 代理主作业</span><span class="sxs-lookup"><span data-stu-id="1aca9-102">Create a SQL Server Agent Master Job</span></span>
  <span data-ttu-id="1aca9-103">本主题说明如何 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用或在中创建主代理作业 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="1aca9-103">This topic describes how to create a master [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="1aca9-104">开始之前</span><span class="sxs-lookup"><span data-stu-id="1aca9-104">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="1aca9-105">限制和局限</span><span class="sxs-lookup"><span data-stu-id="1aca9-105">Limitations and Restrictions</span></span>  
 <span data-ttu-id="1aca9-106">对主 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业所做更改必须传播到所有涉及的目标服务器。</span><span class="sxs-lookup"><span data-stu-id="1aca9-106">Changes to master [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs must be propagated to all involved target servers.</span></span> <span data-ttu-id="1aca9-107">由于在指定那些目标后，目标服务器才开始下载作业，因此 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 建议在完成特定作业的所有作业步骤和作业计划后，再指定任何目标服务器。</span><span class="sxs-lookup"><span data-stu-id="1aca9-107">Because target servers do not initially download a job until those targets are specified, [!INCLUDE[msCoName](../../includes/msconame-md.md)] recommends that you complete all job steps and job schedules for a particular job before you specify any target servers.</span></span> <span data-ttu-id="1aca9-108">否则，必须通过执行 **sp_post_msx_operation** 存储过程或使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]修改作业来手动请求目标服务器重新下载修改后的作业。</span><span class="sxs-lookup"><span data-stu-id="1aca9-108">Otherwise, you must manual request that the target servers download the modified job again, either by executing the **sp_post_msx_operation** stored procedure or modifying the job using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="1aca9-109">有关详细信息，请参阅[sp_post_msx_operation &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-post-msx-operation-transact-sql)或[修改作业](modify-a-job.md)。</span><span class="sxs-lookup"><span data-stu-id="1aca9-109">For more information, see [sp_post_msx_operation &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-post-msx-operation-transact-sql) or [Modify a Job](modify-a-job.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="1aca9-110">Security</span><span class="sxs-lookup"><span data-stu-id="1aca9-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="1aca9-111">权限</span><span class="sxs-lookup"><span data-stu-id="1aca9-111">Permissions</span></span>  
 <span data-ttu-id="1aca9-112">如果分布式作业的步骤与某个代理相关联，则该作业将在目标服务器上该代理帐户的上下文下运行。</span><span class="sxs-lookup"><span data-stu-id="1aca9-112">Distributed jobs that have steps which are associated with a proxy run under the context of the proxy account on the target server.</span></span> <span data-ttu-id="1aca9-113">请确保满足以下条件，否则与代理关联的作业步骤将不会从主服务器下载到目标服务器上：</span><span class="sxs-lookup"><span data-stu-id="1aca9-113">Make sure that the following conditions are met or job steps that are associated with a proxy will not be downloaded from the master server to the target:</span></span>  
  
-   <span data-ttu-id="1aca9-114">注册表子项**\ HKEY_LOCAL_MACHINE \software\microsoft\microsoft SQL Server \\ < *instance_name*> \sql Server Agent\AllowDownloadedJobsToMatchProxyName** (REG_DWORD) 设置为 1 () 为 true。</span><span class="sxs-lookup"><span data-stu-id="1aca9-114">The registry subkey **\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<*instance_name*>\SQL Server Agent\AllowDownloadedJobsToMatchProxyName** (REG_DWORD) is set to 1 (true).</span></span> <span data-ttu-id="1aca9-115">默认情况下，此子项设置为 0 (False)。</span><span class="sxs-lookup"><span data-stu-id="1aca9-115">By default, this subkey is set to 0 (false).</span></span>  
  
-   <span data-ttu-id="1aca9-116">目标服务器上已存在与运行作业步骤的主服务器代理帐户同名的代理帐户。</span><span class="sxs-lookup"><span data-stu-id="1aca9-116">A proxy account exists on the target server that has the same name as the master server proxy account under which the job step runs.</span></span>  
  
 <span data-ttu-id="1aca9-117">从主服务器将使用代理帐户的作业步骤下载到目标服务器时，如果作业步骤失败，可以检查 **msdb** 数据库中 **sysdownloadlist** 表的 **error_message** 列是否存在以下错误消息：</span><span class="sxs-lookup"><span data-stu-id="1aca9-117">If job steps that use proxy accounts fail when downloading them from the master server to the target server, you can check the **error_message** column in the **sysdownloadlist** table in the **msdb** database for the following error messages:</span></span>  
  
-   <span data-ttu-id="1aca9-118">“该作业步骤需要代理帐户，但是目标服务器上禁用了代理匹配功能。”</span><span class="sxs-lookup"><span data-stu-id="1aca9-118">"The job step requires a proxy account, however proxy matching is disabled on the target server."</span></span> <span data-ttu-id="1aca9-119">若要解决此错误，请将 **AllowDownloadedJobsToMatchProxyName** 注册表子项设置为 1。</span><span class="sxs-lookup"><span data-stu-id="1aca9-119">To resolve this error, set the **AllowDownloadedJobsToMatchProxyName** registry subkey to 1.</span></span>  
  
-   <span data-ttu-id="1aca9-120">“找不到代理。”</span><span class="sxs-lookup"><span data-stu-id="1aca9-120">"Proxy not found."</span></span> <span data-ttu-id="1aca9-121">若要解决此错误，请确保目标服务器上已存在与运行作业步骤的主服务器代理帐户同名的代理帐户。</span><span class="sxs-lookup"><span data-stu-id="1aca9-121">To resolve this error, make sure a proxy account exists on the target server that has the same name as the master server proxy account under which the job step runs.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="1aca9-122">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="1aca9-122">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-master-sql-server-agent-job"></a><span data-ttu-id="1aca9-123">创建主 SQL Server 代理作业</span><span class="sxs-lookup"><span data-stu-id="1aca9-123">To create a master SQL Server Agent job</span></span>  
  
1.  <span data-ttu-id="1aca9-124">在 **“对象资源管理器”** 中，单击加号以展开要创建 SQL Server 代理作业的服务器。</span><span class="sxs-lookup"><span data-stu-id="1aca9-124">In the **Object Explorer**, click the plus sign to expand the server where you want to create a SQL Server Agent job.</span></span>  
  
2.  <span data-ttu-id="1aca9-125">单击加号以展开 **“SQL Server 代理”**。</span><span class="sxs-lookup"><span data-stu-id="1aca9-125">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="1aca9-126">右键单击“作业”文件夹，然后选择“新建作业…”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1aca9-126">Right-click the **Jobs** folder and select **New Job...**.</span></span>  
  
4.  <span data-ttu-id="1aca9-127">在 **“新建作业”** 对话框的 **“常规”** 页上，修改作业的常规属性。</span><span class="sxs-lookup"><span data-stu-id="1aca9-127">In the **New Job** dialog box, on the **General** page, modify the general properties of the job.</span></span> <span data-ttu-id="1aca9-128">有关此页上可用选项的详细信息，请参阅[作业属性和新作业 &#40;常规页&#41;](../../integration-services/general-page-of-integration-services-designers-options.md)</span><span class="sxs-lookup"><span data-stu-id="1aca9-128">For more information on the available options on this page, see [Job Properties and New Job &#40;General Page&#41;](../../integration-services/general-page-of-integration-services-designers-options.md)</span></span>  
  
5.  <span data-ttu-id="1aca9-129">在 **“步骤”** 页上，组织作业步骤。</span><span class="sxs-lookup"><span data-stu-id="1aca9-129">On the **Steps** page, organize the job steps.</span></span> <span data-ttu-id="1aca9-130">有关此页上可用选项的详细信息，请参阅[作业属性：新建作业 &#40;步骤页&#41;](job-properties-new-job-steps-page.md)</span><span class="sxs-lookup"><span data-stu-id="1aca9-130">For more information on the available options on this page, see [Job Properties:New Job &#40;Steps Page&#41;](job-properties-new-job-steps-page.md)</span></span>  
  
6.  <span data-ttu-id="1aca9-131">在 **“计划”** 页上，组织作业的计划。</span><span class="sxs-lookup"><span data-stu-id="1aca9-131">On the **Schedules** page, organize schedules for the job.</span></span> <span data-ttu-id="1aca9-132">有关此页上可用选项的详细信息，请参阅[作业属性：新建作业 &#40;计划页&#41;](job-properties-new-job-schedules-page.md)</span><span class="sxs-lookup"><span data-stu-id="1aca9-132">For more information on the available options on this page, see [Job Properties: New Job &#40;Schedules Page&#41;](job-properties-new-job-schedules-page.md)</span></span>  
  
7.  <span data-ttu-id="1aca9-133">在 **“警报”** 页上，组织作业的警报。</span><span class="sxs-lookup"><span data-stu-id="1aca9-133">On the **Alerts** page, organize the alerts for the job.</span></span> <span data-ttu-id="1aca9-134">有关此页上可用选项的详细信息，请参阅[作业属性：新建作业 &#40;警报页&#41;](job-properties-new-job-alerts-page.md)</span><span class="sxs-lookup"><span data-stu-id="1aca9-134">For more information on the available options on this page, see [Job Properties: New Job &#40;Alerts Page&#41;](job-properties-new-job-alerts-page.md)</span></span>  
  
8.  <span data-ttu-id="1aca9-135">在“通知”\*\*\*\* 页上，设置在作业完成时 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理要执行的操作。</span><span class="sxs-lookup"><span data-stu-id="1aca9-135">On the **Notifications** page, set actions for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to perform when the job completes.</span></span> <span data-ttu-id="1aca9-136">有关此页上可用选项的详细信息，请参阅[作业属性：新建作业 &#40;通知页&#41;](job-properties-new-job-notifications-page.md)。</span><span class="sxs-lookup"><span data-stu-id="1aca9-136">For more information on the available options on this page, see [Job Properties: New Job &#40;Notifications Page&#41;](job-properties-new-job-notifications-page.md).</span></span>  
  
9. <span data-ttu-id="1aca9-137">在 **“目标”** 页上，管理作业的目标服务器。</span><span class="sxs-lookup"><span data-stu-id="1aca9-137">On the **Targets** page, manage the target servers for the job.</span></span> <span data-ttu-id="1aca9-138">有关此页上可用选项的详细信息，请参阅[作业属性：新建作业 &#40;目标&#41;](job-properties-new-job-targets-page.md)。</span><span class="sxs-lookup"><span data-stu-id="1aca9-138">For more information on the available options on this page, see [Job Properties: New Job &#40;Targets Page&#41;](job-properties-new-job-targets-page.md).</span></span>  
  
10. <span data-ttu-id="1aca9-139">完成后，单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="1aca9-139">When finished, click **OK**.</span></span>  
  

  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="1aca9-140">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1aca9-140">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-master-sql-server-agent-job"></a><span data-ttu-id="1aca9-141">创建主 SQL Server 代理作业</span><span class="sxs-lookup"><span data-stu-id="1aca9-141">To create a master SQL Server Agent job</span></span>  
  
1.  <span data-ttu-id="1aca9-142">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="1aca9-142">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="1aca9-143">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="1aca9-143">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="1aca9-144">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="1aca9-144">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE msdb ;  
    GO  
    -- Adds a new job executed by the SQLServerAgent service called 'Weekly Sales Data Backup'  
    EXEC dbo.sp_add_job  
        @job_name = N'Weekly Sales Data Backup' ;  
    GO  
    -- Adds a step (operation) to the 'Weekly Sales Data Backup' job.  
    EXEC sp_add_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_name = N'Set database to read only',  
        @subsystem = N'TSQL',  
        @command = N'ALTER DATABASE SALES SET READ_ONLY',   
        @retry_attempts = 5,  
        @retry_interval = 5 ;  
    GO  
    -- Creates a schedule called RunOnce  
    EXEC dbo.sp_add_schedule  
        @schedule_name = N'RunOnce',  
        @freq_type = 1,  
        @active_start_time = 233000 ;  
    USE msdb ;  
    GO  
    -- Sets the 'RunOnce' schedule to the "Weekly Sales Data Backup' Job  
    EXEC sp_attach_schedule  
       @job_name = N'Weekly Sales Data Backup',  
       @schedule_name = N'RunOnce';  
    GO  
    -- assigns the multiserver job Weekly Sales Backups to the server SEATTLE2  
    -- assumes that SEATTLE2 is registered as a target server for the current instance.  
    EXEC dbo.sp_add_jobserver  
        @job_name = N'Weekly Sales Data Backups',  
        @server_name = N'SEATTLE2' ;  
    GO  
    ```  
  
 <span data-ttu-id="1aca9-145">有关详细信息，请参阅：</span><span class="sxs-lookup"><span data-stu-id="1aca9-145">For more information, see:</span></span>  
  
-   [<span data-ttu-id="1aca9-146">sp_add_job (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="1aca9-146">sp_add_job &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-job-transact-sql)  
  
-   [<span data-ttu-id="1aca9-147">sp_add_jobstep (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="1aca9-147">sp_add_jobstep &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql)  
  
-   [<span data-ttu-id="1aca9-148">sp_add_schedule (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="1aca9-148">sp_add_schedule &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-schedule-transact-sql)  
  
-   [<span data-ttu-id="1aca9-149">sp_attach_schedule (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="1aca9-149">sp_attach_schedule &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql)  
  
-   [<span data-ttu-id="1aca9-150">sp_add_jobserver &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="1aca9-150">sp_add_jobserver &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql)  
  

  
  
