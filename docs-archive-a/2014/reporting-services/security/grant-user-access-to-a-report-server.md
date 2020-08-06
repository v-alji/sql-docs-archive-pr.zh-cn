---
title: 授予用户对报表服务器的访问权限 (报表管理器) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- removing role assignments
- permissions [Reporting Services], granting report server access
- roles [Reporting Services], assignments
- modifying role assignments
- deleting role assignments
ms.assetid: 2144c020-3253-4b47-8cda-e14c928bb471
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bceaa648827d756e2b301662ce281b37a76d6839
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688487"
---
# <a name="grant-user-access-to-a-report-server-report-manager"></a><span data-ttu-id="90430-102">授予用户对报表服务器的访问权限（报表管理器）</span><span class="sxs-lookup"><span data-stu-id="90430-102">Grant User Access to a Report Server (Report Manager)</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="90430-103">使用基于角色的安全性向用户授予对报表服务器的访问权限。</span><span class="sxs-lookup"><span data-stu-id="90430-103">uses role-based security to grant user access to a report server.</span></span> <span data-ttu-id="90430-104">在新安装的报表服务器上，只有作为本地 Administrators 组的成员的用户具有对报表服务器内容和操作的权限。</span><span class="sxs-lookup"><span data-stu-id="90430-104">On a new report server installation, only users who are members of the local Administrators group have permissions to report server content and operations.</span></span> <span data-ttu-id="90430-105">若要使其他用户可以使用报表服务器，必须创建将用户帐户或组帐户映射到指定任务集合的预定义角色的角色分配。</span><span class="sxs-lookup"><span data-stu-id="90430-105">To make the report server available to other users, you must create role assignments that map  user or group accounts to a predefined role that specifies a collection of tasks.</span></span>  
  
 <span data-ttu-id="90430-106">**SharePoint 模式报表服务器：** 对于配置为 SharePoint 集成模式的报表服务器，使用 SharePoint 权限从 SharePoint 站点配置访问权限。</span><span class="sxs-lookup"><span data-stu-id="90430-106">**SharePoint mode report servers:** For a report server that is configured for SharePoint integrated mode, you configure access from a SharePoint site using SharePoint permissions.</span></span> <span data-ttu-id="90430-107">对 SharePoint 站点的权限级别确定对报表服务器内容和操作的访问权限。</span><span class="sxs-lookup"><span data-stu-id="90430-107">Permission levels on the SharePoint site determine access to report server content and operations.</span></span> <span data-ttu-id="90430-108">您必须是站点管理员才能授予对 SharePoint 站点的权限。</span><span class="sxs-lookup"><span data-stu-id="90430-108">You must be a site administrator to grant permissions on a SharePoint site.</span></span> <span data-ttu-id="90430-109">有关详细信息，请参阅 [在 SharePoint 站点上授予对报表服务器项的权限](granting-permissions-on-report-server-items-on-a-sharepoint-site.md)。</span><span class="sxs-lookup"><span data-stu-id="90430-109">For more information, see [Granting Permissions on Report Server Items on a SharePoint Site](granting-permissions-on-report-server-items-on-a-sharepoint-site.md).</span></span>  
  
 <span data-ttu-id="90430-110">**本机模式报表服务器：** 本主题侧重于配置为本机模式的报表服务器以及使用报表管理器向角色分配用户。</span><span class="sxs-lookup"><span data-stu-id="90430-110">**Native mode report servers:** This topic is focused on a report server that is configured for native mode and the use of Report Manager to assign users to a role.</span></span> <span data-ttu-id="90430-111">有两种类型的角色：</span><span class="sxs-lookup"><span data-stu-id="90430-111">There are two types of roles:</span></span>  
  
-   <span data-ttu-id="90430-112">项级角色用于查看、添加和管理报表服务器内容、订阅、报表处理和报表历史记录。</span><span class="sxs-lookup"><span data-stu-id="90430-112">Item-level roles are used to view, add, and manage report server content, subscriptions, report processing, and report history.</span></span> <span data-ttu-id="90430-113">可以对根节点（主文件夹）或位于该层次结构中的特定下级文件夹或项定义项级角色分配。</span><span class="sxs-lookup"><span data-stu-id="90430-113">Item-level role assignments are defined on the root node (the Home folder) or on specific folders or items farther down the hierarchy.</span></span>  
  
-   <span data-ttu-id="90430-114">系统级角色授予对不限于任何特定项的站点范围操作的访问权限。</span><span class="sxs-lookup"><span data-stu-id="90430-114">System-level roles grant access to site-wide operations that are not bound to any specific item.</span></span> <span data-ttu-id="90430-115">例如，使用报表生成器和使用共享计划。</span><span class="sxs-lookup"><span data-stu-id="90430-115">Examples include using Report Builder and using shared schedules.</span></span>  
  
     <span data-ttu-id="90430-116">两种类型的角色互为补充，应结合使用。</span><span class="sxs-lookup"><span data-stu-id="90430-116">The two types of roles complement each other and should be used together.</span></span> <span data-ttu-id="90430-117">因此，将用户添加到报表服务器的操作分为两个部分。</span><span class="sxs-lookup"><span data-stu-id="90430-117">For this reason, adding a user to a report server is a two-part operation.</span></span> <span data-ttu-id="90430-118">如果将用户分配到项级角色，则还应将该用户分配到系统级角色。</span><span class="sxs-lookup"><span data-stu-id="90430-118">If you assign a user to an item-level role, you should also assign them to a system-level role.</span></span> <span data-ttu-id="90430-119">将用户分配到角色时，必须选择已定义的角色。</span><span class="sxs-lookup"><span data-stu-id="90430-119">When assigning a user to a role, you must select a role that is already defined.</span></span> <span data-ttu-id="90430-120">若要创建、修改或删除角色，请使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="90430-120">To create, modify, or delete roles, use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="90430-121">有关详细信息，请参阅 [创建、删除或修改角色 (Management Studio)](role-definitions-create-delete-or-modify.md)。</span><span class="sxs-lookup"><span data-stu-id="90430-121">For more information, see [Create, Delete, or Modify a Role &#40;Management Studio&#41;](role-definitions-create-delete-or-modify.md).</span></span>  
  
## <a name="before-you-start"></a><span data-ttu-id="90430-122">开始之前</span><span class="sxs-lookup"><span data-stu-id="90430-122">Before you start</span></span>  
 <span data-ttu-id="90430-123">在将用户添加到本机模式的报表服务器之前查看以下列表。</span><span class="sxs-lookup"><span data-stu-id="90430-123">Review the following list before adding users to a native mode report server.</span></span>  
  
-   <span data-ttu-id="90430-124">您必须是报表服务器计算机上本地 Administrators 组的成员。</span><span class="sxs-lookup"><span data-stu-id="90430-124">You must be a member of the local Administrators group on the report server computer.</span></span> <span data-ttu-id="90430-125">如果在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 或 Windows Server 2008 上部署 [!INCLUDE[wiprlhlong](../../includes/wiprlhlong-md.md)] ，则需要进行额外配置，然后才能在本地管理报表服务器。</span><span class="sxs-lookup"><span data-stu-id="90430-125">If you are deploying [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] on [!INCLUDE[wiprlhlong](../../includes/wiprlhlong-md.md)] or Windows Server 2008, additional configuration is required before you can administer a report server locally.</span></span> <span data-ttu-id="90430-126">有关详细信息，请参阅 [为本地管理配置本机模式报表服务器 (SSRS)](../report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="90430-126">For more information, see [Configure a Native Mode Report Server for Local Administration &#40;SSRS&#41;](../report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).</span></span>  
  
-   <span data-ttu-id="90430-127">若要将此任务委托给其他用户，请创建将用户帐户映射到“内容管理员”和“系统管理员”角色的角色分配。</span><span class="sxs-lookup"><span data-stu-id="90430-127">To delegate this task to other users, create role assignments that map user accounts to Content Manager and System Administrator roles.</span></span> <span data-ttu-id="90430-128">具有“内容管理员”和“系统管理员”权限的用户可以将用户添加到报表服务器。</span><span class="sxs-lookup"><span data-stu-id="90430-128">Users who have Content Manager and System Administrator permissions can add users to a report server.</span></span>  
  
-   <span data-ttu-id="90430-129">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 中，查看“系统角色”和“用户角色”的预定义角色，以便熟悉每个角色中的各种任务。</span><span class="sxs-lookup"><span data-stu-id="90430-129">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], view the predefined roles for System Roles and User Roles so that you are familiar with the kinds of tasks in each role.</span></span> <span data-ttu-id="90430-130">由于报表管理器中不显示任务说明，因此需要在开始添加用户之前熟悉角色。</span><span class="sxs-lookup"><span data-stu-id="90430-130">Task descriptions are not visible in Report Manager, so you will want to be familiar with the roles before you begin adding users.</span></span>  
  
-   <span data-ttu-id="90430-131">根据需要自定义这两个角色或定义其他角色以包括所需的任务集合。</span><span class="sxs-lookup"><span data-stu-id="90430-131">Optionally, customize the roles or define additional roles to include the collection of tasks that you require.</span></span> <span data-ttu-id="90430-132">例如，如果计划对单独的项使用自定义安全设置，则可能希望创建新的角色定义以授予对文件夹的查看访问权限。</span><span class="sxs-lookup"><span data-stu-id="90430-132">For example, if you plan to use custom security settings for individual items, you might want to create a new role definition that grants view-access to folders.</span></span>  
  
### <a name="to-add-a-user-or-group-to-a-system-role"></a><span data-ttu-id="90430-133">向系统角色添加用户或组</span><span class="sxs-lookup"><span data-stu-id="90430-133">To add a user or group to a system role</span></span>  
  
1.  <span data-ttu-id="90430-134">启动 [报表管理器（SSRS 本机模式）](../report-manager-ssrs-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="90430-134">Start [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="90430-135">单击 **“网站设置”** 。</span><span class="sxs-lookup"><span data-stu-id="90430-135">Click **Site Settings**.</span></span>  
  
3.  <span data-ttu-id="90430-136">单击 **“安全性”** 。</span><span class="sxs-lookup"><span data-stu-id="90430-136">Click **Security**.</span></span>  
  
4.  <span data-ttu-id="90430-137">单击 **“新建角色分配”**。</span><span class="sxs-lookup"><span data-stu-id="90430-137">Click **New Role Assignment**.</span></span>  
  
5.  <span data-ttu-id="90430-138">在 "**组或用户名**" 中，按以下格式输入 Windows 域用户或组帐户： \<domain> \\<帐户 \> 。</span><span class="sxs-lookup"><span data-stu-id="90430-138">In **Group or user name**, enter a Windows domain user or group account in this format: \<domain>\\<account\>.</span></span> <span data-ttu-id="90430-139">如果使用窗体身份验证或自定义安全性，则以适用于您的部署的格式指定该用户帐户或组帐户。</span><span class="sxs-lookup"><span data-stu-id="90430-139">If you are using forms authentication or custom security, specify the user or group account in the format that is correct for your deployment.</span></span>  
  
6.  <span data-ttu-id="90430-140">选择一个系统角色，然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="90430-140">Select a system role, and then click **OK**.</span></span>  
  
     <span data-ttu-id="90430-141">角色是可累积的，因此如果同时选择了“系统管理员”和“系统用户”，则用户或组可以执行这两种角色的任务。</span><span class="sxs-lookup"><span data-stu-id="90430-141">Roles are cumulative, so if you select both System Administrator and System User, a user or group will be able to perform the tasks in both roles.</span></span>  
  
7.  <span data-ttu-id="90430-142">重复上述步骤，为其他用户或组创建分配。</span><span class="sxs-lookup"><span data-stu-id="90430-142">Repeat to create assignments for additional users or groups.</span></span>  
  
### <a name="to-add-a-user-or-group-to-an-item-role"></a><span data-ttu-id="90430-143">向项角色添加用户或组</span><span class="sxs-lookup"><span data-stu-id="90430-143">To add a user or group to an item role</span></span>  
  
1.  <span data-ttu-id="90430-144">启动 **“报表管理器”** 并找出您要为其添加用户或组的报表项。</span><span class="sxs-lookup"><span data-stu-id="90430-144">Start **Report Manager** and locate the report item for which you want to add a user or group.</span></span>  
  
2.  <span data-ttu-id="90430-145">悬停在该项之上，然后单击下拉箭头。</span><span class="sxs-lookup"><span data-stu-id="90430-145">Hover over the item, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="90430-146">在下拉菜单中，单击“安全性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="90430-146">In the drop-down menu, click **Security**.</span></span>  
  
4.  <span data-ttu-id="90430-147">单击 **“新建角色分配”**。</span><span class="sxs-lookup"><span data-stu-id="90430-147">Click **New Role Assignment**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="90430-148"> 如果某项当前从父项继承安全性，则在工具栏中单击 **“编辑项安全设置”** 可以更改安全设置。</span><span class="sxs-lookup"><span data-stu-id="90430-148">If an item currently inherits security from a parent item, click **Edit Item Security** in the toolbar to change the security settings.</span></span> <span data-ttu-id="90430-149">然后，单击 **“新建角色分配”**。</span><span class="sxs-lookup"><span data-stu-id="90430-149">Then click **New Role Assignment**.</span></span>  
  
5.  <span data-ttu-id="90430-150">在 "**组或用户名**" 中，按以下格式输入 Windows 域用户或组帐户： \<domain> \\<帐户 \> 。</span><span class="sxs-lookup"><span data-stu-id="90430-150">In **Group or user name**, enter a Windows domain user or group account in this format: \<domain>\\<account\>.</span></span> <span data-ttu-id="90430-151">如果使用窗体身份验证或自定义安全性，则以适用于您的部署的格式指定该用户帐户或组帐户。</span><span class="sxs-lookup"><span data-stu-id="90430-151">If you are using forms authentication or custom security, specify the user or group account in the format that is correct for your deployment.</span></span>  
  
6.  <span data-ttu-id="90430-152">选择一个或多个角色定义（说明用户或组应如何访问该项），再单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="90430-152">Select one or more role definitions that describe how the user or group should access the item, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="90430-153">重复上述步骤，为其他用户或组创建分配。</span><span class="sxs-lookup"><span data-stu-id="90430-153">Repeat to create assignments for additional users or groups.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90430-154">另请参阅</span><span class="sxs-lookup"><span data-stu-id="90430-154">See Also</span></span>  
 <span data-ttu-id="90430-155"> (create-and-manage-role-assignments.md) </span><span class="sxs-lookup"><span data-stu-id="90430-155">(create-and-manage-role-assignments.md)</span></span>   
 <span data-ttu-id="90430-156">[新建角色分配：编辑角色分配页 &#40;报表管理器&#41;](../new-role-assignment-edit-role-assignment-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="90430-156">[New Role Assignment: Edit Role Assignment Page &#40;Report Manager&#41;](../new-role-assignment-edit-role-assignment-page-report-manager.md) </span></span>  
 <span data-ttu-id="90430-157">["安全属性" 页，项 &#40;报表管理器&#41;](../security-properties-page-items-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="90430-157">[Security Properties Page, Items &#40;Report Manager&#41;](../security-properties-page-items-report-manager.md) </span></span>  
 <span data-ttu-id="90430-158">[角色分配](role-assignments.md) </span><span class="sxs-lookup"><span data-stu-id="90430-158">[Role Assignments](role-assignments.md) </span></span>  
 [<span data-ttu-id="90430-159">角色定义</span><span class="sxs-lookup"><span data-stu-id="90430-159">Role Definitions</span></span>](role-definitions.md)  
  
  
