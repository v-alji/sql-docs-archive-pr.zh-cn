---
title: 任务和权限 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- permissions [Reporting Services], tasks
- role-based security [Reporting Services], permissions
- security [Reporting Services], tasks
- security [Reporting Services], permissions
- role-based security [Reporting Services], tasks
- predefined tasks [Reporting Services]
- tasks [Reporting Services]
ms.assetid: d7ff90b5-b976-4270-b9ad-9d7b801d8263
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 01cbf00850c5dd57e7ca1575a1a0cb826c009714
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692661"
---
# <a name="tasks-and-permissions"></a><span data-ttu-id="96230-102">任务和权限</span><span class="sxs-lookup"><span data-stu-id="96230-102">Tasks and Permissions</span></span>
  <span data-ttu-id="96230-103">在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]中，“任务”  是指用户或管理员可以执行的操作。</span><span class="sxs-lookup"><span data-stu-id="96230-103">In [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], *tasks* are actions that a user or administrator can perform.</span></span> <span data-ttu-id="96230-104">任务是预定义的。</span><span class="sxs-lookup"><span data-stu-id="96230-104">Tasks are predefined.</span></span> <span data-ttu-id="96230-105">您不能创建自定义任务，也不能以编程方式或通过工具修改所提供的任务。</span><span class="sxs-lookup"><span data-stu-id="96230-105">You cannot create custom tasks or modify the ones provided either programmatically or through a tool.</span></span> <span data-ttu-id="96230-106">总共有二十五个任务。</span><span class="sxs-lookup"><span data-stu-id="96230-106">There are twenty-five tasks in all.</span></span> <span data-ttu-id="96230-107">这些任务组成了基于角色的安全性中可用的完整操作集。</span><span class="sxs-lookup"><span data-stu-id="96230-107">These tasks comprise the entire set of operations that are available in role-based security.</span></span> <span data-ttu-id="96230-108">部分任务示例包括：“查看报表”、“管理报表”和“管理报表服务器属性”。</span><span class="sxs-lookup"><span data-stu-id="96230-108">Some examples of tasks include "View reports," "Manage reports," and "Manage report server properties."</span></span>  
  
 <span data-ttu-id="96230-109">每个任务由一组权限构成，这些权限也是预定义的。</span><span class="sxs-lookup"><span data-stu-id="96230-109">Each task consists of a set of permissions, which are also predefined.</span></span> <span data-ttu-id="96230-110">例如，“管理文件夹”任务包含创建和删除文件夹以及查看和更新文件夹属性等权限。</span><span class="sxs-lookup"><span data-stu-id="96230-110">For example, the "Manage folders" task contains permissions to create and delete folders and view and update folder properties.</span></span> <span data-ttu-id="96230-111">对每个任务的权限进行了说明，以便更为准确地描述每个任务。</span><span class="sxs-lookup"><span data-stu-id="96230-111">Permissions for each task are documented to provide a more exact description of each task.</span></span> <span data-ttu-id="96230-112">不能直接对权限进行交互操作或者在角色分配中指定权限。</span><span class="sxs-lookup"><span data-stu-id="96230-112">It is not possible to interact with permissions directly or to specify them in role assignments.</span></span> <span data-ttu-id="96230-113">用户的权限是通过角色定义中包括的任务间接授予的。</span><span class="sxs-lookup"><span data-stu-id="96230-113">Users are granted permissions indirectly through the tasks that are included in role definitions.</span></span>  
  
 <span data-ttu-id="96230-114">只有当任务是角色的一部分并且该角色包含在角色分配中时，才能执行该任务。</span><span class="sxs-lookup"><span data-stu-id="96230-114">Tasks can be performed only if they are part of a role and that role is included in a role assignment.</span></span> <span data-ttu-id="96230-115">因此，如果角色中不包括“查看模型”任务，或者角色分配中不包括该角色，则用户就不能查看报表模型。</span><span class="sxs-lookup"><span data-stu-id="96230-115">Thus, if the View Models task is not included in a role, or that role is not included in a role assignment, users cannot view report models.</span></span> <span data-ttu-id="96230-116">下图显示了如何将权限组合到任务中，以及如何将任务组合到角色中以将角色用于特定的角色分配。</span><span class="sxs-lookup"><span data-stu-id="96230-116">The following diagram shows how permissions are combined into tasks, and how tasks are combined into roles that can be used for specific role assignments.</span></span>  
  
 <span data-ttu-id="96230-117">![权限和任务关系图](../media/report-securityobjects.gif "权限和任务关系图")</span><span class="sxs-lookup"><span data-stu-id="96230-117">![Permissions and task diagram](../media/report-securityobjects.gif "Permissions and task diagram")</span></span>  
<span data-ttu-id="96230-118">权限和任务关系图</span><span class="sxs-lookup"><span data-stu-id="96230-118">Permissions and task diagram</span></span>  
  
## <a name="system-and-item-level-tasks"></a><span data-ttu-id="96230-119">系统级任务和项级任务</span><span class="sxs-lookup"><span data-stu-id="96230-119">System and Item Level Tasks</span></span>  
 <span data-ttu-id="96230-120">任务分为两类：系统级任务和项级任务。</span><span class="sxs-lookup"><span data-stu-id="96230-120">Tasks fall into two categories: system level and item level.</span></span> <span data-ttu-id="96230-121">一个角色只能包含单个类别中的任务。</span><span class="sxs-lookup"><span data-stu-id="96230-121">A role can include tasks only from a single category.</span></span> <span data-ttu-id="96230-122">下表对每一类别的任务进行了说明。</span><span class="sxs-lookup"><span data-stu-id="96230-122">The following table describes each category of tasks.</span></span>  
  
|<span data-ttu-id="96230-123">类别</span><span class="sxs-lookup"><span data-stu-id="96230-123">Category</span></span>|<span data-ttu-id="96230-124">说明</span><span class="sxs-lookup"><span data-stu-id="96230-124">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="96230-125">项级任务</span><span class="sxs-lookup"><span data-stu-id="96230-125">Item-Level Tasks</span></span>](tasks-and-permissions-item-level-tasks.md)|<span data-ttu-id="96230-126">对报表服务器管理的项（例如文件夹、报表、报表模型和资源）执行的操作。</span><span class="sxs-lookup"><span data-stu-id="96230-126">Actions that are performed on items managed by a report server, such as folders, reports, report models, and resources.</span></span><br /><br /> <span data-ttu-id="96230-127">项级任务的作用域为报表服务器文件夹命名空间。</span><span class="sxs-lookup"><span data-stu-id="96230-127">Item-level tasks are scoped to the report server folder namespace.</span></span> <span data-ttu-id="96230-128">通过报表服务器上的文件夹或通过 URL 访问的项都受到包含项级任务的角色分配的保护。</span><span class="sxs-lookup"><span data-stu-id="96230-128">All items that you access through the folders on a report server or through URL access are secured by role assignments that include item-level tasks.</span></span>|  
|[<span data-ttu-id="96230-129">系统级任务</span><span class="sxs-lookup"><span data-stu-id="96230-129">System-Level Tasks</span></span>](tasks-and-permissions-system-level-tasks.md)|<span data-ttu-id="96230-130">在系统级执行的操作，例如，管理可用于多个项的作业或共享计划。</span><span class="sxs-lookup"><span data-stu-id="96230-130">Actions that are performed at the system level, such as managing jobs or shared schedules that can be used with many items.</span></span> <span data-ttu-id="96230-131">系统级任务的作用域扩展到报表服务器文件夹命名空间之外。</span><span class="sxs-lookup"><span data-stu-id="96230-131">System-level tasks are scoped outside of the report server folder namespace.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="96230-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="96230-132">See Also</span></span>  
 <span data-ttu-id="96230-133">[角色定义](role-definitions.md) </span><span class="sxs-lookup"><span data-stu-id="96230-133">[Role Definitions](role-definitions.md) </span></span>  
 <span data-ttu-id="96230-134">[预定义角色](role-definitions-predefined-roles.md) </span><span class="sxs-lookup"><span data-stu-id="96230-134">[Predefined Roles](role-definitions-predefined-roles.md) </span></span>  
 [<span data-ttu-id="96230-135">授予对本机模式报表服务器的权限</span><span class="sxs-lookup"><span data-stu-id="96230-135">Granting Permissions on a Native Mode Report Server</span></span>](granting-permissions-on-a-native-mode-report-server.md)  
  
  
