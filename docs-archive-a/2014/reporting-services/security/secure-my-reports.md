---
title: 保护“我的报表”| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- denying My Reports folder access
- private folders [Reporting Services]
- user workspace [Reporting Services]
- security [Reporting Services], My Reports folder
- My Reports folder [Reporting Services]
ms.assetid: 3b23a382-13b8-4196-9a93-7fe62d03a63c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b0a832133852e05c54a80b73fad8a91426840467
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688484"
---
# <a name="secure-my-reports"></a><span data-ttu-id="72540-102">保护“我的报表”</span><span class="sxs-lookup"><span data-stu-id="72540-102">Secure My Reports</span></span>
  <span data-ttu-id="72540-103">“我的报表”功能为使用报表提供了一个由用户管理的工作区。</span><span class="sxs-lookup"><span data-stu-id="72540-103">The My Reports feature provides a user-managed workspace for working with reports.</span></span> <span data-ttu-id="72540-104">为了发挥“我的报表”文件夹应有的作用，该文件夹与其他普通文件夹相比，需要限制条件较少的权限。</span><span class="sxs-lookup"><span data-stu-id="72540-104">In order to serve its intended purpose, the My Reports folder requires less restrictive permissions than other folders that are available for general use.</span></span> <span data-ttu-id="72540-105">只有在其他文件夹中查看和运行报表的权限的用户可能需要一组扩展的权限来管理其“我的报表”文件夹及其所拥有的内容。</span><span class="sxs-lookup"><span data-stu-id="72540-105">Users who have permissions to only view and run reports in other folders might require an expanded set of permissions to manage their My Reports folders and content that they own.</span></span> [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="72540-106">提供专用于此用途的角色分配和角色定义。</span><span class="sxs-lookup"><span data-stu-id="72540-106">provides a specialized role assignment and role definition for this purpose.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="72540-107">“我的报表”只适用于报表管理器。</span><span class="sxs-lookup"><span data-stu-id="72540-107">My Reports is available only in Report Manager.</span></span> <span data-ttu-id="72540-108">该文件夹在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中不可用。</span><span class="sxs-lookup"><span data-stu-id="72540-108">It is not available in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
## <a name="role-assignment-for-my-reports"></a><span data-ttu-id="72540-109">“我的报表”的角色分配</span><span class="sxs-lookup"><span data-stu-id="72540-109">Role Assignment for My Reports</span></span>  
 <span data-ttu-id="72540-110">“我的报表”的角色分配中的元素都是预先设置好的，对于激活“我的报表”文件夹的每个用户，将自动为其创建角色分配。</span><span class="sxs-lookup"><span data-stu-id="72540-110">The role assignment for My Reports has preset elements and is automatically created for each user who activates a My Reports folder.</span></span> <span data-ttu-id="72540-111">对于广泛使用“我的报表”的单位而言，让报表服务器自动分配安全性尤其有用，因为管理员不必为每一个“我的报表”用户授予访问权限。</span><span class="sxs-lookup"><span data-stu-id="72540-111">Having the report server automatically assign security is especially useful for organizations that use My Reports widely because administrators do not have to enable access for each My Reports user.</span></span>  
  
 <span data-ttu-id="72540-112">“我的报表”角色分配由以下元素组成： </span><span class="sxs-lookup"><span data-stu-id="72540-112">A **My Reports** role assignment consists of the following elements:</span></span>  
  
-   <span data-ttu-id="72540-113">用户的我的报表文件夹，位于 "用户" 文件夹中的 " \\ *\<username>* \My 报表" 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="72540-113">The user's My Reports folder, which is located in Users Folders\\*\<username>* \My Reports folder.</span></span>  
  
-   <span data-ttu-id="72540-114">用户帐户，在激活“我的报表”文件夹时确定。</span><span class="sxs-lookup"><span data-stu-id="72540-114">The user account, which is determined when the My Reports folder is activated.</span></span> <span data-ttu-id="72540-115">当用户单击报表管理器中的“我的报表”文件夹时，或将报表从报表设计器发布到“我的报表”文件夹时，将激活一个文件夹。</span><span class="sxs-lookup"><span data-stu-id="72540-115">A folder is activated when a user clicks a My Reports folder in Report Manager or when publishing a report to a My Reports folder from Report Designer.</span></span> <span data-ttu-id="72540-116">当用户请求“我的报表”链接的属性时，也将激活此文件夹。</span><span class="sxs-lookup"><span data-stu-id="72540-116">This folder is also activated when a user requests properties on the My Reports link.</span></span>  
  
-   <span data-ttu-id="72540-117">“我的报表”的预定义角色定义</span><span class="sxs-lookup"><span data-stu-id="72540-117">The predefined role definition for My Reports.</span></span>  
  
## <a name="role-definition-for-my-reports"></a><span data-ttu-id="72540-118">“我的报表”的角色定义</span><span class="sxs-lookup"><span data-stu-id="72540-118">Role Definition for My Reports</span></span>  
 <span data-ttu-id="72540-119">“我的报表”角色定义包含支持对“我的报表”文件夹的内容进行管理的任务。 </span><span class="sxs-lookup"><span data-stu-id="72540-119">The **My Reports** role definition includes tasks that support content management of a My Reports folder.</span></span> <span data-ttu-id="72540-120">“我的报表”  角色设计作为单一用途的角色。</span><span class="sxs-lookup"><span data-stu-id="72540-120">The **My Reports** role is intended to be a single-purpose role.</span></span> <span data-ttu-id="72540-121">虽然您可以将该角色用于任何项级安全策略，但最好不要这样做，以尽量避免为满足其他文件夹要求而修改该角色。</span><span class="sxs-lookup"><span data-stu-id="72540-121">Although you can choose it for any item-level security policy, you should avoid doing so to minimize the chance that you will modify it to accommodate other folder requirements.</span></span> <span data-ttu-id="72540-122">为“我的报表”功能保留“我的报表”角色有助于维护一致的用户体验。 </span><span class="sxs-lookup"><span data-stu-id="72540-122">Reserving the **My Reports** role for the My Reports feature can help you maintain a consistent experience for users.</span></span>  
  
 <span data-ttu-id="72540-123">默认情况下，只有报表服务器管理员才可以修改“我的报表”角色。 </span><span class="sxs-lookup"><span data-stu-id="72540-123">By default, only report server administrators modify the **My Reports** role.</span></span> <span data-ttu-id="72540-124">您可以通过更改“我的报表”角色所包含的任务来自定义“我的报表”角色。 </span><span class="sxs-lookup"><span data-stu-id="72540-124">You can customize the **My Reports** role by changing the tasks it contains.</span></span> <span data-ttu-id="72540-125">您还可以替换其他角色。</span><span class="sxs-lookup"><span data-stu-id="72540-125">You can also substitute a different role.</span></span>  
  
## <a name="denying-access-to-my-reports"></a><span data-ttu-id="72540-126">拒绝访问“我的报表”</span><span class="sxs-lookup"><span data-stu-id="72540-126">Denying Access to My Reports</span></span>  
 <span data-ttu-id="72540-127">可以通过以下方式阻止用户访问“我的报表”：</span><span class="sxs-lookup"><span data-stu-id="72540-127">You can prevent users from accessing My Reports by:</span></span>  
  
-   <span data-ttu-id="72540-128">在“站点设置”页上禁用“我的报表”。</span><span class="sxs-lookup"><span data-stu-id="72540-128">Disabling My Reports on the Site Settings page.</span></span> <span data-ttu-id="72540-129">有关详细信息，请参阅 [启用和禁用“我的报表”](../report-server/enable-and-disable-my-reports.md)。</span><span class="sxs-lookup"><span data-stu-id="72540-129">For more information, see [Enable and Disable My Reports](../report-server/enable-and-disable-my-reports.md).</span></span>  
  
-   <span data-ttu-id="72540-130">删除“我的报表”角色中的所有任务。 </span><span class="sxs-lookup"><span data-stu-id="72540-130">Removing all tasks from the **My Reports** role.</span></span>  
  
 <span data-ttu-id="72540-131">禁用“我的报表”后，将从报表管理器中删除指向“我的报表”文件夹的链接。</span><span class="sxs-lookup"><span data-stu-id="72540-131">When you disable My Reports, the link to a My Reports folder is removed from Report Manager.</span></span> <span data-ttu-id="72540-132">支持“我的报表”的基础文件夹结构（即用户文件夹及其子文件夹）仍然可用，如果用户知道文件夹路径，仍可对其进行访问。</span><span class="sxs-lookup"><span data-stu-id="72540-132">The underlying folder structure that supports My Reports (that is, the Users Folders folder and subfolders) is still available and can be accessed if a user knows the folder path.</span></span> <span data-ttu-id="72540-133">删除“我的报表”角色中的任务可以确保禁止对该文件夹的访问。 </span><span class="sxs-lookup"><span data-stu-id="72540-133">Removing tasks from **My Reports** role ensures that access is prevented.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72540-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="72540-134">See Also</span></span>  
 <span data-ttu-id="72540-135">[保护报表和资源](secure-reports-and-resources.md) </span><span class="sxs-lookup"><span data-stu-id="72540-135">[Secure Reports and Resources](secure-reports-and-resources.md) </span></span>  
 <span data-ttu-id="72540-136">[保护文件夹](secure-folders.md) </span><span class="sxs-lookup"><span data-stu-id="72540-136">[Secure Folders](secure-folders.md) </span></span>  
 [<span data-ttu-id="72540-137">授予对本机模式报表服务器的权限</span><span class="sxs-lookup"><span data-stu-id="72540-137">Granting Permissions on a Native Mode Report Server</span></span>](granting-permissions-on-a-native-mode-report-server.md)  
  
  
