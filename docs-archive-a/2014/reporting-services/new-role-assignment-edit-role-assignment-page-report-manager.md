---
title: 新建角色分配：编辑角色分配页 (报表管理器) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 3319ced0-4b86-42af-b18d-da41a625113c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1640617dbf9836986597ee49d4ca1ddc37fd84ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692287"
---
# <a name="new-role-assignment-edit-role-assignment-page-report-manager"></a><span data-ttu-id="208ce-102">“新建角色分配: 编辑角色分配”页（报表管理器）</span><span class="sxs-lookup"><span data-stu-id="208ce-102">New Role Assignment: Edit Role Assignment Page (Report Manager)</span></span>
  <span data-ttu-id="208ce-103">使用“新建角色分配”或“编辑角色分配”页可以授予对报表服务器项和操作的权限。</span><span class="sxs-lookup"><span data-stu-id="208ce-103">Use the New Role Assignment or Edit Role Assignment page to grant permissions to report server items and operations.</span></span> <span data-ttu-id="208ce-104">需要访问报表服务器的每个用户都必须拥有用来定义访问级别的角色分配。</span><span class="sxs-lookup"><span data-stu-id="208ce-104">Each user who requires access to a report server must have a role assignment that defines the level of access.</span></span> <span data-ttu-id="208ce-105">可以针对根节点或者针对特定的报表、模型、文件夹、资源或共享数据源创建角色分配。</span><span class="sxs-lookup"><span data-stu-id="208ce-105">You can create role assignments at the root node, or on a specific report, model, folder, resource, or shared data source.</span></span> [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] <span data-ttu-id="208ce-106">安全性可以通过您应用到项的角色分配来强制执行。</span><span class="sxs-lookup"><span data-stu-id="208ce-106">security is enforced through role assignments that you apply to items.</span></span> <span data-ttu-id="208ce-107">角色分配将某个组或用户匹配到某个角色定义，每个角色定义标识该组或用户可以执行的与某一特定项相关的任务。</span><span class="sxs-lookup"><span data-stu-id="208ce-107">A role assignment matches a group or user to a role definition, where each role definition identifies the tasks that groups or users can perform with regards to a specific item.</span></span>  
  
 <span data-ttu-id="208ce-108">项级的角色分配的影响面可以更广。</span><span class="sxs-lookup"><span data-stu-id="208ce-108">Item-level role assignments can have a broad impact.</span></span> <span data-ttu-id="208ce-109">虽然它们可以与单个报表或文件夹关联，但还可以在文件夹层次结构中的更高级别定义它们，并且树视图中更低位置的文件夹和项可以继承它们。</span><span class="sxs-lookup"><span data-stu-id="208ce-109">Although they can be associated with a single report or folder, they can also be defined at a high level in the folder hierarchy and be inherited by folders and items that are lower in the tree.</span></span> <span data-ttu-id="208ce-110">有关详细信息，请参阅 [授予用户对报表服务器的访问权限（报表管理器）](security/grant-user-access-to-a-report-server.md)。</span><span class="sxs-lookup"><span data-stu-id="208ce-110">For more information, see [Grant User Access to a Report Server &#40;Report Manager&#41;](security/grant-user-access-to-a-report-server.md).</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="208ce-111">导航</span><span class="sxs-lookup"><span data-stu-id="208ce-111">Navigation</span></span>  
 <span data-ttu-id="208ce-112">使用以下过程导航到用户界面 (UI) 中的这一位置。</span><span class="sxs-lookup"><span data-stu-id="208ce-112">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
###### <a name="to-open-the-new-role-assignment-or-edit-role-assignment-page"></a><span data-ttu-id="208ce-113">打开“新建角色分配”或“编辑角色分配”页</span><span class="sxs-lookup"><span data-stu-id="208ce-113">To open the New Role Assignment or Edit Role Assignment page</span></span>  
  
1.  <span data-ttu-id="208ce-114">打开“报表管理器”，并找出您要为其添加新角色分配或编辑角色分配的项。</span><span class="sxs-lookup"><span data-stu-id="208ce-114">Open Report Manager, and locate an item for which you want to add a new role assignment or edit a role assignment.</span></span>  
  
2.  <span data-ttu-id="208ce-115">悬停在该项之上，然后单击下拉箭头。</span><span class="sxs-lookup"><span data-stu-id="208ce-115">Hover over the item, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="208ce-116">在下拉菜单中，单击“安全性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="208ce-116">In the drop-down menu, click **Security**.</span></span> <span data-ttu-id="208ce-117">这会打开该项的“安全属性”页。</span><span class="sxs-lookup"><span data-stu-id="208ce-117">This opens the Security properties page for the item.</span></span>  
  
4.  <span data-ttu-id="208ce-118">如果您要添加新的角色分配，则在工具栏中单击 **“新建角色分配”**。</span><span class="sxs-lookup"><span data-stu-id="208ce-118">If you want to add a new role assignment, in the toolbar, click **New Role Assignment**.</span></span> <span data-ttu-id="208ce-119">如果您要编辑角色分配，请单击要编辑的组或用户名旁边的 **“编辑”** 。</span><span class="sxs-lookup"><span data-stu-id="208ce-119">If you want to edit a role assignment, click **Edit** next to the group or user name you want to edit.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="208ce-120"> 如果某项当前从父项继承安全性，则在工具栏中单击 **“编辑项安全设置”** 可以更改安全设置。</span><span class="sxs-lookup"><span data-stu-id="208ce-120">If an item currently inherits security from a parent item, click **Edit Item Security** in the toolbar to change the security settings.</span></span>  
  
## <a name="options"></a><span data-ttu-id="208ce-121">选项</span><span class="sxs-lookup"><span data-stu-id="208ce-121">Options</span></span>  
 <span data-ttu-id="208ce-122">**组或用户名**</span><span class="sxs-lookup"><span data-stu-id="208ce-122">**Group or User Name**</span></span>  
 <span data-ttu-id="208ce-123">键入要为其创建角色分配的组或用户帐户的名称。</span><span class="sxs-lookup"><span data-stu-id="208ce-123">Type the name of a group or user account for which the role assignment is being created.</span></span> <span data-ttu-id="208ce-124">组名或用户名必须是有效的 Windows 域帐户。</span><span class="sxs-lookup"><span data-stu-id="208ce-124">The group or user name must be a valid Windows domain account.</span></span> <span data-ttu-id="208ce-125">按以下格式输入帐户： \<domain> \\<帐户 \> 。</span><span class="sxs-lookup"><span data-stu-id="208ce-125">Enter the account in this format: \<domain>\\<account\>.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="208ce-126">此框仅可用于“新建角色分配”页上。</span><span class="sxs-lookup"><span data-stu-id="208ce-126">This box is available only on the New Role Assignment page.</span></span>  
  
 <span data-ttu-id="208ce-127">**角色**</span><span class="sxs-lookup"><span data-stu-id="208ce-127">**Role**</span></span>  
 <span data-ttu-id="208ce-128">显示报表服务器中定义的可用于定义项安全性的所有角色。</span><span class="sxs-lookup"><span data-stu-id="208ce-128">Shows all roles defined on the report server that can be used to define security for items.</span></span> <span data-ttu-id="208ce-129">创建或更改报表或文件夹的角色分配时，选择一个或多个角色，直到组合任务集能够说明应允许用户执行的操作。</span><span class="sxs-lookup"><span data-stu-id="208ce-129">When you create or change a role assignment for a report or folder, select one or more roles until the combined set of tasks describe the actions that the user should be allowed to perform.</span></span> <span data-ttu-id="208ce-130">若要查看每个角色支持的任务集，请使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="208ce-130">To view the set of tasks that each role supports, use [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="208ce-131">不能在报表管理器中查看、创建、修改或删除角色。</span><span class="sxs-lookup"><span data-stu-id="208ce-131">You cannot view, create, modify, or delete roles in Report Manager.</span></span> <span data-ttu-id="208ce-132">有关说明，请参阅[创建、删除或修改角色 &#40;Management Studio&#41;](security/role-definitions-create-delete-or-modify.md)。</span><span class="sxs-lookup"><span data-stu-id="208ce-132">For instructions, see [Create, Delete, or Modify a Role &#40;Management Studio&#41;](security/role-definitions-create-delete-or-modify.md).</span></span>  
  
 <span data-ttu-id="208ce-133">**说明**</span><span class="sxs-lookup"><span data-stu-id="208ce-133">**Description**</span></span>  
 <span data-ttu-id="208ce-134">显示有关角色的其他信息。</span><span class="sxs-lookup"><span data-stu-id="208ce-134">Shows additional information about the role.</span></span> <span data-ttu-id="208ce-135">对于预定义的角色（如**浏览器**或**内容管理器**），说明汇总了每个角色支持的任务。</span><span class="sxs-lookup"><span data-stu-id="208ce-135">For predefined roles such as **Browser** or **Content Manager**, the description summarizes the tasks that each role supports.</span></span>  
  
 <span data-ttu-id="208ce-136">**删除角色分配**</span><span class="sxs-lookup"><span data-stu-id="208ce-136">**Delete Role Assignment**</span></span>  
 <span data-ttu-id="208ce-137">单击以删除用户或组的现有角色分配。</span><span class="sxs-lookup"><span data-stu-id="208ce-137">Click to delete an existing role assignment for a user or a group.</span></span> <span data-ttu-id="208ce-138">您不能删除剩余的最后一个角色分配（每个项必须至少有一个角色分配）。</span><span class="sxs-lookup"><span data-stu-id="208ce-138">You cannot delete a role assignment if it is the only one left (each item must have a minimum of one role assignment).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="208ce-139">此按钮仅可用于“编辑角色分配”页上。</span><span class="sxs-lookup"><span data-stu-id="208ce-139">This button is available only on the Edit Role Assignment page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="208ce-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="208ce-140">See Also</span></span>  
 <span data-ttu-id="208ce-141">[创建、删除或修改角色 &#40;Management Studio&#41;](security/role-definitions-create-delete-or-modify.md) </span><span class="sxs-lookup"><span data-stu-id="208ce-141">[Create, Delete, or Modify a Role &#40;Management Studio&#41;](security/role-definitions-create-delete-or-modify.md) </span></span>  
 <span data-ttu-id="208ce-142">[授予对本机模式报表服务器的权限](security/granting-permissions-on-a-native-mode-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="208ce-142">[Granting Permissions on a Native Mode Report Server](security/granting-permissions-on-a-native-mode-report-server.md) </span></span>  
 <span data-ttu-id="208ce-143">[报表管理器（SSRS 本机模式）](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="208ce-143">[Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="208ce-144">[报表管理器 F1 帮助](../../2014/reporting-services/report-manager-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="208ce-144">[Report Manager F1 Help](../../2014/reporting-services/report-manager-f1-help.md) </span></span>  
 <span data-ttu-id="208ce-145">[角色分配](security/role-assignments.md) </span><span class="sxs-lookup"><span data-stu-id="208ce-145">[Role Assignments](security/role-assignments.md) </span></span>  
 [<span data-ttu-id="208ce-146">授予用户对报表服务器的访问权限（报表管理器）</span><span class="sxs-lookup"><span data-stu-id="208ce-146">Grant User Access to a Report Server &#40;Report Manager&#41;</span></span>](security/grant-user-access-to-a-report-server.md)  
  
  
