---
title: 系统角色属性 (Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.systemroleproperties.f1
ms.assetid: 0210fc2a-74fb-41dd-8e39-4830047ec417
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b37ebb1cb95d6628884d81156c9c1bc29bff86fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579452"
---
# <a name="system-role-properties-management-studio"></a><span data-ttu-id="13acf-102">系统角色属性 (Management Studio)</span><span class="sxs-lookup"><span data-stu-id="13acf-102">System Role Properties (Management Studio)</span></span>
  <span data-ttu-id="13acf-103">使用“系统角色”页可以查看当前为报表服务器定义的系统角色定义。</span><span class="sxs-lookup"><span data-stu-id="13acf-103">Use the System Roles page to view the system role definitions that are currently defined for the report server.</span></span> <span data-ttu-id="13acf-104">系统角色定义包含一组任务的命名集合，这些任务相对于整个站点（而不是单项）执行。</span><span class="sxs-lookup"><span data-stu-id="13acf-104">A system role definition contains a named collection of tasks that are performed relative to the entire site, instead of an individual item.</span></span> <span data-ttu-id="13acf-105">角色定义将分配给用户或组，以据此创建角色分配。</span><span class="sxs-lookup"><span data-stu-id="13acf-105">Role definitions are assigned to a user or groups to create a resulting role assignment.</span></span> <span data-ttu-id="13acf-106">角色定义中的任务指定用户或组可以执行的任务。</span><span class="sxs-lookup"><span data-stu-id="13acf-106">The tasks in the role definition specify what the user or group can do.</span></span>  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="13acf-107">有两个预定义的系统角色定义： **系统管理员** 和 **系统用户**。</span><span class="sxs-lookup"><span data-stu-id="13acf-107">has two predefined system role definitions: **System Administrator** and **System User**.</span></span> <span data-ttu-id="13acf-108">您可以通过更改任务列表来修改这些角色定义，也可以创建支持其他任务组合的新系统角色。</span><span class="sxs-lookup"><span data-stu-id="13acf-108">You can modify these role definitions by changing the task list, or you can create a new system role that supports a different combination of tasks.</span></span> <span data-ttu-id="13acf-109">对角色定义进行编辑将影响包括角色定义的所有角色分配。</span><span class="sxs-lookup"><span data-stu-id="13acf-109">Editing a role definition affects all role assignments that include the role definition.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="13acf-110">系统角色分配仅适用于在本机模式下运行的报表服务器。</span><span class="sxs-lookup"><span data-stu-id="13acf-110">System role assignments are used only on a report server that runs in native mode.</span></span> <span data-ttu-id="13acf-111">如果针对报表服务器配置了 SharePoint 集成，则此页不可用。</span><span class="sxs-lookup"><span data-stu-id="13acf-111">If the report server is configured for SharePoint integration, this page is not available.</span></span>  
  
## <a name="options"></a><span data-ttu-id="13acf-112">选项</span><span class="sxs-lookup"><span data-stu-id="13acf-112">Options</span></span>  
 <span data-ttu-id="13acf-113">**名称**</span><span class="sxs-lookup"><span data-stu-id="13acf-113">**Name**</span></span>  
 <span data-ttu-id="13acf-114">指定系统角色定义的名称。</span><span class="sxs-lookup"><span data-stu-id="13acf-114">Specifies the name of the system role definition.</span></span>  
  
 <span data-ttu-id="13acf-115">**说明**</span><span class="sxs-lookup"><span data-stu-id="13acf-115">**Description**</span></span>  
 <span data-ttu-id="13acf-116">显示系统角色定义的说明。</span><span class="sxs-lookup"><span data-stu-id="13acf-116">Shows a description of the system role definition.</span></span> <span data-ttu-id="13acf-117">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 中，此说明仅在这一页上可见。</span><span class="sxs-lookup"><span data-stu-id="13acf-117">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], this description is only visible in this page.</span></span> <span data-ttu-id="13acf-118">通过报表管理器查看此项的用户在浏览文件夹层次结构时可能会看到此说明。</span><span class="sxs-lookup"><span data-stu-id="13acf-118">Users who view this item through Report Manager may see this description when browsing the folder hierarchy.</span></span>  
  
 <span data-ttu-id="13acf-119">**任务**</span><span class="sxs-lookup"><span data-stu-id="13acf-119">**Task**</span></span>  
 <span data-ttu-id="13acf-120">列出可以为此角色定义选择的所有系统级任务。</span><span class="sxs-lookup"><span data-stu-id="13acf-120">Lists all system-level tasks that can be selected for this role definition.</span></span> <span data-ttu-id="13acf-121">可以在预定义任务列表中添加或删除项，以定义用户通过此角色访问给定项的方式。</span><span class="sxs-lookup"><span data-stu-id="13acf-121">You can add or remove items from the predefined task list to define how users access a given item through this role.</span></span> <span data-ttu-id="13acf-122">不能创建新任务，也不能修改现有任务。</span><span class="sxs-lookup"><span data-stu-id="13acf-122">You cannot create new tasks, and you cannot modify existing tasks.</span></span>  
  
 <span data-ttu-id="13acf-123">**说明**</span><span class="sxs-lookup"><span data-stu-id="13acf-123">**Description**</span></span>  
 <span data-ttu-id="13acf-124">提供每个任务的有关信息。</span><span class="sxs-lookup"><span data-stu-id="13acf-124">Provides information about each task.</span></span> <span data-ttu-id="13acf-125">不能修改任务说明。</span><span class="sxs-lookup"><span data-stu-id="13acf-125">You cannot modify task descriptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13acf-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="13acf-126">See Also</span></span>  
 <span data-ttu-id="13acf-127">[Management Studio 中报表服务器的 F1 帮助](report-server-in-management-studio-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="13acf-127">[Report Server in Management Studio F1 Help](report-server-in-management-studio-f1-help.md) </span></span>  
 <span data-ttu-id="13acf-128">[系统级任务](../security/tasks-and-permissions-system-level-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="13acf-128">[System-Level Tasks](../security/tasks-and-permissions-system-level-tasks.md) </span></span>  
 <span data-ttu-id="13acf-129">[任务和权限](../security/tasks-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="13acf-129">[Tasks and Permissions](../security/tasks-and-permissions.md) </span></span>  
 [<span data-ttu-id="13acf-130">预定义角色</span><span class="sxs-lookup"><span data-stu-id="13acf-130">Predefined Roles</span></span>](../security/role-definitions-predefined-roles.md)  
  
  
