---
title: 新系统角色分配： "编辑系统角色分配" 页 (报表管理器) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 62a22ab9-1eb4-4ce5-8dd7-06b5ed2d9a2a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6e04ec18b8ee27c5897156753c1e4f7991991eae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578694"
---
# <a name="new-system-role-assignments-edit-system-role-assignments-page-report-manager"></a><span data-ttu-id="0de64-102">“新建系统角色分配: 编辑系统角色分配”页（报表管理器）</span><span class="sxs-lookup"><span data-stu-id="0de64-102">New System Role Assignments: Edit System Role Assignments Page (Report Manager)</span></span>
  <span data-ttu-id="0de64-103">使用“新建系统角色分配”页或“编辑系统角色分配”页可以定义报表服务器的安全性。</span><span class="sxs-lookup"><span data-stu-id="0de64-103">Use the New System Role Assignments or Edit System Role Assignments page to define security for the report server.</span></span> <span data-ttu-id="0de64-104">所有安全性都是通过将特定用户或组映射到这些用户或组可以执行的任务的角色分配来定义的。</span><span class="sxs-lookup"><span data-stu-id="0de64-104">All security is defined through role assignments that map specific users or groups to the tasks that they can perform.</span></span> <span data-ttu-id="0de64-105">任务列表表现为您在进行角色分配时选择的角色定义。</span><span class="sxs-lookup"><span data-stu-id="0de64-105">The task list is represented as a role definition that you select when making the role assignment.</span></span>  
  
 <span data-ttu-id="0de64-106">在系统级，您创建或修改的角色分配应用于整个报表服务器。</span><span class="sxs-lookup"><span data-stu-id="0de64-106">At the system level, the role assignments that you create or modify apply to the report server as a whole.</span></span> <span data-ttu-id="0de64-107">例如，创建共享计划的权限是在系统级指定的，因为共享计划在整个系统中使用。</span><span class="sxs-lookup"><span data-stu-id="0de64-107">For example, the ability to create shared schedules is specified at the system level because shared schedules are used throughout the system.</span></span>  
  
 <span data-ttu-id="0de64-108">默认情况下，Reporting Services 提供两个预定义的系统级角色：</span><span class="sxs-lookup"><span data-stu-id="0de64-108">By default, Reporting Services provides two predefined system level roles:</span></span>  
  
-   <span data-ttu-id="0de64-109">系统用户包含允许用户查看报表服务器属性和共享计划的任务，以及允许用户执行报表定义的任务，此类任务允许用户查看已经发布到报表服务器的点击链接型报表。</span><span class="sxs-lookup"><span data-stu-id="0de64-109">System User includes tasks that allow users to view report server properties and shared schedules, and to execute report definitions, which allows users to view clickthrough reports that have been published to the report server.</span></span> <span data-ttu-id="0de64-110">大部分用户都应当获得此角色分配。</span><span class="sxs-lookup"><span data-stu-id="0de64-110">Most users should be assigned to this role.</span></span>  
  
-   <span data-ttu-id="0de64-111">“系统管理员”角色包括用来创建和管理共享计划、设置服务器属性和为其他用户创建系统级角色分配的任务。</span><span class="sxs-lookup"><span data-stu-id="0de64-111">System Administrator includes tasks for creating and managing shared schedules, setting server properties, and creating system-level role assignments for other users.</span></span> <span data-ttu-id="0de64-112">只有极少用户才需要此级别的权限。</span><span class="sxs-lookup"><span data-stu-id="0de64-112">Few users require permissions at this level.</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="0de64-113">导航</span><span class="sxs-lookup"><span data-stu-id="0de64-113">Navigation</span></span>  
 <span data-ttu-id="0de64-114">使用以下过程导航到用户界面 (UI) 中的这一位置。</span><span class="sxs-lookup"><span data-stu-id="0de64-114">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
###### <a name="to-open-the-new-system-role-assignments-or-edit-system-role-assignments-page"></a><span data-ttu-id="0de64-115">打开“新建系统角色分配”或“编辑系统角色分配”页</span><span class="sxs-lookup"><span data-stu-id="0de64-115">To open the New System Role Assignments or Edit System Role Assignments page</span></span>  
  
1.  <span data-ttu-id="0de64-116">打开报表管理器。</span><span class="sxs-lookup"><span data-stu-id="0de64-116">Open Report Manager.</span></span>  
  
2.  <span data-ttu-id="0de64-117">在页面顶部的右角，单击 **“站点设置”**。</span><span class="sxs-lookup"><span data-stu-id="0de64-117">At the top of the page, in the right-hand corner, click **Site Settings**.</span></span> <span data-ttu-id="0de64-118">这会打开该站点的“常规属性”页。</span><span class="sxs-lookup"><span data-stu-id="0de64-118">This opens the General properties page for the site.</span></span>  
  
3.  <span data-ttu-id="0de64-119">选择 "**安全**" 选项卡。您必须具有 "内容管理员" 和 "系统管理员" 权限才能访问此页。</span><span class="sxs-lookup"><span data-stu-id="0de64-119">Select the **Security** tab. You must have Content Manager and System Administrator permissions to access this page.</span></span>  
  
4.  <span data-ttu-id="0de64-120">要创建新的角色分配，在工具栏中单击 **“新建角色分配”** 。</span><span class="sxs-lookup"><span data-stu-id="0de64-120">To create a new role assignment, click **New Role Assignment** in the toolbar.</span></span> <span data-ttu-id="0de64-121">要编辑现有角色分配，请在“安全属性”页上单击组或用户旁边的 **“编辑”** 。</span><span class="sxs-lookup"><span data-stu-id="0de64-121">To edit an existing role assignment, click **Edit** next to a group or user on the Security properties page.</span></span>  
  
## <a name="options"></a><span data-ttu-id="0de64-122">选项</span><span class="sxs-lookup"><span data-stu-id="0de64-122">Options</span></span>  
 <span data-ttu-id="0de64-123">**组或用户**</span><span class="sxs-lookup"><span data-stu-id="0de64-123">**Group or User**</span></span>  
 <span data-ttu-id="0de64-124">键入域中的组或用户帐户的名称。</span><span class="sxs-lookup"><span data-stu-id="0de64-124">Type the name of a group or user account in your domain.</span></span> <span data-ttu-id="0de64-125">如果报表服务器在本地帐户下运行，则必须指定本地组或用户。</span><span class="sxs-lookup"><span data-stu-id="0de64-125">If the report server is running under a local account, you must specify local groups or users.</span></span> <span data-ttu-id="0de64-126">如果报表服务器在域帐户下运行，则必须指定域组或域用户。</span><span class="sxs-lookup"><span data-stu-id="0de64-126">If the report server is running under a domain account, you must specify domain groups or users.</span></span> <span data-ttu-id="0de64-127">按以下格式输入帐户： \<domain> \\<帐户 \> 。</span><span class="sxs-lookup"><span data-stu-id="0de64-127">Enter the account in this format: \<domain>\\<account\>.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0de64-128">此框仅可用于“新建角色分配”页上。</span><span class="sxs-lookup"><span data-stu-id="0de64-128">This box is available only on the New Role Assignment page.</span></span>  
  
 <span data-ttu-id="0de64-129">**角色**</span><span class="sxs-lookup"><span data-stu-id="0de64-129">**Roles**</span></span>  
 <span data-ttu-id="0de64-130">提供可以分配给其他用户的系统级角色的列表。</span><span class="sxs-lookup"><span data-stu-id="0de64-130">Provides a list of system-level roles that you can assign to other users.</span></span> <span data-ttu-id="0de64-131">可以为单个角色分配指定多个角色。</span><span class="sxs-lookup"><span data-stu-id="0de64-131">You can specify multiple roles for a single role assignment.</span></span>  
  
 <span data-ttu-id="0de64-132">报表管理器不显示每个角色中的任务，也不提供用来添加或修改任务的方法。</span><span class="sxs-lookup"><span data-stu-id="0de64-132">Report Manager does not display the tasks in each role or provide a way to add or modify the tasks.</span></span> <span data-ttu-id="0de64-133">您必须按照角色的定义使用角色。</span><span class="sxs-lookup"><span data-stu-id="0de64-133">You must use the roles as they are defined.</span></span> <span data-ttu-id="0de64-134">若要创建、修改或删除角色，请使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="0de64-134">To create, modify, or delete roles, use [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="0de64-135">有关详细信息，请参阅 [创建、删除或修改角色 (Management Studio)](security/role-definitions-create-delete-or-modify.md)。</span><span class="sxs-lookup"><span data-stu-id="0de64-135">For more information, see [Create, Delete, or Modify a Role &#40;Management Studio&#41;](security/role-definitions-create-delete-or-modify.md).</span></span>  
  
 <span data-ttu-id="0de64-136">请注意，如果使用的是具有高级服务的 [!INCLUDE[ssExpressEd2005](../includes/ssexpressed2005-md.md)] ，则必须使用所提供的默认角色。</span><span class="sxs-lookup"><span data-stu-id="0de64-136">Note that if you are using [!INCLUDE[ssExpressEd2005](../includes/ssexpressed2005-md.md)] with Advanced Services, you must use the default roles that are provided.</span></span>  
  
 <span data-ttu-id="0de64-137">**说明**</span><span class="sxs-lookup"><span data-stu-id="0de64-137">**Descriptions**</span></span>  
 <span data-ttu-id="0de64-138">显示有关角色的其他信息。</span><span class="sxs-lookup"><span data-stu-id="0de64-138">Shows additional information about the role.</span></span> <span data-ttu-id="0de64-139">对于预定义角色（如系统用户或系统管理员），说明概述每个角色支持的任务。</span><span class="sxs-lookup"><span data-stu-id="0de64-139">For predefined roles such as System User or System Administrator, the description summarizes the tasks that each role supports.</span></span>  
  
 <span data-ttu-id="0de64-140">**删除角色分配**</span><span class="sxs-lookup"><span data-stu-id="0de64-140">**Delete Role Assignment**</span></span>  
 <span data-ttu-id="0de64-141">单击以删除用户或组的现有角色分配。</span><span class="sxs-lookup"><span data-stu-id="0de64-141">Click to delete an existing role assignment for a user or a group.</span></span> <span data-ttu-id="0de64-142">您不能删除剩余的最后一个角色分配（每个项必须至少有一个角色分配）。</span><span class="sxs-lookup"><span data-stu-id="0de64-142">You cannot delete a role assignment if it is the only one left (each item must have a minimum of one role assignment).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0de64-143">此按钮仅可用于“编辑角色分配”页上。</span><span class="sxs-lookup"><span data-stu-id="0de64-143">This button is available only on the Edit Role Assignment page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0de64-144">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0de64-144">See Also</span></span>  
 <span data-ttu-id="0de64-145">[报表管理器 F1 帮助](../../2014/reporting-services/report-manager-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="0de64-145">[Report Manager F1 Help](../../2014/reporting-services/report-manager-f1-help.md) </span></span>  
 <span data-ttu-id="0de64-146">[角色分配](security/role-assignments.md) </span><span class="sxs-lookup"><span data-stu-id="0de64-146">[Role Assignments](security/role-assignments.md) </span></span>  
 [<span data-ttu-id="0de64-147">角色定义</span><span class="sxs-lookup"><span data-stu-id="0de64-147">Role Definitions</span></span>](security/role-definitions.md)  
  
  
