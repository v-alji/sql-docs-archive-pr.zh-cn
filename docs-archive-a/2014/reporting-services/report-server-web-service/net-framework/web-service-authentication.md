---
title: Web 服务身份验证 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Web service [Reporting Services], authentication
- XML Web service [Reporting Services], authentication
- Report Server Web service, authentication
ms.assetid: 852b4947-a090-4e54-8555-5a503945ceab
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0c7836d6eba8c6ab3f0a8e705ebb79c7ed73eb17
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692680"
---
# <a name="web-service-authentication"></a><span data-ttu-id="09729-102">Web 服务身份验证</span><span class="sxs-lookup"><span data-stu-id="09729-102">Web Service Authentication</span></span>
  <span data-ttu-id="09729-103">可以使用 Windows 身份验证或基本身份验证对针对报表服务器 Web 服务进行的调用进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="09729-103">You can use either Windows Authentication or Basic authentication to authenticate the calls made to the Report Server Web service.</span></span> <span data-ttu-id="09729-104">对报表服务器发出 SOAP 请求的任何客户端都必须实现其中一种支持的身份验证协议的客户端部分。</span><span class="sxs-lookup"><span data-stu-id="09729-104">Any client that makes SOAP requests to the report server must implement the client portion of one of the supported authentication protocols.</span></span> <span data-ttu-id="09729-105">如果你使用的是 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] ，则可以使用托管代码 HTTP 类来实现身份验证。</span><span class="sxs-lookup"><span data-stu-id="09729-105">If you are using the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], you can use the managed code HTTP classes to implement authentication.</span></span> <span data-ttu-id="09729-106">通过使用这些 API，可以轻松地随 SOAP 请求一起发送身份验证信息。</span><span class="sxs-lookup"><span data-stu-id="09729-106">Using these APIs makes it easy to send authentication information along with the SOAP requests.</span></span>  
  
 <span data-ttu-id="09729-107">如果在对报表服务器 Web 服务进行调用之前不具备适当的凭据，则调用将失败。</span><span class="sxs-lookup"><span data-stu-id="09729-107">If you do not have appropriate credentials before you make a call to the Report Server Web service, the call fails.</span></span> <span data-ttu-id="09729-108">在运行时，可以通过在调用 Web 服务的方法之前设置表示该 Web 服务的客户端对象的“Credentials”\*\*\*\* 属性，向该 Web 服务传递凭据。</span><span class="sxs-lookup"><span data-stu-id="09729-108">At run time, you can pass credentials to the Web service by setting the **Credentials** property of the client-side object that represents the Web service before you call its methods.</span></span>  
  
 <span data-ttu-id="09729-109">以下各节包含使用 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 发送凭据的示例代码。</span><span class="sxs-lookup"><span data-stu-id="09729-109">The following sections contain example code that sends credentials using the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span>  
  
## <a name="windows-authentication"></a><span data-ttu-id="09729-110">Windows 身份验证</span><span class="sxs-lookup"><span data-stu-id="09729-110">Windows Authentication</span></span>  
 <span data-ttu-id="09729-111">以下代码将 Windows 凭据传递到 Web 服务。</span><span class="sxs-lookup"><span data-stu-id="09729-111">The following code passes Windows credentials to the Web service.</span></span>  
  
```vb  
Dim rs As New ReportingService()  
rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
```  
  
```csharp  
ReportingService rs = new ReportingService();  
rs.Credentials = System.Net.CredentialCache.DefaultCredentials;  
```  
  
## <a name="basic-authentication"></a><span data-ttu-id="09729-112">基本身份验证</span><span class="sxs-lookup"><span data-stu-id="09729-112">Basic Authentication</span></span>  
 <span data-ttu-id="09729-113">以下代码将基本身份验证凭据传递到 Web 服务。</span><span class="sxs-lookup"><span data-stu-id="09729-113">The following code passes Basic credentials to the Web service.</span></span>  
  
```vb  
Dim rs As New ReportingService()  
rs.Credentials = New System.Net.NetworkCredential("username", "password", "domain")  
```  
  
```csharp  
ReportingService service = new ReportingService();  
service.Credentials = new System.Net.NetworkCredential("username", "password", "domain");  
```  
  
 <span data-ttu-id="09729-114">必须在调用报表服务器 Web 服务的任何方法之前设置凭据。</span><span class="sxs-lookup"><span data-stu-id="09729-114">The credentials must be set before you call any of the methods of the Report Server Web service.</span></span> <span data-ttu-id="09729-115">如果您没有设置凭据，将收到错误代码“HTTP 401 错误: 拒绝访问”。</span><span class="sxs-lookup"><span data-stu-id="09729-115">If you do not set the credentials, you receive the error code an HTTP 401 Error: Access Denied.</span></span> <span data-ttu-id="09729-116">必须在使用服务之前对其进行身份验证，但在设置凭据之后，只要你继续使用同一个服务变量（如 rs\*\*），就不需要再次设置这些凭据。</span><span class="sxs-lookup"><span data-stu-id="09729-116">You must authenticate the service before you use it, but after you have set the credentials, you do not need to set them again as long as you continue to use the same service variable (such as *rs*).</span></span>  
  
## <a name="custom-authentication"></a><span data-ttu-id="09729-117">自定义身份验证</span><span class="sxs-lookup"><span data-stu-id="09729-117">Custom Authentication</span></span>  
 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="09729-118">包含一个编程 API，它向开发人员提供了设计和开发自定义身份验证扩展插件（称为安全扩展插件）的机会。</span><span class="sxs-lookup"><span data-stu-id="09729-118">includes a programming API that provides developers with the opportunity to design and develop custom authentication extensions, known as security extensions.</span></span> <span data-ttu-id="09729-119">有关详细信息，请参阅 [Implementing a Security Extension](../../extensions/security-extension/implementing-a-security-extension.md)。</span><span class="sxs-lookup"><span data-stu-id="09729-119">For more information, see [Implementing a Security Extension](../../extensions/security-extension/implementing-a-security-extension.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09729-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="09729-120">See Also</span></span>  
 <span data-ttu-id="09729-121">[使用 Web 服务和 .NET Framework 生成应用程序](building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="09729-121">[Building Applications Using the Web Service and the .NET Framework](building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 [<span data-ttu-id="09729-122">报表服务器 Web 服务</span><span class="sxs-lookup"><span data-stu-id="09729-122">Report Server Web Service</span></span>](../report-server-web-service.md)  
  
  
