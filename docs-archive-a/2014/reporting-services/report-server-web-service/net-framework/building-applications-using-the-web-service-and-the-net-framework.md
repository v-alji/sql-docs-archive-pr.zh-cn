---
title: 使用 Web 服务和 .NET Framework 生成应用程序 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Report Server Web service, application building
- .NET Framework [Reporting Services]
- XML Web service [Reporting Services], client creation
- reports [Reporting Services], building
- Web service [Reporting Services], application building
- Report Server Web service, client creation
- client configuration [Reporting Services]
- XML Web service [Reporting Services], application building
- Web service [Reporting Services], client creation
ms.assetid: 92a9678c-bc4f-4d7a-ba44-85989bfe27ca
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5f14a0f2d231d54d12129852b6226c02afd211d4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688543"
---
# <a name="building-applications-using-the-web-service-and-the-net-framework"></a><span data-ttu-id="62537-102">Building Applications Using the Web Service and the .NET Framework</span><span class="sxs-lookup"><span data-stu-id="62537-102">Building Applications Using the Web Service and the .NET Framework</span></span>
  <span data-ttu-id="62537-103">利用 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] ，你可以使用熟悉的编程构造（如方法、基元类型和用户定义的复杂类型）来处理 Web 服务。</span><span class="sxs-lookup"><span data-stu-id="62537-103">With the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], you can use familiar programming constructs, such as methods, primitive types, and user-defined complex types to work with Web services.</span></span> <span data-ttu-id="62537-104">[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 包含可用来创建 Web 服务客户端的基础结构和工具，这些客户端可以调用任何符合万维网联盟 (W3C) 标准的 Web 服务。</span><span class="sxs-lookup"><span data-stu-id="62537-104">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] contains an infrastructure and tools you can use to create Web service clients that can call any World Wide Web Consortium (W3C) standards-compliant Web service.</span></span>  
  
 <span data-ttu-id="62537-105">报表服务器 Web 服务客户端是使用简单对象访问协议 (SOAP) 消息与报表服务器通信的任何组件或应用程序。</span><span class="sxs-lookup"><span data-stu-id="62537-105">A Report Server Web service client is any component or application that communicates with a report server using Simple Object Access Protocol (SOAP) messages.</span></span>  
  
 <span data-ttu-id="62537-106">要使用 .NET Framework 创建报表服务器 Web 服务，请按照以下基本步骤进行操作\*\*\*\*：</span><span class="sxs-lookup"><span data-stu-id="62537-106">**To create a Report Server Web service client using the .NET Framework, follow these basic steps:**</span></span>  
  
1.  <span data-ttu-id="62537-107">创建 Web 服务的代理类。</span><span class="sxs-lookup"><span data-stu-id="62537-107">Create a proxy class for the Web service.</span></span>  
  
     <span data-ttu-id="62537-108">为此，将代理类或 Web 引用添加到开发项目中，在客户端代码中引用代理类，并创建该代理的实例。</span><span class="sxs-lookup"><span data-stu-id="62537-108">To do this, add a proxy class or Web reference to your development project, reference the proxy class in your client code, and create an instance of that proxy.</span></span> <span data-ttu-id="62537-109">有关详细信息，请参阅[创建 Web 服务代理](creating-the-web-service-proxy.md)。</span><span class="sxs-lookup"><span data-stu-id="62537-109">For more information, see [Creating the Web Service Proxy](creating-the-web-service-proxy.md).</span></span>  
  
2.  <span data-ttu-id="62537-110">针对报表服务器对 Web 服务客户端进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="62537-110">Authenticate the Web service client with the report server.</span></span>  
  
     <span data-ttu-id="62537-111">为此，将服务对象的 <xref:System.Web.Services.Protocols.WebClientProtocol.Credentials%2A> 属性设置为与报表服务器上经过身份验证的用户的凭据相同。</span><span class="sxs-lookup"><span data-stu-id="62537-111">To do this, set the service object's <xref:System.Web.Services.Protocols.WebClientProtocol.Credentials%2A> property equal to the credentials of an authenticated user on the report server.</span></span> <span data-ttu-id="62537-112">有关详细信息，请参阅 [Web 服务身份验证](web-service-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="62537-112">For more information, see [Web Service Authentication](web-service-authentication.md).</span></span>  
  
3.  <span data-ttu-id="62537-113">调用与您要调用的 Web 服务操作相对应的代理类的方法。</span><span class="sxs-lookup"><span data-stu-id="62537-113">Call the method of the proxy class corresponding to the Web service operation that you want to invoke.</span></span>  
  
     <span data-ttu-id="62537-114">为此，调用 Web 服务方法并提供必需的参数。</span><span class="sxs-lookup"><span data-stu-id="62537-114">To do this, call a Web service method and supply the necessary arguments.</span></span> <span data-ttu-id="62537-115">有关 Web 服务方法的详细信息，请参阅[报表服务器 Web 服务方法](../methods/report-server-web-service-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="62537-115">For more information about the Web service methods, see [Report Server Web Service Methods](../methods/report-server-web-service-methods.md).</span></span> <span data-ttu-id="62537-116">有关调用的详细信息，请参阅[调用 Web 服务方法](calling-web-service-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="62537-116">For more information about calling, see [Calling Web Service Methods](calling-web-service-methods.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="62537-117">本节内容</span><span class="sxs-lookup"><span data-stu-id="62537-117">In This Section</span></span>  
  
|<span data-ttu-id="62537-118">主题</span><span class="sxs-lookup"><span data-stu-id="62537-118">Topic</span></span>|<span data-ttu-id="62537-119">说明</span><span class="sxs-lookup"><span data-stu-id="62537-119">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="62537-120">创建 Web 服务代理</span><span class="sxs-lookup"><span data-stu-id="62537-120">Creating the Web Service Proxy</span></span>](creating-the-web-service-proxy.md)|<span data-ttu-id="62537-121">介绍使用将代理类添加到项目的方法 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="62537-121">Describes the ways to add a proxy class to your project using [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span>|  
|[<span data-ttu-id="62537-122">Web 服务身份验证</span><span class="sxs-lookup"><span data-stu-id="62537-122">Web Service Authentication</span></span>](web-service-authentication.md)|<span data-ttu-id="62537-123">介绍如何对针对报表服务器 Web 服务的调用进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="62537-123">Describes how calls to the Report Server Web service are authenticated.</span></span>|  
|[<span data-ttu-id="62537-124">调用 Web 服务方法</span><span class="sxs-lookup"><span data-stu-id="62537-124">Calling Web Service Methods</span></span>](calling-web-service-methods.md)|<span data-ttu-id="62537-125">介绍如何在中使用 SOAP API 调用 Web 服务方法 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="62537-125">Describes how to use the SOAP API to call Web service methods in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span></span>|  
|[<span data-ttu-id="62537-126">设置 Web 服务的 Url 属性</span><span class="sxs-lookup"><span data-stu-id="62537-126">Setting the Url Property of the Web Service</span></span>](setting-the-url-property-of-the-web-service.md)|<span data-ttu-id="62537-127">说明在创建 Web 引用之后，如何以编程方式将 Web 服务代理定向到新的服务器 URL。</span><span class="sxs-lookup"><span data-stu-id="62537-127">Explains how to programmatically direct your Web service proxy to a new server URL after you have created your Web reference.</span></span>|  
|[<span data-ttu-id="62537-128">提供 Web 服务方法参数</span><span class="sxs-lookup"><span data-stu-id="62537-128">Supplying Web Service Method Arguments</span></span>](supplying-web-service-method-arguments.md)|<span data-ttu-id="62537-129">介绍如何调用 Web 服务方法并提供方法参数。</span><span class="sxs-lookup"><span data-stu-id="62537-129">Describes how to invoke a Web service method and supply method arguments.</span></span>|  
|[<span data-ttu-id="62537-130">省略可选 Web 服务对象的值</span><span class="sxs-lookup"><span data-stu-id="62537-130">Omitting Values for Optional Web Service Objects</span></span>](omitting-values-for-optional-web-service-objects.md)|<span data-ttu-id="62537-131">介绍如何忽略可选 Web 服务对象的值。</span><span class="sxs-lookup"><span data-stu-id="62537-131">Describes how to omit values for optional Web service objects.</span></span>|  
|[<span data-ttu-id="62537-132">使用安全 Web 服务方法</span><span class="sxs-lookup"><span data-stu-id="62537-132">Using Secure Web Service Methods</span></span>](using-secure-web-service-methods.md)|<span data-ttu-id="62537-133">介绍 SecureConnectionLevel 设置以及它影响 Reporting Services SOAP API 使用的方式\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="62537-133">Describes the **SecureConnectionLevel** setting and the way in which it affects the use of the Reporting Services SOAP API.</span></span>|  
|[<span data-ttu-id="62537-134">将设备信息设置传递给呈现扩展插件</span><span class="sxs-lookup"><span data-stu-id="62537-134">Passing Device Information Settings to Rendering Extensions</span></span>](passing-device-information-settings-to-rendering-extensions.md)|<span data-ttu-id="62537-135">介绍用于将报表呈现为不同格式的设备信息设置。</span><span class="sxs-lookup"><span data-stu-id="62537-135">Describes the device information settings that are used to render reports to different formats.</span></span>|  
|[<span data-ttu-id="62537-136">Reporting Services 传递扩展插件设置</span><span class="sxs-lookup"><span data-stu-id="62537-136">Reporting Services Delivery Extension Settings</span></span>](reporting-services-delivery-extension-settings.md)|<span data-ttu-id="62537-137">介绍用于通过报表服务器电子邮件传递报表的设置。</span><span class="sxs-lookup"><span data-stu-id="62537-137">Describes the settings that are used to deliver reports using report server e-mail.</span></span>|  
|[<span data-ttu-id="62537-138">使用 Reporting Services SOAP 标头</span><span class="sxs-lookup"><span data-stu-id="62537-138">Using Reporting Services SOAP Headers</span></span>](../../report-server-web-service-net-framework-soap-headers/using-reporting-services-soap-headers.md)|<span data-ttu-id="62537-139">说明如何在 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中使用 SOAP 标头。</span><span class="sxs-lookup"><span data-stu-id="62537-139">Explains the use of SOAP headers in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="62537-140">介绍 Reporting Services 中的异常处理</span><span class="sxs-lookup"><span data-stu-id="62537-140">Introducing Exception Handling in Reporting Services</span></span>](../../report-server-web-service-net-framework-exception-handling/introducing-exception-handling-in-reporting-services.md)|<span data-ttu-id="62537-141">提供有关 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 处理错误时所用方法的信息。</span><span class="sxs-lookup"><span data-stu-id="62537-141">Provides information about the way in which [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] handles errors.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="62537-142">另请参阅</span><span class="sxs-lookup"><span data-stu-id="62537-142">See Also</span></span>  
 <span data-ttu-id="62537-143">[报表服务器 Web 服务](../report-server-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="62537-143">[Report Server Web Service](../report-server-web-service.md) </span></span>  
 [<span data-ttu-id="62537-144">技术参考 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="62537-144">Technical Reference &#40;SSRS&#41;</span></span>](../../technical-reference-ssrs.md)  
  
  
