---
title: 创建 PowerShell 脚本作业步骤 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- PowerShell [SQL Server], job steps
- jobs [SQL Server Agent], PowerShell
- job steps [PowerShell]
- SQL Server Agent jobs, PowerShell steps
ms.assetid: 50afcf84-fae0-4eb5-9b0f-f2cf144c1433
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4232cdfa584fdcc2e13786ecc9bd00f0c6fe7066
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586058"
---
# <a name="create-a-powershell-script-job-step"></a><span data-ttu-id="1c725-102">Create a PowerShell Script Job Step</span><span class="sxs-lookup"><span data-stu-id="1c725-102">Create a PowerShell Script Job Step</span></span>
  <span data-ttu-id="1c725-103">本主题介绍如何通过使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 或 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中创建和定义执行 PowerShell 脚本的 [!INCLUDE[tsql](../../includes/tsql-md.md)]代理作业步骤。</span><span class="sxs-lookup"><span data-stu-id="1c725-103">This topic describes how to create and define a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job step that executes a PowerShell script in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="1c725-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="1c725-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="1c725-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="1c725-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="1c725-106">安全性</span><span class="sxs-lookup"><span data-stu-id="1c725-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="1c725-107">**若要创建 PowerShell 脚本作业步骤，请使用：**</span><span class="sxs-lookup"><span data-stu-id="1c725-107">**To create a PowerShell Script job step, using:**</span></span>  
  
     [<span data-ttu-id="1c725-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="1c725-108">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="1c725-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1c725-109">Transact-SQL</span></span>](#TSQL)  
  
     [<span data-ttu-id="1c725-110">SQL Server 管理对象</span><span class="sxs-lookup"><span data-stu-id="1c725-110">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="1c725-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="1c725-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="1c725-112">Security</span><span class="sxs-lookup"><span data-stu-id="1c725-112">Security</span></span>  
 <span data-ttu-id="1c725-113">有关详细信息，请参阅[实现 SQL Server 代理安全性](implement-sql-server-agent-security.md)。</span><span class="sxs-lookup"><span data-stu-id="1c725-113">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="1c725-114">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="1c725-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-powershell-script-job-step"></a><span data-ttu-id="1c725-115">创建 PowerShell 脚本作业步骤</span><span class="sxs-lookup"><span data-stu-id="1c725-115">To create a PowerShell Script job step</span></span>  
  
1.  <span data-ttu-id="1c725-116">在**对象资源管理器中，** 连接到的实例 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="1c725-116">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="1c725-117">展开“SQL Server 代理”\*\*\*\*，创建一个新作业或右键单击一个现有作业，再单击“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1c725-117">Expand **SQL Server Agent**, create a new job or right-click an existing job, and then click **Properties**.</span></span> <span data-ttu-id="1c725-118">有关创建作业的详细信息，请参阅 [创建作业](create-jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="1c725-118">For more information on creating a job, see [Creating Jobs](create-jobs.md).</span></span>  
  
3.  <span data-ttu-id="1c725-119">在 **“作业属性”** 对话框中，单击 **“步骤”** 页，再单击 **“新建”**。</span><span class="sxs-lookup"><span data-stu-id="1c725-119">In the **Job Properties** dialog, click the **Steps** page, and then click **New**.</span></span>  
  
4.  <span data-ttu-id="1c725-120">在 **“新建作业步骤”** 对话框中，键入作业的 **“步骤名称”**。</span><span class="sxs-lookup"><span data-stu-id="1c725-120">In the **New Job Step** dialog, type a job **Step name**.</span></span>  
  
5.  <span data-ttu-id="1c725-121">在 **“类型”** 列表中单击 **PowerShell**。</span><span class="sxs-lookup"><span data-stu-id="1c725-121">In the **Type** list, click **PowerShell**.</span></span>  
  
6.  <span data-ttu-id="1c725-122">在 **“运行身份”** 列表中，选择该作业将要使用的代理帐户和凭据。</span><span class="sxs-lookup"><span data-stu-id="1c725-122">In the **Run as** list, select the proxy account with the credentials that the job will use.</span></span>  
  
7.  <span data-ttu-id="1c725-123">在 **“命令”** 框中，输入将为该作业步骤执行的 PowerShell 脚本语法。</span><span class="sxs-lookup"><span data-stu-id="1c725-123">In the **Command** box, enter the PowerShell script syntax that will be executed for the job step.</span></span> <span data-ttu-id="1c725-124">或者，单击 **“打开”** ，选择包含脚本语法的文件。</span><span class="sxs-lookup"><span data-stu-id="1c725-124">Alternately, click **Open** and select a file containing the script syntax.</span></span> <span data-ttu-id="1c725-125">有关 PowerShell 脚本的示例，请参阅下面的 **使用 Transact-SQL** 。</span><span class="sxs-lookup"><span data-stu-id="1c725-125">For an example of a PowerShell script, see **Using Transact-SQL** below.</span></span>  
  
8.  <span data-ttu-id="1c725-126">单击 **“高级”** 页设置以下作业步骤选项：当该作业步骤成功或失败时将执行的操作、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理应该尝试执行该作业步骤的次数以及重试的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="1c725-126">Click the **Advanced** page to set the following job step options: what action to take if the job step succeeds or fails, how many times [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent should try to execute the job step, and how often retry attempts should be made.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="1c725-127">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1c725-127">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-powershell-script-job-step"></a><span data-ttu-id="1c725-128">创建 PowerShell 脚本作业步骤</span><span class="sxs-lookup"><span data-stu-id="1c725-128">To create a PowerShell Script job step</span></span>  
  
1.  <span data-ttu-id="1c725-129">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="1c725-129">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="1c725-130">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="1c725-130">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="1c725-131">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="1c725-131">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- creates a PowerShell job step that finds the processes that use more than 1000 MB of memory and kills them  
    USE msdb;  
    GO  
    EXEC sp_add_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_name = N'Kills all processes that use more than 1000 MB of memory',  
        @subsystem = N'PowerShell',  
        @command = N'Get-Process | Where-Object { $_.WS -gt 1000MB } | Stop-Process',   
        @retry_attempts = 5,  
        @retry_interval = 5 ;  
    GO  
    ```  
  
 <span data-ttu-id="1c725-132">有关详细信息，请参阅[&#40;transact-sql&#41;sp_add_jobstep ](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="1c725-132">For more information, see [sp_add_jobstep &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="1c725-133">使用 SQL Server 管理对象</span><span class="sxs-lookup"><span data-stu-id="1c725-133">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="1c725-134">**创建 PowerShell 脚本作业步骤**</span><span class="sxs-lookup"><span data-stu-id="1c725-134">**To create a PowerShell Script job step**</span></span>  
  
 <span data-ttu-id="1c725-135">通过使用所选的编程语言（如 Visual Basic、Visual C# 或 PowerShell）来使用 `JobStep` 类。</span><span class="sxs-lookup"><span data-stu-id="1c725-135">Use the `JobStep` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span>  
