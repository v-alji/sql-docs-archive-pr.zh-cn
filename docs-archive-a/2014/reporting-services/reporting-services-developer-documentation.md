---
title: 开发人员&#39;指南 (Reporting Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- developer's guide [Reporting Services]
- Reporting Services, programming
- programming [Reporting Services]
ms.assetid: d8afa405-1012-4349-a72d-e10d94f8453d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bcf880db543c891a0ffccab932fddc614df34e17
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691054"
---
# <a name="developer39s-guide-reporting-services"></a><span data-ttu-id="b3423-102">开发人员&#39;指南 (Reporting Services) </span><span class="sxs-lookup"><span data-stu-id="b3423-102">Developer&#39;s Guide (Reporting Services)</span></span>
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="b3423-103">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 提供了多个编程接口，你可以在自己的应用程序中利用这些接口。</span><span class="sxs-lookup"><span data-stu-id="b3423-103">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] offers several programming interfaces that you can leverage in your own applications.</span></span> <span data-ttu-id="b3423-104">您可以使用 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 的现有特性和功能将自定义报表和管理工具置入网站和 Windows 应用程序，也可以扩展 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 平台。</span><span class="sxs-lookup"><span data-stu-id="b3423-104">You can use the existing features and capabilities of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] to build custom reporting and management tools into Web sites and Windows applications, or you can extend the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] platform.</span></span>  
  
 <span data-ttu-id="b3423-105">扩展 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 平台包括创建可用于数据访问、报表传递等等的新组件和资源。</span><span class="sxs-lookup"><span data-stu-id="b3423-105">Extending the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] platform includes creating new components and resources that can be used for data access, report delivery and more.</span></span> <span data-ttu-id="b3423-106">可以向在其组织中使用 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 的公司销售这些组件和资源。</span><span class="sxs-lookup"><span data-stu-id="b3423-106">You can market these components and resources to companies that are using [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] in their organization.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b3423-107">本节内容</span><span class="sxs-lookup"><span data-stu-id="b3423-107">In This Section</span></span>  
 [<span data-ttu-id="b3423-108">将 Reporting Services 集成到应用程序中</span><span class="sxs-lookup"><span data-stu-id="b3423-108">Integrating Reporting Services into Applications</span></span>](application-integration/integrating-reporting-services-into-applications.md)  
 <span data-ttu-id="b3423-109">概述如何使用 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 将报表功能集成到自定义应用程序中。</span><span class="sxs-lookup"><span data-stu-id="b3423-109">Provides an overview of how to use [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] to integrate reporting into custom applications.</span></span> <span data-ttu-id="b3423-110">介绍何时使用直接 URL 访问以及何时使用 Web 服务来访问报表服务器。</span><span class="sxs-lookup"><span data-stu-id="b3423-110">Describes when to use direct URL access and when to use the Web service to access the report server.</span></span>  
  
 [<span data-ttu-id="b3423-111">报表服务器 Web 服务</span><span class="sxs-lookup"><span data-stu-id="b3423-111">Report Server Web Service</span></span>](report-server-web-service/report-server-web-service.md)  
 <span data-ttu-id="b3423-112">通过报表服务器 Web 服务，可以访问报表服务器的完整功能。</span><span class="sxs-lookup"><span data-stu-id="b3423-112">The Report Server Web service provides access to the full functionality of the report server.</span></span> <span data-ttu-id="b3423-113">Web 服务使用 HTTP 上的 SOAP (SOAP over HTTP)，它旨在充当客户端程序与报表服务器之间的通信接口。</span><span class="sxs-lookup"><span data-stu-id="b3423-113">The Web service uses SOAP over HTTP and is designed to act as a communications interface between client programs and the report server.</span></span> <span data-ttu-id="b3423-114">Web 服务及其方法公开报表服务器的功能，并使您能够为报表生命周期的任何部分（从管理到执行）创建自定义工具。</span><span class="sxs-lookup"><span data-stu-id="b3423-114">The Web service and its methods expose the functionality of the report server and allow you to create custom tools for any part of the report life cycle, from management to execution.</span></span>  
  
 [<span data-ttu-id="b3423-115">URL 访问 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="b3423-115">URL Access &#40;SSRS&#41;</span></span>](url-access-ssrs.md)  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] <span data-ttu-id="b3423-116">支持一组完整的基于 URL 的请求，您可以将这些请求用作进行报表导航和查看的快捷访问点。</span><span class="sxs-lookup"><span data-stu-id="b3423-116">supports a complete set of URL-based requests that you can use as a quick and easy access point for report navigation and viewing.</span></span> <span data-ttu-id="b3423-117">可以将此技术与报表服务器 Web 服务结合使用，以便将完整的报表解决方案集成到自定义业务应用程序中。</span><span class="sxs-lookup"><span data-stu-id="b3423-117">You can use this technology in conjunction with the Report Server Web service to integrate a complete reporting solution into your custom business applications.</span></span> <span data-ttu-id="b3423-118">当将报表作为 Web 门户的一部分集成或从 Web 浏览器查看报表时，URl 访问尤其有用。</span><span class="sxs-lookup"><span data-stu-id="b3423-118">URL access is particularly useful when integrating reports as part of a Web portal or when viewing reports from a Web browser.</span></span>  
  
 [<span data-ttu-id="b3423-119">Reporting Services 扩展插件</span><span class="sxs-lookup"><span data-stu-id="b3423-119">Reporting Services Extensions</span></span>](extensions/reporting-services-extensions.md)  
 <span data-ttu-id="b3423-120">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 的模块化体系结构旨在实现可扩展性。</span><span class="sxs-lookup"><span data-stu-id="b3423-120">The modular architecture of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] is designed for extensibility.</span></span> <span data-ttu-id="b3423-121">提供了一个托管代码 API，以便您能够轻松地开发、安装和管理由许多 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 组件使用的扩展插件。</span><span class="sxs-lookup"><span data-stu-id="b3423-121">A managed code API is available so that you can easily develop, install, and manage extensions consumed by many [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] components.</span></span> <span data-ttu-id="b3423-122">您可以使用创建程序集， [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 并添加新的 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 呈现、安全、传递和数据处理功能，以满足不断发展的业务需求。</span><span class="sxs-lookup"><span data-stu-id="b3423-122">You can create assemblies using the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] and add new [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] rendering, security, delivery, and data processing functionality to meet your evolving business needs.</span></span>  
  
 [<span data-ttu-id="b3423-123">自定义报表项</span><span class="sxs-lookup"><span data-stu-id="b3423-123">Custom Report Items</span></span>](custom-report-items/custom-report-items.md)  
 <span data-ttu-id="b3423-124">介绍如何创建自定义报表项，以便向 RDL 添加功能或扩展现有控件的功能。</span><span class="sxs-lookup"><span data-stu-id="b3423-124">Describes how to create Custom Report Items to add functionality to RDL or extend functionality of existing controls.</span></span>  
  
 [<span data-ttu-id="b3423-125">将自定义程序集用于报表</span><span class="sxs-lookup"><span data-stu-id="b3423-125">Using Custom Assemblies with Reports</span></span>](custom-assemblies/using-custom-assemblies-with-reports.md)  
 <span data-ttu-id="b3423-126">介绍如何通过在报表定义中加入代码引用，将自定义程序集用于报表。</span><span class="sxs-lookup"><span data-stu-id="b3423-126">Describes how to use custom assemblies with Reports by including code references within the report definition.</span></span>  
  
 [<span data-ttu-id="b3423-127">访问 Reporting Services WMI 提供程序</span><span class="sxs-lookup"><span data-stu-id="b3423-127">Access the Reporting Services WMI Provider</span></span>](tools/access-the-reporting-services-wmi-provider.md)  
 <span data-ttu-id="b3423-128">介绍如何使用 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] WMI 提供程序以管理报表服务器部署。</span><span class="sxs-lookup"><span data-stu-id="b3423-128">Describes how to use the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] WMI Provider to manage report server deployments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3423-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b3423-129">See Also</span></span>  
 <span data-ttu-id="b3423-130">[Reporting Services &#40;SSRS&#41;](create-deploy-and-manage-mobile-and-paginated-reports.md) </span><span class="sxs-lookup"><span data-stu-id="b3423-130">[Reporting Services &#40;SSRS&#41;](create-deploy-and-manage-mobile-and-paginated-reports.md) </span></span>  
 <span data-ttu-id="b3423-131">[&#40;SSRS&#41;的报表定义语言](reports/report-definition-language-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="b3423-131">[Report Definition Language &#40;SSRS&#41;](reports/report-definition-language-ssrs.md) </span></span>  
 <span data-ttu-id="b3423-132">[SSRS&#41;&#40;技术参考](technical-reference-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="b3423-132">[Technical Reference &#40;SSRS&#41;](technical-reference-ssrs.md) </span></span>  
 [<span data-ttu-id="b3423-133">安全开发 (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="b3423-133">Secure Development &#40;Reporting Services&#41;</span></span>](extensions/secure-development/secure-development-reporting-services.md)  
  
  
