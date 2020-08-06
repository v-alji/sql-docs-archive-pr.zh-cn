---
title: 介绍 Reporting Services 中的异常处理 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Web service [Reporting Services], exception handling
- errors [Reporting Services]
- exceptions [Reporting Services]
- Report Server Web service, exception handling
- XML Web service [Reporting Services], exception handling
ms.assetid: 54381870-ce67-482b-aa83-6a838cdbf9b9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 091b1f40d293515617e369b750a5f18dfe12951b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689284"
---
# <a name="introducing-exception-handling-in-reporting-services"></a><span data-ttu-id="63b08-102">介绍 Reporting Services 中的异常处理</span><span class="sxs-lookup"><span data-stu-id="63b08-102">Introducing Exception Handling in Reporting Services</span></span>
  <span data-ttu-id="63b08-103">如果您的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 应用程序将某一请求发送到报表服务器 Web 服务但该服务无法处理该请求，则该服务会将一个 SOAP 异常返回到客户端。</span><span class="sxs-lookup"><span data-stu-id="63b08-103">If your [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] application sends a request to the Report Server Web service that the service is unable to process, the service returns a SOAP exception to the client.</span></span> <span data-ttu-id="63b08-104">处理报表服务器 Web 服务引发的异常是您开发的应用程序的重要一环，因为可以在错误发生时将有用信息返回给用户。</span><span class="sxs-lookup"><span data-stu-id="63b08-104">Handling exceptions thrown by the Report Server Web service is an important part of the applications that you develop because you can return useful information to users when errors occur.</span></span>  
  
 <span data-ttu-id="63b08-105">本节包含有关处理异常、防止无效用户输入和向用户返回有意义的错误信息的具体信息。</span><span class="sxs-lookup"><span data-stu-id="63b08-105">This section contains specific information about handling exceptions, preventing user input that is not valid, and returning meaningful error information to users.</span></span> <span data-ttu-id="63b08-106">有关异常处理的常规信息，请参阅 SDK 文档中的 "处理和引发异常" [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="63b08-106">For general information about exception handling, see "Handling and Throwing Exceptions" in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK documentation.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="63b08-107">本节内容</span><span class="sxs-lookup"><span data-stu-id="63b08-107">In This Section</span></span>  
  
|<span data-ttu-id="63b08-108">主题</span><span class="sxs-lookup"><span data-stu-id="63b08-108">Topic</span></span>|<span data-ttu-id="63b08-109">说明</span><span class="sxs-lookup"><span data-stu-id="63b08-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="63b08-110">在 Reporting Services 中处理异常</span><span class="sxs-lookup"><span data-stu-id="63b08-110">Handling Exceptions in Reporting Services</span></span>](handling-exceptions-in-reporting-services.md)|<span data-ttu-id="63b08-111">概述 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 中的异常以及 SOAP 在从 Web 服务返回错误时的角色。</span><span class="sxs-lookup"><span data-stu-id="63b08-111">Provides an overview of exceptions in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] and the role of SOAP in returning errors from a Web service.</span></span>|  
|[<span data-ttu-id="63b08-112">Reporting Services 异常处理的最佳实践</span><span class="sxs-lookup"><span data-stu-id="63b08-112">Best Practices for Reporting Services Exception Handling</span></span>](best-practices/best-practices-for-reporting-services-exception-handling.md)|<span data-ttu-id="63b08-113">就如何在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 中处理异常提供建议。</span><span class="sxs-lookup"><span data-stu-id="63b08-113">Provides recommendations on how to handle exceptions in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="63b08-114">Reporting Services SoapException 类</span><span class="sxs-lookup"><span data-stu-id="63b08-114">Reporting Services SoapException Class</span></span>](soapexception-class/reporting-services-soapexception-class.md)|<span data-ttu-id="63b08-115">介绍 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 中的 SoapException 类\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="63b08-115">Describes the **SoapException** class in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="63b08-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="63b08-116">See Also</span></span>  
 [<span data-ttu-id="63b08-117">使用 Web 服务和 .NET Framework 生成应用程序</span><span class="sxs-lookup"><span data-stu-id="63b08-117">Building Applications Using the Web Service and the .NET Framework</span></span>](../report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)  
  
  
