---
title: 系统级任务 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- system-level tasks [Reporting Services]
ms.assetid: 7023b388-40b2-4590-b227-115cf380a1e7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 98f9390664064cd293b80d094d65c903869bc709
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692665"
---
# <a name="system-level-tasks"></a><span data-ttu-id="a7dbe-102">系统级任务</span><span class="sxs-lookup"><span data-stu-id="a7dbe-102">System-Level Tasks</span></span>
  <span data-ttu-id="a7dbe-103">系统级任务是与应用于整个报表服务器站点的操作相关的权限的集合。</span><span class="sxs-lookup"><span data-stu-id="a7dbe-103">A system-level task is a collection of permissions that relate to operations that apply to the report server site as a whole.</span></span> [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="a7dbe-104">还包括应用于特定项的项级任务。</span><span class="sxs-lookup"><span data-stu-id="a7dbe-104">also includes item-level tasks that apply to specific items.</span></span> <span data-ttu-id="a7dbe-105">有关详细信息，请参阅 [项级任务](tasks-and-permissions-item-level-tasks.md)。</span><span class="sxs-lookup"><span data-stu-id="a7dbe-105">For more information, see [Item-Level Tasks](tasks-and-permissions-item-level-tasks.md).</span></span> <span data-ttu-id="a7dbe-106">有关任务和权限总体情况的详细信息，请参阅 [Tasks and Permissions](tasks-and-permissions.md)。</span><span class="sxs-lookup"><span data-stu-id="a7dbe-106">For more information about tasks and permissions in general, see [Tasks and Permissions](tasks-and-permissions.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a7dbe-107">如果以编程方式使用这些任务，则必须使用支持系统级任务的方法。</span><span class="sxs-lookup"><span data-stu-id="a7dbe-107">If you are working with these tasks programmatically, you must use methods that support system-level tasks.</span></span> <span data-ttu-id="a7dbe-108">有关详细信息，请参阅 <xref:ReportService2010.ReportingService2010.ListTasks%2A> 和 <xref:ReportService2010.ReportingService2010.ListRoles%2A>。</span><span class="sxs-lookup"><span data-stu-id="a7dbe-108">For more information, see <xref:ReportService2010.ReportingService2010.ListTasks%2A> and <xref:ReportService2010.ReportingService2010.ListRoles%2A>.</span></span>  
  
## <a name="permissions-in-system-level-tasks"></a><span data-ttu-id="a7dbe-109">系统级任务中的权限</span><span class="sxs-lookup"><span data-stu-id="a7dbe-109">Permissions in System-Level Tasks</span></span>  
 <span data-ttu-id="a7dbe-110">下表给出了各个系统任务的权限集合。</span><span class="sxs-lookup"><span data-stu-id="a7dbe-110">The following table identifies the collection of permissions for each system task.</span></span> <span data-ttu-id="a7dbe-111">所列出的权限仅供参考，目的是为每个任务的可用功能提供更准确的说明。</span><span class="sxs-lookup"><span data-stu-id="a7dbe-111">Permissions are listed for informational purposes only, to provide a more exact description of the functionality available through each task.</span></span>  
  
|<span data-ttu-id="a7dbe-112">任务</span><span class="sxs-lookup"><span data-stu-id="a7dbe-112">Task</span></span>|<span data-ttu-id="a7dbe-113">权限</span><span class="sxs-lookup"><span data-stu-id="a7dbe-113">Permissions</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="a7dbe-114">执行报表定义</span><span class="sxs-lookup"><span data-stu-id="a7dbe-114">Execute report definitions</span></span>|<span data-ttu-id="a7dbe-115">执行报表定义（权限和任务名称相同）</span><span class="sxs-lookup"><span data-stu-id="a7dbe-115">Execute Report Definitions (the permission and task name are the same)</span></span>|  
|<span data-ttu-id="a7dbe-116">生成事件</span><span class="sxs-lookup"><span data-stu-id="a7dbe-116">Generate events</span></span>|<span data-ttu-id="a7dbe-117">生成事件</span><span class="sxs-lookup"><span data-stu-id="a7dbe-117">Generate Events</span></span>|  
|<span data-ttu-id="a7dbe-118">管理作业</span><span class="sxs-lookup"><span data-stu-id="a7dbe-118">Manage jobs</span></span>|<span data-ttu-id="a7dbe-119">读取系统属性</span><span class="sxs-lookup"><span data-stu-id="a7dbe-119">Read System Properties</span></span><br /><br /> <span data-ttu-id="a7dbe-120">更新系统属性</span><span class="sxs-lookup"><span data-stu-id="a7dbe-120">Update System Properties</span></span>|  
|<span data-ttu-id="a7dbe-121">管理报表服务器属性</span><span class="sxs-lookup"><span data-stu-id="a7dbe-121">Manage report server properties</span></span>|<span data-ttu-id="a7dbe-122">读取系统属性</span><span class="sxs-lookup"><span data-stu-id="a7dbe-122">Read System Properties</span></span><br /><br /> <span data-ttu-id="a7dbe-123">更新系统属性</span><span class="sxs-lookup"><span data-stu-id="a7dbe-123">Update System Properties</span></span>|  
|<span data-ttu-id="a7dbe-124">管理角色</span><span class="sxs-lookup"><span data-stu-id="a7dbe-124">Manage roles</span></span>|<span data-ttu-id="a7dbe-125">创建角色</span><span class="sxs-lookup"><span data-stu-id="a7dbe-125">Create Roles</span></span><br /><br /> <span data-ttu-id="a7dbe-126">删除角色</span><span class="sxs-lookup"><span data-stu-id="a7dbe-126">Delete Roles</span></span><br /><br /> <span data-ttu-id="a7dbe-127">读取角色属性</span><span class="sxs-lookup"><span data-stu-id="a7dbe-127">Read Role Properties</span></span><br /><br /> <span data-ttu-id="a7dbe-128">更新角色属性</span><span class="sxs-lookup"><span data-stu-id="a7dbe-128">Update Role Properties</span></span>|  
|<span data-ttu-id="a7dbe-129">管理共享计划</span><span class="sxs-lookup"><span data-stu-id="a7dbe-129">Manage shared schedules</span></span>|<span data-ttu-id="a7dbe-130">创建计划</span><span class="sxs-lookup"><span data-stu-id="a7dbe-130">Create Schedules</span></span>|  
|<span data-ttu-id="a7dbe-131">管理报表服务器安全性</span><span class="sxs-lookup"><span data-stu-id="a7dbe-131">Manage report server security</span></span>|<span data-ttu-id="a7dbe-132">读取系统安全策略</span><span class="sxs-lookup"><span data-stu-id="a7dbe-132">Read System Security Policies</span></span><br /><br /> <span data-ttu-id="a7dbe-133">更新系统安全策略</span><span class="sxs-lookup"><span data-stu-id="a7dbe-133">Update System Security Policies</span></span>|  
|<span data-ttu-id="a7dbe-134">查看报表服务器属性</span><span class="sxs-lookup"><span data-stu-id="a7dbe-134">View report server properties</span></span>|<span data-ttu-id="a7dbe-135">读取系统属性</span><span class="sxs-lookup"><span data-stu-id="a7dbe-135">Read System Properties</span></span>|  
|<span data-ttu-id="a7dbe-136">查看共享计划</span><span class="sxs-lookup"><span data-stu-id="a7dbe-136">View shared schedules</span></span>|<span data-ttu-id="a7dbe-137">读取计划</span><span class="sxs-lookup"><span data-stu-id="a7dbe-137">Read Schedules</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a7dbe-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a7dbe-138">See Also</span></span>  
 [<span data-ttu-id="a7dbe-139">授予对本机模式报表服务器的权限</span><span class="sxs-lookup"><span data-stu-id="a7dbe-139">Granting Permissions on a Native Mode Report Server</span></span>](granting-permissions-on-a-native-mode-report-server.md)  
  
  
