---
title: 删除作业 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- delete jobs
ms.assetid: bffb915e-bc84-4417-aa35-183243ca3312
author: stevestein
ms.author: sstein
ms.openlocfilehash: f66387a1334f91c29b8edddad293d76064430b39
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692098"
---
# <a name="delete-jobs"></a><span data-ttu-id="0e321-102">删除作业</span><span class="sxs-lookup"><span data-stu-id="0e321-102">Delete Jobs</span></span>
  <span data-ttu-id="0e321-103">作业是一系列由 SQL Server 代理按顺序执行的指定操作。</span><span class="sxs-lookup"><span data-stu-id="0e321-103">A job is a specified series of operations performed sequentially by SQL Server Agent.</span></span> <span data-ttu-id="0e321-104">默认情况下，执行完成时不删除作业。</span><span class="sxs-lookup"><span data-stu-id="0e321-104">By default, jobs are not deleted when execution finishes.</span></span> <span data-ttu-id="0e321-105">无论该作业是否成功，你都可以删除一个或多个 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业。</span><span class="sxs-lookup"><span data-stu-id="0e321-105">You can delete one or more [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs regardless of success or failure of the job.</span></span> <span data-ttu-id="0e321-106">还可以配置 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理以在作业成功、失败或完成时自动将其删除。</span><span class="sxs-lookup"><span data-stu-id="0e321-106">You can also configure [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to automatically delete jobs when they succeed, fail, or complete.</span></span>  
  
 <span data-ttu-id="0e321-107">默认情况下， **sysadmin**固定服务器角色的成员可以执行[sp_delete_job &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-job-transact-sql)系统存储过程来删除作业。</span><span class="sxs-lookup"><span data-stu-id="0e321-107">By default, members of the **sysadmin** fixed server role can execute the [sp_delete_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-job-transact-sql) system stored procedure to delete a job.</span></span> <span data-ttu-id="0e321-108">其他用户必须被授予 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb **数据库中下列** 代理固定数据库角色的权限之一：</span><span class="sxs-lookup"><span data-stu-id="0e321-108">Other users must be granted one of the following [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent fixed database roles in the **msdb** database:</span></span>  
  
-   <span data-ttu-id="0e321-109">**SQLAgentUserRole**</span><span class="sxs-lookup"><span data-stu-id="0e321-109">**SQLAgentUserRole**</span></span>  
  
-   <span data-ttu-id="0e321-110">**SQLAgentReaderRole**</span><span class="sxs-lookup"><span data-stu-id="0e321-110">**SQLAgentReaderRole**</span></span>  
  
-   <span data-ttu-id="0e321-111">**SQLAgentOperatorRole**</span><span class="sxs-lookup"><span data-stu-id="0e321-111">**SQLAgentOperatorRole**</span></span>  
  
 <span data-ttu-id="0e321-112">有关这些角色的权限的详细信息，请参阅 [SQL Server 代理固定数据库角色](sql-server-agent-fixed-database-roles.md)。</span><span class="sxs-lookup"><span data-stu-id="0e321-112">For details about the permissions of these roles, see [SQL Server Agent Fixed Database Roles](sql-server-agent-fixed-database-roles.md).</span></span>  
  
 <span data-ttu-id="0e321-113">**sysadmin** 固定服务器角色成员可以通过执行 **sp_delete_job** 删除任何作业。</span><span class="sxs-lookup"><span data-stu-id="0e321-113">Members of the **sysadmin** fixed server role can execute **sp_delete_job** to delete any job.</span></span> <span data-ttu-id="0e321-114">非 **sysadmin** 固定服务器角色成员的用户只能删除该用户所拥有的作业。</span><span class="sxs-lookup"><span data-stu-id="0e321-114">A user that is not a member of the **sysadmin** fixed server role can only delete jobs owned by that user.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="0e321-115">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="0e321-115">Related Tasks</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0e321-116">**说明**</span><span class="sxs-lookup"><span data-stu-id="0e321-116">**Description**</span></span>|<span data-ttu-id="0e321-117">**主题**</span><span class="sxs-lookup"><span data-stu-id="0e321-117">**Topic**</span></span>|  
|<span data-ttu-id="0e321-118">介绍如何删除一个或多个 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业。</span><span class="sxs-lookup"><span data-stu-id="0e321-118">Describes how to delete one or more [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs.</span></span>|[<span data-ttu-id="0e321-119">删除一个或多个作业</span><span class="sxs-lookup"><span data-stu-id="0e321-119">Delete One or More Jobs</span></span>](delete-one-or-more-jobs.md)|  
|<span data-ttu-id="0e321-120">介绍如何配置 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理，以在作业成功、失败或完成时自动将其删除。</span><span class="sxs-lookup"><span data-stu-id="0e321-120">Describes how to configure [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to automatically delete jobs when they succeed, fail, or complete.</span></span>|[<span data-ttu-id="0e321-121">自动删除作业</span><span class="sxs-lookup"><span data-stu-id="0e321-121">Automatically Delete a Job</span></span>](automatically-delete-a-job.md)|  
  
  
