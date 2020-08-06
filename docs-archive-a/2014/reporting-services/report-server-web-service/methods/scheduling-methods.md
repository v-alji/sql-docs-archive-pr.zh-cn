---
title: 计划方法 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- schedules [Reporting Services], methods
- reports [Reporting Services], scheduling
- shared schedules [Reporting Services], methods
- methods [Reporting Services], scheduling
ms.assetid: 68ae13f9-d91e-4572-a82a-8fa42001569e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 735da4f22d523fd40dd031f55e203fa9a4204f5b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578622"
---
# <a name="scheduling-methods"></a><span data-ttu-id="acfb3-102">计划方法</span><span class="sxs-lookup"><span data-stu-id="acfb3-102">Scheduling Methods</span></span>
  <span data-ttu-id="acfb3-103">可以使用这些方法来创建和管理用于报表执行和传递的共享计划，还可以使用这些方法来缓存报表服务器使用的刷新计划。</span><span class="sxs-lookup"><span data-stu-id="acfb3-103">You can use these methods to create and manage shared schedules for report execution and delivery, and to cache refresh plans utilized by the report server.</span></span>  
  
|<span data-ttu-id="acfb3-104">方法</span><span class="sxs-lookup"><span data-stu-id="acfb3-104">Method</span></span>|<span data-ttu-id="acfb3-105">操作</span><span class="sxs-lookup"><span data-stu-id="acfb3-105">Action</span></span>|  
|------------|------------|  
|<xref:ReportService2010.ReportingService2010.CreateCacheRefreshPlan%2A>|<span data-ttu-id="acfb3-106">创建项的缓存刷新计划。</span><span class="sxs-lookup"><span data-stu-id="acfb3-106">Creates a cache refresh plan for an item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.CreateSchedule%2A>|<span data-ttu-id="acfb3-107">创建新的共享计划。</span><span class="sxs-lookup"><span data-stu-id="acfb3-107">Creates a new shared schedule.</span></span>|  
|<xref:ReportService2010.ReportingService2010.DeleteCacheRefreshPlan%2A>|<span data-ttu-id="acfb3-108">删除缓存刷新计划。</span><span class="sxs-lookup"><span data-stu-id="acfb3-108">Deletes a cache refresh plan.</span></span>|  
|<xref:ReportService2010.ReportingService2010.DeleteSchedule%2A>|<span data-ttu-id="acfb3-109">基于特定的计划 ID 删除共享计划。</span><span class="sxs-lookup"><span data-stu-id="acfb3-109">Deletes a shared schedule based on a specific schedule ID.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetCacheRefreshPlanProperties%2A>|<span data-ttu-id="acfb3-110">返回指定的缓存刷新计划的属性。</span><span class="sxs-lookup"><span data-stu-id="acfb3-110">Returns the properties of the specified cache refresh plan.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetScheduleProperties%2A>|<span data-ttu-id="acfb3-111">返回共享计划的属性值。</span><span class="sxs-lookup"><span data-stu-id="acfb3-111">Returns the values of properties of a shared schedule.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListCacheRefreshPlans%2A>|<span data-ttu-id="acfb3-112">返回与目录项关联的缓存刷新计划的列表。</span><span class="sxs-lookup"><span data-stu-id="acfb3-112">Returns a list of the cache refresh plans associated with a catalog item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListScheduledItems%2A>|<span data-ttu-id="acfb3-113">返回与共享计划关联的项的列表。</span><span class="sxs-lookup"><span data-stu-id="acfb3-113">Returns a list of items that are associated with a shared schedule.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListSchedules%2A>|<span data-ttu-id="acfb3-114">返回报表服务器或 SharePoint 网站上的所有共享计划列表。</span><span class="sxs-lookup"><span data-stu-id="acfb3-114">Returns a list of all shared schedules at the report server or the SharePoint site.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListScheduleStates%2A>|<span data-ttu-id="acfb3-115">返回支持的计划状态的列表。</span><span class="sxs-lookup"><span data-stu-id="acfb3-115">Returns a list of supported schedule states.</span></span>|  
|<xref:ReportService2010.ReportingService2010.PauseSchedule%2A>|<span data-ttu-id="acfb3-116">暂停给定计划的执行。</span><span class="sxs-lookup"><span data-stu-id="acfb3-116">Pauses the execution of a given schedule.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ResumeSchedule%2A>|<span data-ttu-id="acfb3-117">恢复已暂停的共享计划。</span><span class="sxs-lookup"><span data-stu-id="acfb3-117">Resumes a shared schedule that has been paused.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetCacheRefreshPlanProperties%2A>|<span data-ttu-id="acfb3-118">设置缓存刷新计划的属性。</span><span class="sxs-lookup"><span data-stu-id="acfb3-118">Sets the properties of a cache refresh plan.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetScheduleProperties%2A>|<span data-ttu-id="acfb3-119">设置共享计划的属性值。</span><span class="sxs-lookup"><span data-stu-id="acfb3-119">Sets the value of properties of a shared schedule.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="acfb3-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="acfb3-120">See Also</span></span>  
 <span data-ttu-id="acfb3-121">[使用 Web 服务和 .NET Framework 生成应用程序](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="acfb3-121">[Building Applications Using the Web Service and the .NET Framework](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 <span data-ttu-id="acfb3-122">[报表服务器 Web 服务](../report-server-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="acfb3-122">[Report Server Web Service](../report-server-web-service.md) </span></span>  
 <span data-ttu-id="acfb3-123">[报表服务器 Web 服务方法](report-server-web-service-methods.md) </span><span class="sxs-lookup"><span data-stu-id="acfb3-123">[Report Server Web Service Methods](report-server-web-service-methods.md) </span></span>  
 [<span data-ttu-id="acfb3-124">技术参考 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="acfb3-124">Technical Reference &#40;SSRS&#41;</span></span>](../../technical-reference-ssrs.md)  
  
  
