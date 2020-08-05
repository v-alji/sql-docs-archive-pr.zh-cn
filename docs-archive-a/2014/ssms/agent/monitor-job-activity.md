---
title: 监视作业活动 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, monitoring
- jobs [SQL Server Agent], monitoring
- monitoring [SQL Server], jobs
- activity monitoring [SQL Server Agent]
- monitoring [SQL Server], SQL Server Agent
- monitoring [SQL Server Agent]
- SQL Server Agent Job Activity Monitor
- SQL Server Agent jobs, monitoring
- performance [SQL Server], jobs
- current activity
ms.assetid: 71cb432b-631d-4b8b-9965-e731b3d8266d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5088e029e90b4556c1559f8c948e8a8734762749
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580528"
---
# <a name="monitor-job-activity"></a><span data-ttu-id="f45aa-102">监视作业活动</span><span class="sxs-lookup"><span data-stu-id="f45aa-102">Monitor Job Activity</span></span>
  <span data-ttu-id="f45aa-103">可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业活动监视器监视在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的实例中定义的所有作业的当前活动。</span><span class="sxs-lookup"><span data-stu-id="f45aa-103">You can monitor the current activity of all defined jobs on an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Job Activity Monitor.</span></span>  
  
## <a name="sql-server-agent-sessions"></a><span data-ttu-id="f45aa-104">SQL Server 代理会话</span><span class="sxs-lookup"><span data-stu-id="f45aa-104">SQL Server Agent Sessions</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="f45aa-105">每当服务启动时，代理都会创建新的会话。</span><span class="sxs-lookup"><span data-stu-id="f45aa-105">Agent creates a new session each time the service starts.</span></span> <span data-ttu-id="f45aa-106">创建新会话后，将用所有现有已定义的作业填充 **msdb** 数据库中的 **sysjobactivity** 表。</span><span class="sxs-lookup"><span data-stu-id="f45aa-106">When a new session is created, the **sysjobactivity** table in the **msdb** database is populated with all the existing defined jobs.</span></span> <span data-ttu-id="f45aa-107">当 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理重新启动时，此表将保留作业的上一次活动。</span><span class="sxs-lookup"><span data-stu-id="f45aa-107">This table preserves the last activity for jobs when [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent is restarted.</span></span> <span data-ttu-id="f45aa-108">每个会话均记录从作业开始到作业结束的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理的正常作业活动。</span><span class="sxs-lookup"><span data-stu-id="f45aa-108">Each session records [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent normal job activity from the start of the job to its finish.</span></span> <span data-ttu-id="f45aa-109">有关这些会话的信息存储在 **msdb** 数据库的 **syssessions** 表中。</span><span class="sxs-lookup"><span data-stu-id="f45aa-109">Information about these sessions is stored in the **syssessions** table of the **msdb** database.</span></span>  
  
## <a name="job-activity-monitor"></a><span data-ttu-id="f45aa-110">作业活动监视器</span><span class="sxs-lookup"><span data-stu-id="f45aa-110">Job Activity Monitor</span></span>  
 <span data-ttu-id="f45aa-111">作业活动监视器允许使用 **查看** sysjobactivity [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]表。</span><span class="sxs-lookup"><span data-stu-id="f45aa-111">The Job Activity Monitor allows you to view the **sysjobactivity** table by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="f45aa-112">您可以查看服务器上的所有作业，或定义筛选器以限制显示的作业数。</span><span class="sxs-lookup"><span data-stu-id="f45aa-112">You can view all jobs on the server, or you can define filters to limit the number of jobs displayed.</span></span> <span data-ttu-id="f45aa-113">还可以通过单击“代理作业活动”\*\*\*\* 网格中的某个列标题来对作业信息进行排序。</span><span class="sxs-lookup"><span data-stu-id="f45aa-113">You can also sort the job information by clicking on a column heading in the **Agent Job Activity** grid.</span></span> <span data-ttu-id="f45aa-114">例如，当选择“上次运行时间”\*\*\*\* 列标题时，可以按上次运行的顺序查看作业。</span><span class="sxs-lookup"><span data-stu-id="f45aa-114">For example, when you select the **Last Run** column heading, you can view the jobs in the order that they were last run.</span></span> <span data-ttu-id="f45aa-115">多次单击列标题可使作业按照上次运行的日期在升序和降序之间切换。</span><span class="sxs-lookup"><span data-stu-id="f45aa-115">Clicking the column heading again toggles the jobs in ascending and descending order based on their last run date.</span></span>  
  
 <span data-ttu-id="f45aa-116">使用作业活动监视器，可以执行下列任务：</span><span class="sxs-lookup"><span data-stu-id="f45aa-116">Using the Job Activity Monitor you can perform the following tasks:</span></span>  
  
-   <span data-ttu-id="f45aa-117">启动和停止作业。</span><span class="sxs-lookup"><span data-stu-id="f45aa-117">Start and stop jobs.</span></span>  
  
-   <span data-ttu-id="f45aa-118">查看作业属性。</span><span class="sxs-lookup"><span data-stu-id="f45aa-118">View job properties.</span></span>  
  
-   <span data-ttu-id="f45aa-119">查看特定作业的历史。</span><span class="sxs-lookup"><span data-stu-id="f45aa-119">View the history for a specific job.</span></span>  
  
-   <span data-ttu-id="f45aa-120">手动刷新“代理作业活动”\*\*\*\* 网格中的信息，或者通过单击“查看刷新设置”\*\*\*\* 设置自动刷新间隔。</span><span class="sxs-lookup"><span data-stu-id="f45aa-120">Refresh the information in the **Agent Job Activity** grid manually or set an automatic refresh interval by clicking **View refresh settings**.</span></span>  
  
 <span data-ttu-id="f45aa-121">若要查看计划运行的作业、当前会话期间运行的作业的最新结果以及当前正在运行或空闲的作业，请使用作业活动监视器。</span><span class="sxs-lookup"><span data-stu-id="f45aa-121">Use the Job Activity Monitor when you want to find out what jobs are scheduled to run, the last outcome of jobs that have run during the current session, and to find out which jobs are currently running or idle.</span></span> <span data-ttu-id="f45aa-122">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理服务意外失败，您可以参考作业活动监视器中的上一次会话来确定正在执行的作业。</span><span class="sxs-lookup"><span data-stu-id="f45aa-122">If the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service fails unexpectedly, you can determine which jobs were in the middle of being executed by looking at the previous session in the Job Activity Monitor.</span></span>  
  
 <span data-ttu-id="f45aa-123">若要打开作业活动监视器，请在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 对象资源管理器中展开“SQL Server 代理”\*\*\*\*，右键单击“作业活动监视器”\*\*\*\*，再单击“查看作业活动”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f45aa-123">To open the Job Activity Monitor, expand **SQL Server Agent** in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] Object Explorer, right-click **Job Activity Monitor**, and click **View Job Activity**.</span></span>  
  
 <span data-ttu-id="f45aa-124">也可以使用存储过程 **sp_help_jobactivity**查看当前会话的作业活动。</span><span class="sxs-lookup"><span data-stu-id="f45aa-124">You can also view job activity for the current session by using the stored procedure **sp_help_jobactivity**.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="f45aa-125">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="f45aa-125">Related Tasks</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f45aa-126">**说明**</span><span class="sxs-lookup"><span data-stu-id="f45aa-126">**Description**</span></span>|<span data-ttu-id="f45aa-127">**主题**</span><span class="sxs-lookup"><span data-stu-id="f45aa-127">**Topic**</span></span>|  
|<span data-ttu-id="f45aa-128">介绍如何查看 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业的运行时状态。</span><span class="sxs-lookup"><span data-stu-id="f45aa-128">Describes how to view the runtime state of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs.</span></span>|[<span data-ttu-id="f45aa-129">View Job Activity</span><span class="sxs-lookup"><span data-stu-id="f45aa-129">View Job Activity</span></span>](view-job-activity.md)|  
  
## <a name="see-also"></a><span data-ttu-id="f45aa-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f45aa-130">See Also</span></span>  
 <span data-ttu-id="f45aa-131">[查看作业活动](view-job-activity.md) </span><span class="sxs-lookup"><span data-stu-id="f45aa-131">[View Job Activity](view-job-activity.md) </span></span>  
 <span data-ttu-id="f45aa-132">[dbo.sysjobactivity &#40;Transact-sql&#41;](/sql/relational-databases/system-tables/dbo-sysjobactivity-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f45aa-132">[dbo.sysjobactivity &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/dbo-sysjobactivity-transact-sql) </span></span>  
 <span data-ttu-id="f45aa-133">[&#40;Transact-sql 的dbo.sys会话&#41;](/sql/relational-databases/system-tables/dbo-syssessions-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f45aa-133">[dbo.syssessions &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/dbo-syssessions-transact-sql) </span></span>  
 [<span data-ttu-id="f45aa-134">sp_help_jobactivity &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="f45aa-134">sp_help_jobactivity &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-help-jobactivity-transact-sql)  
  
  
