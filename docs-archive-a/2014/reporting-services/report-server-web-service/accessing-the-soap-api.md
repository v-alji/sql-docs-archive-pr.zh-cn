---
title: 访问 SOAP API | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- XML Web service [Reporting Services], WSDL
- Web service [Reporting Services], SOAP
- calling Web service
- SOAP [Reporting Services], accessing
- Report Server Web service, SOAP
- Web service [Reporting Services], WSDL
- WSDL [Reporting Services]
- XML Web service [Reporting Services], SOAP
- Report Server Web service, WSDL
- referencing WSDL
ms.assetid: 63bb870a-4dbf-46bd-8921-78f8ebe5fd75
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6e8a0c21bb53deff746cfd916b6ae2c96fa0de19
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590032"
---
# <a name="accessing-the-soap-api"></a><span data-ttu-id="f1025-102">访问 SOAP API</span><span class="sxs-lookup"><span data-stu-id="f1025-102">Accessing the SOAP API</span></span>
  <span data-ttu-id="f1025-103">报表服务器 Web 服务使用通过 HTTP 的简单对象访问协议 (SOAP)，并充当客户端程序和报表服务器之间的通信接口。</span><span class="sxs-lookup"><span data-stu-id="f1025-103">The Report Server Web service uses Simple Object Access Protocol (SOAP) over HTTP and acts as a communications interface between client programs and the report server.</span></span> <span data-ttu-id="f1025-104">该 Web 服务提供两个端点（一个用于报表执行，一个用于报表管理），并且由您可用于访问 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 的完整功能的方法和一组复杂类型对象构成。</span><span class="sxs-lookup"><span data-stu-id="f1025-104">The Web service provides two endpoints - one for report execution and one for report management - and consists of methods and a set of complex type objects that you can use to access the complete functionality of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="f1025-105">若要调用该服务，必须引用 Reporting Services Web 服务描述语言 (WSDL)。</span><span class="sxs-lookup"><span data-stu-id="f1025-105">To call the service, you must reference the Reporting Services Web Services Description Language (WSDL).</span></span>  
  
## <a name="referencing-the-reporting-services-wsdl"></a><span data-ttu-id="f1025-106">引用 Reporting Services WSDL</span><span class="sxs-lookup"><span data-stu-id="f1025-106">Referencing the Reporting Services WSDL</span></span>  
 <span data-ttu-id="f1025-107">若要成功调用某一 Web 服务，您必须知道如何访问该服务、该服务支持的操作、该服务预期的参数以及该服务返回的内容。</span><span class="sxs-lookup"><span data-stu-id="f1025-107">To call a Web service successfully, you must know how to access the service, what operations the service supports, what parameters the service expects, and what the service returns.</span></span> <span data-ttu-id="f1025-108">WSDL 在可由计算机读取或处理的 XML 文档中提供这些信息。</span><span class="sxs-lookup"><span data-stu-id="f1025-108">WSDL provides this information in an XML document that can be read or processed by a computer.</span></span>  
  
 <span data-ttu-id="f1025-109">该报表服务器 Web 服务在三个不同的端点中公开。</span><span class="sxs-lookup"><span data-stu-id="f1025-109">The Report Server Web services are exposed in three different endpoints.</span></span> <span data-ttu-id="f1025-110">该 WSDL 文件的名称对于每个端点并不相同。</span><span class="sxs-lookup"><span data-stu-id="f1025-110">The name of the WSDL file is different for each endpoint.</span></span> <span data-ttu-id="f1025-111"><xref:ReportService2010> 端点包含一些方法，用于管理本机模式或 SharePoint 集成模式下报表服务器中的对象。</span><span class="sxs-lookup"><span data-stu-id="f1025-111">The <xref:ReportService2010> endpoint contains methods for managing objects in a Report Server in either native or SharePoint integrated mode.</span></span> <span data-ttu-id="f1025-112">用于此端点的 WSDL 通过 `ReportService2010.asmx?wsdl.` 访问。</span><span class="sxs-lookup"><span data-stu-id="f1025-112">The WSDL for this endpoint is accessed through `ReportService2010.asmx?wsdl.`</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f1025-113">在 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 中不推荐使用 <xref:ReportService2005> 和 <xref:ReportService2006> 端点。</span><span class="sxs-lookup"><span data-stu-id="f1025-113">The <xref:ReportService2005> and <xref:ReportService2006> endpoints are deprecated in [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].</span></span> <span data-ttu-id="f1025-114"><xref:ReportService2010> 端点包含两个端点的功能和其他管理功能。</span><span class="sxs-lookup"><span data-stu-id="f1025-114">The <xref:ReportService2010> endpoint includes the functionalities of both endpoints and contains additional management features.</span></span>  
  
-   <span data-ttu-id="f1025-115"><xref:ReportExecution2005> 端点允许开发人员以编程方式在报表服务器中处理和呈现报表。</span><span class="sxs-lookup"><span data-stu-id="f1025-115">The <xref:ReportExecution2005> endpoint allows developers to programmatically process and render reports in a Report Server.</span></span> <span data-ttu-id="f1025-116">用于此端点的 WSDL 通过 `ReportExecution2005.asmx?wsdl` 访问。</span><span class="sxs-lookup"><span data-stu-id="f1025-116">The WSDL for this endpoint is accessed through `ReportExecution2005.asmx?wsdl`.</span></span>  
  
 <span data-ttu-id="f1025-117">WSDL 可由支持 SOAP 和 Web 服务的开发工具包（如 SDK）使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="f1025-117">WSDL can be consumed by development kits that support SOAP and Web services, such as the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK.</span></span>  
  
 <span data-ttu-id="f1025-118">以下示例显示指向 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 管理 WSDL 文件的 URL 的格式：</span><span class="sxs-lookup"><span data-stu-id="f1025-118">The following example shows the format of the URL to the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] management WSDL file:</span></span>  
  
```  
http://server/reportserver/ReportService2010.asmx?wsdl  
```  
  
 <span data-ttu-id="f1025-119">下表介绍 URL 中的各元素。</span><span class="sxs-lookup"><span data-stu-id="f1025-119">The following table describes each element in the URL.</span></span>  
  
|<span data-ttu-id="f1025-120">URL 元素</span><span class="sxs-lookup"><span data-stu-id="f1025-120">URL element</span></span>|<span data-ttu-id="f1025-121">说明</span><span class="sxs-lookup"><span data-stu-id="f1025-121">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="f1025-122">服务器</span><span class="sxs-lookup"><span data-stu-id="f1025-122">*server*</span></span>|<span data-ttu-id="f1025-123">报表服务器部署到的服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="f1025-123">The name of the server on which the report server is deployed.</span></span>|  
|<span data-ttu-id="f1025-124">*reportserver*</span><span class="sxs-lookup"><span data-stu-id="f1025-124">*reportserver*</span></span>|<span data-ttu-id="f1025-125">包含 XML Web 服务的文件夹的名称。</span><span class="sxs-lookup"><span data-stu-id="f1025-125">The name of the folder that contains the XML Web service.</span></span> <span data-ttu-id="f1025-126">此名称在设置期间配置。</span><span class="sxs-lookup"><span data-stu-id="f1025-126">This is configured during setup.</span></span>|  
|<span data-ttu-id="f1025-127">*\<endpoint name>.asmx*</span><span class="sxs-lookup"><span data-stu-id="f1025-127">*\<endpoint name>.asmx*</span></span>|<span data-ttu-id="f1025-128">Web 服务端点的名称。</span><span class="sxs-lookup"><span data-stu-id="f1025-128">The name of the web service endpoint.</span></span>|  
  
 <span data-ttu-id="f1025-129">有关 WSDL 格式的详细信息，请参阅万维网联合会 (W3C) WSDL 规范，网址为 http://www.w3.org/TR/wsdl。</span><span class="sxs-lookup"><span data-stu-id="f1025-129">For more information about the WSDL format, see the World Wide Web Consortium (W3C) WSDL specification at http://www.w3.org/TR/wsdl.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1025-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f1025-130">See Also</span></span>  
 <span data-ttu-id="f1025-131">[使用 Web 服务和 .NET Framework 生成应用程序](net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="f1025-131">[Building Applications Using the Web Service and the .NET Framework](net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 [<span data-ttu-id="f1025-132">报表服务器 Web 服务</span><span class="sxs-lookup"><span data-stu-id="f1025-132">Report Server Web Service</span></span>](report-server-web-service.md)  
  
  
