---
title: 查看作业活动 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- viewing job activity
- jobs [SQL Server Agent], viewing
- SQL Server Agent jobs, viewing
- displaying job activity
ms.assetid: 5c284e5e-7775-435d-ac49-f3f12a27ddc7
author: stevestein
ms.author: sstein
ms.openlocfilehash: 56b159952c83ed243c4c5d8012c76e5a2a248519
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693610"
---
# <a name="view-job-activity"></a><span data-ttu-id="66bcc-102">View Job Activity</span><span class="sxs-lookup"><span data-stu-id="66bcc-102">View Job Activity</span></span>
  <span data-ttu-id="66bcc-103">本主题介绍了如何使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 或 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中查看 [!INCLUDE[tsql](../../includes/tsql-md.md)]代理作业的运行时状态。</span><span class="sxs-lookup"><span data-stu-id="66bcc-103">This topic describes how to view the runtime state of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="66bcc-104">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理服务启动后，将创建一个新的会话，并且 msdb\*\*\*\* 数据库的 sysjobactivity\*\*\*\* 表由所有现有的已定义作业填充。</span><span class="sxs-lookup"><span data-stu-id="66bcc-104">When the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service starts, a new session is created and the **sysjobactivity** table in the **msdb** database is populated with all the existing defined jobs.</span></span> <span data-ttu-id="66bcc-105">此表记录当前作业活动和状态。</span><span class="sxs-lookup"><span data-stu-id="66bcc-105">This table records current job activity and status.</span></span> <span data-ttu-id="66bcc-106">您可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理中的作业活动监视器查看作业的当前状态。</span><span class="sxs-lookup"><span data-stu-id="66bcc-106">You can use the Job Activity Monitor in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to view the current state of jobs.</span></span> <span data-ttu-id="66bcc-107">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理服务意外终止，您可以查看 **sysjobactivity** 表以查明服务终止时正在执行哪些作业。</span><span class="sxs-lookup"><span data-stu-id="66bcc-107">If the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service unexpectedly terminates, you can refer to the **sysjobactivity** table to see which jobs were being executed when the service terminated.</span></span>  
  
 <span data-ttu-id="66bcc-108">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="66bcc-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="66bcc-109">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="66bcc-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="66bcc-110">安全性</span><span class="sxs-lookup"><span data-stu-id="66bcc-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="66bcc-111">**若要查看作业活动，请使用：**</span><span class="sxs-lookup"><span data-stu-id="66bcc-111">**To view job activity, using:**</span></span>  
  
     [<span data-ttu-id="66bcc-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="66bcc-112">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="66bcc-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="66bcc-113">Transact-SQL</span></span>](#TSQL)  
  
## <a name="before-you-begin"></a><span data-ttu-id="66bcc-114">开始之前</span><span class="sxs-lookup"><span data-stu-id="66bcc-114">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="66bcc-115">Security</span><span class="sxs-lookup"><span data-stu-id="66bcc-115">Security</span></span>  
 <span data-ttu-id="66bcc-116">有关详细信息，请参阅[实现 SQL Server 代理安全性](implement-sql-server-agent-security.md)。</span><span class="sxs-lookup"><span data-stu-id="66bcc-116">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="66bcc-117">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="66bcc-117">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-job-activity"></a><span data-ttu-id="66bcc-118">查看作业活动</span><span class="sxs-lookup"><span data-stu-id="66bcc-118">To view job activity</span></span>  
  
1.  <span data-ttu-id="66bcc-119">在 **对象资源管理器**中，连接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]的实例，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="66bcc-119">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="66bcc-120">展开 **“SQL Server 代理”**。</span><span class="sxs-lookup"><span data-stu-id="66bcc-120">Expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="66bcc-121">右键单击 "**作业活动监视器**"，然后单击 "**查看作业活动**"。</span><span class="sxs-lookup"><span data-stu-id="66bcc-121">Right-click **Job Activity Monitor** and click **View Job Activity**.</span></span>  
  
4.  <span data-ttu-id="66bcc-122">在 **作业活动监视器**中，可以查看为此服务器定义的每个作业的详细信息。</span><span class="sxs-lookup"><span data-stu-id="66bcc-122">In the **Job Activity Monitor**, you can view details about each job that is defined for this server.</span></span>  
  
5.  <span data-ttu-id="66bcc-123">右键单击一个作业以启动、停止、启用或禁用该作业，按照作业活动监视器中的显示刷新状态，删除该作业，或者查看其历史记录或属性。</span><span class="sxs-lookup"><span data-stu-id="66bcc-123">Right-click a job to start it, stop it, enable or disable it, refresh its status as displayed in the Job Activity Monitor, delete it, or view its history or properties.</span></span>  <span data-ttu-id="66bcc-124">若要启动、停止、启用、禁用或刷新多个作业，请在作业活动监视器中选择多个行，然后右键单击所选内容。</span><span class="sxs-lookup"><span data-stu-id="66bcc-124">To start, stop, enable or disable, or refresh multiple jobs, select multiple rows in the Job Activity Monitor, and right-click your selection.</span></span>  
  
6.  <span data-ttu-id="66bcc-125">若要更新作业活动监视器，请单击 **“刷新”**。</span><span class="sxs-lookup"><span data-stu-id="66bcc-125">To update the Job Activity Monitor, click **Refresh**.</span></span> <span data-ttu-id="66bcc-126">若要查看较少的行，请单击 **“筛选”** ，然后输入筛选参数。</span><span class="sxs-lookup"><span data-stu-id="66bcc-126">To view fewer rows, click **Filter** and enter filter parameters.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="66bcc-127">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="66bcc-127">Using Transact-SQL</span></span>  
  
#### <a name="to-view-job-activity"></a><span data-ttu-id="66bcc-128">查看作业活动</span><span class="sxs-lookup"><span data-stu-id="66bcc-128">To view job activity</span></span>  
  
1.  <span data-ttu-id="66bcc-129">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="66bcc-129">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="66bcc-130">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="66bcc-130">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="66bcc-131">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="66bcc-131">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- lists activity for all jobs that the current user has permission to view.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_help_jobactivity ;  
    GO  
    ```  
  
 <span data-ttu-id="66bcc-132">有关详细信息，请参阅[&#40;transact-sql&#41;sp_help_jobactivity ](/sql/relational-databases/system-stored-procedures/sp-help-jobactivity-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="66bcc-132">For more information, see [sp_help_jobactivity &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-jobactivity-transact-sql).</span></span>  
  
  
