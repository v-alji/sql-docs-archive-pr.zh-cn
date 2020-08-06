---
title: 使用 SOAP 集成 Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Report Server Web service, application integration
- SOAP [Reporting Services]
- SOAP [Reporting Services], about report integration
- integrating reports [Reporting Services]
- Web service [Reporting Services], application integration
ms.assetid: 6bc17af5-883c-4bfa-87d9-48cd7056d145
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7b6fffd65b22900d7c505c4b50ec290b95fe9ab4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577403"
---
# <a name="integrating-reporting-services-using-soap"></a><span data-ttu-id="2374d-102">使用 SOAP 集成 Reporting Services</span><span class="sxs-lookup"><span data-stu-id="2374d-102">Integrating Reporting Services Using SOAP</span></span>
  <span data-ttu-id="2374d-103">[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SOAP API 提供了若干用于开发自定义报表解决方案的 Web 服务终结点。</span><span class="sxs-lookup"><span data-stu-id="2374d-103">The [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SOAP API provides several Web service endpoints for developing custom reporting solutions.</span></span> <span data-ttu-id="2374d-104">这些端点目前分为两个类别：管理和执行。</span><span class="sxs-lookup"><span data-stu-id="2374d-104">The endpoints currently fall into two categories: management and execution.</span></span> <span data-ttu-id="2374d-105">管理功能通过 <xref:ReportService2005>、<xref:ReportService2006> 和 <xref:ReportService2010> 端点公开。</span><span class="sxs-lookup"><span data-stu-id="2374d-105">The management functionality is exposed through the <xref:ReportService2005>, <xref:ReportService2006>, and <xref:ReportService2010> endpoints.</span></span> <span data-ttu-id="2374d-106"><xref:ReportService2005> 端点用于管理配置为本机模式的报表服务器，而 <xref:ReportService2006> 端点用于管理配置为 SharePoint 集成模式的报表服务器。</span><span class="sxs-lookup"><span data-stu-id="2374d-106">The <xref:ReportService2005> endpoint is used for managing a report server that is configured in native mode and the <xref:ReportService2006> endpoint is used for managing a report server that is configured for SharePoint integrated mode.</span></span> <span data-ttu-id="2374d-107"><xref:ReportService2010> 合并了 <xref:ReportService2005> 和 <xref:ReportService2006> 的功能，可以管理配置为本机模式或 SharePoint 集成模式的报表服务器。</span><span class="sxs-lookup"><span data-stu-id="2374d-107">The <xref:ReportService2010> merges the functionalities of <xref:ReportService2005> and <xref:ReportService2006> and can manage a report server that is configured for either native or SharePoint integrated mode.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2374d-108">在 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 中不推荐使用 <xref:ReportService2005> 和 <xref:ReportService2006> 端点。</span><span class="sxs-lookup"><span data-stu-id="2374d-108">The <xref:ReportService2005> and <xref:ReportService2006> endpoints are deprecated in [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].</span></span> <span data-ttu-id="2374d-109"><xref:ReportService2010> 端点包含两个端点的功能和其他管理功能。</span><span class="sxs-lookup"><span data-stu-id="2374d-109">The <xref:ReportService2010> endpoint includes the functionalities of both endpoints and contains additional management features.</span></span>  
  
 <span data-ttu-id="2374d-110">执行功能通过 <xref:ReportExecution2005> 端点公开，当将报表服务器配置为本机模式或 SharePoint 集成模式时使用它。</span><span class="sxs-lookup"><span data-stu-id="2374d-110">The execution functionality is exposed through the <xref:ReportExecution2005> endpoint and it is used when the report server is configured in native or SharePoint integrated mode.</span></span> <span data-ttu-id="2374d-111">以下主题说明如何使用这些端点在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows、SharePoint 和 Web 应用程序中开发报表解决方案。</span><span class="sxs-lookup"><span data-stu-id="2374d-111">The following topics show how these endpoints can be used for developing reporting solutions in [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, SharePoint, and Web applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2374d-112">本节内容</span><span class="sxs-lookup"><span data-stu-id="2374d-112">In This Section</span></span>  
 [<span data-ttu-id="2374d-113">在 Windows 应用程序中使用 SOAP API</span><span class="sxs-lookup"><span data-stu-id="2374d-113">Using the SOAP API in a Windows Application</span></span>](integrating-reporting-services-using-soap-windows-application.md)  
 <span data-ttu-id="2374d-114">介绍如何使用 SOAP API 将 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 集成到 Windows 环境中。</span><span class="sxs-lookup"><span data-stu-id="2374d-114">Describes how to use the SOAP API to integrate [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] into a Windows environment.</span></span>  
  
 [<span data-ttu-id="2374d-115">在 Web 应用程序中使用 SOAP API</span><span class="sxs-lookup"><span data-stu-id="2374d-115">Using the SOAP API in a Web Application</span></span>](integrating-reporting-services-using-soap-web-application.md)  
 <span data-ttu-id="2374d-116">介绍如何使用 SOAP API 将 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 集成到 Web 环境中。</span><span class="sxs-lookup"><span data-stu-id="2374d-116">Describes how to use the SOAP API to integrate [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] into a Web environment.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2374d-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2374d-117">See Also</span></span>  
 <span data-ttu-id="2374d-118">[将 Reporting Services 集成到应用程序中](../application-integration/integrating-reporting-services-into-applications.md) </span><span class="sxs-lookup"><span data-stu-id="2374d-118">[Integrating Reporting Services into Applications](../application-integration/integrating-reporting-services-into-applications.md) </span></span>  
 <span data-ttu-id="2374d-119">[报表服务器 Web 服务](../report-server-web-service/report-server-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="2374d-119">[Report Server Web Service](../report-server-web-service/report-server-web-service.md) </span></span>  
 [<span data-ttu-id="2374d-120">使用 Web 服务和 .NET Framework 生成应用程序</span><span class="sxs-lookup"><span data-stu-id="2374d-120">Building Applications Using the Web Service and the .NET Framework</span></span>](../report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)  
  
  
