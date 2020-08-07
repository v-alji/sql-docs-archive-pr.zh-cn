---
title: 查看作业历史记录 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], history
- viewing job history
- SQL Server Agent jobs, history
- historical information [SQL Server], jobs
- displaying job history
ms.assetid: 3bbd1556-abdb-48a3-b249-546eace76343
author: stevestein
ms.author: sstein
ms.openlocfilehash: e84fafdaeddb5748a8129cd5d71d667db7e5fa37
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691020"
---
# <a name="view-the-job-history"></a><span data-ttu-id="ccd80-102">View the Job History</span><span class="sxs-lookup"><span data-stu-id="ccd80-102">View the Job History</span></span>
  <span data-ttu-id="ccd80-103">本主题说明如何 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 、或 SQL Server 管理对象在中查看代理作业历史记录日志 [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="ccd80-103">This topic describes how to view the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job history log in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or SQL Server Management Objects.</span></span>  
  
-   <span data-ttu-id="ccd80-104">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="ccd80-104">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="ccd80-105">安全性</span><span class="sxs-lookup"><span data-stu-id="ccd80-105">Security</span></span>](#Security)  
  
-   <span data-ttu-id="ccd80-106">**若要查看作业历史记录日志，请使用：**</span><span class="sxs-lookup"><span data-stu-id="ccd80-106">**To view the job history log, using:**</span></span>  
  
     [<span data-ttu-id="ccd80-107">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ccd80-107">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="ccd80-108">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ccd80-108">Transact-SQL</span></span>](#TSQL)  
  
     [<span data-ttu-id="ccd80-109">SQL Server 管理对象</span><span class="sxs-lookup"><span data-stu-id="ccd80-109">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ccd80-110">开始之前</span><span class="sxs-lookup"><span data-stu-id="ccd80-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="ccd80-111">Security</span><span class="sxs-lookup"><span data-stu-id="ccd80-111">Security</span></span>  
 <span data-ttu-id="ccd80-112">有关详细信息，请参阅[实现 SQL Server 代理安全性](implement-sql-server-agent-security.md)。</span><span class="sxs-lookup"><span data-stu-id="ccd80-112">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="ccd80-113">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ccd80-113">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-the-job-history-log"></a><span data-ttu-id="ccd80-114">查看作业历史记录日志</span><span class="sxs-lookup"><span data-stu-id="ccd80-114">To view the job history log</span></span>  
  
1.  <span data-ttu-id="ccd80-115">在**对象资源管理器中，** 连接到的实例 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="ccd80-115">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="ccd80-116">展开 **“SQL Server 代理”**，再展开 **“作业”**。</span><span class="sxs-lookup"><span data-stu-id="ccd80-116">Expand **SQL Server Agent**, and then expand **Jobs**.</span></span>  
  
3.  <span data-ttu-id="ccd80-117">右键单击一个作业，再单击 **“查看历史记录”**。</span><span class="sxs-lookup"><span data-stu-id="ccd80-117">Right-click a job, and then click **View History**.</span></span>  
  
4.  <span data-ttu-id="ccd80-118">在日志文件查看器中，查看作业历史记录。</span><span class="sxs-lookup"><span data-stu-id="ccd80-118">In the Log File Viewer, view the job history.</span></span>  
  
5.  <span data-ttu-id="ccd80-119">若要更新作业历史记录，请单击 **“刷新”**。</span><span class="sxs-lookup"><span data-stu-id="ccd80-119">To update the job history, click **Refresh**.</span></span> <span data-ttu-id="ccd80-120">若要只查看几行，请单击 **“筛选”** 按钮并输入筛选参数。</span><span class="sxs-lookup"><span data-stu-id="ccd80-120">To view fewer rows, click the **Filter** button and enter filter parameters.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="ccd80-121">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ccd80-121">Using Transact-SQL</span></span>  
  
#### <a name="to-view-the-job-history-log"></a><span data-ttu-id="ccd80-122">查看作业历史记录日志</span><span class="sxs-lookup"><span data-stu-id="ccd80-122">To view the job history log</span></span>  
  
1.  <span data-ttu-id="ccd80-123">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="ccd80-123">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="ccd80-124">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="ccd80-124">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="ccd80-125">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="ccd80-125">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- lists all job information for the NightlyBackups job.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_help_jobhistory   
        @job_name = N'NightlyBackups' ;  
    GO  
    ```  
  
 <span data-ttu-id="ccd80-126">有关详细信息，请参阅[&#40;transact-sql&#41;sp_help_jobhistory ](/sql/relational-databases/system-stored-procedures/sp-help-jobhistory-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="ccd80-126">For more information, see [sp_help_jobhistory &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-jobhistory-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="ccd80-127">使用 SQL Server 管理对象</span><span class="sxs-lookup"><span data-stu-id="ccd80-127">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="ccd80-128">**查看作业历史记录日志**</span><span class="sxs-lookup"><span data-stu-id="ccd80-128">**To view the job history log**</span></span>  
  
 <span data-ttu-id="ccd80-129">通过使用所选编程语言（如 Visual Basic、Visual C# 或 PowerShell）来调用 `EnumHistory` 类的 `Job` 方法。</span><span class="sxs-lookup"><span data-stu-id="ccd80-129">Call the `EnumHistory` method of the `Job` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span> <span data-ttu-id="ccd80-130">有关详细信息，请参阅 [SQL Server 管理对象 (SMO)](https://msdn.microsoft.com/library/ms162169.aspx)。</span><span class="sxs-lookup"><span data-stu-id="ccd80-130">For more information, see [SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).</span></span>  
