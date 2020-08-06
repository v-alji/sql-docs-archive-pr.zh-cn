---
title: 创建作业 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], creating
- SQL Server Agent jobs, creating
ms.assetid: b35af2b6-6594-40d1-9861-4d5dd906048c
author: stevestein
ms.author: sstein
ms.openlocfilehash: de74f032924fbb0b6643bd8f3d482481ffb1f983
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577214"
---
# <a name="create-a-job"></a><span data-ttu-id="6864b-102">创建作业</span><span class="sxs-lookup"><span data-stu-id="6864b-102">Create a Job</span></span>
  <span data-ttu-id="6864b-103">本主题说明如何通过使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 SQL Server 管理对象 (SMO) 在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 中创建 SQL Server 代理作业。</span><span class="sxs-lookup"><span data-stu-id="6864b-103">This topic describes how to create a SQL Server Agent job in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or SQL Server Management Objects (SMO).</span></span>  
  
 <span data-ttu-id="6864b-104">若要添加可以发送到操作员的作业步骤、计划、警报和通知，请参阅“请参阅”部分中的主题的链接。</span><span class="sxs-lookup"><span data-stu-id="6864b-104">To add job steps, schedules, alerts, and notifications that can be sent to operators, see the links to topics in the See Also section.</span></span>  
  
-   <span data-ttu-id="6864b-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="6864b-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="6864b-106">限制和局限</span><span class="sxs-lookup"><span data-stu-id="6864b-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="6864b-107">安全性</span><span class="sxs-lookup"><span data-stu-id="6864b-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="6864b-108">**若要创建作业，可使用：**</span><span class="sxs-lookup"><span data-stu-id="6864b-108">**To create a job, using:**</span></span>  
  
     <span data-ttu-id="6864b-109">[SQL Server Management Studio](#SSMSProcedure)，</span><span class="sxs-lookup"><span data-stu-id="6864b-109">[SQL Server Management Studio](#SSMSProcedure),</span></span>  
  
     [<span data-ttu-id="6864b-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="6864b-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="6864b-111">SQL Server 管理对象</span><span class="sxs-lookup"><span data-stu-id="6864b-111">SQL Server Management Objects</span></span>](#SMOProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="6864b-112">开始之前</span><span class="sxs-lookup"><span data-stu-id="6864b-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="6864b-113">限制和局限</span><span class="sxs-lookup"><span data-stu-id="6864b-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="6864b-114">若要创建作业，用户必须是某个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理固定数据库角色或 **sysadmin** 固定服务器角色的成员。</span><span class="sxs-lookup"><span data-stu-id="6864b-114">To create a job, a user must be a member of one of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent fixed database roles or the **sysadmin** fixed server role.</span></span> <span data-ttu-id="6864b-115">作业只能由其所有者或 **sysadmin** 角色的成员进行编辑。</span><span class="sxs-lookup"><span data-stu-id="6864b-115">A job can be edited only by its owner or members of the **sysadmin** role.</span></span> <span data-ttu-id="6864b-116">有关 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理的固定数据库角色的详细信息，请参阅 [SQL Server 代理固定数据库角色](sql-server-agent-fixed-database-roles.md)。</span><span class="sxs-lookup"><span data-stu-id="6864b-116">For more information about the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent fixed database roles, see [SQL Server Agent Fixed Database Roles](sql-server-agent-fixed-database-roles.md).</span></span>  
  
-   <span data-ttu-id="6864b-117">将作业指派给另一个登录名并不保证新所有者有足够的权限来成功运行该作业。</span><span class="sxs-lookup"><span data-stu-id="6864b-117">Assigning a job to another login does not guarantee that the new owner has sufficient permission to run the job successfully.</span></span>  
  
-   <span data-ttu-id="6864b-118">本地作业是由本地 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理进行缓存的。</span><span class="sxs-lookup"><span data-stu-id="6864b-118">Local jobs are cached by the local [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> <span data-ttu-id="6864b-119">因此，任何修改都会隐式强制 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理重新缓存该作业。</span><span class="sxs-lookup"><span data-stu-id="6864b-119">Therefore, any modifications implicitly force [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to re-cache the job.</span></span> <span data-ttu-id="6864b-120">由于直到调用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sp_add_jobserver **时，** 代理才缓存作业，因此最后调用 **sp_add_jobserver** 将更为有效。</span><span class="sxs-lookup"><span data-stu-id="6864b-120">Because [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent does not cache the job until **sp_add_jobserver** is called, it is more efficient to call **sp_add_jobserver** last.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="6864b-121">Security</span><span class="sxs-lookup"><span data-stu-id="6864b-121">Security</span></span>  
  
-   <span data-ttu-id="6864b-122">您必须是系统管理员才可以更改作业的所有者。</span><span class="sxs-lookup"><span data-stu-id="6864b-122">You must be a system administrator to change the owner of a job.</span></span>  
  
-   <span data-ttu-id="6864b-123">为了安全起见，仅作业所有者或 **sysadmin** 角色的成员可以更改作业的定义。</span><span class="sxs-lookup"><span data-stu-id="6864b-123">For security reasons, only the job owner or a member of the **sysadmin** role can change the definition of the job.</span></span> <span data-ttu-id="6864b-124">只有 **sysadmin** 固定服务器角色的成员才可以将作业所有权分配给其他用户，并且他们可以运行任何作业，而不管作业所有者是谁。</span><span class="sxs-lookup"><span data-stu-id="6864b-124">Only members of the **sysadmin** fixed server role can assign job ownership to other users, and they can run any job, regardless of the job owner.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6864b-125">如果将作业所有权重新指派到的用户不是 **sysadmin** 固定服务器角色的成员，而执行作业的步骤需要代理帐户（例如， [!INCLUDE[ssIS](../../includes/ssis-md.md)] 包执行），则请确保该用户可以访问该代理帐户，否则作业将失败。</span><span class="sxs-lookup"><span data-stu-id="6864b-125">If you change job ownership to a user who is not a member of the **sysadmin** fixed server role, and the job is executing job steps that require proxy accounts (for example, [!INCLUDE[ssIS](../../includes/ssis-md.md)] package execution), make sure that the user has access to that proxy account or else the job will fail.</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="6864b-126">权限</span><span class="sxs-lookup"><span data-stu-id="6864b-126">Permissions</span></span>  
 <span data-ttu-id="6864b-127">有关详细信息，请参阅[实现 SQL Server 代理安全性](implement-sql-server-agent-security.md)。</span><span class="sxs-lookup"><span data-stu-id="6864b-127">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="6864b-128">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="6864b-128">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-sql-server-agent-job"></a><span data-ttu-id="6864b-129">创建 SQL Server 代理作业</span><span class="sxs-lookup"><span data-stu-id="6864b-129">To create a SQL Server Agent job</span></span>  
  
1.  <span data-ttu-id="6864b-130">在 **“对象资源管理器”** 中，单击加号以展开要创建 SQL Server 代理作业的服务器。</span><span class="sxs-lookup"><span data-stu-id="6864b-130">In the **Object Explorer**, click the plus sign to expand the server where you want to create a SQL Server Agent job.</span></span>  
  
2.  <span data-ttu-id="6864b-131">单击加号以展开 **“SQL Server 代理”**。</span><span class="sxs-lookup"><span data-stu-id="6864b-131">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="6864b-132">右键单击“作业”文件夹，然后选择“新建作业…”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6864b-132">Right-click the **Jobs** folder and select **New Job...**.</span></span>  
  
4.  <span data-ttu-id="6864b-133">在 **“新建作业”** 对话框的 **“常规”** 页上，修改作业的常规属性。</span><span class="sxs-lookup"><span data-stu-id="6864b-133">In the **New Job** dialog box, on the **General** page, modify the general properties of the job.</span></span> <span data-ttu-id="6864b-134">有关此页上可用选项的详细信息，请参阅[作业属性和新作业 &#40;常规页&#41;](../../integration-services/general-page-of-integration-services-designers-options.md)</span><span class="sxs-lookup"><span data-stu-id="6864b-134">For more information on the available options on this page, see [Job Properties and New Job &#40;General Page&#41;](../../integration-services/general-page-of-integration-services-designers-options.md)</span></span>  
  
5.  <span data-ttu-id="6864b-135">在 **“步骤”** 页上，组织作业步骤。</span><span class="sxs-lookup"><span data-stu-id="6864b-135">On the **Steps** page, organize the job steps.</span></span> <span data-ttu-id="6864b-136">有关此页上可用选项的详细信息，请参阅[作业属性：新建作业 &#40;步骤页&#41;](job-properties-new-job-steps-page.md)</span><span class="sxs-lookup"><span data-stu-id="6864b-136">For more information on the available options on this page, see [Job Properties:New Job &#40;Steps Page&#41;](job-properties-new-job-steps-page.md)</span></span>  
  
6.  <span data-ttu-id="6864b-137">在 **“计划”** 页上，组织作业的计划。</span><span class="sxs-lookup"><span data-stu-id="6864b-137">On the **Schedules** page, organize schedules for the job.</span></span> <span data-ttu-id="6864b-138">有关此页上可用选项的详细信息，请参阅[作业属性：新建作业 &#40;计划页&#41;](job-properties-new-job-schedules-page.md)</span><span class="sxs-lookup"><span data-stu-id="6864b-138">For more information on the available options on this page, see [Job Properties: New Job &#40;Schedules Page&#41;](job-properties-new-job-schedules-page.md)</span></span>  
  
7.  <span data-ttu-id="6864b-139">在 **“警报”** 页上，组织作业的警报。</span><span class="sxs-lookup"><span data-stu-id="6864b-139">On the **Alerts** page, organize the alerts for the job.</span></span> <span data-ttu-id="6864b-140">有关此页上可用选项的详细信息，请参阅[作业属性：新建作业 &#40;警报页&#41;](job-properties-new-job-alerts-page.md)</span><span class="sxs-lookup"><span data-stu-id="6864b-140">For more information on the available options on this page, see [Job Properties: New Job &#40;Alerts Page&#41;](job-properties-new-job-alerts-page.md)</span></span>  
  
8.  <span data-ttu-id="6864b-141">在“通知”\*\*\*\* 页上，设置在作业完成时 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理要执行的操作。</span><span class="sxs-lookup"><span data-stu-id="6864b-141">On the **Notifications** page, set actions for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to perform when the job completes.</span></span> <span data-ttu-id="6864b-142">有关此页上可用选项的详细信息，请参阅[作业属性：新建作业 &#40;通知页&#41;](job-properties-new-job-notifications-page.md)。</span><span class="sxs-lookup"><span data-stu-id="6864b-142">For more information on the available options on this page, see [Job Properties: New Job &#40;Notifications Page&#41;](job-properties-new-job-notifications-page.md).</span></span>  
  
9. <span data-ttu-id="6864b-143">在 **“目标”** 页上，管理作业的目标服务器。</span><span class="sxs-lookup"><span data-stu-id="6864b-143">On the **Targets** page, manage the target servers for the job.</span></span> <span data-ttu-id="6864b-144">有关此页上可用选项的详细信息，请参阅[作业属性：新建作业 &#40;目标&#41;](job-properties-new-job-targets-page.md)。</span><span class="sxs-lookup"><span data-stu-id="6864b-144">For more information on the available options on this page, see [Job Properties: New Job &#40;Targets Page&#41;](job-properties-new-job-targets-page.md).</span></span>  
  
10. <span data-ttu-id="6864b-145">完成后，单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="6864b-145">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="6864b-146">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="6864b-146">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-sql-server-agent-job"></a><span data-ttu-id="6864b-147">创建 SQL Server 代理作业</span><span class="sxs-lookup"><span data-stu-id="6864b-147">To create a SQL Server Agent job</span></span>  
  
1.  <span data-ttu-id="6864b-148">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="6864b-148">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="6864b-149">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="6864b-149">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="6864b-150">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="6864b-150">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    USE msdb ;  
    GO  
    EXEC dbo.sp_add_job  
        @job_name = N'Weekly Sales Data Backup' ;  
    GO  
    EXEC sp_add_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_name = N'Set database to read only',  
        @subsystem = N'TSQL',  
        @command = N'ALTER DATABASE SALES SET READ_ONLY',   
        @retry_attempts = 5,  
        @retry_interval = 5 ;  
    GO  
    EXEC dbo.sp_add_schedule  
        @schedule_name = N'RunOnce',  
        @freq_type = 1,  
        @active_start_time = 233000 ;  
    USE msdb ;  
    GO  
    EXEC sp_attach_schedule  
       @job_name = N'Weekly Sales Data Backup',  
       @schedule_name = N'RunOnce';  
    GO  
    EXEC dbo.sp_add_jobserver  
        @job_name = N'Weekly Sales Data Backup';  
    GO  
    ```  
  
 <span data-ttu-id="6864b-151">有关详细信息，请参阅：</span><span class="sxs-lookup"><span data-stu-id="6864b-151">For more information, see:</span></span>  
  
-   [<span data-ttu-id="6864b-152">sp_add_job (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="6864b-152">sp_add_job &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-job-transact-sql)  
  
-   [<span data-ttu-id="6864b-153">sp_add_jobstep (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="6864b-153">sp_add_jobstep &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql)  
  
-   [<span data-ttu-id="6864b-154">sp_add_schedule (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="6864b-154">sp_add_schedule &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-schedule-transact-sql)  
  
-   [<span data-ttu-id="6864b-155">sp_attach_schedule (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="6864b-155">sp_attach_schedule &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql)  
  
-   [<span data-ttu-id="6864b-156">sp_add_jobserver &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="6864b-156">sp_add_jobserver &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql)  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMOProcedure"></a><span data-ttu-id="6864b-157">使用 SQL Server 管理对象</span><span class="sxs-lookup"><span data-stu-id="6864b-157">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="6864b-158">**创建 SQL Server 代理作业**</span><span class="sxs-lookup"><span data-stu-id="6864b-158">**To create a SQL Server Agent job**</span></span>  
  
 <span data-ttu-id="6864b-159">通过使用所选编程语言（如 Visual Basic、Visual C# 或 PowerShell）来调用 `Create` 类的 `Job` 方法。</span><span class="sxs-lookup"><span data-stu-id="6864b-159">Call the `Create` method of the `Job` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span> <span data-ttu-id="6864b-160">有关示例代码，请参阅 [在 SQL Server 代理中计划自动管理任务](sql-server-agent.md)。</span><span class="sxs-lookup"><span data-stu-id="6864b-160">For example code, see [Scheduling Automatic Administrative Tasks in SQL Server Agent](sql-server-agent.md).</span></span>  
  
##  <a name="SSMSProc2"></a>  
