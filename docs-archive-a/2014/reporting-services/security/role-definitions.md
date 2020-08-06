---
title: 角色定义 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- roles [Reporting Services], creating
- roles [Reporting Services], security
- security [Reporting Services], role definitions
- role-based security [Reporting Services], role definitions
ms.assetid: d1b8dbf0-4462-402e-92dd-0e4835002b6e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 76fcb7f329f6afae890581e045ec64182972bf35
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587178"
---
# <a name="role-definitions"></a><span data-ttu-id="483e4-102">角色定义</span><span class="sxs-lookup"><span data-stu-id="483e4-102">Role Definitions</span></span>
  <span data-ttu-id="483e4-103">在中 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ， *role \* \* 定义*是一组任务的命名集合，用于定义 Report Server 上可用的操作。</span><span class="sxs-lookup"><span data-stu-id="483e4-103">In [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], a *role\*\*definition* is a named collection of tasks that define the operations available on a report server.</span></span> <span data-ttu-id="483e4-104">角色定义提供了报表服务器用于增强安全性的规则。</span><span class="sxs-lookup"><span data-stu-id="483e4-104">Role definitions provide the rules used by the report server to enforce security.</span></span> <span data-ttu-id="483e4-105">当用户尝试执行任务（如发布报表）时，报表服务器将检查用户的角色分配以确定该任务是否包含在其角色定义中。</span><span class="sxs-lookup"><span data-stu-id="483e4-105">When a user attempts to perform a task, such as publishing a report, the report server checks the user's role assignment to determine whether the task is included in their role definition.</span></span> <span data-ttu-id="483e4-106">如果试图执行的任务包括在角色定义中，则提交请求。</span><span class="sxs-lookup"><span data-stu-id="483e4-106">If the task is included in the role definition, the request is submitted.</span></span>  
  
## <a name="using-roles-to-authorize-access-to-a-report-server"></a><span data-ttu-id="483e4-107">使用角色授予对报表服务器的访问权限</span><span class="sxs-lookup"><span data-stu-id="483e4-107">Using Roles to Authorize Access to a Report Server</span></span>  
 <span data-ttu-id="483e4-108">角色只有在角色分配中使用时才有效。</span><span class="sxs-lookup"><span data-stu-id="483e4-108">A role becomes operative only when it is used in a role assignment.</span></span> <span data-ttu-id="483e4-109">有关角色如何提供安全性的详细信息，请参阅 [角色分配](role-assignments.md)。</span><span class="sxs-lookup"><span data-stu-id="483e4-109">For more information about how roles provide security, see [Role Assignments](role-assignments.md).</span></span>  
  
## <a name="types-of-role-definitions"></a><span data-ttu-id="483e4-110">角色定义的类型</span><span class="sxs-lookup"><span data-stu-id="483e4-110">Types of Role Definitions</span></span>  
 <span data-ttu-id="483e4-111">角色定义既可以是项级定义也可以是系统级定义。</span><span class="sxs-lookup"><span data-stu-id="483e4-111">Role definitions are either item-level or system-level definitions.</span></span> <span data-ttu-id="483e4-112">“项级角色定义”\*\* 说明了与在报表服务器上存储和管理的项（如报表、文件夹和模型）相关的任务。</span><span class="sxs-lookup"><span data-stu-id="483e4-112">An *item-level role definition* describes tasks that relate to items that are stored and managed on a report server, such as reports, folder, and models.</span></span> <span data-ttu-id="483e4-113">可以包含在项级角色定义中的任务如：管理报表、查看文件夹和管理单独的订阅。</span><span class="sxs-lookup"><span data-stu-id="483e4-113">Manage reports, View folders, and Manage individual subscriptions are examples of tasks you can include in an item-level role definitions.</span></span> <span data-ttu-id="483e4-114">“系统角色定义” \*\* 包含应用于整个站点的任务。</span><span class="sxs-lookup"><span data-stu-id="483e4-114">A *system role definition* includes tasks that apply to the site as a whole.</span></span> <span data-ttu-id="483e4-115">可以包含在系统角色中的任务如：查看报表服务器属性。</span><span class="sxs-lookup"><span data-stu-id="483e4-115">View report server properties is an example of a task you might include in a system role.</span></span>  
  
## <a name="predefined-roles"></a><span data-ttu-id="483e4-116">预定义角色</span><span class="sxs-lookup"><span data-stu-id="483e4-116">Predefined Roles</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="483e4-117">包含与不同级别的用户交互所对应的预定义角色。</span><span class="sxs-lookup"><span data-stu-id="483e4-117">includes predefined roles that correspond to different levels of user interaction.</span></span> <span data-ttu-id="483e4-118">下面的列表包含可以使用的预定义角色：</span><span class="sxs-lookup"><span data-stu-id="483e4-118">The following list contains the predefined roles you can use:</span></span>  
  
-   <span data-ttu-id="483e4-119">为访问报表服务器内容创建角色分配时可以使用以下项级角色定义：内容管理员、发布者、浏览者、报表生成者和我的报表。</span><span class="sxs-lookup"><span data-stu-id="483e4-119">Content Manager, Publisher, Browser, Report Builder, and My Reports are item-level role definitions that you can use when creating role assignments for accessing report server content.</span></span>  
  
-   <span data-ttu-id="483e4-120">授予对站点操作的访问权限时可以使用以下系统级角色定义：系统管理员和系统用户。</span><span class="sxs-lookup"><span data-stu-id="483e4-120">System Administrator and System User are system-level role definitions that you can use to authorize access to site operations.</span></span>  
  
 <span data-ttu-id="483e4-121">有关详细信息，请参阅 [预定义角色](role-definitions-predefined-roles.md)。</span><span class="sxs-lookup"><span data-stu-id="483e4-121">For more information, see [Predefined Roles](role-definitions-predefined-roles.md).</span></span>  
  
## <a name="creating-a-role-definition"></a><span data-ttu-id="483e4-122">创建角色定义</span><span class="sxs-lookup"><span data-stu-id="483e4-122">Creating a Role Definition</span></span>  
 <span data-ttu-id="483e4-123">若要创建角色，请使用 Management Studio 指定名称及其所包含的任务。</span><span class="sxs-lookup"><span data-stu-id="483e4-123">To create a role, you use Management Studio to specify a name and tasks it contains.</span></span> <span data-ttu-id="483e4-124">必须为项和系统任务创建不同的角色定义。</span><span class="sxs-lookup"><span data-stu-id="483e4-124">You must create separate role definition for item and system tasks.</span></span> <span data-ttu-id="483e4-125">角色可以包含项级任务或系统级任务，但不能同时包含这两种任务。</span><span class="sxs-lookup"><span data-stu-id="483e4-125">Roles can include item-level tasks or system-level tasks, but not both.</span></span> <span data-ttu-id="483e4-126">创建角色定义时，需要提供名称并为角色定义选择一组任务。</span><span class="sxs-lookup"><span data-stu-id="483e4-126">Creating a role definition consists of providing a name and choosing a set of tasks for the definition.</span></span> <span data-ttu-id="483e4-127">若要创建角色定义，您必须具有相应的权限。</span><span class="sxs-lookup"><span data-stu-id="483e4-127">To create a role definition, you must have permission to do so.</span></span> <span data-ttu-id="483e4-128">“设置各项的安全性”任务可以提供这些权限。</span><span class="sxs-lookup"><span data-stu-id="483e4-128">The "Set security for individual items" task provides these permissions.</span></span> <span data-ttu-id="483e4-129">默认情况下，分配了预定义的 **“内容管理员”** 角色的管理员和用户可以执行此任务。</span><span class="sxs-lookup"><span data-stu-id="483e4-129">By default, administrators and users who are assigned to the predefined **Content Manager** role can perform this task.</span></span>  
  
 <span data-ttu-id="483e4-130">角色必须拥有唯一的名称。</span><span class="sxs-lookup"><span data-stu-id="483e4-130">A role must have a unique name.</span></span> <span data-ttu-id="483e4-131">角色定义中至少必须包含一个任务才会有效。</span><span class="sxs-lookup"><span data-stu-id="483e4-131">To be valid, the role definition must contain at least one task.</span></span> <span data-ttu-id="483e4-132">有关详细信息，请参阅 [Tasks and Permissions](tasks-and-permissions.md)。</span><span class="sxs-lookup"><span data-stu-id="483e4-132">For more information, see [Tasks and Permissions](tasks-and-permissions.md).</span></span>  
  
 <span data-ttu-id="483e4-133">若要创建角色定义，请使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="483e4-133">To create a role definition, use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="483e4-134">有关详细信息，请参阅 [创建、删除或修改角色 (Management Studio)](role-definitions-create-delete-or-modify.md)。</span><span class="sxs-lookup"><span data-stu-id="483e4-134">For more information, see [Create, Delete, or Modify a Role &#40;Management Studio&#41;](role-definitions-create-delete-or-modify.md).</span></span>  
  
 <span data-ttu-id="483e4-135">在创建角色定义后，可以通过在角色分配中选择该角色定义来使用它。</span><span class="sxs-lookup"><span data-stu-id="483e4-135">After you create a role definition, you can use it by selecting it in a role assignment.</span></span> <span data-ttu-id="483e4-136">有关详细信息，请参阅 [授予用户对报表服务器的访问权限（报表管理器）](grant-user-access-to-a-report-server.md)。</span><span class="sxs-lookup"><span data-stu-id="483e4-136">For more information, see [Grant User Access to a Report Server &#40;Report Manager&#41;](grant-user-access-to-a-report-server.md).</span></span>  
  
## <a name="customize-or-delete-a-role-definition"></a><span data-ttu-id="483e4-137">修改或删除角色定义</span><span class="sxs-lookup"><span data-stu-id="483e4-137">Customize or Delete a Role Definition</span></span>  
 <span data-ttu-id="483e4-138">可以修改预定义角色，也可以用自定义角色替换它们。</span><span class="sxs-lookup"><span data-stu-id="483e4-138">Predefined roles can be modified or replaced with custom roles.</span></span> <span data-ttu-id="483e4-139">若要修改角色，请向角色定义中添加任务或从角色定义中删除任务。</span><span class="sxs-lookup"><span data-stu-id="483e4-139">To modify a role, you add to or remove tasks from the role definition.</span></span> <span data-ttu-id="483e4-140">不能对角色重命名。</span><span class="sxs-lookup"><span data-stu-id="483e4-140">You cannot rename a role.</span></span> <span data-ttu-id="483e4-141">您所进行的任何更改都会立即应用到包含该角色定义的所有角色分配中。</span><span class="sxs-lookup"><span data-stu-id="483e4-141">Any changes you make are applied immediately to all role assignments that include the role definition.</span></span>  
  
 <span data-ttu-id="483e4-142">如果不再使用该角色定义，可以删除它。</span><span class="sxs-lookup"><span data-stu-id="483e4-142">You can delete a role definition if you are no longer using it.</span></span> <span data-ttu-id="483e4-143">只要启用了“我的报表”功能，就不能删除为此功能选择的角色定义。</span><span class="sxs-lookup"><span data-stu-id="483e4-143">You cannot delete the role definition that is selected for the My Reports feature as long as that feature is enabled.</span></span> <span data-ttu-id="483e4-144">在删除用于“我的报表”功能的角色定义之前，首先必须禁用该功能，或为该功能另选一个角色定义以供使用。</span><span class="sxs-lookup"><span data-stu-id="483e4-144">Before you can delete the role definition used for My Reports, you must first disable the feature or select a different role definition to use with it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="483e4-145">另请参阅</span><span class="sxs-lookup"><span data-stu-id="483e4-145">See Also</span></span>  
 <span data-ttu-id="483e4-146">[任务和权限](tasks-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="483e4-146">[Tasks and Permissions](tasks-and-permissions.md) </span></span>  
 <span data-ttu-id="483e4-147">[授予对本机模式报表服务器的权限](granting-permissions-on-a-native-mode-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="483e4-147">[Granting Permissions on a Native Mode Report Server](granting-permissions-on-a-native-mode-report-server.md) </span></span>  
 <span data-ttu-id="483e4-148">[创建、删除或修改角色 &#40;Management Studio&#41;](role-definitions-create-delete-or-modify.md) </span><span class="sxs-lookup"><span data-stu-id="483e4-148">[Create, Delete, or Modify a Role &#40;Management Studio&#41;](role-definitions-create-delete-or-modify.md) </span></span>  
 <span data-ttu-id="483e4-149">[授予用户对报表服务器的访问权限 &#40;报表管理器&#41;](grant-user-access-to-a-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="483e4-149">[Grant User Access to a Report Server &#40;Report Manager&#41;](grant-user-access-to-a-report-server.md) </span></span>  
 <span data-ttu-id="483e4-150">[修改或删除角色分配 &#40;报表管理器&#41;](role-assignments-modify-or-delete.md) </span><span class="sxs-lookup"><span data-stu-id="483e4-150">[Modify or Delete a Role Assignment &#40;Report Manager&#41;](role-assignments-modify-or-delete.md) </span></span>  
 [<span data-ttu-id="483e4-151">在 SharePoint 站点上为报表服务器项设置权限（SharePoint 集成模式下的 Reporting Services）</span><span class="sxs-lookup"><span data-stu-id="483e4-151">Set Permissions for Report Server Items on a SharePoint Site &#40;Reporting Services in SharePoint Integrated Mode&#41;</span></span>](set-permissions-for-report-server-items-on-a-sharepoint-site.md)  
  
  
