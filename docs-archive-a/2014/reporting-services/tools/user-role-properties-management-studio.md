---
title: 用户角色属性 (Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.userroleproperties.f1
ms.assetid: c8b22236-a8b1-4e15-b1ff-4e1909b602d3
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6f79953abdf5e3d1cdb03de8c5feeb6b2de34ab7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689732"
---
# <a name="user-role-properties-management-studio"></a><span data-ttu-id="eea93-102">用户角色属性 (Management Studio)</span><span class="sxs-lookup"><span data-stu-id="eea93-102">User Role Properties (Management Studio)</span></span>
  <span data-ttu-id="eea93-103">使用此页，可以查看项级角色定义中所包含的任务，</span><span class="sxs-lookup"><span data-stu-id="eea93-103">Use this page to view which tasks are included in an item-level role definition.</span></span> <span data-ttu-id="eea93-104">还可以更改任务列表或修改角色说明。</span><span class="sxs-lookup"><span data-stu-id="eea93-104">You can also use this page to change the task list or modify a role description.</span></span>  
  
 <span data-ttu-id="eea93-105">项级角色定义是用户相对于特定项（即文件夹、报表、资源或共享数据源）所执行的一组指定任务。</span><span class="sxs-lookup"><span data-stu-id="eea93-105">An item-level role definition is a named collection of tasks that users perform relative to a specific item (that is, a folder, report, resource, or shared data source).</span></span> <span data-ttu-id="eea93-106">角色定义将分配给用户或组，以便在报表管理器中创建角色分配。</span><span class="sxs-lookup"><span data-stu-id="eea93-106">Role definitions are assigned to a user or group to create a role assignment in Report Manager.</span></span> <span data-ttu-id="eea93-107">角色定义中的任务描述用户或组可以执行的任务。</span><span class="sxs-lookup"><span data-stu-id="eea93-107">The tasks in the role definition describe what the user or group can do.</span></span>  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="eea93-108">包含了用户可以使用的多个预定义项级角色定义。</span><span class="sxs-lookup"><span data-stu-id="eea93-108">includes a number of predefined item-level role definitions that you can work with.</span></span> <span data-ttu-id="eea93-109">可以通过更改每个角色定义的任务列表来修改角色定义。</span><span class="sxs-lookup"><span data-stu-id="eea93-109">You can modify the role definitions by changing the task list of each one.</span></span> <span data-ttu-id="eea93-110">对角色定义进行编辑将影响包括角色定义的所有角色分配。</span><span class="sxs-lookup"><span data-stu-id="eea93-110">Editing a role definition affects all role assignments that include the role definition.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="eea93-111">用户角色分配仅适用于在本机模式下运行的报表服务器。</span><span class="sxs-lookup"><span data-stu-id="eea93-111">User role assignments are used only on a report server that runs in native mode.</span></span> <span data-ttu-id="eea93-112">如果将报表服务器配置为 SharePoint 集成，则该页显示有关在 SharePoint 站点上定义的角色和权限级别的只读信息。</span><span class="sxs-lookup"><span data-stu-id="eea93-112">If the report server is configured for SharePoint integration, this page displays read-only information about the roles and permission levels that are defined on the SharePoint site.</span></span>  
  
## <a name="options"></a><span data-ttu-id="eea93-113">选项</span><span class="sxs-lookup"><span data-stu-id="eea93-113">Options</span></span>  
 <span data-ttu-id="eea93-114">**名称**</span><span class="sxs-lookup"><span data-stu-id="eea93-114">**Name**</span></span>  
 <span data-ttu-id="eea93-115">指定角色定义的名称。</span><span class="sxs-lookup"><span data-stu-id="eea93-115">Specifies the name of the role definition.</span></span>  
  
 <span data-ttu-id="eea93-116">**说明**</span><span class="sxs-lookup"><span data-stu-id="eea93-116">**Description**</span></span>  
 <span data-ttu-id="eea93-117">显示角色定义的说明。</span><span class="sxs-lookup"><span data-stu-id="eea93-117">Shows a description of the role definition.</span></span> <span data-ttu-id="eea93-118">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，该说明仅在此页上可见。</span><span class="sxs-lookup"><span data-stu-id="eea93-118">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], this description is only visible in this page.</span></span> <span data-ttu-id="eea93-119">在报表管理器中，该说明可帮助用户确定是否在角色分配中使用该角色。</span><span class="sxs-lookup"><span data-stu-id="eea93-119">In Report Manager, this description helps users decide whether to use the role in a role assignment.</span></span>  
  
 <span data-ttu-id="eea93-120">**任务**</span><span class="sxs-lookup"><span data-stu-id="eea93-120">**Task**</span></span>  
 <span data-ttu-id="eea93-121">列出可为此角色定义选择的所有项级任务。</span><span class="sxs-lookup"><span data-stu-id="eea93-121">Lists all item-level tasks that can be selected for this role definition.</span></span> <span data-ttu-id="eea93-122">可以在预定义任务列表中添加或删除项，以定义用户通过此角色访问给定项的方式。</span><span class="sxs-lookup"><span data-stu-id="eea93-122">You can add or remove items from the predefined task list to define how users access a given item through this role.</span></span> <span data-ttu-id="eea93-123">不能创建新任务，也不能修改现有任务。</span><span class="sxs-lookup"><span data-stu-id="eea93-123">You cannot create new tasks, and you cannot modify existing tasks.</span></span> <span data-ttu-id="eea93-124">只有 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中才显示角色定义的任务列表。</span><span class="sxs-lookup"><span data-stu-id="eea93-124">The task list of a role definition appears only in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="eea93-125">**任务说明**</span><span class="sxs-lookup"><span data-stu-id="eea93-125">**Task Description**</span></span>  
 <span data-ttu-id="eea93-126">提供每个任务的有关信息。</span><span class="sxs-lookup"><span data-stu-id="eea93-126">Provides information about each task.</span></span> <span data-ttu-id="eea93-127">不能修改任务说明。</span><span class="sxs-lookup"><span data-stu-id="eea93-127">You cannot modify task descriptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eea93-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="eea93-128">See Also</span></span>  
 <span data-ttu-id="eea93-129">[项级任务](../security/tasks-and-permissions-item-level-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="eea93-129">[Item-Level Tasks](../security/tasks-and-permissions-item-level-tasks.md) </span></span>  
 <span data-ttu-id="eea93-130">[角色定义](../security/role-definitions.md) </span><span class="sxs-lookup"><span data-stu-id="eea93-130">[Role Definitions](../security/role-definitions.md) </span></span>  
 <span data-ttu-id="eea93-131">[Management Studio 中报表服务器的 F1 帮助](report-server-in-management-studio-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="eea93-131">[Report Server in Management Studio F1 Help](report-server-in-management-studio-f1-help.md) </span></span>  
 <span data-ttu-id="eea93-132">[任务和权限](../security/tasks-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="eea93-132">[Tasks and Permissions](../security/tasks-and-permissions.md) </span></span>  
 [<span data-ttu-id="eea93-133">预定义角色</span><span class="sxs-lookup"><span data-stu-id="eea93-133">Predefined Roles</span></span>](../security/role-definitions-predefined-roles.md)  
  
  
