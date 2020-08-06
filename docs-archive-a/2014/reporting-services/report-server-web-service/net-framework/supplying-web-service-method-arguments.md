---
title: 提供 Web 服务方法参数 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Report Server Web service, methods
- Web service [Reporting Services], methods
- methods [Reporting Services], arguments
- XML Web service [Reporting Services], methods
ms.assetid: f7b9ca05-fc4c-4b30-8e5d-172dd0f4a832
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3ef5188934628589751fe92d1839da0efb265766
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692683"
---
# <a name="supplying-web-service-method-arguments"></a><span data-ttu-id="952cf-102">提供 Web 服务方法参数</span><span class="sxs-lookup"><span data-stu-id="952cf-102">Supplying Web Service Method Arguments</span></span>
  <span data-ttu-id="952cf-103">报表服务器 Web 服务方法通过 HTTP 上的 SOAP 向位于指定 URL 处的服务发送请求。</span><span class="sxs-lookup"><span data-stu-id="952cf-103">A Report Server Web service method sends a request to the service at a given URL using SOAP over HTTP.</span></span> <span data-ttu-id="952cf-104">此服务接收请求，对其进行处理，然后返回响应。</span><span class="sxs-lookup"><span data-stu-id="952cf-104">The service receives the request, processes it, and then returns a response.</span></span> <span data-ttu-id="952cf-105">这些请求和响应采用 XML 文档形式。</span><span class="sxs-lookup"><span data-stu-id="952cf-105">These requests and responses are in the form of XML documents.</span></span>  
  
## <a name="optional-parameters"></a><span data-ttu-id="952cf-106">可选参数</span><span class="sxs-lookup"><span data-stu-id="952cf-106">Optional Parameters</span></span>  
 <span data-ttu-id="952cf-107">在某些情况下，Web 服务方法可能具有可选输入参数。</span><span class="sxs-lookup"><span data-stu-id="952cf-107">In some cases, a Web service method can have optional input parameters.</span></span> <span data-ttu-id="952cf-108">即使 Web 服务方法的某个输入参数是可选的，也仍必须包含它并将参数值设置为 `null`（在 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 中为 `Nothing`）。</span><span class="sxs-lookup"><span data-stu-id="952cf-108">Even if an input parameter for a Web service method is optional, you must still include it and set the parameter value to `null` (`Nothing` in [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]).</span></span> <span data-ttu-id="952cf-109">将参数值设置为 `null` 后，可将 SOAP 请求中该参数的元素值设置为 `null`。</span><span class="sxs-lookup"><span data-stu-id="952cf-109">Setting a parameter value to `null` sets the element value for that parameter in the SOAP request to `null`.</span></span>  
  
 <span data-ttu-id="952cf-110">以下示例使用 <xref:ReportService2010.ReportingService2010.CreateFolder%2A> 方法在 Sales 文件夹中创建名为 Product Sales 的新文件夹。</span><span class="sxs-lookup"><span data-stu-id="952cf-110">The following example uses the <xref:ReportService2010.ReportingService2010.CreateFolder%2A> method to create a new folder named Product Sales in the Sales folder.</span></span> <span data-ttu-id="952cf-111">通过为文件夹属性提供 `null` 值，将不会为该文件夹提供用户特定的属性：</span><span class="sxs-lookup"><span data-stu-id="952cf-111">By supplying a `null` value for the folder properties, no user-specific properties are supplied for the folder:</span></span>  
  
```  
// C#  
rs.CreateFolder("Product Sales", "/Sales", null);  
```  
  
## <a name="complex-data-types"></a><span data-ttu-id="952cf-112">复杂数据类型</span><span class="sxs-lookup"><span data-stu-id="952cf-112">Complex Data Types</span></span>  
 <span data-ttu-id="952cf-113">报表服务器 Web 服务的核心类为 <xref:ReportService2010.ReportingService2010>，您可以使用它调用 SOAP 操作或代理类的 Web 方法。</span><span class="sxs-lookup"><span data-stu-id="952cf-113">The core class of the Report Server Web service is <xref:ReportService2010.ReportingService2010>, which you use to invoke the SOAP operations or Web methods of the proxy class.</span></span> <span data-ttu-id="952cf-114">为了支持该类及其方法，[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 包含用户定义的、特定于 Web 服务方法的输入和输出参数的复杂数据类型。</span><span class="sxs-lookup"><span data-stu-id="952cf-114">To support this class and its methods, [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] includes user-defined, complex data types that are specific to the input and output parameters of the Web service methods.</span></span> <span data-ttu-id="952cf-115">这些复杂数据类型是所生成的代理类的一部分，可在环境中进行开发时使用 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="952cf-115">These complex data types are part of the generated proxy class, which you can use when developing in the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] environment.</span></span>  
  
 <span data-ttu-id="952cf-116">当您生成代理类时，在 WSDL 文件中定义的复杂数据类型将由该代理的各个类表示，这些类包含与复杂数据类型的各种 SOAP 元素相对应的属性。</span><span class="sxs-lookup"><span data-stu-id="952cf-116">When you generate a proxy class, the complex data types that are defined in the WSDL file are represented by the classes of the proxy, which include properties that correspond to the various SOAP elements of the complex data types.</span></span> <span data-ttu-id="952cf-117">这些数据类型的序列成为由您在代码中可以枚举的对象组成的数组。</span><span class="sxs-lookup"><span data-stu-id="952cf-117">Sequences of these data types become arrays of objects that you can enumerate through in your code.</span></span> <span data-ttu-id="952cf-118">这样，就不再需要直接使用在 SOAP 消息中发送的 XML 结构。</span><span class="sxs-lookup"><span data-stu-id="952cf-118">This eliminates the need to work directly with the XML structures sent in SOAP messages.</span></span> <span data-ttu-id="952cf-119">[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 将为您处理该转换。</span><span class="sxs-lookup"><span data-stu-id="952cf-119">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] handles that translation for you.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="952cf-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="952cf-120">See Also</span></span>  
 <span data-ttu-id="952cf-121">[使用 Web 服务和 .NET Framework 生成应用程序](building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="952cf-121">[Building Applications Using the Web Service and the .NET Framework](building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 <span data-ttu-id="952cf-122">[报表服务器 Web 服务](../report-server-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="952cf-122">[Report Server Web Service](../report-server-web-service.md) </span></span>  
 [<span data-ttu-id="952cf-123">技术参考 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="952cf-123">Technical Reference &#40;SSRS&#41;</span></span>](../../technical-reference-ssrs.md)  
  
  
