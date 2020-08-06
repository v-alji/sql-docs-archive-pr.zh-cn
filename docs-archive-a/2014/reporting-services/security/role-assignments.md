---
title: 角色分配 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- users [Reporting Services]
- roles [Reporting Services]
- role-based security [Reporting Services], role assignments
- groups [Reporting Services]
- security [Reporting Services], role assignments
ms.assetid: 600e112c-1897-48a6-93c0-6e9f3f12dc01
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f156a009dfce8d91c3d3c8460160a4fdad62b573
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587181"
---
# <a name="role-assignments"></a><span data-ttu-id="e5839-102">角色分配</span><span class="sxs-lookup"><span data-stu-id="e5839-102">Role Assignments</span></span>
  <span data-ttu-id="e5839-103">在 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]中，“角色分配”  确定对报表服务器上的存储项和报表服务器自身的访问权限。</span><span class="sxs-lookup"><span data-stu-id="e5839-103">In [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], *role assignments* determine access to stored items and to the report server itself.</span></span> <span data-ttu-id="e5839-104">角色分配由以下几部分组成：</span><span class="sxs-lookup"><span data-stu-id="e5839-104">A role assignment has the following parts:</span></span>  
  
-   <span data-ttu-id="e5839-105">要控制其访问权限的安全对象。</span><span class="sxs-lookup"><span data-stu-id="e5839-105">A securable item for which you want to control access.</span></span> <span data-ttu-id="e5839-106">安全对象的示例包括文件夹、报表和资源。</span><span class="sxs-lookup"><span data-stu-id="e5839-106">Examples of securable items include folders, reports, and resources.</span></span>  
  
-   <span data-ttu-id="e5839-107">可由 Windows 安全性或其他身份验证机制进行身份验证的用户帐户或组帐户。</span><span class="sxs-lookup"><span data-stu-id="e5839-107">A user or group account that can be authenticated by Windows security or another authentication mechanism.</span></span>  
  
-   <span data-ttu-id="e5839-108">定义一组任务的角色定义。</span><span class="sxs-lookup"><span data-stu-id="e5839-108">Role definitions that define a set of tasks.</span></span> <span data-ttu-id="e5839-109">角色定义的示例包括“系统管理员” \*\*\*\*、“内容管理员” \*\*\*\* 和“发布者” \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e5839-109">Examples of role definitions include **System Administrator**, **Content Manager**, and **Publisher**.</span></span>  
  
 <span data-ttu-id="e5839-110">角色分配在文件夹层次结构中可以继承。</span><span class="sxs-lookup"><span data-stu-id="e5839-110">Role assignments are inherited within the folder hierarchy.</span></span> <span data-ttu-id="e5839-111">文件夹中包含的所有报表、共享数据源、资源和子文件夹将自动继承为文件夹定义的角色分配。</span><span class="sxs-lookup"><span data-stu-id="e5839-111">The role assignment that is defined for a folder is automatically inherited by all reports, shared data sources, resources, and subfolders contained within that folder.</span></span> <span data-ttu-id="e5839-112">您可以通过为各项分别定义角色分配来覆盖继承的安全性。</span><span class="sxs-lookup"><span data-stu-id="e5839-112">You can override inherited security by defining role assignments for individual items.</span></span> <span data-ttu-id="e5839-113">文件夹层次结构的所有部分都必须至少由一个角色分配进行保护。</span><span class="sxs-lookup"><span data-stu-id="e5839-113">All parts of the folder hierarchy must be secured by at least one role assignment.</span></span> <span data-ttu-id="e5839-114">不能创建不安全的项，而且在处理设置时应采用安全的方式，以避免创建不安全的项。</span><span class="sxs-lookup"><span data-stu-id="e5839-114">You cannot create an unsecured item or manipulate settings in a way that produces an unsecured item.</span></span>  
  
 <span data-ttu-id="e5839-115">下图显示了一个角色分配，它将一个组和一个特定用户映射到文件夹 B 的“发布者” \*\*\*\* 角色：</span><span class="sxs-lookup"><span data-stu-id="e5839-115">The following diagram illustrates a role assignment that maps a group and a specific user to the **Publisher** role for Folder B.</span></span>  
  
 <span data-ttu-id="e5839-116">![角色分配关系图](../media/report-securityarch.gif "角色分配关系图")</span><span class="sxs-lookup"><span data-stu-id="e5839-116">![Role assignments diagram](../media/report-securityarch.gif "Role assignments diagram")</span></span>  
<span data-ttu-id="e5839-117">角色分配关系图</span><span class="sxs-lookup"><span data-stu-id="e5839-117">Role assignments diagram</span></span>  
  
## <a name="system-level-and-item-level-role-assignments"></a><span data-ttu-id="e5839-118">系统级和项级角色分配</span><span class="sxs-lookup"><span data-stu-id="e5839-118">System-Level and Item-Level Role Assignments</span></span>  
 <span data-ttu-id="e5839-119">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中基于角色的安全性归为以下级别：</span><span class="sxs-lookup"><span data-stu-id="e5839-119">Role-based security in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] is organized into the following levels:</span></span>  
  
-   <span data-ttu-id="e5839-120">项级角色分配控制对报表服务器文件夹层次结构中报表、文件夹、报表模型、共享数据源和资源的访问权限。</span><span class="sxs-lookup"><span data-stu-id="e5839-120">Item-level role assignments control access to reports, folders, report models, shared data sources, and resources in the report server folder hierarchy.</span></span> <span data-ttu-id="e5839-121">对特定项或主文件夹创建角色分配时，定义的就是项级角色分配。</span><span class="sxs-lookup"><span data-stu-id="e5839-121">Item-level role assignments are defined when create a role assignment on a specific item or on the Home folder.</span></span>  
  
-   <span data-ttu-id="e5839-122">系统角色分配将授予涉及整个服务器范围的操作（例如，管理作业就是一个系统级操作）。</span><span class="sxs-lookup"><span data-stu-id="e5839-122">System role assignments authorize operations that are scoped to the server as a whole (for example, the ability to manage jobs is a system level operation).</span></span> <span data-ttu-id="e5839-123">系统角色分配与系统管理员并不相同。</span><span class="sxs-lookup"><span data-stu-id="e5839-123">A system role assignment is not the equivalent of a system administrator.</span></span> <span data-ttu-id="e5839-124">它不能授予可分配对报表服务器的完全控制权限的高级权限。</span><span class="sxs-lookup"><span data-stu-id="e5839-124">It does not confer advanced permissions that grant full control of a report server.</span></span>  
  
 <span data-ttu-id="e5839-125">系统角色分配并不授予对文件夹层次结构中的项的访问权限。</span><span class="sxs-lookup"><span data-stu-id="e5839-125">A system role assignment does not authorize access to items in the folder hierarchy.</span></span> <span data-ttu-id="e5839-126">系统安全性和项安全性是互斥的。</span><span class="sxs-lookup"><span data-stu-id="e5839-126">System and item security are mutually exclusive.</span></span> <span data-ttu-id="e5839-127">对于任何给定的用户或组，您可能需要同时创建系统级和项级角色分配，才可为其提供对报表服务器的充分访问权限。</span><span class="sxs-lookup"><span data-stu-id="e5839-127">For any given user or group, you might need to create both a system-level and item-level role assignment to provide sufficient access to a report server.</span></span>  
  
## <a name="users-and-groups-in-role-assignments"></a><span data-ttu-id="e5839-128">角色分配中的用户和组</span><span class="sxs-lookup"><span data-stu-id="e5839-128">Users and Groups in Role Assignments</span></span>  
 <span data-ttu-id="e5839-129">您在角色分配中指定的用户帐户或组帐户都是域帐户。</span><span class="sxs-lookup"><span data-stu-id="e5839-129">The users or group accounts that you specify in role assignments are domain accounts.</span></span> <span data-ttu-id="e5839-130">报表服务器可以引用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 域（如果使用的是自定义安全扩展插件，则可以是其他安全模式）中的用户和组，但不能创建或管理其中的用户和组。</span><span class="sxs-lookup"><span data-stu-id="e5839-130">The report server references, but does not create or manage, users and groups from a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows domain (or another security model if you are using a custom security extension).</span></span>  
  
 <span data-ttu-id="e5839-131">在应用于任何给定项的所有角色分配中，任意两个角色分配所指定的用户或组都不得相同。</span><span class="sxs-lookup"><span data-stu-id="e5839-131">Of all the role assignments that apply to any given item, no two can specify the same user or group.</span></span> <span data-ttu-id="e5839-132">如果某个用户帐户也是组帐户的成员，而您为该用户和组都指定了角色分配，那么，该用户将可以使用这两个角色分配的任务。</span><span class="sxs-lookup"><span data-stu-id="e5839-132">If a user account is also a member of a group account, and you have role assignments for both, the combined set of tasks for both role assignments are available to the user.</span></span>  
  
 <span data-ttu-id="e5839-133">当您将用户添加到已指定角色分配的组时，必须重置 Internet Information Services (IIS)，新的角色分配才会对该用户生效。</span><span class="sxs-lookup"><span data-stu-id="e5839-133">When you add a user to a group that is already part of a role assignment, you must reset Internet Information Services (IIS) for the new role assignment to take effect for that user.</span></span>  
  
## <a name="predefined-role-assignments"></a><span data-ttu-id="e5839-134">预定义角色分配</span><span class="sxs-lookup"><span data-stu-id="e5839-134">Predefined Role Assignments</span></span>  
 <span data-ttu-id="e5839-135">默认情况下，将实现预定义角色分配，以允许本地管理员管理报表服务器。</span><span class="sxs-lookup"><span data-stu-id="e5839-135">By default, predefined role assignments are implemented that allow local administrators to manage the report server.</span></span> <span data-ttu-id="e5839-136">您必须添加其他角色分配，才可向其他用户授予访问权限。</span><span class="sxs-lookup"><span data-stu-id="e5839-136">You must add additional role assignments to grant access to other users.</span></span>  
  
 <span data-ttu-id="e5839-137">有关提供默认安全性的预定义角色分配的详细信息，请参阅 [预定义角色](role-definitions-predefined-roles.md)。</span><span class="sxs-lookup"><span data-stu-id="e5839-137">For more information about the predefined role assignments that provide default security, see [Predefined Roles](role-definitions-predefined-roles.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5839-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e5839-138">See Also</span></span>  
 <span data-ttu-id="e5839-139">[创建、删除或修改角色 &#40;Management Studio&#41;](role-definitions-create-delete-or-modify.md) </span><span class="sxs-lookup"><span data-stu-id="e5839-139">[Create, Delete, or Modify a Role &#40;Management Studio&#41;](role-definitions-create-delete-or-modify.md) </span></span>  
 <span data-ttu-id="e5839-140">[授予用户对报表服务器的访问权限 &#40;报表管理器&#41;](grant-user-access-to-a-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="e5839-140">[Grant User Access to a Report Server &#40;Report Manager&#41;](grant-user-access-to-a-report-server.md) </span></span>  
 <span data-ttu-id="e5839-141">[修改或删除角色分配 &#40;报表管理器&#41;](role-assignments-modify-or-delete.md) </span><span class="sxs-lookup"><span data-stu-id="e5839-141">[Modify or Delete a Role Assignment &#40;Report Manager&#41;](role-assignments-modify-or-delete.md) </span></span>  
 <span data-ttu-id="e5839-142">[为 sharepoint 站点上的报表服务器项设置权限 &#40;Reporting Services 在 SharePoint 集成模式下&#41;](set-permissions-for-report-server-items-on-a-sharepoint-site.md) </span><span class="sxs-lookup"><span data-stu-id="e5839-142">[Set Permissions for Report Server Items on a SharePoint Site &#40;Reporting Services in SharePoint Integrated Mode&#41;](set-permissions-for-report-server-items-on-a-sharepoint-site.md) </span></span>  
 [<span data-ttu-id="e5839-143">授予对本机模式报表服务器的权限</span><span class="sxs-lookup"><span data-stu-id="e5839-143">Granting Permissions on a Native Mode Report Server</span></span>](granting-permissions-on-a-native-mode-report-server.md)  
  
  
