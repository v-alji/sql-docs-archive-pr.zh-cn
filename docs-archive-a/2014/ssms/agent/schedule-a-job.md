---
title: 安排作业计划 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- scheduling jobs [SQL Server]
- SQL Server Agent jobs, scheduling
- jobs [SQL Server Agent], scheduling
ms.assetid: f626390a-a3df-4970-b7a7-a0529e4a109c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1077766d6853ed7c029b8eefa76515c89ad861fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689236"
---
# <a name="schedule-a-job"></a><span data-ttu-id="9739c-102">Schedule a Job</span><span class="sxs-lookup"><span data-stu-id="9739c-102">Schedule a Job</span></span>
  <span data-ttu-id="9739c-103">本主题介绍如何安排 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业计划。</span><span class="sxs-lookup"><span data-stu-id="9739c-103">This topic describes how to schedule a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job.</span></span>  
  
-   <span data-ttu-id="9739c-104">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="9739c-104">**Before you begin:** ,</span></span>  
  
     [<span data-ttu-id="9739c-105">安全性</span><span class="sxs-lookup"><span data-stu-id="9739c-105">Security</span></span>](#Security)  
  
-   <span data-ttu-id="9739c-106">**若要安排作业计划，可使用：**</span><span class="sxs-lookup"><span data-stu-id="9739c-106">**To schedule a job, using:**</span></span>  
  
     [<span data-ttu-id="9739c-107">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="9739c-107">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="9739c-108">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="9739c-108">Transact-SQL</span></span>](#TSQL)  
  
     [<span data-ttu-id="9739c-109">SQL Server 管理对象</span><span class="sxs-lookup"><span data-stu-id="9739c-109">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="9739c-110">开始之前</span><span class="sxs-lookup"><span data-stu-id="9739c-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="9739c-111">Security</span><span class="sxs-lookup"><span data-stu-id="9739c-111">Security</span></span>  
 <span data-ttu-id="9739c-112">有关详细信息，请参阅[实现 SQL Server 代理安全性](implement-sql-server-agent-security.md)。</span><span class="sxs-lookup"><span data-stu-id="9739c-112">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="9739c-113">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="9739c-113">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-and-attach-a-schedule-to-a-job"></a><span data-ttu-id="9739c-114">创建计划并将其附加到作业中</span><span class="sxs-lookup"><span data-stu-id="9739c-114">To create and attach a schedule to a job</span></span>  
  
1.  <span data-ttu-id="9739c-115">在**对象资源管理器中，** 连接到的实例 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="9739c-115">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="9739c-116">展开“SQL Server 代理”\*\*\*\*，展开“作业”\*\*\*\*，右键单击要计划的作业，并单击“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9739c-116">Expand **SQL Server Agent**, expand **Jobs**, right-click the job you want to schedule, and click **Properties**.</span></span>  
  
3.  <span data-ttu-id="9739c-117">选择 **“计划”** 页，再单击 **“新建”**。</span><span class="sxs-lookup"><span data-stu-id="9739c-117">Select the **Schedules** page, and then click **New**.</span></span>  
  
4.  <span data-ttu-id="9739c-118">在 **“名称”** 框中，键入新计划的名称。</span><span class="sxs-lookup"><span data-stu-id="9739c-118">In the **Name** box, type a name for the new schedule.</span></span>  
  
5.  <span data-ttu-id="9739c-119">如果不希望计划在创建后立即生效，则清除 **“启用”** 复选框。</span><span class="sxs-lookup"><span data-stu-id="9739c-119">Clear the **Enabled** check box if you do not want the schedule to take effect immediately following its creation.</span></span>  
  
6.  <span data-ttu-id="9739c-120">对于 **“计划类型”**，请选择下列操作之一：</span><span class="sxs-lookup"><span data-stu-id="9739c-120">For **Schedule Type**, select one of the following:</span></span>  
  
    -   <span data-ttu-id="9739c-121">单击 **“SQL Server 代理启动时自动启动”** ，在启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服务时启动作业。</span><span class="sxs-lookup"><span data-stu-id="9739c-121">Click **Start automatically when SQL Server Agent starts** to start the job when the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service is started.</span></span>  
  
    -   <span data-ttu-id="9739c-122">单击 **“CPU 空闲时启动”** ，在 CPU 达到空闲条件时启动作业。</span><span class="sxs-lookup"><span data-stu-id="9739c-122">Click **Start whenever the CPUs become idle** to start the job when the CPUs reach an idle condition.</span></span>  
  
    -   <span data-ttu-id="9739c-123">如果希望反复运行计划，则单击 **“重复执行”** 。</span><span class="sxs-lookup"><span data-stu-id="9739c-123">Click **Recurring** if you want a schedule to run repeatedly.</span></span> <span data-ttu-id="9739c-124">若要设置重复执行的计划，请完成对话框上的 **“频率”**、 **“每天频率”** 和 **“持续时间”** 组。</span><span class="sxs-lookup"><span data-stu-id="9739c-124">To set the recurring schedule, complete the **Frequency**, **Daily Frequency**, and **Duration** groups on the dialog.</span></span>  
  
    -   <span data-ttu-id="9739c-125">如果希望仅运行一次计划，请单击 **“执行一次”** 。</span><span class="sxs-lookup"><span data-stu-id="9739c-125">Click **One time** if you want the schedule to run only once.</span></span> <span data-ttu-id="9739c-126">若要设置“执行一次”\*\*\*\* 计划，请完成对话框上的“执行一次”\*\*\*\* 组。</span><span class="sxs-lookup"><span data-stu-id="9739c-126">To set the **One time** schedule, complete the **One-time occurrence** group on the dialog.</span></span>  
  
#### <a name="to-attach-a-schedule-to-a-job"></a><span data-ttu-id="9739c-127">将计划附加到作业中</span><span class="sxs-lookup"><span data-stu-id="9739c-127">To attach a schedule to a job</span></span>  
  
1.  <span data-ttu-id="9739c-128">在**对象资源管理器中，** 连接到的实例 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="9739c-128">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="9739c-129">展开“SQL Server 代理”\*\*\*\*，展开“作业”\*\*\*\*，右键单击要计划的作业，然后单击“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9739c-129">Expand **SQL Server Agent**, expand **Jobs**, right-click the job that you want to schedule, and click **Properties**.</span></span>  
  
3.  <span data-ttu-id="9739c-130">选择 **“计划”** 页，再单击 **“选取”**。</span><span class="sxs-lookup"><span data-stu-id="9739c-130">Select the **Schedules** page, and then click **Pick**.</span></span>  
  
4.  <span data-ttu-id="9739c-131">选择要附加的计划，然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="9739c-131">Select the schedule that you want to attach, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="9739c-132">在“作业属性”\*\*\*\* 对话框中，双击附加的计划。</span><span class="sxs-lookup"><span data-stu-id="9739c-132">In the **Job Properties** dialog box, double-click the attached schedule.</span></span>  
  
6.  <span data-ttu-id="9739c-133">验证是否正确设置了 **“开始日期”** 。</span><span class="sxs-lookup"><span data-stu-id="9739c-133">Verify that **Start date** is set correctly.</span></span> <span data-ttu-id="9739c-134">如果该选项的设置不正确，则将日期设置为要让计划启动的日期，然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="9739c-134">If it is not, set the date when you want for the schedule to start, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="9739c-135">在 **“作业属性”** 对话框中，单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="9739c-135">In the **Job Properties** dialog box, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="9739c-136">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="9739c-136">Using Transact-SQL</span></span>  
  
#### <a name="to-schedule-a-job"></a><span data-ttu-id="9739c-137">安排作业计划</span><span class="sxs-lookup"><span data-stu-id="9739c-137">To schedule a job</span></span>  
  
1.  <span data-ttu-id="9739c-138">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="9739c-138">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="9739c-139">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="9739c-139">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="9739c-140">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="9739c-140">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    USE msdb ;  
    GO  
    -- creates a schedule named NightlyJobs.   
    -- Jobs that use this schedule execute every day when the time on the server is 01:00.   
    EXEC sp_add_schedule  
        @schedule_name = N'NightlyJobs' ,  
        @freq_type = 4,  
        @freq_interval = 1,  
        @active_start_time = 010000 ;  
    GO  
    -- attaches the schedule to the job BackupDatabase  
    EXEC sp_attach_schedule  
       @job_name = N'BackupDatabase',  
       @schedule_name = N'NightlyJobs' ;  
    GO  
    ```  
  
 <span data-ttu-id="9739c-141">有关详细信息，请参阅[sp_add_schedule &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-schedule-transact-sql)和[sp_attach_schedule &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="9739c-141">For more information, see [sp_add_schedule &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-schedule-transact-sql) and [sp_attach_schedule &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="9739c-142">使用 SQL Server 管理对象</span><span class="sxs-lookup"><span data-stu-id="9739c-142">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="9739c-143">通过使用所选的编程语言（如 Visual Basic、Visual C# 或 PowerShell）来使用 `JobSchedule` 类。</span><span class="sxs-lookup"><span data-stu-id="9739c-143">Use the `JobSchedule` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span> <span data-ttu-id="9739c-144">有关详细信息，请参阅[SQL Server 管理对象 (SMO)](https://msdn.microsoft.com/library/ms162169.aspx)。</span><span class="sxs-lookup"><span data-stu-id="9739c-144">For more information, see[SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).</span></span>  
