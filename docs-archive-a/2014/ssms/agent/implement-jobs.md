---
title: 执行作业 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent]
- SQL Server Agent jobs
- SQL Server Agent jobs, about jobs
- jobs [SQL Server Agent], about jobs
ms.assetid: 69e06724-25c7-4fb3-8a5b-3d4596f21756
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1925b3113db8d7c57ac4344958c0247763cfd1b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577199"
---
# <a name="implement-jobs"></a><span data-ttu-id="6dadd-102">执行作业</span><span class="sxs-lookup"><span data-stu-id="6dadd-102">Implement Jobs</span></span>
  <span data-ttu-id="6dadd-103">您可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业来自动执行日常管理任务并反复运行它们，从而提高管理效率。</span><span class="sxs-lookup"><span data-stu-id="6dadd-103">You can use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs to automate routine administrative tasks and run them on a recurring basis, making administration more efficient.</span></span>  
  
 <span data-ttu-id="6dadd-104">作业是一系列由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理按顺序执行的指定操作。</span><span class="sxs-lookup"><span data-stu-id="6dadd-104">A job is a specified series of operations performed sequentially by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> <span data-ttu-id="6dadd-105">作业可以执行一系列活动，包括运行 [!INCLUDE[tsql](../../includes/tsql-md.md)] 脚本、命令行应用程序、Microsoft ActiveX 脚本、Integration Services 包、Analysis Services 命令和查询或复制任务。</span><span class="sxs-lookup"><span data-stu-id="6dadd-105">A job can perform a wide range of activities, including running [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts, command-line applications, Microsoft ActiveX scripts, Integration Services packages, Analysis Services commands and queries, or Replication tasks.</span></span> <span data-ttu-id="6dadd-106">作业可以运行重复任务或那些可计划的任务，它们可以通过生成警报来自动通知用户作业状态，从而极大地简化了 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理。</span><span class="sxs-lookup"><span data-stu-id="6dadd-106">Jobs can run repetitive tasks or those that can be scheduled, and they can automatically notify users of job status by generating alerts, thereby greatly simplifying [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] administration.</span></span>  
  
 <span data-ttu-id="6dadd-107">可以手动运行作业，也可以将作业配置为根据计划或响应警报来运行。</span><span class="sxs-lookup"><span data-stu-id="6dadd-107">You can run a job manually, or you can configure it to run according to a schedule or in response to alerts.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="6dadd-108">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="6dadd-108">Related Tasks</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6dadd-109">**说明**</span><span class="sxs-lookup"><span data-stu-id="6dadd-109">**Description**</span></span>|<span data-ttu-id="6dadd-110">**主题**</span><span class="sxs-lookup"><span data-stu-id="6dadd-110">**Topic**</span></span>|  
|<span data-ttu-id="6dadd-111">包含有关创建作业和分配所有权的信息。</span><span class="sxs-lookup"><span data-stu-id="6dadd-111">Contains information about creating jobs and assigning ownership.</span></span>|[<span data-ttu-id="6dadd-112">创建作业</span><span class="sxs-lookup"><span data-stu-id="6dadd-112">Create Jobs</span></span>](create-jobs.md)|  
|<span data-ttu-id="6dadd-113">包含有关将作业组织到目录的信息。</span><span class="sxs-lookup"><span data-stu-id="6dadd-113">Contains information about organizing jobs into categories.</span></span>|[<span data-ttu-id="6dadd-114">组织作业</span><span class="sxs-lookup"><span data-stu-id="6dadd-114">Organize Jobs</span></span>](organize-jobs.md)|  
|<span data-ttu-id="6dadd-115">说明可以创建的各种作业步骤以及如何管理它们。</span><span class="sxs-lookup"><span data-stu-id="6dadd-115">Contains information about the different kinds of job steps you can create and how to manage them.</span></span>|[<span data-ttu-id="6dadd-116">管理作业步骤</span><span class="sxs-lookup"><span data-stu-id="6dadd-116">Manage Job Steps</span></span>](manage-job-steps.md)|  
|<span data-ttu-id="6dadd-117">说明如何定义作业的开始运行时间和运行频率。</span><span class="sxs-lookup"><span data-stu-id="6dadd-117">Contains information about how to define when jobs start running and how often they should run.</span></span>|[<span data-ttu-id="6dadd-118">创建计划并将计划附加到作业</span><span class="sxs-lookup"><span data-stu-id="6dadd-118">Create and Attach Schedules to Jobs</span></span>](create-and-attach-schedules-to-jobs.md)|  
|<span data-ttu-id="6dadd-119">介绍手动运行作业（不根据计划）。</span><span class="sxs-lookup"><span data-stu-id="6dadd-119">Contains information about manually running jobs (without a schedule).</span></span>|[<span data-ttu-id="6dadd-120">运行作业</span><span class="sxs-lookup"><span data-stu-id="6dadd-120">Run Jobs</span></span>](run-jobs.md)|  
|<span data-ttu-id="6dadd-121">说明如何将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理配置为响应作业。</span><span class="sxs-lookup"><span data-stu-id="6dadd-121">Contains information about how you can configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to respond to jobs.</span></span> <span data-ttu-id="6dadd-122">例如，可以将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理配置为作业完成时通知管理员。</span><span class="sxs-lookup"><span data-stu-id="6dadd-122">For example, you can configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to notify administrators when jobs are finished.</span></span>|[<span data-ttu-id="6dadd-123">指定作业响应</span><span class="sxs-lookup"><span data-stu-id="6dadd-123">Specify Job Responses</span></span>](specify-job-responses.md)|  
|<span data-ttu-id="6dadd-124">包含有关如何查看现有作业、作业执行后的历史记录以及如何修改现有作业的信息。</span><span class="sxs-lookup"><span data-stu-id="6dadd-124">Contains information about how to view existing jobs, their history once executes, and how to modify them.</span></span>|[<span data-ttu-id="6dadd-125">查看或修改作业</span><span class="sxs-lookup"><span data-stu-id="6dadd-125">View or Modify Jobs</span></span>](view-or-modify-jobs.md)|  
|<span data-ttu-id="6dadd-126">包含有关如何删除作业的信息。</span><span class="sxs-lookup"><span data-stu-id="6dadd-126">Contains information about how to delete jobs.</span></span>|[<span data-ttu-id="6dadd-127">删除作业</span><span class="sxs-lookup"><span data-stu-id="6dadd-127">Delete Jobs</span></span>](delete-jobs.md)|  
  
## <a name="see-also"></a><span data-ttu-id="6dadd-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6dadd-128">See Also</span></span>  
 [<span data-ttu-id="6dadd-129">实现 SQL Server 代理安全性</span><span class="sxs-lookup"><span data-stu-id="6dadd-129">Implement SQL Server Agent Security</span></span>](implement-sql-server-agent-security.md)  
  
  
