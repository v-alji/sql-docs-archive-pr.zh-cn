---
title: rsAccessedDenied - Reporting Services 错误 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- rsAccessDenied error
ms.assetid: 2f76b1bf-96a2-4755-b76b-84e933220efc
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 194006c2ef6f22b9bc27e9e8cbe1eebd027ed6b5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587157"
---
# <a name="rsaccesseddenied---reporting-services-error"></a><span data-ttu-id="311fa-102">rsAccessedDenied - Reporting Services 错误</span><span class="sxs-lookup"><span data-stu-id="311fa-102">rsAccessedDenied - Reporting Services Error</span></span>
  <span data-ttu-id="311fa-103">当用户没有权限进行操作时，会出现 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 错误 **rsAccessedDenied** 。</span><span class="sxs-lookup"><span data-stu-id="311fa-103">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] error **rsAccessedDenied** occurs when a user does not have permission to perform an action.</span></span> <span data-ttu-id="311fa-104">例如，用户没有允许他们打开报表的角色分配，或者没有用所需的权限打开其浏览器。</span><span class="sxs-lookup"><span data-stu-id="311fa-104">For, example, they do not have a role assignment that allows them to open a report or they did not open their browser with the required permissions.</span></span>  
  
||  
|-|  
|<span data-ttu-id="311fa-105">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 本机模式 | SharePoint 模式</span><span class="sxs-lookup"><span data-stu-id="311fa-105">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode &#124; SharePoint mode</span></span>|  
  
-   <span data-ttu-id="311fa-106">如果通过 URL 直接访问报表服务器时发生这种错误，则该例外情况将映射到 HTTP 401 错误。</span><span class="sxs-lookup"><span data-stu-id="311fa-106">If the error occurred while accessing the report server directly through a URL, the exception is mapped to an HTTP 401 error.</span></span>  
  
-   <span data-ttu-id="311fa-107">如果使用报表管理器或其他工具时发生这种错误，则该错误会显示在错误页中。</span><span class="sxs-lookup"><span data-stu-id="311fa-107">If the error occurred while using Report Manager or another tool, the error appears in an error page.</span></span>  
  
-   <span data-ttu-id="311fa-108">如果计划操作、订阅或传递时发生这种错误，则该错误仅显示在报表服务器日志文件中。</span><span class="sxs-lookup"><span data-stu-id="311fa-108">If the error occurred during a scheduled operation, subscription, or delivery, the error will appear in the report server log file only.</span></span>  
  
## <a name="details"></a><span data-ttu-id="311fa-109">详细信息</span><span class="sxs-lookup"><span data-stu-id="311fa-109">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="311fa-110">**产品名称**</span><span class="sxs-lookup"><span data-stu-id="311fa-110">**Product Name**</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="311fa-111">**事件 ID**</span><span class="sxs-lookup"><span data-stu-id="311fa-111">**Event ID**</span></span>|<span data-ttu-id="311fa-112">rsAccessedDenied</span><span class="sxs-lookup"><span data-stu-id="311fa-112">rsAccessedDenied</span></span>|  
|<span data-ttu-id="311fa-113">**事件源**</span><span class="sxs-lookup"><span data-stu-id="311fa-113">**Event Source**</span></span>|<span data-ttu-id="311fa-114">Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings</span><span class="sxs-lookup"><span data-stu-id="311fa-114">Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings</span></span>|  
|<span data-ttu-id="311fa-115">组件 </span><span class="sxs-lookup"><span data-stu-id="311fa-115">**Component**</span></span>|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
|<span data-ttu-id="311fa-116">**消息正文**</span><span class="sxs-lookup"><span data-stu-id="311fa-116">**Message Text**</span></span>|<span data-ttu-id="311fa-117">为用户“mydomain\myAccount”授予的权限不足，无法执行此操作。</span><span class="sxs-lookup"><span data-stu-id="311fa-117">The permissions granted to user 'mydomain\myAccount' are insufficient for performing this operation.</span></span> <span data-ttu-id="311fa-118">(rsAccessDenied) (ReportingServicesLibrary)</span><span class="sxs-lookup"><span data-stu-id="311fa-118">(rsAccessDenied) (ReportingServicesLibrary)</span></span>|  
  
## <a name="user-action"></a><span data-ttu-id="311fa-119">用户操作</span><span class="sxs-lookup"><span data-stu-id="311fa-119">User Action</span></span>  
 <span data-ttu-id="311fa-120">通过角色分配授予访问报表服务器内容和操作的权限。</span><span class="sxs-lookup"><span data-stu-id="311fa-120">Permission to access report server content and operations are granted through role assignments.</span></span> <span data-ttu-id="311fa-121">在新安装中，只有本地管理员才拥有访问报表服务器的权限。</span><span class="sxs-lookup"><span data-stu-id="311fa-121">On a new installation, only local administrators have access to a report server.</span></span> <span data-ttu-id="311fa-122">若要向其他用户授予访问权限，本地管理员必须创建指定域用户帐户或组帐户的角色分配、一个或多个定义用户可以执行的任务的角色，以及作用域（通常是主文件夹或报表服务器文件夹层次结构的根节点）。</span><span class="sxs-lookup"><span data-stu-id="311fa-122">To grant access to other users, a local administrator must create a role assignment that specifies a domain user or group account, one or more roles that define the tasks the user can perform, and a scope (usually the Home folder or root node of the report server folder hierarchy).</span></span> <span data-ttu-id="311fa-123">可以使用报表管理器创建角色分配。</span><span class="sxs-lookup"><span data-stu-id="311fa-123">You can use Report Manager to create the role assignments.</span></span> <span data-ttu-id="311fa-124">有关详细信息，请在 SQL Server 联机丛书中搜索“角色分配”。</span><span class="sxs-lookup"><span data-stu-id="311fa-124">For more information, search for "Role Assignments" in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="311fa-125">此错误也由报表服务器的本地管理引起的。</span><span class="sxs-lookup"><span data-stu-id="311fa-125">This error is also caused by local administration of the report server.</span></span> <span data-ttu-id="311fa-126">有关详细信息，请参阅 [为本地管理配置本机模式报表服务器 (SSRS)](../report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="311fa-126">For more information, see [Configure a Native Mode Report Server for Local Administration &#40;SSRS&#41;](../report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="311fa-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="311fa-127">See Also</span></span>  
 <span data-ttu-id="311fa-128">[角色分配](../security/role-assignments.md) </span><span class="sxs-lookup"><span data-stu-id="311fa-128">[Role Assignments](../security/role-assignments.md) </span></span>  
 <span data-ttu-id="311fa-129">[授予对本机模式报表服务器的权限](../security/granting-permissions-on-a-native-mode-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="311fa-129">[Granting Permissions on a Native Mode Report Server](../security/granting-permissions-on-a-native-mode-report-server.md) </span></span>  
 [<span data-ttu-id="311fa-130">角色和权限 (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="311fa-130">Roles and Permissions &#40;Reporting Services&#41;</span></span>](../security/roles-and-permissions-reporting-services.md)  
  
  
