---
title: 修改或删除角色分配（报表管理器）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- removing role assignments
- roles [Reporting Services], assignments
- system roles [Reporting Services]
- modifying role assignments
- deleting role assignments
ms.assetid: 523bdd32-92cb-4b48-a3a9-d58b2385bde7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d67c5cdb7647d50008f72890e4ac3e3c7eed456e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689770"
---
# <a name="modify-or-delete-a-role-assignment-report-manager"></a><span data-ttu-id="85422-102">修改或删除角色分配（报表管理器）</span><span class="sxs-lookup"><span data-stu-id="85422-102">Modify or Delete a Role Assignment (Report Manager)</span></span>
  <span data-ttu-id="85422-103">角色分配将组或用户帐户映射到包含可执行任务的预定义的角色定义。</span><span class="sxs-lookup"><span data-stu-id="85422-103">A role assignment maps a group or user account to a predefined role definition that includes tasks that can be performed.</span></span> <span data-ttu-id="85422-104">角色分配确定用户可针对文件夹、报表、模型或其他内容类型执行的操作类型。</span><span class="sxs-lookup"><span data-stu-id="85422-104">It determines the types of operations that a user can perform relative to a folder, report, model, or other content type.</span></span> <span data-ttu-id="85422-105">若要创建、修改或删除角色分配，请使用报表管理器。</span><span class="sxs-lookup"><span data-stu-id="85422-105">To create, modify, or delete role assignments, you use Report Manager.</span></span> <span data-ttu-id="85422-106">在为特定用户或组创建了角色分配之后，您还可以通过选择其他角色来修改它。</span><span class="sxs-lookup"><span data-stu-id="85422-106">After you create a role assignment for a particular user or group, you can modify it later by selecting a different role.</span></span> <span data-ttu-id="85422-107">如果要撤消对报表报务器的权限，可从报表服务器删除角色分配。</span><span class="sxs-lookup"><span data-stu-id="85422-107">If you want to revoke permissions to a report server, you can delete a role assignment from the report server.</span></span>  
  
 <span data-ttu-id="85422-108">根据您的目标，其他方法可能会更合适。</span><span class="sxs-lookup"><span data-stu-id="85422-108">Depending on your objective, alternative approaches might be more appropriate.</span></span> <span data-ttu-id="85422-109">例如自定义或创建新的角色定义，或者在 Active Directory 中修改组帐户的成员身份。</span><span class="sxs-lookup"><span data-stu-id="85422-109">Examples include customizing or creating a new role definition, or modifying the membership of a group account in Active Directory.</span></span>  
  
 <span data-ttu-id="85422-110">例如，假定有一组需要完全管理内容的用户，但他们不应具有与“内容管理员”关联的所有权限。</span><span class="sxs-lookup"><span data-stu-id="85422-110">For example, suppose you have a group of users who need to fully manage their content, but should not have the full set of permissions associated with Content Manager.</span></span> <span data-ttu-id="85422-111">在这种情况下，您可以创建一个名为“部门内容管理员”的新角色定义，其中包括“内容管理员”中除 **“设置项的安全策略”** 以外的所有任务。</span><span class="sxs-lookup"><span data-stu-id="85422-111">In this case, you could create a new role definition called Department Content Manager that includes all of the tasks in Content Manager except **Set security policies for items**.</span></span>  
  
 <span data-ttu-id="85422-112">同样，如果您是系统管理员或网络管理员，并且对于您来说管理 Active Directory 组帐户比在报表管理器中管理角色分配更加容易，则您可以通过为组帐户创建一个角色分配来减少管理角色分配的开销，并且在用户不需要再访问报表时调整组成员身份。</span><span class="sxs-lookup"><span data-stu-id="85422-112">Similarly, if you are a system or network administrator and it is easier for you to manage Active Directory group accounts than role assignments in Report Manager, you could reduce the overhead of managing role assignments by creating a single role assignment for a group account, and then adjust group membership when users no longer require access to reports.</span></span>  
  
 <span data-ttu-id="85422-113">如果您确定修改或删除角色分配是最佳做法，那么，请记住要同时检查系统角色分配和项角色分配。</span><span class="sxs-lookup"><span data-stu-id="85422-113">If you determine that modifying or deleting a role assignment is the best approach, remember to check for both system role assignments and item role assignments.</span></span> <span data-ttu-id="85422-114">每种类型的角色分配都是通过报表管理器中不同的页面配置的。</span><span class="sxs-lookup"><span data-stu-id="85422-114">Each type of role assignment is configured through different pages in Report Manager.</span></span>  
  
### <a name="to-modify-or-delete-a-system-role-assignment"></a><span data-ttu-id="85422-115">修改或删除系统角色分配</span><span class="sxs-lookup"><span data-stu-id="85422-115">To modify or delete a system role assignment</span></span>  
  
1.  <span data-ttu-id="85422-116">启动 [报表管理器（SSRS 本机模式）](../report-manager-ssrs-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="85422-116">Start [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="85422-117">单击 **“网站设置”** 。</span><span class="sxs-lookup"><span data-stu-id="85422-117">Click **Site Settings**.</span></span>  
  
3.  <span data-ttu-id="85422-118">单击 **“安全性”** 。</span><span class="sxs-lookup"><span data-stu-id="85422-118">Click **Security**.</span></span> <span data-ttu-id="85422-119">将按帐户名列出当前为服务器或扩展部署定义的所有系统级角色分配。</span><span class="sxs-lookup"><span data-stu-id="85422-119">All system-level role assignments currently defined for the server or scale-out deployment are listed by account name.</span></span>  
  
4.  <span data-ttu-id="85422-120">查找要修改或删除的角色分配。</span><span class="sxs-lookup"><span data-stu-id="85422-120">Find the role assignment that you want to modify or delete.</span></span>  
  
5.  <span data-ttu-id="85422-121">若要为特定用户或组添加或删除角色，请单击 **“编辑”**。</span><span class="sxs-lookup"><span data-stu-id="85422-121">To add or remove the role for a particular user or group, click **Edit**.</span></span>  
  
6.  <span data-ttu-id="85422-122">若要删除角色分配，请单击该用户或组名旁边的复选框，再单击 **“删除”**。</span><span class="sxs-lookup"><span data-stu-id="85422-122">To delete a role assignment, click the check box next to the user or group name, and then click **Delete**.</span></span>  
  
### <a name="to-modify-or-delete-an-item-role-assignment"></a><span data-ttu-id="85422-123">修改或删除项角色分配</span><span class="sxs-lookup"><span data-stu-id="85422-123">To modify or delete an item role assignment</span></span>  
  
1.  <span data-ttu-id="85422-124">启动 **“报表管理器”** 并找出您要为其编辑或删除角色分配的项。</span><span class="sxs-lookup"><span data-stu-id="85422-124">Start **Report Manager** and locate the item for which you want to edit or delete a role assignment.</span></span>  
  
2.  <span data-ttu-id="85422-125">悬停在该项之上，然后单击下拉箭头。</span><span class="sxs-lookup"><span data-stu-id="85422-125">Hover over the item, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="85422-126">在下拉菜单中，单击“安全性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="85422-126">In the drop-down menu, click **Security**.</span></span>  
  
4.  <span data-ttu-id="85422-127">查找要修改或删除的角色分配。</span><span class="sxs-lookup"><span data-stu-id="85422-127">Find the role assignment that you want to modify or delete.</span></span>  
  
5.  <span data-ttu-id="85422-128">若要为特定用户或组添加或删除角色，请单击 **“编辑”**。</span><span class="sxs-lookup"><span data-stu-id="85422-128">To add or remove the role for a particular user or group, click **Edit**.</span></span>  
  
6.  <span data-ttu-id="85422-129">若要删除角色分配，请单击该用户或组名旁边的复选框，再单击 **“删除”**。</span><span class="sxs-lookup"><span data-stu-id="85422-129">To delete a role assignment, click the check box next to the user or group name, and then click **Delete**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85422-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="85422-130">See Also</span></span>  
 <span data-ttu-id="85422-131"> (create-and-manage-role-assignments.md) </span><span class="sxs-lookup"><span data-stu-id="85422-131">(create-and-manage-role-assignments.md)</span></span>   
 <span data-ttu-id="85422-132">[角色分配](role-assignments.md) </span><span class="sxs-lookup"><span data-stu-id="85422-132">[Role Assignments](role-assignments.md) </span></span>  
 <span data-ttu-id="85422-133">["站点设置" 页 &#40;报表管理器&#41;](../site-settings-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="85422-133">[Site Settings Page &#40;Report Manager&#41;](../site-settings-page-report-manager.md) </span></span>  
 [<span data-ttu-id="85422-134">“新建系统角色分配: 编辑系统角色分配”页（报表管理器）</span><span class="sxs-lookup"><span data-stu-id="85422-134">New System Role Assignments: Edit System Role Assignments Page &#40;Report Manager&#41;</span></span>](../new-system-role-assignments-edit-system-role-assignments-page-report-manager.md)  
  
  
