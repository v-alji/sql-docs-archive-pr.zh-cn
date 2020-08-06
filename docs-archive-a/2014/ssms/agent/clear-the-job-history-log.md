---
title: 清除作业历史记录日志 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], history
- clearing job history log
- logs [SQL Server], jobs
- SQL Server Agent jobs, history
- historical information [SQL Server], jobs
ms.assetid: 34b9398a-c409-4040-8ea1-0deceb18f961
author: stevestein
ms.author: sstein
ms.openlocfilehash: 813c2c7c86a769eea09a093f2de999460d78ef54
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591079"
---
# <a name="clear-the-job-history-log"></a><span data-ttu-id="e2398-102">Clear the Job History Log</span><span class="sxs-lookup"><span data-stu-id="e2398-102">Clear the Job History Log</span></span>
  <span data-ttu-id="e2398-103">本主题说明如何 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 、或 SQL Server 管理对象删除代理作业历史记录日志的内容 [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="e2398-103">This topic describes how to delete the contents of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job history log in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or SQL Server Management Objects.</span></span>  
  
 <span data-ttu-id="e2398-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="e2398-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="e2398-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="e2398-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="e2398-106">安全性</span><span class="sxs-lookup"><span data-stu-id="e2398-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="e2398-107">**若要清除作业历史记录日志，请使用：**</span><span class="sxs-lookup"><span data-stu-id="e2398-107">**To clear the job history log, using:**</span></span>  
  
     [<span data-ttu-id="e2398-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e2398-108">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="e2398-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e2398-109">Transact-SQL</span></span>](#TSQL)  
  
     [<span data-ttu-id="e2398-110">SQL Server 管理对象</span><span class="sxs-lookup"><span data-stu-id="e2398-110">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="e2398-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="e2398-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="e2398-112">Security</span><span class="sxs-lookup"><span data-stu-id="e2398-112">Security</span></span>  
 <span data-ttu-id="e2398-113">有关详细信息，请参阅[实现 SQL Server 代理安全性](implement-sql-server-agent-security.md)。</span><span class="sxs-lookup"><span data-stu-id="e2398-113">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="e2398-114">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e2398-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-clear-the-job-history-log"></a><span data-ttu-id="e2398-115">清除作业历史记录日志</span><span class="sxs-lookup"><span data-stu-id="e2398-115">To clear the job history log</span></span>  
  
1.  <span data-ttu-id="e2398-116">在**对象资源管理器中，** 连接到的实例 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="e2398-116">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="e2398-117">展开 **“SQL Server 代理”**，再展开 **“作业”**。</span><span class="sxs-lookup"><span data-stu-id="e2398-117">Expand **SQL Server Agent**, and then expand **Jobs**.</span></span>  
  
3.  <span data-ttu-id="e2398-118">右键单击某个作业，再单击 **“查看历史记录”**。</span><span class="sxs-lookup"><span data-stu-id="e2398-118">Right-click a job and click **View history**.</span></span>  
  
4.  <span data-ttu-id="e2398-119">在 **“日志文件查看器”** 中，选择要清除其历史记录的作业，再执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="e2398-119">In the **Log File Viewer**, select the job for which you want to clear history, and then do one of the following:</span></span>  
  
    -   <span data-ttu-id="e2398-120">单击 **“删除”**，再单击 **“删除历史记录”** 对话框中的 **“删除所有历史记录”** 。</span><span class="sxs-lookup"><span data-stu-id="e2398-120">Click **Delete**, and then click **Delete all history** in the **Delete History** dialog.</span></span> <span data-ttu-id="e2398-121">可以删除所有作业历史记录，或者仅删除早于指定日期的历史记录。</span><span class="sxs-lookup"><span data-stu-id="e2398-121">You can delete all job history or only history that is older than a specified date.</span></span> <span data-ttu-id="e2398-122">若要删除所有作业历史记录，请单击 **“删除所有历史记录”**。</span><span class="sxs-lookup"><span data-stu-id="e2398-122">If you want to remove all job history, click **Delete all history**.</span></span> <span data-ttu-id="e2398-123">如果只删除较早的作业历史记录日志，请单击 **“删除以下时间之前的历史记录”**，然后指定日期。</span><span class="sxs-lookup"><span data-stu-id="e2398-123">If you only want to remove older job history logs, click **Delete history before**, and then specify a date.</span></span>  
  
    -   <span data-ttu-id="e2398-124">单击 **“作业状态”** （如果要清除多服务器作业的历史记录日志）。</span><span class="sxs-lookup"><span data-stu-id="e2398-124">Click **Job status** if you want to clear the history log of a multiserver job.</span></span> <span data-ttu-id="e2398-125">单击 **“作业”**，单击某个作业名，再单击 **“查看远程作业历史记录”**。</span><span class="sxs-lookup"><span data-stu-id="e2398-125">Click **Job**, click a job name, and then click **View Remote Job History**.</span></span>  
  
5.  <span data-ttu-id="e2398-126">单击“删除” 。</span><span class="sxs-lookup"><span data-stu-id="e2398-126">Click **Delete**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="e2398-127">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e2398-127">Using Transact-SQL</span></span>  
  
#### <a name="to-clear-the-job-history-log"></a><span data-ttu-id="e2398-128">清除作业历史记录日志</span><span class="sxs-lookup"><span data-stu-id="e2398-128">To clear the job history log</span></span>  
  
1.  <span data-ttu-id="e2398-129">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="e2398-129">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="e2398-130">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="e2398-130">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="e2398-131">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="e2398-131">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- example removes the history for a job named NightlyBackups.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_purge_jobhistory  
        @job_name = N'NightlyBackups' ;  
    GO  
    ```  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="e2398-132">使用 SQL Server 管理对象</span><span class="sxs-lookup"><span data-stu-id="e2398-132">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="e2398-133">**清除作业历史记录日志**</span><span class="sxs-lookup"><span data-stu-id="e2398-133">**To clear the job history log**</span></span>  
  
 <span data-ttu-id="e2398-134">通过使用所选的编程语言（如 Visual Basic、Visual C# 或 PowerShell）来使用 `PurgeJobHistory` 类的 `JobServer` 方法。</span><span class="sxs-lookup"><span data-stu-id="e2398-134">Use the `PurgeJobHistory` method of the `JobServer` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span> <span data-ttu-id="e2398-135">有关详细信息，请参阅 [SQL Server 管理对象 (SMO)](https://msdn.microsoft.com/library/ms162169.aspx)。</span><span class="sxs-lookup"><span data-stu-id="e2398-135">For more information, see [SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).</span></span>  
  
  
