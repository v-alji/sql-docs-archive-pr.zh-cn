---
title: 创建作业 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], creating
- SQL Server Agent jobs, creating
ms.assetid: 465fb7fc-7622-4252-a178-ea51691c935b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 706b9348eed5b190f99543a74e7019dc1bde5978
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689258"
---
# <a name="create-jobs"></a><span data-ttu-id="abb6a-102">创建作业</span><span class="sxs-lookup"><span data-stu-id="abb6a-102">Create Jobs</span></span>
  <span data-ttu-id="abb6a-103">作业是一系列由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理按顺序执行的指定操作。</span><span class="sxs-lookup"><span data-stu-id="abb6a-103">A job is a specified series of operations performed sequentially by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> <span data-ttu-id="abb6a-104">一个作业可以执行各种类型的活动，包括运行 [!INCLUDE[tsql](../../includes/tsql-md.md)] 脚本、命令提示符应用程序、Microsoft ActiveX 脚本、Integration Services 包、Analysis Services 命令和查询或复制任务。</span><span class="sxs-lookup"><span data-stu-id="abb6a-104">A job can perform a wide range of activities, including running [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts, command prompt applications, Microsoft ActiveX scripts, Integration Services packages, Analysis Services commands and queries, or Replication tasks.</span></span> <span data-ttu-id="abb6a-105">作业可以运行重复或可计划的任务，然后它们可以通过生成警报来自动通知用户作业状态，从而极大地简化了 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理。</span><span class="sxs-lookup"><span data-stu-id="abb6a-105">Jobs can run repetitive or schedulable tasks, and they can automatically notify users of job status by generating alerts, thereby greatly simplifying [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] administration.</span></span>  
  
 <span data-ttu-id="abb6a-106">若要创建作业，用户必须是某个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理固定数据库角色或 **sysadmin** 固定服务器角色的成员。</span><span class="sxs-lookup"><span data-stu-id="abb6a-106">To create a job, a user must be a member of one of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent fixed database roles or the **sysadmin** fixed server role.</span></span> <span data-ttu-id="abb6a-107">作业只能由其所有者或 **sysadmin** 角色的成员进行编辑。</span><span class="sxs-lookup"><span data-stu-id="abb6a-107">A job can be edited only by its owner or members of the **sysadmin** role.</span></span> <span data-ttu-id="abb6a-108">**sysadmin** 角色的成员可以将作业所有权分配给其他用户，并且他们可以运行所有人的作业。</span><span class="sxs-lookup"><span data-stu-id="abb6a-108">Members of the **sysadmin** role can assign job ownership to other users, and they can run any job, regardless of the job owner.</span></span> <span data-ttu-id="abb6a-109">有关 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理的固定数据库角色的详细信息，请参阅 [SQL Server 代理固定数据库角色](sql-server-agent-fixed-database-roles.md)。</span><span class="sxs-lookup"><span data-stu-id="abb6a-109">For more information about the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent fixed database roles, see [SQL Server Agent Fixed Database Roles](sql-server-agent-fixed-database-roles.md).</span></span>  
  
 <span data-ttu-id="abb6a-110">可以编写作业，使其运行在企业内的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 本地实例或多个实例上。</span><span class="sxs-lookup"><span data-stu-id="abb6a-110">Jobs can be written to run on the local instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or on multiple instances across an enterprise.</span></span> <span data-ttu-id="abb6a-111">必须设置至少一台主服务器以及一台或多台目标服务器，才能在多台服务器上运行作业。</span><span class="sxs-lookup"><span data-stu-id="abb6a-111">To run jobs on multiple servers, you must set up at least one master server and one or more target servers.</span></span> <span data-ttu-id="abb6a-112">有关主服务器和目标服务器的详细信息，请参阅 [企业范围的自动化管理](automated-administration-across-an-enterprise.md)</span><span class="sxs-lookup"><span data-stu-id="abb6a-112">For more information about master and target servers, see [Automated Administration Across an Enterprise](automated-administration-across-an-enterprise.md)</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="abb6a-113">代理在作业历史记录中记录作业和作业步骤信息。</span><span class="sxs-lookup"><span data-stu-id="abb6a-113">Agent records job and job step information in the job history.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="abb6a-114">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="abb6a-114">Related Tasks</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="abb6a-115">**说明**</span><span class="sxs-lookup"><span data-stu-id="abb6a-115">**Description**</span></span>|<span data-ttu-id="abb6a-116">**主题**</span><span class="sxs-lookup"><span data-stu-id="abb6a-116">**Topic**</span></span>|  
|<span data-ttu-id="abb6a-117">介绍如何创建 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业。</span><span class="sxs-lookup"><span data-stu-id="abb6a-117">Describes how to create a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job.</span></span>|[<span data-ttu-id="abb6a-118">创建作业</span><span class="sxs-lookup"><span data-stu-id="abb6a-118">Create a Job</span></span>](create-a-job.md)|  
|<span data-ttu-id="abb6a-119">介绍如何将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业的所有权重新指派给另一用户。</span><span class="sxs-lookup"><span data-stu-id="abb6a-119">Describes how to reassign ownership of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs to another user.</span></span>|[<span data-ttu-id="abb6a-120">将作业所有权授予其他人</span><span class="sxs-lookup"><span data-stu-id="abb6a-120">Give Others Ownership of a Job</span></span>](give-others-ownership-of-a-job.md)|  
|<span data-ttu-id="abb6a-121">介绍如何设置 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业历史记录日志。</span><span class="sxs-lookup"><span data-stu-id="abb6a-121">Describes how to set up the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job history log.</span></span>|[<span data-ttu-id="abb6a-122">Set Up the Job History Log</span><span class="sxs-lookup"><span data-stu-id="abb6a-122">Set Up the Job History Log</span></span>](set-up-the-job-history-log.md)|  
  
## <a name="see-also"></a><span data-ttu-id="abb6a-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="abb6a-123">See Also</span></span>  
 <span data-ttu-id="abb6a-124">[管理作业步骤](manage-job-steps.md) </span><span class="sxs-lookup"><span data-stu-id="abb6a-124">[Manage Job Steps](manage-job-steps.md) </span></span>  
 <span data-ttu-id="abb6a-125">[企业范围的自动化管理](automated-administration-across-an-enterprise.md) </span><span class="sxs-lookup"><span data-stu-id="abb6a-125">[Automated Administration Across an Enterprise](automated-administration-across-an-enterprise.md) </span></span>  
 <span data-ttu-id="abb6a-126">[创建计划并将计划附加到作业](create-and-attach-schedules-to-jobs.md) </span><span class="sxs-lookup"><span data-stu-id="abb6a-126">[Create and Attach Schedules to Jobs](create-and-attach-schedules-to-jobs.md) </span></span>  
 <span data-ttu-id="abb6a-127">[运行作业](run-jobs.md) </span><span class="sxs-lookup"><span data-stu-id="abb6a-127">[Run Jobs](run-jobs.md) </span></span>  
 [<span data-ttu-id="abb6a-128">查看或修改作业</span><span class="sxs-lookup"><span data-stu-id="abb6a-128">View or Modify Jobs</span></span>](view-or-modify-jobs.md)  
  
  
