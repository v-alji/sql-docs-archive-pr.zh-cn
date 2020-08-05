---
title: "\"安全属性\" 页，项 (报表管理器) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 351b8503-354f-4b1b-a7ac-f1245d978da0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 297ae2ceefad89d64c59b5da25d51d541917c894
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580563"
---
# <a name="security-properties-page-items-report-manager"></a><span data-ttu-id="62f40-102">项的“安全性”属性页（报表管理器）</span><span class="sxs-lookup"><span data-stu-id="62f40-102">Security Properties Page, Items (Report Manager)</span></span>
  <span data-ttu-id="62f40-103">使用“安全属性”页可以查看或修改安全设置，以确定对文件夹、报表、模型、资源和共享数据源的访问。</span><span class="sxs-lookup"><span data-stu-id="62f40-103">Use the Security properties page to view or modify the security settings that determine access to folders, reports, models, resources, and shared data sources.</span></span> <span data-ttu-id="62f40-104">此页可用于您有权保护的项。</span><span class="sxs-lookup"><span data-stu-id="62f40-104">This page is available for items that you have permission to secure.</span></span>  
  
 <span data-ttu-id="62f40-105">对项的访问是通过指定某个组或用户可以执行的任务的角色分配来定义的。</span><span class="sxs-lookup"><span data-stu-id="62f40-105">Access to items is defined through role assignments that specify the tasks that a group or user can perform.</span></span> <span data-ttu-id="62f40-106">角色分配包含一个用户名或组名，以及指定一组任务的一个或多个角色定义。</span><span class="sxs-lookup"><span data-stu-id="62f40-106">A role assignment consists of one user or group name and one or more role definitions that specify a collection of tasks.</span></span>  
  
 <span data-ttu-id="62f40-107">安全设置是从根文件夹以及依次向下的各子文件夹和这些文件夹中的项继承而来。</span><span class="sxs-lookup"><span data-stu-id="62f40-107">Security settings are inherited from the root folder down to subfolders and items within those folders.</span></span> <span data-ttu-id="62f40-108">除非明确中断继承的安全性，否则子文件夹和项将继承父项的安全上下文。</span><span class="sxs-lookup"><span data-stu-id="62f40-108">Unless you explicitly break inherited security, subfolders and items inherit the security context of a parent item.</span></span> <span data-ttu-id="62f40-109">如果为位于层次结构中间的某个文件夹重新定义安全策略，其所有子项（包括子文件夹）将采用新的安全设置。</span><span class="sxs-lookup"><span data-stu-id="62f40-109">If you redefine a security policy for a folder in the middle of the hierarchy, all its child items, including subfolders, assume the new security settings.</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="62f40-110">导航</span><span class="sxs-lookup"><span data-stu-id="62f40-110">Navigation</span></span>  
 <span data-ttu-id="62f40-111">使用以下过程导航到用户界面 (UI) 中的这一位置。</span><span class="sxs-lookup"><span data-stu-id="62f40-111">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
###### <a name="to-open-the-security-page-for-an-item"></a><span data-ttu-id="62f40-112">打开项的“安全性”页</span><span class="sxs-lookup"><span data-stu-id="62f40-112">To open the Security page for an item</span></span>  
  
1.  <span data-ttu-id="62f40-113">打开报表管理器，找到要配置安全设置的项。</span><span class="sxs-lookup"><span data-stu-id="62f40-113">Open Report Manager, and locate the item for which you want to configure security settings.</span></span>  
  
2.  <span data-ttu-id="62f40-114">悬停在该项之上，然后单击下拉箭头。</span><span class="sxs-lookup"><span data-stu-id="62f40-114">Hover over the item, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="62f40-115">在下拉菜单中，执行以下步骤之一：</span><span class="sxs-lookup"><span data-stu-id="62f40-115">In the drop-down menu, perform one of the following steps:</span></span>  
  
    -   <span data-ttu-id="62f40-116">单击 **“安全性”** 。</span><span class="sxs-lookup"><span data-stu-id="62f40-116">Click **Security**.</span></span> <span data-ttu-id="62f40-117">这会打开该项的“安全属性”页。</span><span class="sxs-lookup"><span data-stu-id="62f40-117">This opens the Security properties page for the item.</span></span>  
  
    -   <span data-ttu-id="62f40-118">单击 **“管理”** 以打开该项的“常规属性”页。</span><span class="sxs-lookup"><span data-stu-id="62f40-118">Click **Manage** to open the General properties page for the item.</span></span> <span data-ttu-id="62f40-119">然后，选择 **“安全性”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="62f40-119">Then select the **Security** tab.</span></span>  
  
 <span data-ttu-id="62f40-120">**编辑项安全设置**</span><span class="sxs-lookup"><span data-stu-id="62f40-120">**Edit Item Security**</span></span>  
 <span data-ttu-id="62f40-121">单击此选项可更改为当前项定义安全性的方式。</span><span class="sxs-lookup"><span data-stu-id="62f40-121">Click to change how security is defined for the current item.</span></span> <span data-ttu-id="62f40-122">如果编辑文件夹的安全性，则更改将应用于当前文件夹及其所有子文件夹的内容。</span><span class="sxs-lookup"><span data-stu-id="62f40-122">If you are editing security for a folder, your changes apply to the contents of the current folder and any subfolders.</span></span>  
  
 <span data-ttu-id="62f40-123">此按钮对于主文件夹不可用。</span><span class="sxs-lookup"><span data-stu-id="62f40-123">This button is not available for the Home folder.</span></span>  
  
 <span data-ttu-id="62f40-124">编辑项安全性时可以使用以下按钮。</span><span class="sxs-lookup"><span data-stu-id="62f40-124">The following buttons become available when you edit item security.</span></span>  
  
 <span data-ttu-id="62f40-125">**删除**</span><span class="sxs-lookup"><span data-stu-id="62f40-125">**Delete**</span></span>  
 <span data-ttu-id="62f40-126">选中要删除的组名或用户名旁边的复选框，再单击 **“删除”**。</span><span class="sxs-lookup"><span data-stu-id="62f40-126">Select the check box next to the group or user name that you want to delete and click **Delete**.</span></span> <span data-ttu-id="62f40-127">如果角色分配是剩余的唯一角色分配，或者如果它是定义报表服务器的安全基线的内置角色分配（如“Built-in\Administrators”），则不能删除该角色分配。</span><span class="sxs-lookup"><span data-stu-id="62f40-127">You cannot delete a role assignment if it is the only one remaining, or if it is a built-in role assignment (for example, "Built-in\Administrators") that defines the security baseline for the report server.</span></span> <span data-ttu-id="62f40-128">删除角色分配不会删除组或用户帐户或角色定义。</span><span class="sxs-lookup"><span data-stu-id="62f40-128">Deleting a role assignment does not delete a group or user account or role definitions.</span></span>  
  
 <span data-ttu-id="62f40-129">**新建角色分配**</span><span class="sxs-lookup"><span data-stu-id="62f40-129">**New Role Assignment**</span></span>  
 <span data-ttu-id="62f40-130">单击此选项可打开“新建角色分配”页，该页用于为当前项创建其他角色分配。</span><span class="sxs-lookup"><span data-stu-id="62f40-130">Click to open the New Role Assignment page, which is used to create additional role assignments for the current item.</span></span> <span data-ttu-id="62f40-131">有关详细信息，请参阅 "[新建角色分配：编辑角色分配" 页 &#40;报表管理器&#41;](../../2014/reporting-services/new-role-assignment-edit-role-assignment-page-report-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="62f40-131">For more information, see [New Role Assignment: Edit Role Assignment Page &#40;Report Manager&#41;](../../2014/reporting-services/new-role-assignment-edit-role-assignment-page-report-manager.md).</span></span>  
  
 <span data-ttu-id="62f40-132">**恢复到父级安全设置**</span><span class="sxs-lookup"><span data-stu-id="62f40-132">**Revert to Parent Security**</span></span>  
 <span data-ttu-id="62f40-133">单击此选项可将安全设置重置到其直接父文件夹的安全设置。</span><span class="sxs-lookup"><span data-stu-id="62f40-133">Click to reset the security settings to that of the immediate parent folder.</span></span> <span data-ttu-id="62f40-134">如果贯穿报表服务器文件夹层次结构的继承是完整的，则使用顶层文件夹（即主文件夹）的安全设置。</span><span class="sxs-lookup"><span data-stu-id="62f40-134">If inheritance is unbroken throughout the report server folder hierarchy, the security settings of the top-level folder, Home, are used.</span></span>  
  
 <span data-ttu-id="62f40-135">**组或用户**</span><span class="sxs-lookup"><span data-stu-id="62f40-135">**Group or User**</span></span>  
 <span data-ttu-id="62f40-136">列出属于当前项的现有角色分配的组和用户。</span><span class="sxs-lookup"><span data-stu-id="62f40-136">Lists the groups and users that are part of an existing role assignment for the current item.</span></span> <span data-ttu-id="62f40-137">当前文件夹的现有角色分配是为此列中显示的组和用户定义的。</span><span class="sxs-lookup"><span data-stu-id="62f40-137">Existing role assignments for the current folder are defined for the groups and users that appear in this column.</span></span> <span data-ttu-id="62f40-138">单击组名或用户名可以查看或编辑角色分配的详细信息。</span><span class="sxs-lookup"><span data-stu-id="62f40-138">You can click a group or user name to view or edit role assignment details.</span></span>  
  
 <span data-ttu-id="62f40-139">**角色**</span><span class="sxs-lookup"><span data-stu-id="62f40-139">**Roles**</span></span>  
 <span data-ttu-id="62f40-140">列出属于现有角色分配的一个或多个角色定义。</span><span class="sxs-lookup"><span data-stu-id="62f40-140">Lists one or more role definitions that are part of an existing role assignment.</span></span> <span data-ttu-id="62f40-141">如果为一个组帐户或用户帐户分配了多个角色，则该组或用户可以执行属于这些角色的所有任务。</span><span class="sxs-lookup"><span data-stu-id="62f40-141">If multiple roles are assigned to a group or user account, that group or user can perform all tasks that belong to those roles.</span></span> <span data-ttu-id="62f40-142">若要查看与角色关联的任务，请使用 SQL Server Management Studio 来查看每个角色定义中的任务。</span><span class="sxs-lookup"><span data-stu-id="62f40-142">To view the tasks that are associated with a role, use SQL Server Management Studio to view the tasks in each role definition.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62f40-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="62f40-143">See Also</span></span>  
 <span data-ttu-id="62f40-144">[报表管理器 F1 帮助](../../2014/reporting-services/report-manager-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="62f40-144">[Report Manager F1 Help](../../2014/reporting-services/report-manager-f1-help.md) </span></span>  
 <span data-ttu-id="62f40-145">[预定义角色](security/role-definitions-predefined-roles.md) </span><span class="sxs-lookup"><span data-stu-id="62f40-145">[Predefined Roles](security/role-definitions-predefined-roles.md) </span></span>  
 <span data-ttu-id="62f40-146">[授予对本机模式报表服务器的权限](security/granting-permissions-on-a-native-mode-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="62f40-146">[Granting Permissions on a Native Mode Report Server](security/granting-permissions-on-a-native-mode-report-server.md) </span></span>  
 <span data-ttu-id="62f40-147">[角色分配](security/role-assignments.md) </span><span class="sxs-lookup"><span data-stu-id="62f40-147">[Role Assignments](security/role-assignments.md) </span></span>  
 [<span data-ttu-id="62f40-148">角色定义</span><span class="sxs-lookup"><span data-stu-id="62f40-148">Role Definitions</span></span>](security/role-definitions.md)  
  
  
