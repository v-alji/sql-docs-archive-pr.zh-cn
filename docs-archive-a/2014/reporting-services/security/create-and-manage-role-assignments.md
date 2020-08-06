---
title: 创建和管理角色分配 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- removing role assignments
- roles [Reporting Services], assignments
- security [Reporting Services], role assignments
- modifying role assignments
- deleting role assignments
ms.assetid: 086d0987-b43c-4834-8372-e08fb4b432f8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2064e2a6d4dda99ed6b8b61de363b84d073d8ef9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689276"
---
# <a name="create-and-manage-role-assignments"></a><span data-ttu-id="89323-102">创建和管理角色分配</span><span class="sxs-lookup"><span data-stu-id="89323-102">Create and Manage Role Assignments</span></span>
  <span data-ttu-id="89323-103">“ \*\* 角色分配”是确定用户或组是否可以访问特定报表服务器项或执行操作的安全策略。</span><span class="sxs-lookup"><span data-stu-id="89323-103">A *role assignment* is a security policy that determines whether a user or group can access a specific report server item or perform an operation.</span></span> <span data-ttu-id="89323-104">角色分配由单个用户帐户名或组帐户名以及一个或多个角色定义组成。</span><span class="sxs-lookup"><span data-stu-id="89323-104">A role assignment consists of a single user or group account name and one or more role definitions.</span></span>  
  
 <span data-ttu-id="89323-105">角色分配的作用域为“ \*\* 项级”或“ \*\* 系统级”。</span><span class="sxs-lookup"><span data-stu-id="89323-105">Role assignments are scoped to the *item level* or *system level*.</span></span>  
  
-   <span data-ttu-id="89323-106">项级角色分配总是在报表服务器文件夹层次结构中的特定项或分支的上下文中创建。</span><span class="sxs-lookup"><span data-stu-id="89323-106">An item-level role assignment is always created in the context of a specific item or branch in the report server folder hierarchy.</span></span> <span data-ttu-id="89323-107">您需要导航到具体的文件夹或项，才能为其创建角色分配。</span><span class="sxs-lookup"><span data-stu-id="89323-107">You navigate to a specific folder or item to create a role assignment for it.</span></span>  
  
-   <span data-ttu-id="89323-108">系统级角色分配向所选用户赋予执行影响整个报表服务器站点的任务的能力。</span><span class="sxs-lookup"><span data-stu-id="89323-108">System-level role assignments give selected users the capability to perform tasks that affect the report server site as a whole.</span></span> <span data-ttu-id="89323-109">这些任务包括创建共享计划、管理作业、在报表生成器中处理报表以及设置属性。</span><span class="sxs-lookup"><span data-stu-id="89323-109">These tasks include creating shared schedules, managing jobs, processing reports in Report Builder, and setting properties.</span></span> <span data-ttu-id="89323-110">系统级安全性不提供对报表服务器文件夹层次结构中的项的访问权限。</span><span class="sxs-lookup"><span data-stu-id="89323-110">System-level security does not convey access to items in the report server folder hierarchy.</span></span>  
  
## <a name="creating-an-item-level-role-assignment"></a><span data-ttu-id="89323-111">创建项级角色分配</span><span class="sxs-lookup"><span data-stu-id="89323-111">Creating an Item-level Role Assignment</span></span>  
 <span data-ttu-id="89323-112">若要创建或管理角色分配，请使用报表管理器，打开要保护的项的安全属性页。</span><span class="sxs-lookup"><span data-stu-id="89323-112">To create or manage role assignments, use Report Manager and open the Security property pages of the item that you want to secure.</span></span>  
  
 <span data-ttu-id="89323-113">必须为需要访问报表服务器的每个用户或组帐户创建一个单独的角色分配。</span><span class="sxs-lookup"><span data-stu-id="89323-113">You must create a separate role assignment for each user or group account that requires access to the report server.</span></span> <span data-ttu-id="89323-114">如果帐户所属的域不是报表服务器所在的域，指定帐户时请包括域名。</span><span class="sxs-lookup"><span data-stu-id="89323-114">If the account is on a domain other than the one that contains the report server, include the domain name.</span></span> <span data-ttu-id="89323-115">指定帐户后，可以选择一个或多个角色定义。</span><span class="sxs-lookup"><span data-stu-id="89323-115">After you specify an account, you can choose one or more role definitions.</span></span> <span data-ttu-id="89323-116">这些角色定义是可累加的。</span><span class="sxs-lookup"><span data-stu-id="89323-116">The role definitions are additive.</span></span> <span data-ttu-id="89323-117">对于特定用户或组，其角色分配支持所有定义的所有任务的合集。</span><span class="sxs-lookup"><span data-stu-id="89323-117">The combined set of all tasks from all definitions are supported in the assignment for a particular user or group.</span></span>  
  
 <span data-ttu-id="89323-118">若要扩大访问范围，应该在文件夹层次结构的上级选择项（如根节点“主文件夹”）。</span><span class="sxs-lookup"><span data-stu-id="89323-118">To enable widespread access, you should choose an item that is high in the folder hierarchy (for example, the root node Home).</span></span> <span data-ttu-id="89323-119">然后，您可以创建后续角色分配来锁定文件夹层次结构的特定区域。</span><span class="sxs-lookup"><span data-stu-id="89323-119">You can then create subsequent role assignments to lock down specific areas of the folder hierarchy.</span></span>  
  
 <span data-ttu-id="89323-120">您必须是报表服务器计算机上的本地管理员组的成员，才能创建角色分配。</span><span class="sxs-lookup"><span data-stu-id="89323-120">You must be a member of the local Administrator's group on the report server computer to create a role assignment.</span></span> <span data-ttu-id="89323-121">您可以通过将其他用户分配给 \*\*\*\* 内容管理员角色来委托该责任。</span><span class="sxs-lookup"><span data-stu-id="89323-121">You can delegate that responsibility by assigning other users to the **Content Manager** role.</span></span>  
  
 <span data-ttu-id="89323-122">有关详细信息，请参阅 [授予用户对报表服务器的访问权限（报表管理器）](grant-user-access-to-a-report-server.md)。</span><span class="sxs-lookup"><span data-stu-id="89323-122">For more information, see [Grant User Access to a Report Server &#40;Report Manager&#41;](grant-user-access-to-a-report-server.md).</span></span>  
  
## <a name="creating-a-system-level-role-assignment"></a><span data-ttu-id="89323-123">创建系统级角色分配</span><span class="sxs-lookup"><span data-stu-id="89323-123">Creating a System-level Role Assignment</span></span>  
 <span data-ttu-id="89323-124">若要创建或管理系统级角色分配，请使用报表管理器，打开“站点设置”页。</span><span class="sxs-lookup"><span data-stu-id="89323-124">To create or manage a system-level role assignment, use Report Manager and open the Site Settings page.</span></span>  
  
 <span data-ttu-id="89323-125">系统级和项级角色分配一同进行。</span><span class="sxs-lookup"><span data-stu-id="89323-125">System-level and item-level role assignments go together.</span></span> <span data-ttu-id="89323-126">您应为拥有项级角色分配的每个用户或组创建系统级角色分配。</span><span class="sxs-lookup"><span data-stu-id="89323-126">You should create a system-level role assignment for each user or group that has an item-level role assignment.</span></span>  
  
 <span data-ttu-id="89323-127">系统级角色分配包括的权限广泛，但不包括项级角色分配中的权限。</span><span class="sxs-lookup"><span data-stu-id="89323-127">System-level role assignments include a wide range of permissions, but they do not include permissions that are part of an item-level role assignment.</span></span> <span data-ttu-id="89323-128">与计算机上的系统权限相比，报告服务器上的系统角色不提供包括所有可能操作的完整集合的全面权限。</span><span class="sxs-lookup"><span data-stu-id="89323-128">In contrast with system permissions on a computer, system roles in Reporting Servers do not convey overarching permissions that include the full set of all possible operations.</span></span> <span data-ttu-id="89323-129">相反，系统级角色分配不过是作用域为报表服务器站点的任务的集合。</span><span class="sxs-lookup"><span data-stu-id="89323-129">Instead, system-level role assignments are simply a set of tasks that are scoped to the report server site.</span></span> <span data-ttu-id="89323-130">通过系统角色分配所提供的权限确定用户能否查看应用程序属性（如主页的图像或标题）、查看或管理共享计划或者使用报表生成器。</span><span class="sxs-lookup"><span data-stu-id="89323-130">Permissions that are conveyed through system role assignments determine whether users can view application properties (such as the image or title of the Home page), view or manage shared schedules, or use Report Builder.</span></span>  
  
 <span data-ttu-id="89323-131">有关详细信息，请参阅 [授予用户对报表服务器的访问权限（报表管理器）](grant-user-access-to-a-report-server.md) 和 [预定义角色](role-definitions-predefined-roles.md)。</span><span class="sxs-lookup"><span data-stu-id="89323-131">For more information, see [Grant User Access to a Report Server &#40;Report Manager&#41;](grant-user-access-to-a-report-server.md) and [Predefined Roles](role-definitions-predefined-roles.md).</span></span>  
  
## <a name="modifying-a-role-assignment"></a><span data-ttu-id="89323-132">修改角色分配</span><span class="sxs-lookup"><span data-stu-id="89323-132">Modifying a Role Assignment</span></span>  
 <span data-ttu-id="89323-133">您可以随时修改角色分配。</span><span class="sxs-lookup"><span data-stu-id="89323-133">You can modify a role assignment at any time.</span></span> <span data-ttu-id="89323-134">所做的更改将在保存角色分配后生效。</span><span class="sxs-lookup"><span data-stu-id="89323-134">Your changes take effect when you save the role assignment.</span></span> <span data-ttu-id="89323-135">角色分配的更改不会影响用户会话。</span><span class="sxs-lookup"><span data-stu-id="89323-135">User sessions are not affected by role assignment changes.</span></span> <span data-ttu-id="89323-136">如果在用户打开某个报表期间将角色分配修改为拒绝其访问该报表，则只要会话处于活动状态，用户仍然可以继续使用该报表。</span><span class="sxs-lookup"><span data-stu-id="89323-136">If a user has a report open, and you modify a role assignment to deny access, the user can continue using the report as long as the session is active.</span></span>  
  
 <span data-ttu-id="89323-137">为已经是某个角色分配一部分的组添加用户帐户时，将会出现延迟，然后该用户帐户才能够通过组帐户策略访问项。</span><span class="sxs-lookup"><span data-stu-id="89323-137">If you add a user account to a group that is already part of a role assignment, there will be a delay before the user account is able to access items through the group account policies.</span></span> <span data-ttu-id="89323-138">此延迟由身份验证令牌的 Internet 信息服务 (IIS) 缓存导致。</span><span class="sxs-lookup"><span data-stu-id="89323-138">This delay is caused by Internet Information Services (IIS) caching of authentication tokens.</span></span> <span data-ttu-id="89323-139">您可以等待这些令牌刷新（等待时间通常为十五分钟），也可以重置 IIS 以立即更新缓存。</span><span class="sxs-lookup"><span data-stu-id="89323-139">You can either wait for the tokens to refresh (typically, the wait period is fifteen minutes) or you can reset IIS to update the cache immediately.</span></span>  
  
 <span data-ttu-id="89323-140">一次只能修改一个角色分配。</span><span class="sxs-lookup"><span data-stu-id="89323-140">You can only modify one role assignment at a time.</span></span> <span data-ttu-id="89323-141">您不能通过执行全局搜索-替换操作来更改角色定义名称或角色分配设置，也不能通过这种方式查找包括特定用户或组的所有角色分配。</span><span class="sxs-lookup"><span data-stu-id="89323-141">You cannot perform a global search-and-replace operation to change role definition names or role assignment settings, or to find all the role assignments that include a specific user or group.</span></span>  
  
## <a name="deleting-a-role-assignment"></a><span data-ttu-id="89323-142">删除角色分配</span><span class="sxs-lookup"><span data-stu-id="89323-142">Deleting a Role Assignment</span></span>  
 <span data-ttu-id="89323-143">若要删除角色分配，请选择要删除的每个角色分配旁边的复选框，然后单击 **“删除”**。</span><span class="sxs-lookup"><span data-stu-id="89323-143">You can delete role assignments by selecting the checkbox by each assignment you want to delete, and then clicking **Delete**.</span></span> <span data-ttu-id="89323-144">另一种删除角色分配的方法是单击 **“恢复到父级安全设置”**。</span><span class="sxs-lookup"><span data-stu-id="89323-144">You can also delete role assignments by clicking **Revert to Parent Security**.</span></span> <span data-ttu-id="89323-145">当单击此按钮后，将删除项的现有角色分配，并改用通过父项提供的角色分配。</span><span class="sxs-lookup"><span data-stu-id="89323-145">When you click this button, the existing role assignments for the item are deleted, and those that are provided through a parent item are used instead.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89323-146">另请参阅</span><span class="sxs-lookup"><span data-stu-id="89323-146">See Also</span></span>  
 <span data-ttu-id="89323-147">[授予用户对报表服务器的访问权限 &#40;报表管理器&#41;](grant-user-access-to-a-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="89323-147">[Grant User Access to a Report Server &#40;Report Manager&#41;](grant-user-access-to-a-report-server.md) </span></span>  
 <span data-ttu-id="89323-148">[修改或删除角色分配 &#40;报表管理器&#41;](role-assignments-modify-or-delete.md) </span><span class="sxs-lookup"><span data-stu-id="89323-148">[Modify or Delete a Role Assignment &#40;Report Manager&#41;](role-assignments-modify-or-delete.md) </span></span>  
 <span data-ttu-id="89323-149">[角色分配](role-assignments.md) </span><span class="sxs-lookup"><span data-stu-id="89323-149">[Role Assignments](role-assignments.md) </span></span>  
 <span data-ttu-id="89323-150">[角色定义](role-definitions.md) </span><span class="sxs-lookup"><span data-stu-id="89323-150">[Role Definitions](role-definitions.md) </span></span>  
 <span data-ttu-id="89323-151">[预定义角色](role-definitions-predefined-roles.md) </span><span class="sxs-lookup"><span data-stu-id="89323-151">[Predefined Roles](role-definitions-predefined-roles.md) </span></span>  
 [<span data-ttu-id="89323-152">授予对本机模式报表服务器的权限</span><span class="sxs-lookup"><span data-stu-id="89323-152">Granting Permissions on a Native Mode Report Server</span></span>](granting-permissions-on-a-native-mode-report-server.md)  
  
  
