---
title: 启动作业 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], starting
- SQL Server Agent jobs, starting
- starting jobs
ms.assetid: cec9f7f7-d0a7-4239-9dc5-a69c011ebaa0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4d5af895df518a915dacd953331b9139471933aa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692084"
---
# <a name="start-a-job"></a><span data-ttu-id="64885-102">启动作业</span><span class="sxs-lookup"><span data-stu-id="64885-102">Start a Job</span></span>
  <span data-ttu-id="64885-103">本主题说明如何 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 SQL Server 管理对象在中开始运行代理作业 [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="64885-103">This topic describes how to start running a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] or SQL Server Management Objects.</span></span>  
  
 <span data-ttu-id="64885-104">作业是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理执行的一系列指定操作。</span><span class="sxs-lookup"><span data-stu-id="64885-104">A job is a specified series of actions that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent performs.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="64885-105">代理作业可以在一个本地服务器上运行，也可以在多个远程服务器上运行。</span><span class="sxs-lookup"><span data-stu-id="64885-105">Agent jobs can run on one local server or on multiple remote servers.</span></span>  
  
-   <span data-ttu-id="64885-106">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="64885-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="64885-107">安全性</span><span class="sxs-lookup"><span data-stu-id="64885-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="64885-108">**若要启动作业，可使用：**</span><span class="sxs-lookup"><span data-stu-id="64885-108">**To start a job, using:**</span></span>  
  
     [<span data-ttu-id="64885-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="64885-109">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="64885-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="64885-110">Transact-SQL</span></span>](#TSQL)  
  
     [<span data-ttu-id="64885-111">SQL Server 管理对象</span><span class="sxs-lookup"><span data-stu-id="64885-111">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="64885-112">开始之前</span><span class="sxs-lookup"><span data-stu-id="64885-112">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="64885-113">Security</span><span class="sxs-lookup"><span data-stu-id="64885-113">Security</span></span>  
 <span data-ttu-id="64885-114">有关详细信息，请参阅[实现 SQL Server 代理安全性](implement-sql-server-agent-security.md)。</span><span class="sxs-lookup"><span data-stu-id="64885-114">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="64885-115">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="64885-115">Using SQL Server Management Studio</span></span>  
  
### <a name="to-start-a-job"></a><span data-ttu-id="64885-116">启动作业</span><span class="sxs-lookup"><span data-stu-id="64885-116">To start a job</span></span>  
  
1.  <span data-ttu-id="64885-117">在**对象资源管理器中，** 连接到的实例 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="64885-117">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="64885-118">展开 **“SQL Server 代理”** ，再展开 **“作业”**。</span><span class="sxs-lookup"><span data-stu-id="64885-118">Expand **SQL Server Agent,** and expand **Jobs**.</span></span> <span data-ttu-id="64885-119">根据您希望作业以何种方式启动，执行下列操作之一：</span><span class="sxs-lookup"><span data-stu-id="64885-119">Depending on how you want the job to start, do one of the following:</span></span>  
  
    -   <span data-ttu-id="64885-120">如果使用的是单台服务器或目标服务器，或者正在一台主服务器上运行一个本地服务器作业，请右键单击要启动的作业，然后单击“启动作业”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="64885-120">If you are working on a single server, or working on a target server, or running a local server job on a master server, right-click the job you want to start, and then click **Start Job**.</span></span>  
  
    -   <span data-ttu-id="64885-121">若要启动多个作业，请右键单击“作业活动监视器”\*\*\*\*，然后单击“查看作业活动”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="64885-121">If you want to start multiple jobs, right-click **Job Activity Monitor**, and then click **View Job Activity**.</span></span> <span data-ttu-id="64885-122">在作业活动监视器中，可以选择多个作业，右键单击所选作业，再单击“启动作业”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="64885-122">In the Job Activity Monitor you can select multiple jobs, right-click your selection, and click **Start Jobs**.</span></span>  
  
    -   <span data-ttu-id="64885-123">如果使用的是主服务器并且希望所有目标服务器同时运行作业，请右键单击要启动的作业、单击“启动作业”\*\*\*\*，然后单击“在所有目标服务器上启动”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="64885-123">If you are working on a master server and want all targeted servers to run the job simultaneously, right-click the job you want to start, click **Start Job**, and then click **Start on all targeted servers**.</span></span>  
  
    -   <span data-ttu-id="64885-124">如果使用的是主服务器并且希望指定运行作业的目标服务器，请右键单击要启动的作业、单击“启动作业”\*\*\*\*，然后单击“在特定的目标服务器上启动”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="64885-124">If you are working on a master server and want to specify target servers for the job, right-click the job you want to start, click **Start Job**, and then click **Start on specific target servers**.</span></span> <span data-ttu-id="64885-125">在 **“发布下载指令”** 对话框中，选中 **“以下目标服务器”** 复选框，然后选择运行该作业的每台目标服务器。</span><span class="sxs-lookup"><span data-stu-id="64885-125">In the **Post Download Instructions** dialog box, select the **These target servers** check box, and then select each target server on which this job should run.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="64885-126">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="64885-126">Using Transact-SQL</span></span>  
  
### <a name="to-start-a-job"></a><span data-ttu-id="64885-127">启动作业</span><span class="sxs-lookup"><span data-stu-id="64885-127">To start a job</span></span>  
  
1.  <span data-ttu-id="64885-128">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="64885-128">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="64885-129">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="64885-129">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="64885-130">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="64885-130">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- starts a job named Weekly Sales Data Backup.    
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_start_job N'Weekly Sales Data Backup' ;  
    GO  
    ```  
  
 <span data-ttu-id="64885-131">有关详细信息，请参阅 [sp_start_job (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-start-job-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="64885-131">For more information, see [sp_start_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-start-job-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="64885-132">使用 SQL Server 管理对象</span><span class="sxs-lookup"><span data-stu-id="64885-132">Using SQL Server Management Objects</span></span>  

### <a name="to-start-a-job"></a><span data-ttu-id="64885-133">启动作业</span><span class="sxs-lookup"><span data-stu-id="64885-133">To start a job</span></span>
  
 <span data-ttu-id="64885-134">通过使用所选编程语言（如 Visual Basic、Visual C# 或 PowerShell）来调用 `Start` 类的 `Job` 方法。</span><span class="sxs-lookup"><span data-stu-id="64885-134">Call the `Start` method of the `Job` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span> <span data-ttu-id="64885-135">有关详细信息，请参阅 [SQL Server 管理对象 (SMO)](https://msdn.microsoft.com/library/ms162169.aspx)。</span><span class="sxs-lookup"><span data-stu-id="64885-135">For more information, see [SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).</span></span>  
