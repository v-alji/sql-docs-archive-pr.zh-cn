---
title: 停止作业 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], stopping
- SQL Server Agent jobs, stopping
- stopping jobs
ms.assetid: 4249328a-24d8-4284-9d1d-7d04ed90e3d7
author: stevestein
ms.author: sstein
ms.openlocfilehash: 78986e85dd8ee808f5fb621182d903a94bbc5eb7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682653"
---
# <a name="stop-a-job"></a><span data-ttu-id="fa326-102">Stop a Job</span><span class="sxs-lookup"><span data-stu-id="fa326-102">Stop a Job</span></span>
  <span data-ttu-id="fa326-103">本主题说明如何停止 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业。</span><span class="sxs-lookup"><span data-stu-id="fa326-103">This topic describes how to stop a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job.</span></span> <span data-ttu-id="fa326-104">作业是 SQL Server 代理执行的一系列指定操作。</span><span class="sxs-lookup"><span data-stu-id="fa326-104">A job is a specified series of actions that SQL Server Agent performs.</span></span>  
  
-   <span data-ttu-id="fa326-105">**开始之前：** ，</span><span class="sxs-lookup"><span data-stu-id="fa326-105">**Before you begin:**  ,</span></span>  
  
     [<span data-ttu-id="fa326-106">限制和局限</span><span class="sxs-lookup"><span data-stu-id="fa326-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="fa326-107">安全性</span><span class="sxs-lookup"><span data-stu-id="fa326-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="fa326-108">**若要停止作业，请使用：**</span><span class="sxs-lookup"><span data-stu-id="fa326-108">**To stop a job, using:**</span></span>  
  
     [<span data-ttu-id="fa326-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="fa326-109">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="fa326-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="fa326-110">Transact-SQL</span></span>](#TSQL)  
  
     [<span data-ttu-id="fa326-111">SQL Server 管理对象</span><span class="sxs-lookup"><span data-stu-id="fa326-111">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="fa326-112">开始之前</span><span class="sxs-lookup"><span data-stu-id="fa326-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="fa326-113">限制和局限</span><span class="sxs-lookup"><span data-stu-id="fa326-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="fa326-114">如果作业当前正在执行 **CmdExec** 或 **PowerShell**类型的步骤，则强制提前结束正在运行的进程（例如 MyProgram.exe）。</span><span class="sxs-lookup"><span data-stu-id="fa326-114">If a job is currently executing a step of type **CmdExec** or **PowerShell**, the process that is being run (for example, MyProgram.exe) is forced to end prematurely.</span></span> <span data-ttu-id="fa326-115">这可能会导致不可预知的行为，如进程正在使用的文件保持为打开状态。</span><span class="sxs-lookup"><span data-stu-id="fa326-115">This can cause unpredictable behavior, such as files that are being used by the process being held open.</span></span>  
  
-   <span data-ttu-id="fa326-116">对于多服务器作业，针对该作业的 STOP 指令将发布到该作业的所有目标服务器中。</span><span class="sxs-lookup"><span data-stu-id="fa326-116">For a multiserver job, a STOP instruction for the job is posted to all target servers of the job.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="fa326-117">Security</span><span class="sxs-lookup"><span data-stu-id="fa326-117">Security</span></span>  
 <span data-ttu-id="fa326-118">有关详细信息，请参阅[实现 SQL Server 代理安全性](implement-sql-server-agent-security.md)。</span><span class="sxs-lookup"><span data-stu-id="fa326-118">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="fa326-119">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="fa326-119">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-stop-a-job"></a><span data-ttu-id="fa326-120">停止作业</span><span class="sxs-lookup"><span data-stu-id="fa326-120">To stop a job</span></span>  
  
1.  <span data-ttu-id="fa326-121">在**对象资源管理器中，** 连接到的实例 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="fa326-121">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="fa326-122">展开 **“SQL Server 代理”**，再展开 **“作业”**，右键单击要停止的作业，再单击 **“停止作业”**。</span><span class="sxs-lookup"><span data-stu-id="fa326-122">Expand **SQL Server Agent**, expand **Jobs**, right-click the job you want to stop, and then click **Stop Job**.</span></span>  
  
3.  <span data-ttu-id="fa326-123">若要停止多个作业，请右键单击 **“作业活动监视器”**，然后单击 **“查看作业活动”**。</span><span class="sxs-lookup"><span data-stu-id="fa326-123">If you want to stop multiple jobs, right-click **Job Activity Monitor**, and then click **View Job Activity**.</span></span> <span data-ttu-id="fa326-124">在作业活动监视器中，选择要停止的作业，右键单击所选内容，然后单击 **“停止作业”**。</span><span class="sxs-lookup"><span data-stu-id="fa326-124">In the Job Activity Monitor, select the jobs you want to stop, right-click your selection, and then click **Stop Jobs**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="fa326-125">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="fa326-125">Using Transact-SQL</span></span>  
  
### <a name="to-stop-a-job"></a><span data-ttu-id="fa326-126">停止作业</span><span class="sxs-lookup"><span data-stu-id="fa326-126">To stop a job</span></span>  
  
1.  <span data-ttu-id="fa326-127">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="fa326-127">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="fa326-128">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="fa326-128">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="fa326-129">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="fa326-129">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- stops a job named Weekly Sales Data Backup  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_stop_job  
        N'Weekly Sales Data Backup' ;  
    GO  
    ```  
  
 <span data-ttu-id="fa326-130">有关详细信息，请参阅[&#40;transact-sql&#41;sp_stop_job ](/sql/relational-databases/system-stored-procedures/sp-stop-job-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="fa326-130">For more information, see [sp_stop_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-stop-job-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="fa326-131">使用 SQL Server 管理对象</span><span class="sxs-lookup"><span data-stu-id="fa326-131">Using SQL Server Management Objects</span></span>  

### <a name="to-stop-a-job"></a><span data-ttu-id="fa326-132">停止作业</span><span class="sxs-lookup"><span data-stu-id="fa326-132">To stop a job</span></span>
  
 <span data-ttu-id="fa326-133">通过使用所选编程语言（如 Visual Basic、Visual C# 或 PowerShell）来调用 `Stop` 类的 `Job` 方法。</span><span class="sxs-lookup"><span data-stu-id="fa326-133">Call the `Stop` method of the `Job` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span> <span data-ttu-id="fa326-134">有关详细信息，请参阅 [SQL Server 管理对象 (SMO)](https://msdn.microsoft.com/library/ms162169.aspx)。</span><span class="sxs-lookup"><span data-stu-id="fa326-134">For more information, see [SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).</span></span>  
