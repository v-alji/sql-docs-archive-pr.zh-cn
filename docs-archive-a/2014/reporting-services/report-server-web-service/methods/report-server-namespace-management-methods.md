---
title: 报表服务器命名空间管理方法 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- reports [Reporting Services], managing
- management methods [Reporting Services]
- methods [Reporting Services], about methods
- methods [Reporting Services]
ms.assetid: 2aa43ce9-f51e-408a-8ce0-b40d3dd62561
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1b2dc38976406aaa0fa799e7a58ee340e5449d34
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688547"
---
# <a name="report-server-namespace-management-methods"></a><span data-ttu-id="749c3-102">报表服务器命名空间管理方法</span><span class="sxs-lookup"><span data-stu-id="749c3-102">Report Server Namespace Management Methods</span></span>
  <span data-ttu-id="749c3-103">报表服务器管理 Web 服务包含可用于管理报表服务器数据库中的报表、文件夹和资源的方法。</span><span class="sxs-lookup"><span data-stu-id="749c3-103">The Report Server Management Web service contains methods that you can use to manage reports, folders, and resources in the report server database.</span></span>  
  
|<span data-ttu-id="749c3-104">方法</span><span class="sxs-lookup"><span data-stu-id="749c3-104">Method</span></span>|<span data-ttu-id="749c3-105">操作</span><span class="sxs-lookup"><span data-stu-id="749c3-105">Action</span></span>|  
|------------|------------|  
|<xref:ReportService2010.ReportingService2010.CancelJob%2A>|<span data-ttu-id="749c3-106">取消某一作业的执行。</span><span class="sxs-lookup"><span data-stu-id="749c3-106">Cancels execution of a job.</span></span>|  
|<xref:ReportService2010.ReportingService2010.CreateFolder%2A>|<span data-ttu-id="749c3-107">将文件夹添加到报表服务器数据库或 SharePoint 库。</span><span class="sxs-lookup"><span data-stu-id="749c3-107">Adds a folder to the report server database or SharePoint library.</span></span>|  
|<xref:ReportService2010.ReportingService2010.CreateCatalogItem%2A>|<span data-ttu-id="749c3-108">将新项添加到报表服务器数据库或 SharePoint 库。</span><span class="sxs-lookup"><span data-stu-id="749c3-108">Adds a new item to a report server database or SharePoint library.</span></span> <span data-ttu-id="749c3-109">此方法适用于`Report`、`Model`、`Dataset`、`Component`、`Resource`和`DataSource`项类型。</span><span class="sxs-lookup"><span data-stu-id="749c3-109">This method applies to the `Report`, `Model`, `Dataset`, `Component`, `Resource`, and `DataSource` item types.</span></span>|  
|<span data-ttu-id="749c3-110">M:ReportService2010.ReportingService2010.CreateReportEditSession(System.String,System.String,System.Byte[],ReportService2010.Warning[]@)</span><span class="sxs-lookup"><span data-stu-id="749c3-110">M:ReportService2010.ReportingService2010.CreateReportEditSession(System.String,System.String,System.Byte[],ReportService2010.Warning[]@)</span></span>|<span data-ttu-id="749c3-111">创建新的报表编辑会话。</span><span class="sxs-lookup"><span data-stu-id="749c3-111">Creates a new report edit session.</span></span>|  
|<xref:ReportService2010.ReportingService2010.DeleteItem%2A>|<span data-ttu-id="749c3-112">从报表服务器数据库或 SharePoint 库删除项。</span><span class="sxs-lookup"><span data-stu-id="749c3-112">Removes an item from the report server database or SharePoint library.</span></span>|  
|<xref:ReportService2010.ReportingService2010.FindItems%2A>|<span data-ttu-id="749c3-113">返回报表服务器数据库或 SharePoint 库中与指定的搜索条件匹配的项。</span><span class="sxs-lookup"><span data-stu-id="749c3-113">Returns the items in the report server database or SharePoint library that match the specified search criteria.</span></span>|  
|<xref:ReportService2010.ReportingService2010.FireEvent%2A>|<span data-ttu-id="749c3-114">基于提供的参数触发事件。</span><span class="sxs-lookup"><span data-stu-id="749c3-114">Triggers an event based on the supplied parameters.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetExtensionSettings%2A>|<span data-ttu-id="749c3-115">返回针对给定扩展插件的设置列表。</span><span class="sxs-lookup"><span data-stu-id="749c3-115">Returns a list of settings for a given extension.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetItemType%2A>|<span data-ttu-id="749c3-116">检索报表服务器数据库或 SharePoint 库中某一项的类型（如果该项存在）。</span><span class="sxs-lookup"><span data-stu-id="749c3-116">Retrieves the type of an item in the report server database or SharePoint library, if the item exists.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetProperties%2A>|<span data-ttu-id="749c3-117">对于报表服务器数据库或 SharePoint 库中的项返回一个或多个属性的值。</span><span class="sxs-lookup"><span data-stu-id="749c3-117">Returns the values of one or more properties on an item in the report server database or SharePoint library.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetItemDefinition%2A>|<span data-ttu-id="749c3-118">检索项的定义或内容。</span><span class="sxs-lookup"><span data-stu-id="749c3-118">Retrieves the definition or content for an item.</span></span> <span data-ttu-id="749c3-119">此方法适用于`Report`、`Model`、`Dataset`、`Component`、`Resource`和`DataSource`项类型。</span><span class="sxs-lookup"><span data-stu-id="749c3-119">This method applies to the `Report`, `Model`, `Dataset`, `Component`, `Resource`, and `DataSource` item types.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetItemReferences%2A>|<span data-ttu-id="749c3-120">返回与项关联的目录项引用的列表。</span><span class="sxs-lookup"><span data-stu-id="749c3-120">Returns a list of catalog item references associated with an item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetReportServerConfigInfo%2A>|<span data-ttu-id="749c3-121">返回有关连接的报表服务器实例或扩展部署中所有报表服务器实例的信息。</span><span class="sxs-lookup"><span data-stu-id="749c3-121">Returns information on the connected report server instance or all the report server instances in a scale-out deployment.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetSystemProperties%2A>|<span data-ttu-id="749c3-122">返回一个或多个系统属性。</span><span class="sxs-lookup"><span data-stu-id="749c3-122">Returns one or more system properties.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListChildren%2A>|<span data-ttu-id="749c3-123">获取指定文件夹的子级的列表。</span><span class="sxs-lookup"><span data-stu-id="749c3-123">Gets a list of children of a specified folder.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListDatabaseCredentialRetrievalOptions%2A>|<span data-ttu-id="749c3-124">返回支持的凭据检索选项列表。</span><span class="sxs-lookup"><span data-stu-id="749c3-124">Returns a list of supported credential retrieval options.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListEvents%2A>|<span data-ttu-id="749c3-125">返回在报表服务器配置文件中出现的事件扩展插件的列表。</span><span class="sxs-lookup"><span data-stu-id="749c3-125">Returns a list of event extensions as they appear in the report server configuration file.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListJobs%2A>|<span data-ttu-id="749c3-126">返回报表服务器上运行的作业的列表。</span><span class="sxs-lookup"><span data-stu-id="749c3-126">Returns a list of jobs running on the report server.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListExtensions%2A>|<span data-ttu-id="749c3-127">返回为给定扩展插件类型配置的扩展插件的列表。</span><span class="sxs-lookup"><span data-stu-id="749c3-127">Returns a list of extensions that are configured for a given extension type.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListExtensionTypes%2A>|<span data-ttu-id="749c3-128">返回支持的扩展插件类型的列表。</span><span class="sxs-lookup"><span data-stu-id="749c3-128">Returns a list of supported extension types.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListItemTypes%2A>|<span data-ttu-id="749c3-129">返回支持的目录项类型的列表。</span><span class="sxs-lookup"><span data-stu-id="749c3-129">Returns a list of supported catalog item types.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListJobActions%2A>|<span data-ttu-id="749c3-130">返回支持的作业操作的列表。</span><span class="sxs-lookup"><span data-stu-id="749c3-130">Returns a list of supported job actions.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListJobStates%2A>|<span data-ttu-id="749c3-131">返回支持的作业状态的列表。</span><span class="sxs-lookup"><span data-stu-id="749c3-131">Returns a list of supported job states.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListJobTypes%2A>|<span data-ttu-id="749c3-132">返回支持的作业类型的列表。</span><span class="sxs-lookup"><span data-stu-id="749c3-132">Returns a list of supported job types.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListParents%2A>|<span data-ttu-id="749c3-133">检索给定项的父项。</span><span class="sxs-lookup"><span data-stu-id="749c3-133">Retrieves parent items for the given item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListSecurityScopes%2A>|<span data-ttu-id="749c3-134">返回支持的安全范围的列表。</span><span class="sxs-lookup"><span data-stu-id="749c3-134">Returns a list of supported security scopes.</span></span>|  
|<xref:ReportService2010.ReportingService2010.Logoff%2A>|<span data-ttu-id="749c3-135">注销发出 Web 服务请求的当前用户。</span><span class="sxs-lookup"><span data-stu-id="749c3-135">Logs out the current user making Web service requests.</span></span> <span data-ttu-id="749c3-136">此方法仅适用于本机模式。</span><span class="sxs-lookup"><span data-stu-id="749c3-136">This method only applies to native mode.</span></span>|  
|<xref:ReportService2010.ReportingService2010.LogonUser%2A>|<span data-ttu-id="749c3-137">使用户登录，然后验证对报表服务器 Web 服务的用户请求。</span><span class="sxs-lookup"><span data-stu-id="749c3-137">Logs on a user and authenticates a user request to the Report Server Web service.</span></span> <span data-ttu-id="749c3-138">此方法仅适用于本机模式。</span><span class="sxs-lookup"><span data-stu-id="749c3-138">This method only applies to native mode.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetItemReferences%2A>|<span data-ttu-id="749c3-139">设置与项关联的目录项。</span><span class="sxs-lookup"><span data-stu-id="749c3-139">Sets the catalog items associated with an item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.MoveItem%2A>|<span data-ttu-id="749c3-140">移动和/或重命名某项。</span><span class="sxs-lookup"><span data-stu-id="749c3-140">Moves and/or renames an item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetProperties%2A>|<span data-ttu-id="749c3-141">设置项的一个或多个属性。</span><span class="sxs-lookup"><span data-stu-id="749c3-141">Sets one or more properties of an item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetItemDefinition%2A>|<span data-ttu-id="749c3-142">设置指定项的定义或内容。</span><span class="sxs-lookup"><span data-stu-id="749c3-142">Sets the definition or content for a specified item.</span></span> <span data-ttu-id="749c3-143">此方法适用于`Report`、`Model`、`Dataset`、`Component`、`Resource`和`DataSource`项类型。</span><span class="sxs-lookup"><span data-stu-id="749c3-143">This method applies to the `Report`, `Model`, `Dataset`, `Component`, `Resource`, and `DataSource` item types.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetSystemProperties%2A>|<span data-ttu-id="749c3-144">在报表服务器或 SharePoint 场中设置一个或多个系统属性。</span><span class="sxs-lookup"><span data-stu-id="749c3-144">Sets one or more system properties in the report server or SharePoint farm.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ValidateExtensionSettings%2A>|<span data-ttu-id="749c3-145">验证 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 扩展插件设置。</span><span class="sxs-lookup"><span data-stu-id="749c3-145">Validates [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] extension settings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="749c3-146">另请参阅</span><span class="sxs-lookup"><span data-stu-id="749c3-146">See Also</span></span>  
 <span data-ttu-id="749c3-147">[使用 Web 服务和 .NET Framework 生成应用程序](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="749c3-147">[Building Applications Using the Web Service and the .NET Framework](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 <span data-ttu-id="749c3-148">[报表服务器 Web 服务](../report-server-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="749c3-148">[Report Server Web Service](../report-server-web-service.md) </span></span>  
 <span data-ttu-id="749c3-149">[报表服务器 Web 服务方法](report-server-web-service-methods.md) </span><span class="sxs-lookup"><span data-stu-id="749c3-149">[Report Server Web Service Methods](report-server-web-service-methods.md) </span></span>  
 [<span data-ttu-id="749c3-150">技术参考 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="749c3-150">Technical Reference &#40;SSRS&#41;</span></span>](../../technical-reference-ssrs.md)  
  
  
