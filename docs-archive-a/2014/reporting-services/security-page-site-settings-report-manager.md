---
title: “安全性”页（站点设置， 报表管理器) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: acc9a905-90f8-4544-aec6-b2ab3a1b0015
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 997806b8bba92d210a8d108a7101e086f21abb74
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580568"
---
# <a name="security-page-site-settings-report-manager"></a><span data-ttu-id="1a6b0-103">“安全性”页（站点设置，</span><span class="sxs-lookup"><span data-stu-id="1a6b0-103">Security Page (Site Settings.</span></span> <span data-ttu-id="1a6b0-104">报表管理器）</span><span class="sxs-lookup"><span data-stu-id="1a6b0-104">Report Manager)</span></span>
  <span data-ttu-id="1a6b0-105">使用“安全性”页可以查看用来控制报表服务器站点访问权限的系统角色分配。</span><span class="sxs-lookup"><span data-stu-id="1a6b0-105">Use the Security page to view the system role assignments that control access to the report server site.</span></span> <span data-ttu-id="1a6b0-106">系统角色分配存在于报表服务器命名空间或文件夹层次结构范围之外。</span><span class="sxs-lookup"><span data-stu-id="1a6b0-106">System role assignments exist outside of the scope of the report server namespace or folder hierarchy.</span></span> <span data-ttu-id="1a6b0-107">系统角色分配是全局性的，不能随具体项的变化而变化。</span><span class="sxs-lookup"><span data-stu-id="1a6b0-107">System role assignments are global and cannot vary for specific items.</span></span> <span data-ttu-id="1a6b0-108">通过系统角色分配支持的操作包括创建和使用共享计划、使用报表生成器以及为某些服务器功能设置默认值。</span><span class="sxs-lookup"><span data-stu-id="1a6b0-108">Operations that are supported through system role assignments include creating and using shared schedules, using Report Builder, and setting default values for some server features.</span></span>  
  
 <span data-ttu-id="1a6b0-109">在安装报表服务器时将创建默认的系统角色分配。</span><span class="sxs-lookup"><span data-stu-id="1a6b0-109">A default system role assignment is created when the report server is installed.</span></span> <span data-ttu-id="1a6b0-110">此系统角色分配授予本地系统管理员管理报表服务器环境的权限。</span><span class="sxs-lookup"><span data-stu-id="1a6b0-110">This system role assignment grants permissions to local system administrators to manage the report server environment.</span></span> <span data-ttu-id="1a6b0-111">即使删除系统角色分配，本地系统管理员也可以随时设置本地报表服务器的安全性。</span><span class="sxs-lookup"><span data-stu-id="1a6b0-111">A local system administrator can always set security for a local report server, even if system role assignments are deleted.</span></span>  
  
 <span data-ttu-id="1a6b0-112">所有其他需要访问报表生成器或共享计划的用户都必须获得系统角色分配。</span><span class="sxs-lookup"><span data-stu-id="1a6b0-112">All other users who require access to Report Builder or shared schedules must be assigned to a system role assignment.</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="1a6b0-113">导航</span><span class="sxs-lookup"><span data-stu-id="1a6b0-113">Navigation</span></span>  
 <span data-ttu-id="1a6b0-114">使用以下过程导航到用户界面 (UI) 中的这一位置。</span><span class="sxs-lookup"><span data-stu-id="1a6b0-114">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
###### <a name="to-open-the-security-page-for-site-settings"></a><span data-ttu-id="1a6b0-115">打开站点设置的“安全性”页</span><span class="sxs-lookup"><span data-stu-id="1a6b0-115">To open the Security page for Site Settings</span></span>  
  
1.  <span data-ttu-id="1a6b0-116">打开报表管理器。</span><span class="sxs-lookup"><span data-stu-id="1a6b0-116">Open Report Manager.</span></span>  
  
2.  <span data-ttu-id="1a6b0-117">单击页面顶部的 **“站点设置”**。</span><span class="sxs-lookup"><span data-stu-id="1a6b0-117">At the top of the page, click **Site Settings**.</span></span> <span data-ttu-id="1a6b0-118">这会打开该站点的“常规属性”页。</span><span class="sxs-lookup"><span data-stu-id="1a6b0-118">This opens the General Properties page of the site.</span></span>  
  
3.  <span data-ttu-id="1a6b0-119">选择“安全”\*\*\*\* 选项卡。</span><span class="sxs-lookup"><span data-stu-id="1a6b0-119">Select the **Security** tab.</span></span>  
  
## <a name="options"></a><span data-ttu-id="1a6b0-120">选项</span><span class="sxs-lookup"><span data-stu-id="1a6b0-120">Options</span></span>  
 <span data-ttu-id="1a6b0-121">**删除**</span><span class="sxs-lookup"><span data-stu-id="1a6b0-121">**Delete**</span></span>  
 <span data-ttu-id="1a6b0-122">单击此选项可删除现有的角色分配。</span><span class="sxs-lookup"><span data-stu-id="1a6b0-122">Click to delete an existing role assignment.</span></span> <span data-ttu-id="1a6b0-123">在单击 **“删除”** 之前，请选中要删除的组名或用户名旁的复选框。</span><span class="sxs-lookup"><span data-stu-id="1a6b0-123">Before clicking **Delete**, select the check box next to the group or user name that you want to remove.</span></span> <span data-ttu-id="1a6b0-124">如果只剩下一个角色分配，则不能删除它。</span><span class="sxs-lookup"><span data-stu-id="1a6b0-124">You cannot delete a role assignment if it is the only one remaining.</span></span> <span data-ttu-id="1a6b0-125">删除角色分配不会删除组或用户帐户或角色定义。</span><span class="sxs-lookup"><span data-stu-id="1a6b0-125">Deleting a role assignment does not delete a group or user account or role definitions.</span></span>  
  
 <span data-ttu-id="1a6b0-126">**新建角色分配**</span><span class="sxs-lookup"><span data-stu-id="1a6b0-126">**New Role Assignment**</span></span>  
 <span data-ttu-id="1a6b0-127">单击此选项可打开“新建系统角色分配”页，通过该页可以为报表服务器站点创建其他系统角色分配。</span><span class="sxs-lookup"><span data-stu-id="1a6b0-127">Click to open the New System Role Assignments page, which is used to create additional system role assignments for the report server site.</span></span> <span data-ttu-id="1a6b0-128">有关详细信息，请参阅 "[新建系统角色分配：编辑系统角色分配" 页 &#40;报表管理器&#41;](../../2014/reporting-services/new-system-role-assignments-edit-system-role-assignments-page-report-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="1a6b0-128">For more information, see [New System Role Assignments: Edit System Role Assignments Page &#40;Report Manager&#41;](../../2014/reporting-services/new-system-role-assignments-edit-system-role-assignments-page-report-manager.md).</span></span>  
  
 <span data-ttu-id="1a6b0-129">**编辑**</span><span class="sxs-lookup"><span data-stu-id="1a6b0-129">**Edit**</span></span>  
 <span data-ttu-id="1a6b0-130">单击此选项可打开“编辑系统角色分配”页，通过该页可以为报表服务器站点编辑各个系统角色分配。</span><span class="sxs-lookup"><span data-stu-id="1a6b0-130">Click to open the Edit System Role Assignments page, which is used to edit individual system role assignments for the report server site.</span></span> <span data-ttu-id="1a6b0-131">有关详细信息，请参阅 "[新建系统角色分配：编辑系统角色分配" 页 &#40;报表管理器&#41;](../../2014/reporting-services/new-system-role-assignments-edit-system-role-assignments-page-report-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="1a6b0-131">For more information, see [New System Role Assignments: Edit System Role Assignments Page &#40;Report Manager&#41;](../../2014/reporting-services/new-system-role-assignments-edit-system-role-assignments-page-report-manager.md).</span></span>  
  
 <span data-ttu-id="1a6b0-132">**组或用户**</span><span class="sxs-lookup"><span data-stu-id="1a6b0-132">**Group or User**</span></span>  
 <span data-ttu-id="1a6b0-133">列出属于现有角色分配的组和用户。</span><span class="sxs-lookup"><span data-stu-id="1a6b0-133">Lists the groups and users that are part of an existing role assignment.</span></span> <span data-ttu-id="1a6b0-134">当前文件夹的现有角色分配是为此列中显示的组和用户定义的。</span><span class="sxs-lookup"><span data-stu-id="1a6b0-134">Existing role assignments for the current folder are defined for the groups and users that appear in this column.</span></span> <span data-ttu-id="1a6b0-135">单击组名或用户名旁边的 **“编辑”** 可以查看或编辑角色分配的详细信息。</span><span class="sxs-lookup"><span data-stu-id="1a6b0-135">Click **Edit** next to a group or user name to view or edit role assignment details.</span></span>  
  
 <span data-ttu-id="1a6b0-136">**角色**</span><span class="sxs-lookup"><span data-stu-id="1a6b0-136">**Roles**</span></span>  
 <span data-ttu-id="1a6b0-137">列出属于现有角色分配的一个或多个角色定义。</span><span class="sxs-lookup"><span data-stu-id="1a6b0-137">Lists one or more role definitions that are part of an existing role assignment.</span></span> <span data-ttu-id="1a6b0-138">如果给一个组或用户帐户分配了多个角色，那么该组或用户帐户可以执行属于所有这些角色的全部任务。</span><span class="sxs-lookup"><span data-stu-id="1a6b0-138">If multiple roles are assigned to a group or user account, that group or user can perform all tasks that belong to all roles.</span></span> <span data-ttu-id="1a6b0-139">若要查看每个角色支持的任务集，请使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="1a6b0-139">To view the set of tasks that each role supports, use [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="1a6b0-140">不能在报表管理器中查看、创建、修改或删除角色。</span><span class="sxs-lookup"><span data-stu-id="1a6b0-140">You cannot view, create, modify, or delete roles in Report Manager.</span></span> <span data-ttu-id="1a6b0-141">有关说明，请参阅[创建、删除或修改角色 &#40;Management Studio&#41;](security/role-definitions-create-delete-or-modify.md)。</span><span class="sxs-lookup"><span data-stu-id="1a6b0-141">For instructions, see [Create, Delete, or Modify a Role &#40;Management Studio&#41;](security/role-definitions-create-delete-or-modify.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a6b0-142">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1a6b0-142">See Also</span></span>  
 <span data-ttu-id="1a6b0-143">[报表管理器 F1 帮助](../../2014/reporting-services/report-manager-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="1a6b0-143">[Report Manager F1 Help](../../2014/reporting-services/report-manager-f1-help.md) </span></span>  
 [<span data-ttu-id="1a6b0-144">授予对本机模式报表服务器的权限</span><span class="sxs-lookup"><span data-stu-id="1a6b0-144">Granting Permissions on a Native Mode Report Server</span></span>](security/granting-permissions-on-a-native-mode-report-server.md)  
  
  
