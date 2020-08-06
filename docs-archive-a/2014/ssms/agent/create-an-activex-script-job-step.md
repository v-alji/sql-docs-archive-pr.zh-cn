---
title: 创建 ActiveX 脚本作业步骤 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- ActiveX scripting jobs [SQL Server]
- job steps [Analysis Services]
ms.assetid: e6c46c6b-2d61-4571-bc8e-a831cd6e6302
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6604ba75af7acdd5bd2521433e8310c74150ce8f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682661"
---
# <a name="create-an-activex-script-job-step"></a><span data-ttu-id="0276b-102">Create an ActiveX Script Job Step</span><span class="sxs-lookup"><span data-stu-id="0276b-102">Create an ActiveX Script Job Step</span></span>
  <span data-ttu-id="0276b-103">本主题介绍如何在中创建和定义 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业步骤， [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 该步骤使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 、或 SQL Server 管理对象执行 ActiveX 脚本 [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="0276b-103">This topic describes how to create and define a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job step in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] that executes an ActiveX script by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or SQL Server Management Objects.</span></span>  
  
-   <span data-ttu-id="0276b-104">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="0276b-104">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="0276b-105">限制和局限</span><span class="sxs-lookup"><span data-stu-id="0276b-105">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="0276b-106">安全性</span><span class="sxs-lookup"><span data-stu-id="0276b-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="0276b-107">**若要创建 Transact-SQL 作业步骤，可使用：**</span><span class="sxs-lookup"><span data-stu-id="0276b-107">**To create a Transact-SQL job step, using:**</span></span>  
  
     [<span data-ttu-id="0276b-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="0276b-108">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="0276b-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="0276b-109">Transact-SQL</span></span>](#TSQL)  
  
     [<span data-ttu-id="0276b-110">SQL Server 管理对象</span><span class="sxs-lookup"><span data-stu-id="0276b-110">SQL Server Management Objects</span></span>](#SMO)  
  
## <a name="before-you-begin"></a><span data-ttu-id="0276b-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="0276b-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="0276b-112">限制和局限</span><span class="sxs-lookup"><span data-stu-id="0276b-112">Limitations and Restrictions</span></span>  
 [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="0276b-113">Security</span><span class="sxs-lookup"><span data-stu-id="0276b-113">Security</span></span>  
 <span data-ttu-id="0276b-114">有关详细信息，请参阅[实现 SQL Server 代理安全性](implement-sql-server-agent-security.md)。</span><span class="sxs-lookup"><span data-stu-id="0276b-114">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="0276b-115">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="0276b-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-an-activex-script-job-step"></a><span data-ttu-id="0276b-116">创建 ActiveX 脚本作业步骤</span><span class="sxs-lookup"><span data-stu-id="0276b-116">To create an ActiveX Script job step</span></span>  
  
1.  <span data-ttu-id="0276b-117">在**对象资源管理器中，** 连接到的实例 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="0276b-117">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="0276b-118">展开“SQL Server 代理”\*\*\*\*，创建一个新作业或右键单击一个现有作业，再单击“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0276b-118">Expand **SQL Server Agent**, create a new job or right-click an existing job, and then click **Properties**.</span></span> <span data-ttu-id="0276b-119">有关创建作业的详细信息，请参阅 [创建作业](create-jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="0276b-119">For more information on creating a job, see [Creating Jobs](create-jobs.md).</span></span>  
  
3.  <span data-ttu-id="0276b-120">在 **“作业属性”** 对话框中，单击 **“步骤”** 页，再单击 **“新建”**。</span><span class="sxs-lookup"><span data-stu-id="0276b-120">In the **Job Properties** dialog, click the **Steps** page, and then click **New**.</span></span>  
  
4.  <span data-ttu-id="0276b-121">在 **“新建作业步骤”** 对话框中，键入作业的 **“步骤名称”**。</span><span class="sxs-lookup"><span data-stu-id="0276b-121">In the **New Job Step** dialog, type a job **Step name**.</span></span>  
  
5.  <span data-ttu-id="0276b-122">在 **“类型”** 列表中，单击 **“ActiveX 脚本”**。</span><span class="sxs-lookup"><span data-stu-id="0276b-122">In the **Type** list, click **ActiveX Script**.</span></span>  
  
6.  <span data-ttu-id="0276b-123">在 **“运行身份”** 列表中，选择该作业将要使用的代理帐户和凭据。</span><span class="sxs-lookup"><span data-stu-id="0276b-123">In the **Run as** list, select the proxy account with the credentials that the job will use.</span></span>  
  
7.  <span data-ttu-id="0276b-124">选择编写脚本的 **“语言”** 。</span><span class="sxs-lookup"><span data-stu-id="0276b-124">Select the **Language** in which the script was written.</span></span> <span data-ttu-id="0276b-125">或者，单击 **“其他”** ，然后输入编写脚本使用的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] ActiveX 脚本语言。</span><span class="sxs-lookup"><span data-stu-id="0276b-125">Alternatively, click **Other** and then enter the name of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] ActiveX scripting language in which the script will be written.</span></span>  
  
8.  <span data-ttu-id="0276b-126">在 **“命令”** 框中，输入将要对作业步骤执行的脚本语法。</span><span class="sxs-lookup"><span data-stu-id="0276b-126">In the **Command** box, enter the script syntax that will be executed for the job step.</span></span> <span data-ttu-id="0276b-127">或者，单击 **“打开”** ，选择包含脚本语法的文件。</span><span class="sxs-lookup"><span data-stu-id="0276b-127">Alternately, click **Open** and select a file containing the script syntax.</span></span>  
  
9. <span data-ttu-id="0276b-128">单击 **“高级”** 页设置以下作业步骤选项：当该作业步骤成功或失败时将执行的操作、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理应该尝试执行该作业步骤的次数以及重试的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="0276b-128">Click the **Advanced** page to set the following job step options: what action to take if the job step succeeds or fails, how many times [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent should try to execute the job step, and how often retry attempts should be made.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="0276b-129">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="0276b-129">Using Transact-SQL</span></span>  
  
#### <a name="to-create-an-activex-script-job-step"></a><span data-ttu-id="0276b-130">创建 ActiveX 脚本作业步骤</span><span class="sxs-lookup"><span data-stu-id="0276b-130">To create an ActiveX Script job step</span></span>  
  
1.  <span data-ttu-id="0276b-131">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="0276b-131">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="0276b-132">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="0276b-132">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="0276b-133">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="0276b-133">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- create an ActiveX Script job step written in VBScript that creates a restore point  
    USE msdb;  
    GO  
    EXEC sp_add_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_name = N'Create a restore point',  
        @subsystem = N'ACTIVESCRIPTING',  
        @command = N'Const RESTORE_POINT = 20  
  
    strComputer = "."  
    Set objWMIService = GetObject("winmgmts:" _  
        & "{impersonationLevel=impersonate}!\\" & strComputer & "\root\default")  
  
    Set objItem = objWMIService.Get("SystemRestore")  
    errResults = objItem.Restore(RESTORE_POINT)',   
        @retry_attempts = 5,  
        @retry_interval = 5 ;  
    GO  
    ```  
  
 <span data-ttu-id="0276b-134">有关详细信息，请参阅[&#40;transact-sql&#41;sp_add_jobstep ](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="0276b-134">For more information, see [sp_add_jobstep &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="0276b-135">使用 SQL Server 管理对象</span><span class="sxs-lookup"><span data-stu-id="0276b-135">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="0276b-136">**创建 ActiveX 脚本作业步骤**</span><span class="sxs-lookup"><span data-stu-id="0276b-136">**To create an ActiveX Script job step**</span></span>  
  
 <span data-ttu-id="0276b-137">通过使用所选的编程语言（如 Visual Basic、Visual C# 或 PowerShell）来使用 `JobStep` 类。</span><span class="sxs-lookup"><span data-stu-id="0276b-137">Use the `JobStep` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span>  
