---
title: 将作业状态写入 Windows 应用程序日志 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- status information [SQL Server], jobs
- SQL Server Agent jobs, status
- writing job status to log
- jobs [SQL Server Agent], status
- logs [SQL Server], jobs
ms.assetid: 3b813702-8f61-40ec-bf3b-ce9deb7e68be
author: stevestein
ms.author: sstein
ms.openlocfilehash: 67bdd7948d1722e49976d5e48b571c684431cd1c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691015"
---
# <a name="write-the-job-status-to-the-windows-application-log"></a><span data-ttu-id="fe9f6-102">Write the Job Status to the Windows Application Log</span><span class="sxs-lookup"><span data-stu-id="fe9f6-102">Write the Job Status to the Windows Application Log</span></span>
  <span data-ttu-id="fe9f6-103">本主题介绍如何 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在中配置代理 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ，以便通过使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 、或 SQL Server 管理对象将作业状态写入 Windows 应用程序事件日志 [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="fe9f6-103">This topic describes how to configure [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] to write job status to the Windows application event log by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or SQL Server Management Objects.</span></span>  
  
 <span data-ttu-id="fe9f6-104">作业响应可确保数据库管理员知道作业完成的时间和作业运行频率。</span><span class="sxs-lookup"><span data-stu-id="fe9f6-104">Job responses ensure that database administrators know when jobs complete and how frequently they run.</span></span> <span data-ttu-id="fe9f6-105">典型的作业响应包括：</span><span class="sxs-lookup"><span data-stu-id="fe9f6-105">Typical job responses include:</span></span>  
  
-   <span data-ttu-id="fe9f6-106">使用电子邮件、电子寻呼或 **net send** 消息通知操作员。</span><span class="sxs-lookup"><span data-stu-id="fe9f6-106">Notifying the operator by using e-mail, electronic paging, or a **net send** message.</span></span> <span data-ttu-id="fe9f6-107">如果操作员必须执行后续操作，应使用其中的某种作业响应。</span><span class="sxs-lookup"><span data-stu-id="fe9f6-107">Use one of these job responses if the operator must perform a follow-up action.</span></span> <span data-ttu-id="fe9f6-108">例如，当一个备份作业成功地完成之后，必须通知操作员取出备份磁带并将其存放在安全处。</span><span class="sxs-lookup"><span data-stu-id="fe9f6-108">For example, if a backup job completes successfully, the operator must be notified to remove the backup tape and store it in a safe location.</span></span>  
  
-   <span data-ttu-id="fe9f6-109">将事件消息写入 Windows 应用程序日志。</span><span class="sxs-lookup"><span data-stu-id="fe9f6-109">Writing an event message to the Windows application log.</span></span> <span data-ttu-id="fe9f6-110">只能对失败的作业使用这种响应。</span><span class="sxs-lookup"><span data-stu-id="fe9f6-110">You can use this response only for failed jobs.</span></span>  
  
-   <span data-ttu-id="fe9f6-111">自动删除作业。</span><span class="sxs-lookup"><span data-stu-id="fe9f6-111">Automatically deleting the job.</span></span> <span data-ttu-id="fe9f6-112">如果确信不需要再次运行该作业，可以使用这种作业响应。</span><span class="sxs-lookup"><span data-stu-id="fe9f6-112">Use this job response if you are certain that you do not need to rerun this job.</span></span>  
  
 <span data-ttu-id="fe9f6-113">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="fe9f6-113">**In This Topic**</span></span>  
  
-   <span data-ttu-id="fe9f6-114">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="fe9f6-114">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="fe9f6-115">安全性</span><span class="sxs-lookup"><span data-stu-id="fe9f6-115">Security</span></span>](#Security)  
  
-   <span data-ttu-id="fe9f6-116">**若要将作业状态写入 Windows 应用程序日志，请使用：**</span><span class="sxs-lookup"><span data-stu-id="fe9f6-116">**To write the job status to the Windows application log, using:**</span></span>  
  
     [<span data-ttu-id="fe9f6-117">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="fe9f6-117">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="fe9f6-118">SQL Server 管理对象</span><span class="sxs-lookup"><span data-stu-id="fe9f6-118">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="fe9f6-119">开始之前</span><span class="sxs-lookup"><span data-stu-id="fe9f6-119">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="fe9f6-120">Security</span><span class="sxs-lookup"><span data-stu-id="fe9f6-120">Security</span></span>  
 <span data-ttu-id="fe9f6-121">有关详细信息，请参阅[实现 SQL Server 代理安全性](implement-sql-server-agent-security.md)。</span><span class="sxs-lookup"><span data-stu-id="fe9f6-121">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="fe9f6-122">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="fe9f6-122">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-write-job-status-to-the-windows-application-log"></a><span data-ttu-id="fe9f6-123">将作业状态写入 Windows 应用程序日志</span><span class="sxs-lookup"><span data-stu-id="fe9f6-123">To write job status to the Windows application log</span></span>  
  
1.  <span data-ttu-id="fe9f6-124">在**对象资源管理器中，** 连接到的实例 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="fe9f6-124">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="fe9f6-125">展开 **“SQL Server 代理”**，展开 **“作业”**，右键单击要编辑的作业，再单击 **“属性”**。</span><span class="sxs-lookup"><span data-stu-id="fe9f6-125">Expand **SQL Server Agent**, expand **Jobs**, right-click the job you want to edit, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="fe9f6-126">选择 **“通知”** 页。</span><span class="sxs-lookup"><span data-stu-id="fe9f6-126">Select the **Notifications** page.</span></span>  
  
4.  <span data-ttu-id="fe9f6-127">请检查 **“写入 Windows 应用程序事件日志”**，然后执行下列操作之一：</span><span class="sxs-lookup"><span data-stu-id="fe9f6-127">Check **Write to Windows application event log**, and choose one of the following:</span></span>  
  
    -   <span data-ttu-id="fe9f6-128">单击“当作业成功时”\*\*\*\*，以在作业成功完成时记录作业状态。</span><span class="sxs-lookup"><span data-stu-id="fe9f6-128">Click**When the job succeeds**to log the job status when the job completes successfully.</span></span>  
  
    -   <span data-ttu-id="fe9f6-129">单击“当作业失败时”\*\*\*\*，以在作业未成功完成时记录作业状态。</span><span class="sxs-lookup"><span data-stu-id="fe9f6-129">Click**When the job fails**to log the job status when the job completes unsuccessfully.</span></span>  
  
    -   <span data-ttu-id="fe9f6-130">单击“当作业完成时”\*\*\*\*，以便无论完成状态如何，都记录作业状态。</span><span class="sxs-lookup"><span data-stu-id="fe9f6-130">Click**When the job completes** to log the job status regardless of completion status.</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="fe9f6-131">使用 SQL Server 管理对象</span><span class="sxs-lookup"><span data-stu-id="fe9f6-131">Using SQL Server Management Objects</span></span>  

### <a name="to-write-job-status-to-the-windows-application-log"></a><span data-ttu-id="fe9f6-132">将作业状态写入 Windows 应用程序日志</span><span class="sxs-lookup"><span data-stu-id="fe9f6-132">To write job status to the Windows application log</span></span>
  
 <span data-ttu-id="fe9f6-133">通过使用所选编程语言（如 Visual Basic、Visual C# 或 PowerShell）来调用 `EventLogLevel` 类的 `Job` 属性。</span><span class="sxs-lookup"><span data-stu-id="fe9f6-133">Call the `EventLogLevel` property of the `Job` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span>  
  
 <span data-ttu-id="fe9f6-134">下列代码示例将作业设置为在作业完成执行时生成操作系统事件日志条目。</span><span class="sxs-lookup"><span data-stu-id="fe9f6-134">The following code example sets the job to generate an operating system event log entry when the job execution finishes.</span></span>  
  
```powershell
$srv = new-object Microsoft.SqlServer.Management.Smo.Server("(local)")  
$jb = new-object Microsoft.SqlServer.Management.Smo.Agent.Job($srv.JobServer, "Test Job")  
$jb.EventLogLevel = [Microsoft.SqlServer.Management.Smo.Agent.CompletionAction]::Always  
```  
