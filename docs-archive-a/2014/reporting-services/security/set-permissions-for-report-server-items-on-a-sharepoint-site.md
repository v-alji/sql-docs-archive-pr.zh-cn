---
title: 为 sharepoint 站点上的报表服务器项设置权限) SharePoint 集成模式下的 (Reporting Services |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- permissions [Reporting Services], SharePoint integrated mode
- SharePoint integration [Reporting Services], permissions
ms.assetid: 2467c657-a3bf-4ec3-a88c-8877df19823d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f38497843ca99342f13952153d7fed957564e006
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688480"
---
# <a name="set-permissions-for-report-server-items-on-a-sharepoint-site-reporting-services-in-sharepoint-integrated-mode"></a><span data-ttu-id="326e7-102">在 SharePoint 站点上为报表服务器项设置权限（SharePoint 集成模式下的 Reporting Services）</span><span class="sxs-lookup"><span data-stu-id="326e7-102">Set Permissions for Report Server Items on a SharePoint Site (Reporting Services in SharePoint Integrated Mode)</span></span>
  <span data-ttu-id="326e7-103">如果默认安全设置未提供您需要的访问权限级别，则可以创建新的权限级别以提供对特定报表服务器项或操作的访问权限。</span><span class="sxs-lookup"><span data-stu-id="326e7-103">If default security settings do not provide the level of access that you require, you can create new permission levels to provide access to specific report server items or operations.</span></span> <span data-ttu-id="326e7-104">如果希望限制对特定报表的访问权限，则自定义安全设置非常有用。</span><span class="sxs-lookup"><span data-stu-id="326e7-104">Custom security settings can be useful if you want to restrict access to a particular report.</span></span>  
  
 <span data-ttu-id="326e7-105">您必须是站点所有者才能创建权限级别和组。</span><span class="sxs-lookup"><span data-stu-id="326e7-105">You must be a site owner to create permission levels and groups.</span></span> <span data-ttu-id="326e7-106">权限级别通用于整个站点。</span><span class="sxs-lookup"><span data-stu-id="326e7-106">Permission levels are used globally throughout a site.</span></span> <span data-ttu-id="326e7-107">如果您创建新的权限级别，其他站点所有者也将可以使用它。</span><span class="sxs-lookup"><span data-stu-id="326e7-107">If you create a new permission level, it will be available to other site owners.</span></span>  
  
 <span data-ttu-id="326e7-108">大多数权限都继承自父站点。</span><span class="sxs-lookup"><span data-stu-id="326e7-108">Most permissions are inherited from a parent site.</span></span> <span data-ttu-id="326e7-109">如果您对特定库或项分配权限，则会中断权限继承并引发额外开销，即如何管理站点层次结构中该分支的权限。</span><span class="sxs-lookup"><span data-stu-id="326e7-109">If you assign permissions on a specific library or item, you break permission inheritance and incur additional overhead in how manage permissions for that branch of your site hierarchy.</span></span>  
  
 <span data-ttu-id="326e7-110">可以对报表定义 (.rdl)、模型 (.smdl) 和共享数据源 (.rsds) 文件设置权限。</span><span class="sxs-lookup"><span data-stu-id="326e7-110">You can set permissions on report definition (.rdl), model (.smdl), and shared data source (.rsds) files.</span></span> <span data-ttu-id="326e7-111">无法在同一个项目上结合使用继承的权限和托管的权限。</span><span class="sxs-lookup"><span data-stu-id="326e7-111">You cannot combine inherited and managed permissions on the same item.</span></span> <span data-ttu-id="326e7-112">如果选择直接管理权限，则继承的权限将不会对当前项产生任何影响。</span><span class="sxs-lookup"><span data-stu-id="326e7-112">If you choose to manage permissions directly, inherited permissions will have no effect on the current item.</span></span> <span data-ttu-id="326e7-113">如果希望以后恢复权限继承，则可以选择 **“操作”** 菜单中的 **“继承权限”** 。</span><span class="sxs-lookup"><span data-stu-id="326e7-113">If you want to resume permission inheritance later, you can select **Inherit Permissions** on the **Actions** menu.</span></span>  
  
 <span data-ttu-id="326e7-114">若要设置对模型中的实体和透视的权限，您必须拥有该模型的“完全控制”级权限。</span><span class="sxs-lookup"><span data-stu-id="326e7-114">To set permissions on entities and perspectives in a model, you must have Full Control level of permission for the model.</span></span> <span data-ttu-id="326e7-115">“完全控制”包括“管理权限”，后者是授予站点所有者和其他拥有“完全控制”级权限的 SharePoint 组的站点级权限。</span><span class="sxs-lookup"><span data-stu-id="326e7-115">Full Control includes "Manage Permissions", which is a site level permission that is granted to site owners and other SharePoint groups who have Full Control level of permission.</span></span> <span data-ttu-id="326e7-116">如果希望使特定用户能够设置模型项安全性，则必须中断权限继承并授予用户或组对该模型文件的提升权限（如“完全控制”）。</span><span class="sxs-lookup"><span data-stu-id="326e7-116">If you want to offer specific users the ability to set model item security, you must break permission inheritance and grant elevated permissions (such as Full Control) to the user or group on the model file.</span></span> <span data-ttu-id="326e7-117">授予对某项（如库中的文件）的“完全控制”权限时，权限的作用域将仅限于该项，不会扩展到父项或同一库中的其他项。</span><span class="sxs-lookup"><span data-stu-id="326e7-117">When you grant Full Control on an item such as a file in the library, the permissions are scoped to that item and do not extend to the parent or to other items within the same library.</span></span> <span data-ttu-id="326e7-118">用户拥有模型的“管理权限”权限后，便可以通过 SharePoint 站点或模型设计器设置模型项安全性。</span><span class="sxs-lookup"><span data-stu-id="326e7-118">After the user has Manage Permissions permission on the model, he or she can use set model item security via the SharePoint site or Model Designer.</span></span>  
  
### <a name="to-set-permissions-on-an-individual-report-model-or-data-source"></a><span data-ttu-id="326e7-119">对单个报表、模型或数据源设置权限</span><span class="sxs-lookup"><span data-stu-id="326e7-119">To set permissions on an individual report, model, or data source</span></span>  
  
1.  <span data-ttu-id="326e7-120">如果库尚未打开，请在“快速启动”上单击其名称。</span><span class="sxs-lookup"><span data-stu-id="326e7-120">If the library is not already open, click its name on the Quick Launch.</span></span> <span data-ttu-id="326e7-121">如果未显示库的名称，请单击 **“查看所有网站内容”** ，然后单击库的名称。</span><span class="sxs-lookup"><span data-stu-id="326e7-121">If the name of your library does not appear, click **View All Site Content**, and then click the name of your library.</span></span>  
  
2.  <span data-ttu-id="326e7-122">指向报表、报表模型或共享数据源文件。</span><span class="sxs-lookup"><span data-stu-id="326e7-122">Point to the report, report model, or shared data source file.</span></span>  
  
3.  <span data-ttu-id="326e7-123">单击向下箭头，并在菜单上单击 **“管理权限”** 。</span><span class="sxs-lookup"><span data-stu-id="326e7-123">Click the down arrow, and on the menu, click **Manage Permissions**.</span></span>  
  
4.  <span data-ttu-id="326e7-124">在 **“操作”** 菜单上，单击 **“编辑权限”** ，然后单击 **“确定”** 以确认此操作。</span><span class="sxs-lookup"><span data-stu-id="326e7-124">On the **Actions** menu, click **Edit Permissions**, and then click **OK** to confirm the action.</span></span>  
  
5.  <span data-ttu-id="326e7-125">若要为尚未拥有文件使用权限的用户或组授予权限，请单击 **“新建”** ，然后单击 **“添加用户”** 。</span><span class="sxs-lookup"><span data-stu-id="326e7-125">To give permissions to a user or group that does not yet have permissions to use the file, click **New**, and then click **Add Users**.</span></span>  
  
6.  <span data-ttu-id="326e7-126">若要删除或修改现有用户或组的权限，请单击用户或组旁边的复选框，单击 **“操作”** ，然后单击 **“删除用户权限”** 或 **“编辑用户权限”** 。</span><span class="sxs-lookup"><span data-stu-id="326e7-126">To remove or modify permissions for an existing user or group, click the check box next to the user or group, click **Actions**, and then click **Remove User Permissions** or **Edit User Permissions**.</span></span>  
  
### <a name="to-set-permissions-that-enable-model-item-security"></a><span data-ttu-id="326e7-127">设置启用模型项安全性的权限</span><span class="sxs-lookup"><span data-stu-id="326e7-127">To set permissions that enable model item security</span></span>  
  
1.  <span data-ttu-id="326e7-128">使用拥有 SharePoint 站点的“管理权限”权限的帐户登录该站点。</span><span class="sxs-lookup"><span data-stu-id="326e7-128">Log in to the SharePoint site using an account that has Manage Permissions permission on the site.</span></span>  
  
2.  <span data-ttu-id="326e7-129">打开包含模型的库。</span><span class="sxs-lookup"><span data-stu-id="326e7-129">Open the library that contains the model.</span></span>  
  
3.  <span data-ttu-id="326e7-130">指向模型。</span><span class="sxs-lookup"><span data-stu-id="326e7-130">Point to the model.</span></span>  
  
4.  <span data-ttu-id="326e7-131">单击该模型旁边的向下箭头，并单击 **“管理权限”** 。</span><span class="sxs-lookup"><span data-stu-id="326e7-131">Click the down arrow next to the model, and click **Manage Permissions**.</span></span>  
  
5.  <span data-ttu-id="326e7-132">单击 **“操作”** 。</span><span class="sxs-lookup"><span data-stu-id="326e7-132">Click **Actions**.</span></span>  
  
6.  <span data-ttu-id="326e7-133">单击 **“编辑权限”** 。</span><span class="sxs-lookup"><span data-stu-id="326e7-133">Click **Edit Permissions**.</span></span> <span data-ttu-id="326e7-134">单击“确定”。 </span><span class="sxs-lookup"><span data-stu-id="326e7-134">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="326e7-135">单击 **“新建”** 。</span><span class="sxs-lookup"><span data-stu-id="326e7-135">Click **New**.</span></span>  
  
8.  <span data-ttu-id="326e7-136">单击“添加用户”。 </span><span class="sxs-lookup"><span data-stu-id="326e7-136">Click **Add Users**.</span></span>  
  
9. <span data-ttu-id="326e7-137">在“用户/组”中输入用户帐户。</span><span class="sxs-lookup"><span data-stu-id="326e7-137">In Users/Groups, enter the user account.</span></span>  
  
10. <span data-ttu-id="326e7-138">选择 **“直接授予用户权限”** 。</span><span class="sxs-lookup"><span data-stu-id="326e7-138">Select **Give users permission directly**.</span></span>  
  
11. <span data-ttu-id="326e7-139">单击 **“完全控制”** 。</span><span class="sxs-lookup"><span data-stu-id="326e7-139">Click **Full Control**.</span></span>  
  
12. <span data-ttu-id="326e7-140">单击“确定”。 </span><span class="sxs-lookup"><span data-stu-id="326e7-140">Click **OK**.</span></span> <span data-ttu-id="326e7-141">用户具备管理特定模型权限的能力后，便可以打开模型并在模型内编辑权限。</span><span class="sxs-lookup"><span data-stu-id="326e7-141">Once a user has the ability to manage permissions for a specific model, he or she can open the model to edit permissions within the model.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="326e7-142">另请参阅</span><span class="sxs-lookup"><span data-stu-id="326e7-142">See Also</span></span>  
 <span data-ttu-id="326e7-143">[将 Windows SharePoint Services 中的内置安全性用于报表服务器项](use-built-in-security-in-windows-sharepoint-services-for-report-server-items.md) </span><span class="sxs-lookup"><span data-stu-id="326e7-143">[Use Built-in Security in Windows SharePoint Services for Report Server Items](use-built-in-security-in-windows-sharepoint-services-for-report-server-items.md) </span></span>  
 <span data-ttu-id="326e7-144">[在 SharePoint Web 应用程序中设置报表服务器操作的权限](set-permissions-for-report-server-operations-in-a-sharepoint-web-application.md) </span><span class="sxs-lookup"><span data-stu-id="326e7-144">[Set Permissions for Report Server Operations in a SharePoint Web Application](set-permissions-for-report-server-operations-in-a-sharepoint-web-application.md) </span></span>  
 <span data-ttu-id="326e7-145">[Reporting Services 中的角色和任务与 SharePoint 组和权限的比较](../reporting-services-roles-tasks-vs-sharepoint-groups-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="326e7-145">[Compare Roles and Tasks in Reporting Services to SharePoint Groups and Permissions](../reporting-services-roles-tasks-vs-sharepoint-groups-permissions.md) </span></span>  
 <span data-ttu-id="326e7-146">[报表服务器项的 SharePoint 站点和列表权限参考](sharepoint-site-and-list-permission-reference-for-report-server-items.md) </span><span class="sxs-lookup"><span data-stu-id="326e7-146">[SharePoint Site and List Permission Reference for Report Server Items](sharepoint-site-and-list-permission-reference-for-report-server-items.md) </span></span>  
 [<span data-ttu-id="326e7-147">在 SharePoint 站点上授予对报表服务器项的权限</span><span class="sxs-lookup"><span data-stu-id="326e7-147">Granting Permissions on Report Server Items on a SharePoint Site</span></span>](granting-permissions-on-report-server-items-on-a-sharepoint-site.md)  
  
  
