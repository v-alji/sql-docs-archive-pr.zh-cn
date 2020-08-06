---
title: 报表服务器 Web 服务终结点 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- management endpoints [Reporting Services]
- Web service [Reporting Services], endpoints
- endpoints [Reporting Services]
- execution endpoints [Reporting Services]
- Report Server Web service, endpoints
ms.assetid: f3f5d85f-9359-4508-bc5a-7f78a3cf7421
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 70281c5171eb37d9888d663542a7850820c81bea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690348"
---
# <a name="report-server-web-service-endpoints"></a><span data-ttu-id="d69d7-102">报表服务器 Web 服务端点</span><span class="sxs-lookup"><span data-stu-id="d69d7-102">Report Server Web Service Endpoints</span></span>
  <span data-ttu-id="d69d7-103">报表服务器 Web 服务提供了几个端点，用于管理报表服务器以及执行和导航报表。</span><span class="sxs-lookup"><span data-stu-id="d69d7-103">The Report Server Web service provides several endpoints for managing a report server as well as executing and navigating reports.</span></span>  
  
## <a name="the-management-endpoints"></a><span data-ttu-id="d69d7-104">管理端点</span><span class="sxs-lookup"><span data-stu-id="d69d7-104">The Management Endpoints</span></span>  
 <span data-ttu-id="d69d7-105">有三个端点可用于管理报表服务器上的对象，即：<xref:ReportService2005>、<xref:ReportService2006> 和 <xref:ReportService2010>。</span><span class="sxs-lookup"><span data-stu-id="d69d7-105">There are three endpoints available for managing objects on a report server, <xref:ReportService2005>, <xref:ReportService2006>, and <xref:ReportService2010>.</span></span> <span data-ttu-id="d69d7-106"><xref:ReportService2005> 端点用于管理配置为本机模式的报表服务器上的对象。</span><span class="sxs-lookup"><span data-stu-id="d69d7-106">The <xref:ReportService2005> endpoint is used for managing objects on a report server that is configured for native mode.</span></span> <span data-ttu-id="d69d7-107"><xref:ReportService2006> 端点用于管理配置为 SharePoint 集成模式的报表服务器上的对象。</span><span class="sxs-lookup"><span data-stu-id="d69d7-107">The <xref:ReportService2006> endpoint is used for managing objects on a report server that is configured for SharePoint integrated mode.</span></span> <span data-ttu-id="d69d7-108"><xref:ReportService2010> 终结点合并了 <xref:ReportService2005> 和 <xref:ReportService2006> 的功能，可以管理为本机或 SharePoint 集成模式配置的报表服务器上的对象。</span><span class="sxs-lookup"><span data-stu-id="d69d7-108">The <xref:ReportService2010> endpoint merges the functionalities of <xref:ReportService2005> and <xref:ReportService2006> and can manage objects on a report server that are configured for either native or SharePoint integrated mode.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="d69d7-109">当报表服务器配置为 SharePoint 集成模式时，<xref:ReportService2005> API 将返回 `rsOperationNotSupportedSharePointMode` 错误。</span><span class="sxs-lookup"><span data-stu-id="d69d7-109">When a report server is configured for SharePoint integrated mode, the <xref:ReportService2005> APIs will return an `rsOperationNotSupportedSharePointMode` error.</span></span> <span data-ttu-id="d69d7-110">如果报表服务器配置为本机模式，<xref:ReportService2006> API 将返回 `rsOperationNotSupportedNativeMode` 错误。</span><span class="sxs-lookup"><span data-stu-id="d69d7-110">If the report server is configured for native mode, the <xref:ReportService2006> APIs will return an `rsOperationNotSupportedNativeMode` error.</span></span> <span data-ttu-id="d69d7-111">同样，在非预期模式中使用 <xref:ReportService2010> 中的模式特定 API 时，API 将返回相应的错误。</span><span class="sxs-lookup"><span data-stu-id="d69d7-111">Similarly, when mode-specific APIs in <xref:ReportService2010> are used on unintended modes, the APIs will return the respective errors.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d69d7-112">在 [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] 中不推荐使用 <xref:ReportService2005> 和 <xref:ReportService2006> 端点。</span><span class="sxs-lookup"><span data-stu-id="d69d7-112">The <xref:ReportService2005> and <xref:ReportService2006> endpoints are deprecated in [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)].</span></span> <span data-ttu-id="d69d7-113"><xref:ReportService2010> 端点包含两个端点的功能和其他管理功能。</span><span class="sxs-lookup"><span data-stu-id="d69d7-113">The <xref:ReportService2010> endpoint includes the functionalities of both endpoints and contains additional management features.</span></span>  
  
 <span data-ttu-id="d69d7-114">如果将报表服务器配置为本机模式或 SharePoint 集成模式，则可以使用以下 URL 之一访问管理端点的 WSDL：</span><span class="sxs-lookup"><span data-stu-id="d69d7-114">If the report server is configured for native mode or SharePoint integrate mode, the WSDL for the management endpoint can be accessed using one of the following URL:</span></span>  
  
```  
http://<Server Name>/ReportServer/ReportService2010.asmx?wsdl  
```  
  
 <span data-ttu-id="d69d7-115">有关详细信息，请参阅[访问 SOAP API](../accessing-the-soap-api.md)。</span><span class="sxs-lookup"><span data-stu-id="d69d7-115">For more information, see [Accessing the SOAP API](../accessing-the-soap-api.md).</span></span>  
  
## <a name="the-execution-endpoint"></a><span data-ttu-id="d69d7-116">执行端点</span><span class="sxs-lookup"><span data-stu-id="d69d7-116">The Execution Endpoint</span></span>  
 <span data-ttu-id="d69d7-117">通过 <xref:ReportExecution2005> 端点，开发人员可以轻松地从处于本机模式和 SharePoint 集成模式下的报表服务器自定义报表处理和呈现。</span><span class="sxs-lookup"><span data-stu-id="d69d7-117">The <xref:ReportExecution2005> endpoint makes it easy for developers to customize report processing and rendering from a report server in both native and SharePoint integrated modes.</span></span> <span data-ttu-id="d69d7-118">此端点包含报表服务器 Web 服务的先前版本中提供的类和方法。</span><span class="sxs-lookup"><span data-stu-id="d69d7-118">The endpoint includes classes and methods that existed in earlier versions of the Report Server Web service.</span></span> <span data-ttu-id="d69d7-119">此外，还向报表服务器 Web 服务添加了许多通过执行端点公开的新类和新方法。</span><span class="sxs-lookup"><span data-stu-id="d69d7-119">In addition, many new classes and methods have been added to the Report Server Web service that are exposed through the execution endpoint.</span></span>  
  
 <span data-ttu-id="d69d7-120">可以使用以下 URL 访问管理端点的 WSDL：</span><span class="sxs-lookup"><span data-stu-id="d69d7-120">The WSDL for the management endpoint can be accessed using the following URL:</span></span>  
  
```  
http://<Server Name>/ReportServer/ReportExecution2005.asmx?wsdl  
```  
  
 <span data-ttu-id="d69d7-121">如果将报表服务器配置为 SharePoint 集成模式，则可以使用以下 URL 访问 WSDL：</span><span class="sxs-lookup"><span data-stu-id="d69d7-121">If the report server is configured for SharePoint integrate mode, the WSDL can be accessed using the following URL:</span></span>  
  
```  
http://<Server Name>/<Site Name>/_vti_bin/ReportServer/ReportExecution2005.asmx?wsdl  
```  
  
 <span data-ttu-id="d69d7-122">有关详细信息，请参阅[访问 SOAP API](../accessing-the-soap-api.md)。</span><span class="sxs-lookup"><span data-stu-id="d69d7-122">For more information, please see [Accessing the SOAP API](../accessing-the-soap-api.md).</span></span>  
  
## <a name="sharepoint-proxy-endpoints"></a><span data-ttu-id="d69d7-123">SharePoint 代理端点</span><span class="sxs-lookup"><span data-stu-id="d69d7-123">SharePoint Proxy Endpoints</span></span>  
 <span data-ttu-id="d69d7-124">当报表服务器配置为 SharePoint 集成模式且已安装 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 外接程序时，将在 SharePoint 服务器上安装一组代理端点。</span><span class="sxs-lookup"><span data-stu-id="d69d7-124">When a report server is configured for SharePoint integrated mode and the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Add-in has been installed, a set of proxy endpoints are installed on the SharePoint server.</span></span> <span data-ttu-id="d69d7-125">当将报表服务器配置为 SharePoint 集成模式时，代理端点是用于开发报表解决方案的主要 API。</span><span class="sxs-lookup"><span data-stu-id="d69d7-125">The proxy endpoints are the primary API for developing report solutions when a report server is configured for SharePoint integrated mode.</span></span> <span data-ttu-id="d69d7-126">当针对代理端点进行开发时，[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 外接程序在可信帐户身份验证模式下管理 SharePoint 服务器与报表服务器之间的凭据交换。</span><span class="sxs-lookup"><span data-stu-id="d69d7-126">When developing against the proxy endpoints, the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Add-in manages the exchange of credentials between the SharePoint server and the report server in Trusted account authentication mode.</span></span> <span data-ttu-id="d69d7-127">当针对报表服务器端点进行开发时，调用应用程序必须在可信帐户身份验证模式下管理凭据交换。</span><span class="sxs-lookup"><span data-stu-id="d69d7-127">When developing against the report server endpoints, the calling application will have to manage the credential exchange in Trusted account authentication mode.</span></span> <span data-ttu-id="d69d7-128">下表列出随 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 外接程序安装的端点。</span><span class="sxs-lookup"><span data-stu-id="d69d7-128">The following table lists the endpoints that are installed with the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Add-in.</span></span>  
  
|<span data-ttu-id="d69d7-129">代理端点</span><span class="sxs-lookup"><span data-stu-id="d69d7-129">Proxy Endpoint</span></span>|<span data-ttu-id="d69d7-130">说明</span><span class="sxs-lookup"><span data-stu-id="d69d7-130">Description</span></span>|  
|--------------------|-----------------|  
|<xref:ReportService2006>|<span data-ttu-id="d69d7-131">为管理配置为 SharePoint 集成模式的报表服务器提供 API。</span><span class="sxs-lookup"><span data-stu-id="d69d7-131">Provides the APIs for managing a report server that is configured for SharePoint integrate mode.</span></span> <span data-ttu-id="d69d7-132">**注意：** 此终结点在中已弃用 [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="d69d7-132">**Note:**  This endpoint is deprecated in [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)].</span></span>|  
|<xref:ReportService2010>|<span data-ttu-id="d69d7-133">为管理配置为本机模式或 SharePoint 集成模式的报表服务器提供 API。</span><span class="sxs-lookup"><span data-stu-id="d69d7-133">Provides the APIs for managing a report server that is configured for either native or SharePoint integrated mode.</span></span>|  
|<xref:ReportExecution2005>|<span data-ttu-id="d69d7-134">提供用于运行和导航报表的 API。</span><span class="sxs-lookup"><span data-stu-id="d69d7-134">Provides the APIs for running and navigating reports.</span></span>|  
|<xref:ReportServiceAuthentication>|<span data-ttu-id="d69d7-135">提供 API，以便在将 SharePoint Web 应用程序配置为窗体身份验证时，针对报表服务器对用户进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="d69d7-135">Provides the APIs for authenticating users against a report server when the SharePoint Web application is configured for Forms Authentication.</span></span>|  
  
 <span data-ttu-id="d69d7-136">以下是引用 SharePoint 站点上代理端点的示例 URL。</span><span class="sxs-lookup"><span data-stu-id="d69d7-136">The following are example URLs for referencing the proxy endpoints on a SharePoint site.</span></span>  
  
```  
http://<Server Name>/<Site Name>/_vti_bin/ReportServer/ReportService2010.asmx  
```  
  
```  
http://<Server Name>/<Site Name>/_vti_bin/ReportServer/ReportExecution2005.asmx  
```  
  
```  
http://<Server Name>/<Site Name>/_vti_bin/ReportServer/ReportServiceAuthentication.asmx  
```  
  
## <a name="see-also"></a><span data-ttu-id="d69d7-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d69d7-137">See Also</span></span>  
 [<span data-ttu-id="d69d7-138">使用 Web 服务和 .NET Framework 生成应用程序</span><span class="sxs-lookup"><span data-stu-id="d69d7-138">Building Applications Using the Web Service and the .NET Framework</span></span>](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md)  
  
  
