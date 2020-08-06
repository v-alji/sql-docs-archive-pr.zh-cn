---
title: 授予对本机模式报表服务器的权限 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- roles [Reporting Services], creating
- authorization [Reporting Services]
- server security [Reporting Services]
- role-based security [Reporting Services]
- items [Reporting Services], security
- permissions [Reporting Services], native mode
- published reports [Reporting Services], security
- reports [Reporting Services], security
- report items [Reporting Services], security
- role-based security [Reporting Services], about role-based security
- security [Reporting Services], role-based
ms.assetid: 260dc2e9-546c-4f04-9fa1-977e23c9d68c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 22967a7c9c6b8cc3e14ecffed117d1ab821788f4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590564"
---
# <a name="granting-permissions-on-a-native-mode-report-server"></a><span data-ttu-id="d73ae-102">授予对本机模式报表服务器的权限</span><span class="sxs-lookup"><span data-stu-id="d73ae-102">Granting Permissions on a Native Mode Report Server</span></span>
  <span data-ttu-id="d73ae-103">SQL Server [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 使用基于角色的授权和身份验证子系统来确定哪些用户可以在报表服务器上执行操作和访问项。</span><span class="sxs-lookup"><span data-stu-id="d73ae-103">SQL Server [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] uses role-based authorization and an authentication subsystem to determine who can perform operations and access items on a report server.</span></span> <span data-ttu-id="d73ae-104">基于角色的授权将角色分为用户或组可以执行的操作组。</span><span class="sxs-lookup"><span data-stu-id="d73ae-104">Role-based authorization categorizes into roles the set of actions that a user or group can perform.</span></span> <span data-ttu-id="d73ae-105">身份验证基于内置的 Windows 身份验证或您提供的自定义身份验证模块。</span><span class="sxs-lookup"><span data-stu-id="d73ae-105">Authentication is based on built-in Windows Authentication or a custom authentication module that you provide.</span></span> <span data-ttu-id="d73ae-106">您对这两种身份验证类型都可以使用预定义或自定义角色。</span><span class="sxs-lookup"><span data-stu-id="d73ae-106">You can use predefined or custom roles with either authentication type.</span></span>  
  
## <a name="using-roles-to-grant-report-server-access"></a><span data-ttu-id="d73ae-107">使用角色授予报表服务器访问权限</span><span class="sxs-lookup"><span data-stu-id="d73ae-107">Using Roles to Grant Report Server Access</span></span>  
 <span data-ttu-id="d73ae-108">所有用户都在定义特定访问级别的角色上下文中与报表服务器进行交互。</span><span class="sxs-lookup"><span data-stu-id="d73ae-108">All users interact with a report server within the context of a role that defines a specific level of access.</span></span> [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="d73ae-109">提供了预定义的角色，您可以为用户和组分配这些角色，从而让其可以立即访问报表服务器。</span><span class="sxs-lookup"><span data-stu-id="d73ae-109">includes predefined roles that you can assign to users and groups to provide immediate access to a report server.</span></span> <span data-ttu-id="d73ae-110">预定义角色例如有“内容管理员”\*\*\*\*、“发布者”\*\*\*\* 和“浏览者”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d73ae-110">**ContentManager**, **Publisher**, and **Browser** are examples of predefined roles.</span></span> <span data-ttu-id="d73ae-111">每个角色定义一个相关任务的集合。</span><span class="sxs-lookup"><span data-stu-id="d73ae-111">Each role defines a collection of related tasks.</span></span> <span data-ttu-id="d73ae-112">例如，“发布者”  具有添加报表和创建用于存储这些报表的文件夹的权限。</span><span class="sxs-lookup"><span data-stu-id="d73ae-112">For example, a **Publisher** has permission to add reports and create folders for storing those reports.</span></span>  
  
 <span data-ttu-id="d73ae-113">角色分配通常从父节点继承，但是您可以通过为特定项创建新的角色分配来打破权限继承。</span><span class="sxs-lookup"><span data-stu-id="d73ae-113">Role assignments are typically inherited from a parent node, but you can break permission inheritance by creating a new role assignment for a particular item.</span></span> <span data-ttu-id="d73ae-114">某个用户作为一个报表的“内容管理员” \*\*\*\* 角色成员的同时也可以是另一个报表的“浏览者” \*\*\*\* 角色的成员。</span><span class="sxs-lookup"><span data-stu-id="d73ae-114">A user who is a member of the **Content Manager** role for one report may be a member of the **Browser** role for another report.</span></span>  
  
 <span data-ttu-id="d73ae-115">若要授予对报表服务器项和操作的访问权限，请遵循下列原则：</span><span class="sxs-lookup"><span data-stu-id="d73ae-115">To grant access to report server items and operations, follow these guidelines:</span></span>  
  
1.  <span data-ttu-id="d73ae-116">检查预定义角色，以确定是否可以按原样使用它们。</span><span class="sxs-lookup"><span data-stu-id="d73ae-116">Review the predefined roles to determine whether you can use them as is.</span></span> <span data-ttu-id="d73ae-117">如果需要调整任务或额外定义角色，应该在开始向用户分配特定角色之前执行这些操作。</span><span class="sxs-lookup"><span data-stu-id="d73ae-117">If you need to adjust the tasks or define additional roles, you should do this before you begin assigning users to specific roles.</span></span> <span data-ttu-id="d73ae-118">有关每个角色的详细信息，请参阅 [预定义角色](role-definitions-predefined-roles.md)。</span><span class="sxs-lookup"><span data-stu-id="d73ae-118">For more information about each role, see [Predefined Roles](role-definitions-predefined-roles.md).</span></span>  
  
2.  <span data-ttu-id="d73ae-119">明确需要访问报表服务器的用户和组以及访问级别。</span><span class="sxs-lookup"><span data-stu-id="d73ae-119">Identify which users and groups require access to the report server, and at what level.</span></span> <span data-ttu-id="d73ae-120">应该为大多数用户分配 **“浏览者”** 角色或 **“报表生成者”** 角色。</span><span class="sxs-lookup"><span data-stu-id="d73ae-120">Most users should be assigned to the **Browser** role or the **Report Builder** role.</span></span> <span data-ttu-id="d73ae-121">应该为少量用户分配 **“发布者”** 角色。</span><span class="sxs-lookup"><span data-stu-id="d73ae-121">A smaller number of users should be assigned to the **Publisher** role.</span></span> <span data-ttu-id="d73ae-122">应该只为极少数用户分配 **“内容管理员”** 角色。</span><span class="sxs-lookup"><span data-stu-id="d73ae-122">Very few users should be assigned to **Content Manager**.</span></span>  
  
3.  <span data-ttu-id="d73ae-123">对主文件夹（这是报表服务器文件夹层次结构的顶级文件夹），使用报表管理器为需要访问权限的每个用户或组分配角色。</span><span class="sxs-lookup"><span data-stu-id="d73ae-123">Use Report Manager to assign roles on the Home folder (this is the top-level folder of the report server folder hierarchy) for each user or group who requires access.</span></span>  
  
4.  <span data-ttu-id="d73ae-124">在站点级，使用预定义的角色“系统用户”\*\*\*\* 和“系统管理员”\*\*\*\* 在报表管理器的“站点设置”页为每个用户和组创建系统级角色分配。</span><span class="sxs-lookup"><span data-stu-id="d73ae-124">At the site level, on the Site Settings page in Report Manager, create a system-level role assignment for each user and group using the predefined roles **System User** and **System Administrator**.</span></span>  
  
5.  <span data-ttu-id="d73ae-125">根据需要为特定文件夹、报表和其他项创建额外的角色分配。</span><span class="sxs-lookup"><span data-stu-id="d73ae-125">Create additional role assignments as needed for specific folders, reports, and other items.</span></span> <span data-ttu-id="d73ae-126">应避免创建大量角色分配。</span><span class="sxs-lookup"><span data-stu-id="d73ae-126">Avoid creating a large number of role assignments.</span></span> <span data-ttu-id="d73ae-127">如果创建过多的角色分配，将很难跟踪每个用户的不同权限级别。</span><span class="sxs-lookup"><span data-stu-id="d73ae-127">If you create too many, it will be difficult to keep track of the different permission levels for each user.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d73ae-128">如果已将报表服务器配置为在 SharePoint 集成模式下运行，则必须设置对 SharePoint 站点的权限以授予对报表服务器项的访问权限。</span><span class="sxs-lookup"><span data-stu-id="d73ae-128">If you configured a report server to run in SharePoint integrated mode, you must set permissions on the SharePoint site to grant access to report server items.</span></span> <span data-ttu-id="d73ae-129">有关详细信息，请参阅 [在 SharePoint 站点上授予对报表服务器项的权限](granting-permissions-on-report-server-items-on-a-sharepoint-site.md)。</span><span class="sxs-lookup"><span data-stu-id="d73ae-129">For more information, see [Granting Permissions on Report Server Items on a SharePoint Site](granting-permissions-on-report-server-items-on-a-sharepoint-site.md).</span></span>  
  
## <a name="who-sets-permissions"></a><span data-ttu-id="d73ae-130">由谁设置权限</span><span class="sxs-lookup"><span data-stu-id="d73ae-130">Who Sets Permissions</span></span>  
 <span data-ttu-id="d73ae-131">最初，只有属于本地管理员组成员的用户才可以访问报表服务器。</span><span class="sxs-lookup"><span data-stu-id="d73ae-131">Initially, only users who are members of the local administrators group can access a report server.</span></span> [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="d73ae-132">安装时将分配两个默认的角色，它们可向本地管理员组成员授予项级和系统级的访问权限。</span><span class="sxs-lookup"><span data-stu-id="d73ae-132">is installed with two default role assignments that grant item-level and system-level access to members of the local administrators group.</span></span> <span data-ttu-id="d73ae-133">本地管理员可以使用这些内置角色分配授予对其他用户的 Report Server 访问权限，并管理 Report Server 项目。</span><span class="sxs-lookup"><span data-stu-id="d73ae-133">Local Administrators can use these built-in role assignments to grant report server access to other users and manage report server items.</span></span> <span data-ttu-id="d73ae-134">不能删除内置角色分配。</span><span class="sxs-lookup"><span data-stu-id="d73ae-134">The built-in role assignments cannot be deleted.</span></span> <span data-ttu-id="d73ae-135">本地管理员始终具有完全管理报表服务器实例的权限。</span><span class="sxs-lookup"><span data-stu-id="d73ae-135">A local administrator always has permission to fully manage a report server instance.</span></span>  
 
 <span data-ttu-id="d73ae-136">需要进行其他配置才能在运行 Windows Vista 或 Windows Server 2008 的本地计算机上管理报表服务器实例。</span><span class="sxs-lookup"><span data-stu-id="d73ae-136">Additional configuration is required before you can administer a report server instance on a local computer that runs Windows Vista or Windows Server 2008.</span></span> <span data-ttu-id="d73ae-137">有关详细信息，请参阅 [为本地管理配置本机模式报表服务器 (SSRS)](../report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="d73ae-137">For more information, see [Configure a Native Mode Report Server for Local Administration &#40;SSRS&#41;](../report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).</span></span>  
  
## <a name="how-permissions-are-stored"></a><span data-ttu-id="d73ae-138">如何存储权限</span><span class="sxs-lookup"><span data-stu-id="d73ae-138">How Permissions are Stored</span></span>  
 <span data-ttu-id="d73ae-139">角色分配和定义都存储在报表服务器数据库中。</span><span class="sxs-lookup"><span data-stu-id="d73ae-139">Role assignments and definitions are stored in the report server database.</span></span> <span data-ttu-id="d73ae-140">如果使用的是多种客户端工具或编程接口，则所有访问都受限于为整个报表服务器实例定义的权限。</span><span class="sxs-lookup"><span data-stu-id="d73ae-140">If you are using variety of client tools or programmatic interfaces, all access is subject to the permissions that are defined for the report server instance as a whole.</span></span> <span data-ttu-id="d73ae-141">如果在扩展部署中配置了多个报表服务器，则对一个实例定义的角色分配存储在共享数据库中，并由同一扩展部署中的所有其他实例使用。</span><span class="sxs-lookup"><span data-stu-id="d73ae-141">If you are configuring multiple report servers in a scale-out-deployment, the role assignments that you define on one instance are stored in a shared database and used by all the other instances in the same scale-out deployment.</span></span> <span data-ttu-id="d73ae-142">因为角色分配与它们所保护的项一起存储，所以可以将数据库移到另一个报表服务器实例，而不会丢失已定义的权限。</span><span class="sxs-lookup"><span data-stu-id="d73ae-142">Because role assignments are stored with the items they secure, you can move the database to another report server instance without losing the permissions you defined.</span></span>  
  
## <a name="tasks-and-tools-for-managing-permissions"></a><span data-ttu-id="d73ae-143">管理权限的任务和工具</span><span class="sxs-lookup"><span data-stu-id="d73ae-143">Tasks and tools for Managing Permissions</span></span>  
 <span data-ttu-id="d73ae-144">使用以下工具可以管理角色定义和分配。</span><span class="sxs-lookup"><span data-stu-id="d73ae-144">Use the following tools to manage role definitions and assignments.</span></span>  
  
|<span data-ttu-id="d73ae-145">工具</span><span class="sxs-lookup"><span data-stu-id="d73ae-145">Tool</span></span>|<span data-ttu-id="d73ae-146">任务</span><span class="sxs-lookup"><span data-stu-id="d73ae-146">Tasks</span></span>|  
|----------|-----------|  
|<span data-ttu-id="d73ae-147">Management Studio - 用于查看、修改、创建和删除角色定义。</span><span class="sxs-lookup"><span data-stu-id="d73ae-147">Management Studio - Used to view, modify, create, and delete role definitions.</span></span>|[<span data-ttu-id="d73ae-148">创建、删除或修改角色 (Management Studio)</span><span class="sxs-lookup"><span data-stu-id="d73ae-148">Create, Delete, or Modify a Role &#40;Management Studio&#41;</span></span>](role-definitions-create-delete-or-modify.md)|  
|<span data-ttu-id="d73ae-149">报表管理器 - 用于为用户和组分配角色。</span><span class="sxs-lookup"><span data-stu-id="d73ae-149">Report Manager - Used to assign users and groups to roles.</span></span>|[<span data-ttu-id="d73ae-150">授予用户对报表服务器的访问权限（报表管理器）</span><span class="sxs-lookup"><span data-stu-id="d73ae-150">Grant User Access to a Report Server &#40;Report Manager&#41;</span></span>](grant-user-access-to-a-report-server.md)<br /><br /> [<span data-ttu-id="d73ae-151">修改或删除角色分配（报表管理器）</span><span class="sxs-lookup"><span data-stu-id="d73ae-151">Modify or Delete a Role Assignment &#40;Report Manager&#41;</span></span>](role-assignments-modify-or-delete.md)|  
  
## <a name="see-also"></a><span data-ttu-id="d73ae-152">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d73ae-152">See Also</span></span>  
 <span data-ttu-id="d73ae-153">[预定义角色](role-definitions-predefined-roles.md) </span><span class="sxs-lookup"><span data-stu-id="d73ae-153">[Predefined Roles](role-definitions-predefined-roles.md) </span></span>  
 <span data-ttu-id="d73ae-154">[授予对 SharePoint 站点上的报表服务器项的权限](granting-permissions-on-report-server-items-on-a-sharepoint-site.md) </span><span class="sxs-lookup"><span data-stu-id="d73ae-154">[Granting Permissions on Report Server Items on a SharePoint Site](granting-permissions-on-report-server-items-on-a-sharepoint-site.md) </span></span>  
 <span data-ttu-id="d73ae-155">[针对报表服务器的身份验证](authentication-with-the-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="d73ae-155">[Authentication with the Report Server](authentication-with-the-report-server.md) </span></span>  
 <span data-ttu-id="d73ae-156"> (create-and-manage-role-assignments.md) </span><span class="sxs-lookup"><span data-stu-id="d73ae-156">(create-and-manage-role-assignments.md)</span></span>   
 <span data-ttu-id="d73ae-157">[Reporting Services 安全和保护](reporting-services-security-and-protection.md) </span><span class="sxs-lookup"><span data-stu-id="d73ae-157">[Reporting Services Security and Protection](reporting-services-security-and-protection.md) </span></span>  
 [<span data-ttu-id="d73ae-158">报表服务器内容管理（SSRS 本机模式）</span><span class="sxs-lookup"><span data-stu-id="d73ae-158">Report Server Content Management &#40;SSRS Native Mode&#41;</span></span>](../report-server/report-server-content-management-ssrs-native-mode.md)  
  
  
