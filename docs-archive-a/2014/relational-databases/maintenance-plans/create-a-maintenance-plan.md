---
title: 创建维护计划 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- maintenance plans [SQL Server], creating
ms.assetid: a945cb65-ba7a-42f4-bbd9-6ec675745523
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3df0c1cd06427deb051a9c4214d03084b44c6f9b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589059"
---
# <a name="create-a-maintenance-plan"></a><span data-ttu-id="61dbb-102">创建维护计划</span><span class="sxs-lookup"><span data-stu-id="61dbb-102">Create a Maintenance Plan</span></span>
  <span data-ttu-id="61dbb-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中创建单服务器或多服务器维护计划。</span><span class="sxs-lookup"><span data-stu-id="61dbb-103">This topic describes how to create a single server or multiserver maintenance plan in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="61dbb-104">通过使用 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]，您可以通过以下两种方式之一创建这些维护计划：使用维护计划向导或设计图面。</span><span class="sxs-lookup"><span data-stu-id="61dbb-104">Using [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], you can create these maintenance plans in one of two ways: by either using the Maintenance Plan Wizard or the design surface.</span></span> <span data-ttu-id="61dbb-105">向导是创建基本维护计划的最佳方法，而使用设计图面创建计划允许您使用增强的工作流。</span><span class="sxs-lookup"><span data-stu-id="61dbb-105">The Wizard is best for creating basic maintenance plans, while creating a plan using the design surface allows you to utilize enhanced workflow.</span></span>  
  
 <span data-ttu-id="61dbb-106">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="61dbb-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="61dbb-107">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="61dbb-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="61dbb-108">限制和局限</span><span class="sxs-lookup"><span data-stu-id="61dbb-108">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="61dbb-109">安全性</span><span class="sxs-lookup"><span data-stu-id="61dbb-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="61dbb-110">**若要创建维护计划，请使用：**</span><span class="sxs-lookup"><span data-stu-id="61dbb-110">**To create a maintenance plan, using:**</span></span>  
  
     [<span data-ttu-id="61dbb-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="61dbb-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="61dbb-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="61dbb-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="61dbb-113">开始之前</span><span class="sxs-lookup"><span data-stu-id="61dbb-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="61dbb-114">限制和局限</span><span class="sxs-lookup"><span data-stu-id="61dbb-114">Limitations and Restrictions</span></span>  
 <span data-ttu-id="61dbb-115">若要创建多服务器维护计划，必须配置包含一个主服务器和一个（或多个）目标服务器的多服务器环境。</span><span class="sxs-lookup"><span data-stu-id="61dbb-115">To create a multiserver maintenance plan, a multiserver environment containing one master server and one or more target servers must be configured.</span></span> <span data-ttu-id="61dbb-116">必须在主服务器上创建和维护多服务器维护计划。</span><span class="sxs-lookup"><span data-stu-id="61dbb-116">Multiserver maintenance plans must be created and maintained on the master server.</span></span> <span data-ttu-id="61dbb-117">在目标服务器上可以查看这些计划，但不能进行维护。</span><span class="sxs-lookup"><span data-stu-id="61dbb-117">These plans can be viewed, but not maintained, on target servers.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="61dbb-118">Security</span><span class="sxs-lookup"><span data-stu-id="61dbb-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="61dbb-119">权限</span><span class="sxs-lookup"><span data-stu-id="61dbb-119">Permissions</span></span>  
 <span data-ttu-id="61dbb-120">若要创建或管理维护计划，您必须是 **sysadmin** 固定服务器角色的成员。</span><span class="sxs-lookup"><span data-stu-id="61dbb-120">To create or manage Maintenance Plans, you must be a member of the **sysadmin** fixed server role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="61dbb-121">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="61dbb-121">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-maintenance-plan-using-the-maintenance-plan-wizard"></a><span data-ttu-id="61dbb-122">使用维护计划向导创建维护计划</span><span class="sxs-lookup"><span data-stu-id="61dbb-122">To create a maintenance plan using the Maintenance Plan Wizard</span></span>  
  
1.  <span data-ttu-id="61dbb-123">在对象资源管理器中，单击加号以便展开您要创建维护计划的服务器。</span><span class="sxs-lookup"><span data-stu-id="61dbb-123">In Object Explorer, click the plus sign to expand the server where you want to create a maintenance plan.</span></span>  
  
2.  <span data-ttu-id="61dbb-124">单击加号以便展开 **“管理”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="61dbb-124">Click the plus sign to expand the **Management** folder.</span></span>  
  
3.  <span data-ttu-id="61dbb-125">右键单击“维护计划”文件夹，然后选择“维护计划向导”。</span><span class="sxs-lookup"><span data-stu-id="61dbb-125">Right-click the **Maintenance Plans** folder and select **Maintenance Plan Wizard**.</span></span>  
  
4.  <span data-ttu-id="61dbb-126">按照向导中显示的步骤创建维护计划。</span><span class="sxs-lookup"><span data-stu-id="61dbb-126">Follow the steps of the wizard to create a maintenance plan.</span></span> <span data-ttu-id="61dbb-127">有关详细信息，请参阅 [Use the Maintenance Plan Wizard](use-the-maintenance-plan-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="61dbb-127">For more information, see [Use the Maintenance Plan Wizard](use-the-maintenance-plan-wizard.md).</span></span>  
  
#### <a name="to-create-a-maintenance-plan-using-the-design-surface"></a><span data-ttu-id="61dbb-128">使用设计图面创建维护计划</span><span class="sxs-lookup"><span data-stu-id="61dbb-128">To create a maintenance plan using the design surface</span></span>  
  
1.  <span data-ttu-id="61dbb-129">在对象资源管理器中，单击加号以便展开您要创建维护计划的服务器。</span><span class="sxs-lookup"><span data-stu-id="61dbb-129">In Object Explorer, click the plus sign to expand the server where you want to create a maintenance plan.</span></span>  
  
2.  <span data-ttu-id="61dbb-130">单击加号以便展开 **“管理”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="61dbb-130">Click the plus sign to expand the **Management** folder.</span></span>  
  
3.  <span data-ttu-id="61dbb-131">右键单击“维护计划”  文件夹，然后选择“新建维护计划” 。</span><span class="sxs-lookup"><span data-stu-id="61dbb-131">Right-click the **Maintenance Plans** folder and select **New Maintenance Plan**.</span></span>  
  
4.  <span data-ttu-id="61dbb-132">按照[创建维护计划（维护计划设计图面）](create-a-maintenance-plan-maintenance-plan-design-surface.md)中的步骤创建维护计划。</span><span class="sxs-lookup"><span data-stu-id="61dbb-132">Create a maintenance plan following the steps in [Create a Maintenance Plan &#40;Maintenance Plan Design Surface&#41;](create-a-maintenance-plan-maintenance-plan-design-surface.md).</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="61dbb-133">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="61dbb-133">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-maintenance-plan"></a><span data-ttu-id="61dbb-134">创建维护计划</span><span class="sxs-lookup"><span data-stu-id="61dbb-134">To create a maintenance plan</span></span>  
  
1.  <span data-ttu-id="61dbb-135">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="61dbb-135">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="61dbb-136">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="61dbb-136">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="61dbb-137">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="61dbb-137">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE msdb;  
    GO  
    --  Adds a new job, executed by the SQL Server Agent service, called "HistoryCleanupTask_1".  
    EXEC dbo.sp_add_job  
       @job_name = N'HistoryCleanupTask_1',   
       @enabled = 1,   
       @description = N'Clean up old task history' ;   
    GO  
    -- Adds a job step for reorganizing all of the indexes in the HumanResources.Employee table to the HistoryCleanupTask_1 job.   
    EXEC dbo.sp_add_jobstep  
        @job_name = N'HistoryCleanupTask_1',   
        @step_name = N'Reorganize all indexes on HumanResources.Employee table',   
        @subsystem = N'TSQL',   
        @command = N'USE AdventureWorks2012  
    GO  
    ALTER INDEX AK_Employee_LoginID ON HumanResources.Employee REORGANIZE WITH ( LOB_COMPACTION = ON )   
    GO  
    USE AdventureWorks2012  
    GO  
    ALTER INDEX AK_Employee_NationalIDNumber ON HumanResources.Employee REORGANIZE WITH ( LOB_COMPACTION = ON )   
    GO  
    USE AdventureWorks2012  
    GO  
    ALTER INDEX AK_Employee_rowguid ON HumanResources.Employee REORGANIZE WITH ( LOB_COMPACTION = ON )   
    GO  
    USE AdventureWorks2012  
    GO  
    ALTER INDEX IX_Employee_OrganizationLevel_OrganizationNode ON HumanResources.Employee REORGANIZE WITH ( LOB_COMPACTION = ON )   
    GO  
    USE AdventureWorks2012  
    GO  
    ALTER INDEX IX_Employee_OrganizationNode ON HumanResources.Employee REORGANIZE WITH ( LOB_COMPACTION = ON )   
    GO  
    USE AdventureWorks2012  
    GO  
    ALTER INDEX PK_Employee_BusinessEntityID ON HumanResources.Employee REORGANIZE WITH ( LOB_COMPACTION = ON )   
    GO  
    ',   
        @retry_attempts = 5,   
        @retry_interval = 5 ;   
    GO  
    -- Creates a schedule named RunOnce that executes every day when the time on the server is 23:00.   
    EXEC dbo.sp_add_schedule  
        @schedule_name = N'RunOnce',   
        @freq_type = 4,   
        @freq_interval = 1,   
        @active_start_time = 233000 ;   
    GO  
    -- Attaches the RunOnce schedule to the job HistoryCleanupTask_1.   
    EXEC sp_attach_schedule  
       @job_name = N'HistoryCleanupTask_1'  
       @schedule_name = N'RunOnce' ;   
    GO  
  
    ```  
  
 <span data-ttu-id="61dbb-138">有关详细信息，请参阅：</span><span class="sxs-lookup"><span data-stu-id="61dbb-138">For more information, see:</span></span>  
  
-   [<span data-ttu-id="61dbb-139">sp_add_job (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="61dbb-139">sp_add_job &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-job-transact-sql)  
  
-   [<span data-ttu-id="61dbb-140">sp_add_jobstep (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="61dbb-140">sp_add_jobstep &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql)  
  
-   [<span data-ttu-id="61dbb-141">sp_add_schedule (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="61dbb-141">sp_add_schedule &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-schedule-transact-sql)  
  
-   [<span data-ttu-id="61dbb-142">sp_attach_schedule (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="61dbb-142">sp_attach_schedule &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql)  
  
  
