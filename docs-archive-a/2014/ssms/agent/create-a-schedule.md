---
title: 创建计划 | Microsoft Docs
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
- schedules [SQL Server], jobs
ms.assetid: 8c7ef3b3-c06d-4a27-802d-ed329dc86ef3
author: stevestein
ms.author: sstein
ms.openlocfilehash: ac71a61163dceb06697b61ef24fce2117d57cf2f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590020"
---
# <a name="create-a-schedule"></a><span data-ttu-id="0176a-102">Create a Schedule</span><span class="sxs-lookup"><span data-stu-id="0176a-102">Create a Schedule</span></span>
  <span data-ttu-id="0176a-103">可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 SQL Server 管理对象在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中创建 [!INCLUDE[tsql](../../includes/tsql-md.md)]代理作业的计划。</span><span class="sxs-lookup"><span data-stu-id="0176a-103">You can create a schedule for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or SQL Server Management Objects.</span></span>  
  
-   <span data-ttu-id="0176a-104">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="0176a-104">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="0176a-105">安全性</span><span class="sxs-lookup"><span data-stu-id="0176a-105">Security</span></span>](#Security)  
  
-   <span data-ttu-id="0176a-106">**若要创建计划，可使用：**</span><span class="sxs-lookup"><span data-stu-id="0176a-106">**To create a schedule, using:**</span></span>  
  
     [<span data-ttu-id="0176a-107">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="0176a-107">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="0176a-108">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="0176a-108">Transact-SQL</span></span>](#TSQL)  
  
     [<span data-ttu-id="0176a-109">SQL Server 管理对象</span><span class="sxs-lookup"><span data-stu-id="0176a-109">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="0176a-110">开始之前</span><span class="sxs-lookup"><span data-stu-id="0176a-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="0176a-111">Security</span><span class="sxs-lookup"><span data-stu-id="0176a-111">Security</span></span>  
 <span data-ttu-id="0176a-112">有关详细信息，请参阅[实现 SQL Server 代理安全性](implement-sql-server-agent-security.md)。</span><span class="sxs-lookup"><span data-stu-id="0176a-112">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="0176a-113">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="0176a-113">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-schedule"></a><span data-ttu-id="0176a-114">创建计划</span><span class="sxs-lookup"><span data-stu-id="0176a-114">To create a schedule</span></span>  
  
1.  <span data-ttu-id="0176a-115">在**对象资源管理器中，** 连接到的实例 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="0176a-115">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="0176a-116">展开 **“SQL Server 代理”**，右键单击 **“作业”**，然后单击 **“管理计划”**。</span><span class="sxs-lookup"><span data-stu-id="0176a-116">Expand **SQL Server Agent**, right-click **Jobs**, and select **Manage Schedules**.</span></span>  
  
3.  <span data-ttu-id="0176a-117">在 **“管理计划”** 对话框中，单击 **“新建”**。</span><span class="sxs-lookup"><span data-stu-id="0176a-117">In the **Manage Schedules** dialog box, click **New**.</span></span>  
  
4.  <span data-ttu-id="0176a-118">在 **“名称”** 框中，键入新计划的名称。</span><span class="sxs-lookup"><span data-stu-id="0176a-118">In the **Name** box, type a name for the new schedule.</span></span>  
  
5.  <span data-ttu-id="0176a-119">如果不希望计划在创建后立即生效，请清除 **“启用”** 复选框。</span><span class="sxs-lookup"><span data-stu-id="0176a-119">If you do not want the schedule to take effect immediately after it has been created, clear the **Enabled** check box.</span></span>  
  
6.  <span data-ttu-id="0176a-120">对于 **“计划类型”**，请选择下列操作之一：</span><span class="sxs-lookup"><span data-stu-id="0176a-120">For **Schedule Type**, select one of the following:</span></span>  
  
    -   <span data-ttu-id="0176a-121">若要在 CPU 达到空闲条件时启动作业，请单击 **“CPU 空闲时启动”**。</span><span class="sxs-lookup"><span data-stu-id="0176a-121">To start the job when the CPUs reach an idle condition, click **Start whenever the CPUs become idle**.</span></span>  
  
    -   <span data-ttu-id="0176a-122">如果希望反复运行计划，请单击 **“重复执行”**。</span><span class="sxs-lookup"><span data-stu-id="0176a-122">If you want a schedule to run repeatedly, click **Recurring**.</span></span> <span data-ttu-id="0176a-123">若要设置重复执行的计划，请完成对话框上的 **“频率”**、 **“每天频率”** 和 **“持续时间”** 组。</span><span class="sxs-lookup"><span data-stu-id="0176a-123">To set the recurring schedule, complete the **Frequency**, **Daily Frequency**, and **Duration** groups on the dialog.</span></span>  
  
    -   <span data-ttu-id="0176a-124">如果希望仅运行一次计划，请单击 **“执行一次”**。</span><span class="sxs-lookup"><span data-stu-id="0176a-124">If you want the schedule to run only one time, click **One time**.</span></span> <span data-ttu-id="0176a-125">若要设置 **“执行一次”** 计划，请完成对话框上的 **“执行一次”** 组。</span><span class="sxs-lookup"><span data-stu-id="0176a-125">To set the **One time** schedule, complete the **One-time occurrence** group on the dialog box.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="0176a-126">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="0176a-126">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-schedule"></a><span data-ttu-id="0176a-127">创建计划</span><span class="sxs-lookup"><span data-stu-id="0176a-127">To create a schedule</span></span>  
  
1.  <span data-ttu-id="0176a-128">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="0176a-128">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="0176a-129">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="0176a-129">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="0176a-130">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="0176a-130">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- creates a schedule named RunOnce.   
    -- The schedule runs one time, at 23:30 on the day that the schedule is created.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_add_schedule  
        @schedule_name = N'RunOnce',  
        @freq_type = 1,  
        @active_start_time = 233000 ;  
  
    GO  
    ```  
  
 <span data-ttu-id="0176a-131">有关详细信息，请参阅[&#40;transact-sql&#41;sp_add_schedule ](/sql/relational-databases/system-stored-procedures/sp-add-schedule-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="0176a-131">For more information, see [sp_add_schedule &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-schedule-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="0176a-132">使用 SQL Server 管理对象</span><span class="sxs-lookup"><span data-stu-id="0176a-132">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="0176a-133">**创建计划**</span><span class="sxs-lookup"><span data-stu-id="0176a-133">**To create a schedule**</span></span>  
  
 <span data-ttu-id="0176a-134">通过使用所选的编程语言（如 Visual Basic、Visual C# 或 PowerShell）来使用 `JobSchedule` 类。</span><span class="sxs-lookup"><span data-stu-id="0176a-134">Use the `JobSchedule` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span> <span data-ttu-id="0176a-135">有关详细信息，请参阅 [SQL Server 管理对象 (SMO)](https://msdn.microsoft.com/library/ms162169.aspx)。</span><span class="sxs-lookup"><span data-stu-id="0176a-135">For more information, see [SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).</span></span>  
