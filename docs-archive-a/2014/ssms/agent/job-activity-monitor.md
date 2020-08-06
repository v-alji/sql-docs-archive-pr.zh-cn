---
title: 作业活动监视器 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- SQL12.SWB.ACTIVITYMON.F1
- sql12.ag.jobactivitymonitor.alljobs.f1
ms.assetid: 11f2182c-5f71-46f8-8d2b-74f0fc48f2d6
author: stevestein
ms.author: sstein
ms.openlocfilehash: f6f89d5448f0885c85229c2808ee6f85bf6fa071
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689251"
---
# <a name="job-activity-monitor"></a><span data-ttu-id="aee6a-102">作业活动监视器</span><span class="sxs-lookup"><span data-stu-id="aee6a-102">Job Activity Monitor</span></span>
  <span data-ttu-id="aee6a-103">使用此页可以查看 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业的当前活动。</span><span class="sxs-lookup"><span data-stu-id="aee6a-103">Use this page to view the current activity of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs.</span></span> <span data-ttu-id="aee6a-104">单击“筛选器”\*\*\*\* 可以限制显示的作业。</span><span class="sxs-lookup"><span data-stu-id="aee6a-104">Click **Filter** to limit the jobs displayed.</span></span> <span data-ttu-id="aee6a-105">“代理作业活动”\*\*\*\* 网格是只读的。</span><span class="sxs-lookup"><span data-stu-id="aee6a-105">The **Agent Job Activity** grid is read-only.</span></span> <span data-ttu-id="aee6a-106">单击列标题可以对网格进行排序。</span><span class="sxs-lookup"><span data-stu-id="aee6a-106">Click on the column headers to sort the grid.</span></span> <span data-ttu-id="aee6a-107">若要修改作业，请双击该作业以打开“作业属性”\*\*\*\* 对话框。</span><span class="sxs-lookup"><span data-stu-id="aee6a-107">To modify a job, double-click the job to open the **Job Properties** dialog box.</span></span> <span data-ttu-id="aee6a-108">右键单击网格中的作业，可以启动作业以运行其所有作业步骤，在特定作业步骤处启动作业，禁用或启用作业，刷新作业，删除作业，查看作业的历史记录以及查看作业属性。</span><span class="sxs-lookup"><span data-stu-id="aee6a-108">Right-click a job in the grid to start it running all job steps, start at a particular job step, disable or enable the job, refresh the job, delete the job, view the history of the job, or view the properties of the job.</span></span> <span data-ttu-id="aee6a-109">单击“刷新”\*\*\*\* 可以将网格更新为当前信息。</span><span class="sxs-lookup"><span data-stu-id="aee6a-109">Click **Refresh** to update the grid with current information.</span></span>  
  
## <a name="options"></a><span data-ttu-id="aee6a-110">选项</span><span class="sxs-lookup"><span data-stu-id="aee6a-110">Options</span></span>  
 <span data-ttu-id="aee6a-111">**名称**</span><span class="sxs-lookup"><span data-stu-id="aee6a-111">**Name**</span></span>  
 <span data-ttu-id="aee6a-112">作业的名称。</span><span class="sxs-lookup"><span data-stu-id="aee6a-112">Name of the job.</span></span>  
  
 <span data-ttu-id="aee6a-113">**已启用**</span><span class="sxs-lookup"><span data-stu-id="aee6a-113">**Enabled**</span></span>  
 <span data-ttu-id="aee6a-114">说明作业是已启用（“是”\*\*\*\*）还是未启用（“否”\*\*\*\*）。</span><span class="sxs-lookup"><span data-stu-id="aee6a-114">Whether the job is enabled (**yes**) or not enabled (**no**).</span></span>  
  
 <span data-ttu-id="aee6a-115">**状态** <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="aee6a-115">**Status** <sup>1</sup></span></span>  
 <span data-ttu-id="aee6a-116">作业的当前状态。</span><span class="sxs-lookup"><span data-stu-id="aee6a-116">Current status of the job.</span></span>  
  
 <span data-ttu-id="aee6a-117">**上次运行结果**</span><span class="sxs-lookup"><span data-stu-id="aee6a-117">**Last Run Outcome**</span></span>  
 <span data-ttu-id="aee6a-118">作业上次运行时的状态。</span><span class="sxs-lookup"><span data-stu-id="aee6a-118">Job status when last run.</span></span>  
  
 <span data-ttu-id="aee6a-119">**上次运行时间**</span><span class="sxs-lookup"><span data-stu-id="aee6a-119">**Last Run**</span></span>  
 <span data-ttu-id="aee6a-120">上次使用服务器的本地日期和时间运行作业的日期和时间。</span><span class="sxs-lookup"><span data-stu-id="aee6a-120">Date and time job was last run using the local date and time of the server.</span></span>  
  
 <span data-ttu-id="aee6a-121">**下一次运行** <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="aee6a-121">**Next Run** <sup>1</sup></span></span>  
 <span data-ttu-id="aee6a-122">计划下次使用服务器的本地日期和时间运行作业的日期和时间。</span><span class="sxs-lookup"><span data-stu-id="aee6a-122">Date and time the job is next scheduled to run using the local date and time of the server.</span></span>  
  
 <span data-ttu-id="aee6a-123">**类别**</span><span class="sxs-lookup"><span data-stu-id="aee6a-123">**Category**</span></span>  
 <span data-ttu-id="aee6a-124">分配给作业的作业类别。</span><span class="sxs-lookup"><span data-stu-id="aee6a-124">The job category assigned to the job.</span></span>  
  
 <span data-ttu-id="aee6a-125">**运行**</span><span class="sxs-lookup"><span data-stu-id="aee6a-125">**Runnable**</span></span>  
 <span data-ttu-id="aee6a-126">在作业可以运行时为“是”\*\*\*\*；在作业无法运行时为“否”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="aee6a-126">**Yes** if the job can be run; **No** if the job cannot be run.</span></span> <span data-ttu-id="aee6a-127">如果作业没有步骤或没有目标服务器，则无法运行该作业。</span><span class="sxs-lookup"><span data-stu-id="aee6a-127">A job is not runnable if it has no steps or if it has no target server.</span></span>  
  
 <span data-ttu-id="aee6a-128">**计划**</span><span class="sxs-lookup"><span data-stu-id="aee6a-128">**Scheduled**</span></span>  
 <span data-ttu-id="aee6a-129">在作业已分配给作业计划时为“是”\*\*\*\*；在作业没有计划时为“否”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="aee6a-129">**Yes** if the job is assigned to a job schedule; **No** if the job has no schedule.</span></span>  
  
 <span data-ttu-id="aee6a-130"><sup>1</sup>只有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sysadmin 固定服务器角色和服务器管理员组的成员才能看到此列中的值。</span><span class="sxs-lookup"><span data-stu-id="aee6a-130"><sup>1</sup>Only members of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sysadmin fixed server role and the server administrators group can see values in this column.</span></span> <span data-ttu-id="aee6a-131">SQLAgentOperatorRole 角色的成员不能看到此列中的值。</span><span class="sxs-lookup"><span data-stu-id="aee6a-131">Members of the SQLAgentOperatorRole role cannot see values in this column.</span></span>  
  
#### <a name="to-open-the-job-activity-monitor"></a><span data-ttu-id="aee6a-132">打开作业活动监视器</span><span class="sxs-lookup"><span data-stu-id="aee6a-132">To open the Job Activity Monitor</span></span>  
  
-   <span data-ttu-id="aee6a-133">在“对象资源管理器”\*\*\*\* 中，展开服务器，展开“SQL Server 代理”\*\*\*\*，右键单击“作业活动监视器”\*\*\*\*，再单击“查看作业活动”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="aee6a-133">In **Object Explorer**, expand your server, expand **SQL Server Agent**, right-click **Job Activity Monitor**, and then click **View Job Activity**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aee6a-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="aee6a-134">See Also</span></span>  
 [<span data-ttu-id="aee6a-135">监视作业活动</span><span class="sxs-lookup"><span data-stu-id="aee6a-135">Monitor Job Activity</span></span>](monitor-job-activity.md)  
  
  
