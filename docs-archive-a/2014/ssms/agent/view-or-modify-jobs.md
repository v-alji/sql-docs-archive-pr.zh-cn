---
title: 查看或修改作业 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], modifying
- jobs [SQL Server Agent], viewing
- modifying jobs
- viewing jobs
- SQL Server Agent jobs, viewing
- SQL Server Agent jobs, modifying
- displaying jobs
ms.assetid: 57f649b8-190c-4304-abd7-7ca5297deab7
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5d0d731d25c20597be3ac84adfacd8973e4a51cd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689224"
---
# <a name="view-or-modify-jobs"></a><span data-ttu-id="15f96-102">查看或修改作业</span><span class="sxs-lookup"><span data-stu-id="15f96-102">View or Modify Jobs</span></span>
  <span data-ttu-id="15f96-103">您可以查看任何已创建的作业。</span><span class="sxs-lookup"><span data-stu-id="15f96-103">You can view any job you have created.</span></span> <span data-ttu-id="15f96-104">运行完一个作业后，还可以查看它的历史记录。</span><span class="sxs-lookup"><span data-stu-id="15f96-104">After you have run a job, you can also view its history.</span></span> <span data-ttu-id="15f96-105">查看作业历史记录使您可以查看作业何时运行、整个作业的状态以及作业中每步作业的状态。</span><span class="sxs-lookup"><span data-stu-id="15f96-105">Viewing a job's history allows you to see when the job ran, the status of the job as a whole, and the status of each job step in the job.</span></span> <span data-ttu-id="15f96-106">在作业成功完成后，您可以查看该作业过去是否曾失败，还可以查看作业每次运行时创建的输出内容。</span><span class="sxs-lookup"><span data-stu-id="15f96-106">You can see whether the job ever failed in the past, when the job last completed successfully, and what output the job created each time the job ran.</span></span> <span data-ttu-id="15f96-107">**sysadmin** 固定服务器角色的成员可以查看或修改所有人的作业。</span><span class="sxs-lookup"><span data-stu-id="15f96-107">Members of the **sysadmin** fixed server role can view or modify any job, regardless of the owner.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="15f96-108">作业至少必须运行一次，才会有作业历史记录。</span><span class="sxs-lookup"><span data-stu-id="15f96-108">A job must have been executed at least one time for there to be a job history.</span></span> <span data-ttu-id="15f96-109">您可以限制作业历史记录日志的总大小以及其中每个作业的大小。</span><span class="sxs-lookup"><span data-stu-id="15f96-109">You can limit the total size of the job history log and the size per job.</span></span>  
  
 <span data-ttu-id="15f96-110">最后，您还可以修改作业以满足新的要求。</span><span class="sxs-lookup"><span data-stu-id="15f96-110">Finally, you can modify a job to meet new requirements.</span></span> <span data-ttu-id="15f96-111">可以修改：</span><span class="sxs-lookup"><span data-stu-id="15f96-111">You can modify:</span></span>  
  
-   <span data-ttu-id="15f96-112">响应选项</span><span class="sxs-lookup"><span data-stu-id="15f96-112">Response options</span></span>  
  
-   <span data-ttu-id="15f96-113">计划</span><span class="sxs-lookup"><span data-stu-id="15f96-113">Schedules</span></span>  
  
-   <span data-ttu-id="15f96-114">作业步骤</span><span class="sxs-lookup"><span data-stu-id="15f96-114">Job steps</span></span>  
  
-   <span data-ttu-id="15f96-115">所有权</span><span class="sxs-lookup"><span data-stu-id="15f96-115">Ownership</span></span>  
  
-   <span data-ttu-id="15f96-116">作业类别</span><span class="sxs-lookup"><span data-stu-id="15f96-116">Job category</span></span>  
  
-   <span data-ttu-id="15f96-117">目标服务器（仅适用于多服务器作业）</span><span class="sxs-lookup"><span data-stu-id="15f96-117">Target servers (multiserver jobs only)</span></span>  
  
 <span data-ttu-id="15f96-118">为了确保对多服务器作业所做的更改生效，必须将这些更改发布到下载列表中，使目标服务器可以下载更新的作业。</span><span class="sxs-lookup"><span data-stu-id="15f96-118">To make sure that changes to multiserver jobs take effect, you must post the changes to the download list so that target servers can download the updated job.</span></span> <span data-ttu-id="15f96-119">若要确保目标服务器具有最新的作业定义，请在更新完多服务器作业后，按如下所示发布一条 INSERT 指令：</span><span class="sxs-lookup"><span data-stu-id="15f96-119">To ensure that target servers have the most current job definitions, post an INSERT instruction after you update the multiserver job as follows:</span></span>  
  
```  
EXECUTE sp_post_msx_operation 'INSERT', 'JOB', '<job id>'  
```  
  
 <span data-ttu-id="15f96-120">有关详细信息，请参阅[&#40;transact-sql&#41;sp_purge_jobhistory ](/sql/relational-databases/system-stored-procedures/sp-purge-jobhistory-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="15f96-120">For more information, see [sp_purge_jobhistory &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-purge-jobhistory-transact-sql).</span></span>  
  
 <span data-ttu-id="15f96-121">**sysadmin** 固定服务器角色的成员可以查看任何作业的定义或历史记录，还可以修改任何作业。</span><span class="sxs-lookup"><span data-stu-id="15f96-121">Members of the **sysadmin** fixed server role can view the definition or history of any job, and can modify any job.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="15f96-122">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="15f96-122">Related Tasks</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="15f96-123">**说明**</span><span class="sxs-lookup"><span data-stu-id="15f96-123">**Description**</span></span>|<span data-ttu-id="15f96-124">**主题**</span><span class="sxs-lookup"><span data-stu-id="15f96-124">**Topic**</span></span>|  
|<span data-ttu-id="15f96-125">说明如何查看 [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 代理作业。</span><span class="sxs-lookup"><span data-stu-id="15f96-125">Describes how to view [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent jobs.</span></span>|[<span data-ttu-id="15f96-126">View a Job</span><span class="sxs-lookup"><span data-stu-id="15f96-126">View a Job</span></span>](view-a-job.md)|  
|<span data-ttu-id="15f96-127">说明如何查看 [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 代理作业历史记录日志。</span><span class="sxs-lookup"><span data-stu-id="15f96-127">Describes how to view the [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent job history log.</span></span>|[<span data-ttu-id="15f96-128">查看作业历史记录</span><span class="sxs-lookup"><span data-stu-id="15f96-128">View the Job History</span></span>](view-the-job-history.md)|  
|<span data-ttu-id="15f96-129">说明如何删除 [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 代理作业历史记录日志的内容。</span><span class="sxs-lookup"><span data-stu-id="15f96-129">Describes how to delete the contents of the [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent job history log.</span></span>|[<span data-ttu-id="15f96-130">清除作业历史记录日志</span><span class="sxs-lookup"><span data-stu-id="15f96-130">Clear the Job History Log</span></span>](clear-the-job-history-log.md)|  
|<span data-ttu-id="15f96-131">说明如何设置 [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 代理作业历史记录日志的大小限制。</span><span class="sxs-lookup"><span data-stu-id="15f96-131">Describes how to set size limits for [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent job history logs.</span></span>|[<span data-ttu-id="15f96-132">调整作业历史记录日志的大小</span><span class="sxs-lookup"><span data-stu-id="15f96-132">Resize the Job History Log</span></span>](resize-the-job-history-log.md)|  
|<span data-ttu-id="15f96-133">说明如何更改 [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 代理作业的属性。</span><span class="sxs-lookup"><span data-stu-id="15f96-133">Describes how to change the properties of [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent jobs.</span></span>|[<span data-ttu-id="15f96-134">修改作业</span><span class="sxs-lookup"><span data-stu-id="15f96-134">Modify a Job</span></span>](modify-a-job.md)|  
  
## <a name="see-also"></a><span data-ttu-id="15f96-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="15f96-135">See Also</span></span>  
 [<span data-ttu-id="15f96-136">dbo.sysjobhistory &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="15f96-136">dbo.sysjobhistory &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-tables/dbo-sysjobhistory-transact-sql)  
  
  
