---
title: 在 Reporting Services 中处理异常 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- SOAP [Reporting Services], exceptions
- .NET Framework [Reporting Services]
- exceptions [Reporting Services], about exception handling
- SoapException object
ms.assetid: 1a443432-2db5-48c5-bc29-433b4688082f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1d887853b475f7b4d673d7b04343ae9bc71644d3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691075"
---
# <a name="handling-exceptions-in-reporting-services"></a><span data-ttu-id="3faca-102">在 Reporting Services 中处理异常</span><span class="sxs-lookup"><span data-stu-id="3faca-102">Handling Exceptions in Reporting Services</span></span>
  <span data-ttu-id="3faca-103">在无法完成某一 Reporting Services SOAP API 客户端请求时，报表服务器将返回错误，而非预期调用结果。</span><span class="sxs-lookup"><span data-stu-id="3faca-103">When a Reporting Services SOAP API client request cannot be completed, the report server returns an error rather than the expected results of the call.</span></span> <span data-ttu-id="3faca-104">在无法完成调用时，针对报表服务器 Web 服务的错误将以 SOAP Fault\*\*\*\* XML 元素的形式返回。</span><span class="sxs-lookup"><span data-stu-id="3faca-104">When a call cannot complete, an error for the Report Server Web service is returned as a SOAP **Fault** XML element.</span></span> <span data-ttu-id="3faca-105">该错误的主要描述性元素是 detail\*\*\*\* 元素，它包括报表服务器提供的所有错误消息以及所有附加的 Web 服务错误信息。</span><span class="sxs-lookup"><span data-stu-id="3faca-105">The key descriptive element of the fault is the **detail** element, which includes all of the error information provided by the report server as well as any additional Web service error information.</span></span> <span data-ttu-id="3faca-106">detail\*\*\*\* 元素中的关键信息是报表服务器错误代码。</span><span class="sxs-lookup"><span data-stu-id="3faca-106">The key information in the **detail** element is the report server error code.</span></span> <span data-ttu-id="3faca-107">基于这些消息和错误代码，您可以确定要在应用程序中执行的相应后续操作。</span><span class="sxs-lookup"><span data-stu-id="3faca-107">Based on the message and error code, you can determine the next appropriate action to take in your applications.</span></span> <span data-ttu-id="3faca-108">有关 SOAP 错误的详细信息，请参阅万维网联合会 (W3C) 网站，网址为 http://www.w3.org/TR/SOAP。</span><span class="sxs-lookup"><span data-stu-id="3faca-108">For more information about SOAP faults, see the World Wide Web Consortium (W3C) Web site at http://www.w3.org/TR/SOAP.</span></span>  
  
## <a name="soap-faults-and-the-net-framework"></a><span data-ttu-id="3faca-109">SOAP 错误和 .NET Framework</span><span class="sxs-lookup"><span data-stu-id="3faca-109">SOAP Faults and the .NET Framework</span></span>  
 <span data-ttu-id="3faca-110">在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 中，如果在对 Web 服务的客户端请求中出现错误，则报表服务器将通过引发 SoapException\*\*\*\* 对象向调用 Web 服务的客户端代码传达此错误。</span><span class="sxs-lookup"><span data-stu-id="3faca-110">In the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], if an error occurs in a client request to the Web service, the report server communicates the error to the client code that calls the Web service by throwing a **SoapException** object.</span></span> <span data-ttu-id="3faca-111">SoapException\*\*\*\* 包装 SOAP 错误中包含的信息。</span><span class="sxs-lookup"><span data-stu-id="3faca-111">The **SoapException** wraps the information contained in a SOAP fault.</span></span> <span data-ttu-id="3faca-112">SoapException\*\*\*\* 的 Detail\*\*\*\* 属性映射到 SOAP 错误中的 detail\*\*\*\* 元素。</span><span class="sxs-lookup"><span data-stu-id="3faca-112">The **Detail** property of the **SoapException** maps to the **detail** element in the SOAP fault.</span></span> <span data-ttu-id="3faca-113">应用程序应使用 try/catch 块捕获 SoapException\*\*\*\* 对象，并且使用 SoapException\*\*\*\* 的 Detail\*\*\*\* 属性执行适当操作。</span><span class="sxs-lookup"><span data-stu-id="3faca-113">Applications should catch the **SoapException** object with a try/catch block and use the **Detail** property of the **SoapException** to take appropriate action.</span></span> <span data-ttu-id="3faca-114">有关 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 中的 SoapException\*\*\*\* 类和 Detail\*\*\*\* 属性的详细信息，请参阅 [Reporting Services SoapException 类](soapexception-class/reporting-services-soapexception-class.md)。</span><span class="sxs-lookup"><span data-stu-id="3faca-114">For more information about the **SoapException** class and the **Detail** property in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], see [Reporting Services SoapException Class](soapexception-class/reporting-services-soapexception-class.md).</span></span> <span data-ttu-id="3faca-115">有关 SoapException\*\*\*\* 类的详细信息，请参阅 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK 文档。</span><span class="sxs-lookup"><span data-stu-id="3faca-115">For more information about the **SoapException** class, see the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3faca-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3faca-116">See Also</span></span>  
 <span data-ttu-id="3faca-117">[Detail 属性](soapexception-class/detail-property.md) </span><span class="sxs-lookup"><span data-stu-id="3faca-117">[Detail Property](soapexception-class/detail-property.md) </span></span>  
 <span data-ttu-id="3faca-118">[介绍 Reporting Services 中的异常处理](introducing-exception-handling-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="3faca-118">[Introducing Exception Handling in Reporting Services](introducing-exception-handling-in-reporting-services.md) </span></span>  
 [<span data-ttu-id="3faca-119">Reporting Services SoapException 类</span><span class="sxs-lookup"><span data-stu-id="3faca-119">Reporting Services SoapException Class</span></span>](soapexception-class/reporting-services-soapexception-class.md)  
  
  
