---
title: 创建、删除或修改角色 (Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- roles [Reporting Services], creating
- deleting roles
- removing roles
- roles [Reporting Services], definitions
- modifying roles
- roles [Reporting Services], deleting
- roles [Reporting Services], modifying
ms.assetid: 3d1d56e6-a283-44a7-8417-36cb4d2c74d1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 543bddda88e41af39d3200df4728716d46b3ae8b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691582"
---
# <a name="create-delete-or-modify-a-role-management-studio"></a><span data-ttu-id="537a0-102">创建、删除或修改角色 (Management Studio)</span><span class="sxs-lookup"><span data-stu-id="537a0-102">Create, Delete, or Modify a Role (Management Studio)</span></span>
  <span data-ttu-id="537a0-103">Reporting Services 提供了定义对报表服务器的访问级别的预定义角色。</span><span class="sxs-lookup"><span data-stu-id="537a0-103">Reporting Services provides predefined roles that define a level of access to a report server.</span></span> <span data-ttu-id="537a0-104">需要访问报表服务器的每个用户或组都通过说明可以执行的任务的角色来进行访问。</span><span class="sxs-lookup"><span data-stu-id="537a0-104">Each user or group who requires access to report server does so through a role that describes the tasks that can be performed.</span></span> <span data-ttu-id="537a0-105">这些角色是对作为整体的报表服务器进行定义的。</span><span class="sxs-lookup"><span data-stu-id="537a0-105">Roles are defined for the report server as a whole.</span></span> <span data-ttu-id="537a0-106">不能对报表服务器的特定部分改变角色定义，也不能指定根据不同情况以不同的方式使用角色。</span><span class="sxs-lookup"><span data-stu-id="537a0-106">You cannot vary a role definition for specific parts of the report server, or specify that a role be used differently depending on the circumstances.</span></span>  
  
 <span data-ttu-id="537a0-107">若要创建、修改或删除角色，请使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="537a0-107">To create, modify, or delete roles, use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="537a0-108">只能删除未使用的角色。</span><span class="sxs-lookup"><span data-stu-id="537a0-108">You can only delete roles that are not used.</span></span>  
  
 <span data-ttu-id="537a0-109">若要将所创建的角色分配给用户或组，请使用报表管理器。</span><span class="sxs-lookup"><span data-stu-id="537a0-109">To assign users and groups to the roles that you create, use Report Manager.</span></span> <span data-ttu-id="537a0-110">有关详细信息，请参阅 [授予用户对报表服务器的访问权限（报表管理器）](grant-user-access-to-a-report-server.md)。</span><span class="sxs-lookup"><span data-stu-id="537a0-110">For more information, see [Grant User Access to a Report Server &#40;Report Manager&#41;](grant-user-access-to-a-report-server.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="537a0-111">如果报表服务器配置为 SharePoint 集成模式，并且已连接到与该报表服务器集成的 SharePoint 站点，则可以查看和修改控制对报表服务器内容和操作的访问权限的权限级别。</span><span class="sxs-lookup"><span data-stu-id="537a0-111">If the report server is configured for SharePoint integrated mode, and you connected to the SharePoint site that the report server is integrated with, you can view and modify the permission levels that control access to report server content and operations.</span></span>  
  
### <a name="to-create-a-role-definition"></a><span data-ttu-id="537a0-112">创建角色定义</span><span class="sxs-lookup"><span data-stu-id="537a0-112">To create a role definition</span></span>  
  
1.  <span data-ttu-id="537a0-113">在对象资源管理器中，展开报表服务器节点。</span><span class="sxs-lookup"><span data-stu-id="537a0-113">In Object Explorer, expand a report server node.</span></span>  
  
2.  <span data-ttu-id="537a0-114">展开“安全性”文件夹。</span><span class="sxs-lookup"><span data-stu-id="537a0-114">Expand the Security folder.</span></span>  
  
3.  <span data-ttu-id="537a0-115">要创建项目级角色定义，请右键单击“角色”，再指向“新建角色”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="537a0-115">If you are creating an item-level role definition, right-click **Roles**, and point to **New Role**.</span></span>  
  
     <span data-ttu-id="537a0-116">或者，若要创建系统级角色定义，请右键单击“系统角色”，再指向“新建系统角色”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="537a0-116">Or, if you are creating a system-level role definition, right-click **System Roles**, and point to **New System Role**.</span></span>  
  
4.  <span data-ttu-id="537a0-117">为角色键入唯一名称。</span><span class="sxs-lookup"><span data-stu-id="537a0-117">Type a unique name for the role.</span></span> <span data-ttu-id="537a0-118">名称必须至少包含一个字符。</span><span class="sxs-lookup"><span data-stu-id="537a0-118">A name must contain at least one character.</span></span> <span data-ttu-id="537a0-119">它也可以包括空格和特定的一些符号，但不能包括以下字符：; ?</span><span class="sxs-lookup"><span data-stu-id="537a0-119">It can also include spaces and certain symbols, but not the characters ; ?</span></span> <span data-ttu-id="537a0-120">： \@ & = +，$/\* \< > |"或/。</span><span class="sxs-lookup"><span data-stu-id="537a0-120">: \@ & = + , $ / \* \< > | " or /.</span></span>  
  
5.  <span data-ttu-id="537a0-121">根据需要，可以键入说明。</span><span class="sxs-lookup"><span data-stu-id="537a0-121">Optionally type a description.</span></span> <span data-ttu-id="537a0-122">在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 中，此说明仅在此页上可见。</span><span class="sxs-lookup"><span data-stu-id="537a0-122">In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] this description is visible only on this page.</span></span> <span data-ttu-id="537a0-123">通过报表管理器查看此项的用户可以在该工具中看到此说明。</span><span class="sxs-lookup"><span data-stu-id="537a0-123">Users who view this item through Report Manager can see this description in that tool.</span></span>  
  
6.  <span data-ttu-id="537a0-124">选择此角色的成员可以执行的任务。</span><span class="sxs-lookup"><span data-stu-id="537a0-124">Select the tasks that members of this role can perform.</span></span>  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-delete-or-modify-a-role-definition"></a><span data-ttu-id="537a0-125">删除或修改角色定义</span><span class="sxs-lookup"><span data-stu-id="537a0-125">To delete or modify a role definition</span></span>  
  
1.  <span data-ttu-id="537a0-126">在对象资源管理器中，展开报表服务器节点。</span><span class="sxs-lookup"><span data-stu-id="537a0-126">In Object Explorer, expand a report server node.</span></span>  
  
2.  <span data-ttu-id="537a0-127">展开“安全性”文件夹。</span><span class="sxs-lookup"><span data-stu-id="537a0-127">Expand the Security folder.</span></span>  
  
3.  <span data-ttu-id="537a0-128">若要删除或修改项目级角色定义，请展开“角色”文件夹。</span><span class="sxs-lookup"><span data-stu-id="537a0-128">To delete or modify an item-level role definition, expand the Roles folder.</span></span> <span data-ttu-id="537a0-129">执行以下某种方案：</span><span class="sxs-lookup"><span data-stu-id="537a0-129">Perform one of the following:</span></span>  
  
    1.  <span data-ttu-id="537a0-130">要删除角色定义，请右键单击该项，再单击“删除”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="537a0-130">To delete a role definition, right-click the item and click **Delete**.</span></span> <span data-ttu-id="537a0-131">此时，将显示 **“删除对象”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="537a0-131">The **Delete Object** dialog box is displayed.</span></span> [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
    2.  <span data-ttu-id="537a0-132">要修改角色定义，请右键单击该项，再单击“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="537a0-132">To modify a role definition, right-click the item and click **Properties**.</span></span> <span data-ttu-id="537a0-133">将显示 **“用户角色属性”** 对话框的“常规”页。</span><span class="sxs-lookup"><span data-stu-id="537a0-133">The General page of the **User Role Properties** dialog box is displayed.</span></span>  
  
         <span data-ttu-id="537a0-134">选择此角色的成员可以执行的任务，再单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="537a0-134">Select the tasks that members of this role can perform, and click **OK**.</span></span>  
  
4.  <span data-ttu-id="537a0-135">要删除或修改系统级角色定义，请展开“系统角色”文件夹  。</span><span class="sxs-lookup"><span data-stu-id="537a0-135">To delete or modify a system-level role definition, expand the **System Roles** folder.</span></span> <span data-ttu-id="537a0-136">执行以下某种方案：</span><span class="sxs-lookup"><span data-stu-id="537a0-136">Perform one of the following:</span></span>  
  
    1.  <span data-ttu-id="537a0-137">要删除系统角色定义，请右键单击该项，再单击“删除”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="537a0-137">To delete a system role definition, right-click the item and click **Delete**.</span></span> <span data-ttu-id="537a0-138">此时，将显示 **“删除对象”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="537a0-138">The **Delete Object** dialog box is displayed.</span></span> [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
    2.  <span data-ttu-id="537a0-139">要修改系统角色定义，请右键单击该项，再单击“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="537a0-139">To modify a system role definition, right-click the item and click **Properties**.</span></span> <span data-ttu-id="537a0-140">将显示 **“系统角色属性”** 对话框的“常规”页。</span><span class="sxs-lookup"><span data-stu-id="537a0-140">The General page of the **System Role Properties** dialog box is displayed.</span></span>  
  
         <span data-ttu-id="537a0-141">选择此角色的成员可以执行的任务，再单击 **“确定”** 以应用更改。</span><span class="sxs-lookup"><span data-stu-id="537a0-141">Select the tasks that members of this role can perform, and click **OK** to apply the changes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="537a0-142">另请参阅</span><span class="sxs-lookup"><span data-stu-id="537a0-142">See Also</span></span>  
 <span data-ttu-id="537a0-143">[在 Management Studio 中连接到报表服务器](../tools/connect-to-a-report-server-in-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="537a0-143">[Connect to a Report Server in Management Studio](../tools/connect-to-a-report-server-in-management-studio.md) </span></span>  
 <span data-ttu-id="537a0-144"> (create-and-manage-role-assignments.md) </span><span class="sxs-lookup"><span data-stu-id="537a0-144">(create-and-manage-role-assignments.md)</span></span>   
 [<span data-ttu-id="537a0-145">SQL Server Management Studio 中的 Reporting Services (SSRS)</span><span class="sxs-lookup"><span data-stu-id="537a0-145">Reporting Services in SQL Server Management Studio &#40;SSRS&#41;</span></span>](../tools/reporting-services-in-sql-server-management-studio-ssrs.md)  
  
  
