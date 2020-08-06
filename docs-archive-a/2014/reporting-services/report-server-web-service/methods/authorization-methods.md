---
title: 授权方法 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- security [Reporting Services], reports
- authorization [Reporting Services]
- reports [Reporting Services], security
- tasks [Reporting Services]
- roles [Reporting Services], methods
ms.assetid: 45e9cf2c-facf-4801-9482-c855403f42a8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b04a21b5075e939a4732e2f8ec219e169f4ba440
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691595"
---
# <a name="authorization-methods"></a><span data-ttu-id="927b4-102">授权方法</span><span class="sxs-lookup"><span data-stu-id="927b4-102">Authorization Methods</span></span>
  <span data-ttu-id="927b4-103">可以使用这些方法管理报表服务器上的任务、角色和策略。</span><span class="sxs-lookup"><span data-stu-id="927b4-103">You can use these methods to manage tasks, roles, and policies on the report server.</span></span>  
  
|<span data-ttu-id="927b4-104">方法</span><span class="sxs-lookup"><span data-stu-id="927b4-104">Method</span></span>|<span data-ttu-id="927b4-105">操作</span><span class="sxs-lookup"><span data-stu-id="927b4-105">Action</span></span>|  
|------------|------------|  
|<xref:ReportService2010.ReportingService2010.CreateRole%2A>|<span data-ttu-id="927b4-106">将新的角色添加到报表服务器数据库。</span><span class="sxs-lookup"><span data-stu-id="927b4-106">Adds a new role to the report server database.</span></span> <span data-ttu-id="927b4-107">此方法仅适用于本机模式。</span><span class="sxs-lookup"><span data-stu-id="927b4-107">This method =applies to native mode only.</span></span>|  
|<xref:ReportService2010.ReportingService2010.DeleteRole%2A>|<span data-ttu-id="927b4-108">从报表服务器数据库删除角色。</span><span class="sxs-lookup"><span data-stu-id="927b4-108">Deletes a role from the report server database.</span></span> <span data-ttu-id="927b4-109">此方法仅适用于本机模式。</span><span class="sxs-lookup"><span data-stu-id="927b4-109">This method applies to native mode only.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetPermissions%2A>|<span data-ttu-id="927b4-110">返回与报表服务器数据库或 SharePoint 库中特定项相关联的用户权限。</span><span class="sxs-lookup"><span data-stu-id="927b4-110">Returns the user permissions that are associated with a particular item in the report server database or SharePoint library.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetPolicies%2A>|<span data-ttu-id="927b4-111">返回与报表服务器数据库或 SharePoint 库中特定项相关联的策略。</span><span class="sxs-lookup"><span data-stu-id="927b4-111">Returns the policies that are associated with a particular item in the report server database or SharePoint library.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetRoleProperties%2A>|<span data-ttu-id="927b4-112">返回角色元数据属性和关联任务的集合。</span><span class="sxs-lookup"><span data-stu-id="927b4-112">Returns role metadata properties and a collection of associated tasks.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetSystemPermissions%2A>|<span data-ttu-id="927b4-113">返回用户的系统权限。</span><span class="sxs-lookup"><span data-stu-id="927b4-113">Returns the user's system permissions.</span></span> <span data-ttu-id="927b4-114">此方法仅适用于本机模式。</span><span class="sxs-lookup"><span data-stu-id="927b4-114">This method applies to native mode only.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetSystemPolicies%2A>|<span data-ttu-id="927b4-115">返回系统策略，包括这些策略与之关联的组和角色。</span><span class="sxs-lookup"><span data-stu-id="927b4-115">Returns the system policies, including groups and roles with which they are associated.</span></span> <span data-ttu-id="927b4-116">此方法仅适用于本机模式。</span><span class="sxs-lookup"><span data-stu-id="927b4-116">This method applies to native mode only.</span></span>|  
|<xref:ReportService2010.ReportingService2010.InheritParentSecurity%2A>|<span data-ttu-id="927b4-117">删除与报表服务器数据库中特定项相关联的策略，并将该项的安全策略设置为其父级的策略。</span><span class="sxs-lookup"><span data-stu-id="927b4-117">Deletes the policies that are associated with a particular item in the report server database and sets the security policies for the item to those of its parent.</span></span>|  
|<xref:ReportService2010.ReportingService2010.IsSSLRequired%2A>|<span data-ttu-id="927b4-118">返回一个布尔值，指示是否需要安全套接字层 (SSL) 协议才能使用 <xref:ReportService2010> 端点。</span><span class="sxs-lookup"><span data-stu-id="927b4-118">Returns a Boolean value that indicates whether the Secure Socket Layer (SSL) protocol is required to use the <xref:ReportService2010> end point.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListRoles%2A>|<span data-ttu-id="927b4-119">返回报表服务器管理的角色的名称和说明。</span><span class="sxs-lookup"><span data-stu-id="927b4-119">Returns the names and descriptions of roles that are managed by the report server.</span></span>|  
|<xref:ReportExecution2005.ReportExecutionService.ListSecureMethods%2A>|<span data-ttu-id="927b4-120">返回在调用时需要安全连接的 <xref:ReportExecution2005> 端点中简单对象访问协议 (SOAP) 方法的列表。</span><span class="sxs-lookup"><span data-stu-id="927b4-120">Returns a list of Simple Object Access Protocol (SOAP) methods in the <xref:ReportExecution2005> endpoint that require a secure connection when invoked.</span></span> <span data-ttu-id="927b4-121">报表服务器的 `SecureConnectionLevel` 设置用于确定返回的方法。</span><span class="sxs-lookup"><span data-stu-id="927b4-121">The `SecureConnectionLevel` setting of the report server is used to determine which methods are returned.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListTasks%2A>|<span data-ttu-id="927b4-122">返回报表服务器管理的任务。</span><span class="sxs-lookup"><span data-stu-id="927b4-122">Returns the tasks that are managed by the report server.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetPolicies%2A>|<span data-ttu-id="927b4-123">设置与指定的项关联的策略。</span><span class="sxs-lookup"><span data-stu-id="927b4-123">Sets the policies that are associated with a specified item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetRoleProperties%2A>|<span data-ttu-id="927b4-124">设置角色元数据属性并将一组任务与某一角色相关联。</span><span class="sxs-lookup"><span data-stu-id="927b4-124">Sets role metadata properties and associates a set of tasks with a role.</span></span> <span data-ttu-id="927b4-125">此方法仅适用于本机模式。</span><span class="sxs-lookup"><span data-stu-id="927b4-125">This method applies to native mode only.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetSystemPolicies%2A>|<span data-ttu-id="927b4-126">设置定义组及其关联角色的系统策略。</span><span class="sxs-lookup"><span data-stu-id="927b4-126">Sets the system policy that defines groups and their associated roles.</span></span> <span data-ttu-id="927b4-127">此方法仅适用于本机模式。</span><span class="sxs-lookup"><span data-stu-id="927b4-127">This method applies to native mode only.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="927b4-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="927b4-128">See Also</span></span>  
 <span data-ttu-id="927b4-129">[使用 Web 服务和 .NET Framework 生成应用程序](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="927b4-129">[Building Applications Using the Web Service and the .NET Framework](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 <span data-ttu-id="927b4-130">[报表服务器 Web 服务](../report-server-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="927b4-130">[Report Server Web Service](../report-server-web-service.md) </span></span>  
 <span data-ttu-id="927b4-131">[报表服务器 Web 服务方法](report-server-web-service-methods.md) </span><span class="sxs-lookup"><span data-stu-id="927b4-131">[Report Server Web Service Methods](report-server-web-service-methods.md) </span></span>  
 [<span data-ttu-id="927b4-132">技术参考 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="927b4-132">Technical Reference &#40;SSRS&#41;</span></span>](../../technical-reference-ssrs.md)  
  
  
