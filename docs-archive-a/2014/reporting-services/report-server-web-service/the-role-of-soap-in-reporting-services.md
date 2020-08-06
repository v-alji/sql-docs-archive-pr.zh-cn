---
title: SOAP 在 Reporting Services 中的作用 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Web service [Reporting Services], SOAP
- SOAP [Reporting Services], role in Reporting Services
- Report Server Web service, SOAP
- XML Web service [Reporting Services], SOAP
ms.assetid: f229c3ef-f2ca-448f-98f1-b8df350b9992
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 05445eb1c95c5761595944867b6d0c20a6f1a412
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689782"
---
# <a name="the-role-of-soap-in-reporting-services"></a><span data-ttu-id="f40ed-102">The Role of SOAP in Reporting Services</span><span class="sxs-lookup"><span data-stu-id="f40ed-102">The Role of SOAP in Reporting Services</span></span>
  <span data-ttu-id="f40ed-103">报表服务器 Web 服务使用简单对象访问协议 (SOAP) 消息通过网络发送基于文本的命令。</span><span class="sxs-lookup"><span data-stu-id="f40ed-103">The Report Server Web service uses Simple Object Access Protocol (SOAP) messaging to send text-based commands over a network.</span></span> <span data-ttu-id="f40ed-104">这些命令采用的形式为使用 HTTP 通过万维网发送的 XML 文本。</span><span class="sxs-lookup"><span data-stu-id="f40ed-104">These commands take the form of XML text that is sent over the World Wide Web using HTTP.</span></span> <span data-ttu-id="f40ed-105">通过将 SOAP 用作其通信协议，报表服务器 Web 服务使应用程序和组件能够使用开放和广为接受的基础结构与报表服务器交换数据。</span><span class="sxs-lookup"><span data-stu-id="f40ed-105">By using SOAP as its communication protocol, the Report Server Web service allows applications and components to exchange data with the report server using an open and widely accepted infrastructure.</span></span> <span data-ttu-id="f40ed-106">SOAP 标准在 www.w3.org/TR/SOAP 中定义。</span><span class="sxs-lookup"><span data-stu-id="f40ed-106">The SOAP standard is defined at www.w3.org/TR/SOAP.</span></span>  
  
 <span data-ttu-id="f40ed-107">对于任何客户端应用程序，只要它识别 SOAP 且可以发送 SOAP 请求，它就可以充当 SOAP 客户端。</span><span class="sxs-lookup"><span data-stu-id="f40ed-107">Any client application can act as a SOAP client as long as it is SOAP-aware and can send SOAP requests.</span></span> <span data-ttu-id="f40ed-108">报表管理器就是一个此类 SOAP 客户端。</span><span class="sxs-lookup"><span data-stu-id="f40ed-108">Report Manager is one such SOAP client.</span></span> <span data-ttu-id="f40ed-109">它向报表服务器数据库（其中存储所有报表和与报表相关的内容）提供了一个接口。</span><span class="sxs-lookup"><span data-stu-id="f40ed-109">It provides an interface to the report server database in which all reports and report-related content is stored.</span></span> <span data-ttu-id="f40ed-110">每个用户都可以使用此应用程序对报表服务器命名空间中的报表和文件夹进行浏览和管理。</span><span class="sxs-lookup"><span data-stu-id="f40ed-110">End users can use the application to browse through and manage reports and folders in the report server namespace.</span></span> <span data-ttu-id="f40ed-111">报表管理器建立在报表服务器 Web 服务基础结构之上。</span><span class="sxs-lookup"><span data-stu-id="f40ed-111">Report Manager is built on the Report Server Web service infrastructure.</span></span>  
  
 <span data-ttu-id="f40ed-112">报表服务器充当 SOAP 服务器，它是一项识别 SOAP 的服务，可以从 SOAP 客户端接受请求并创建适当的响应。</span><span class="sxs-lookup"><span data-stu-id="f40ed-112">A report server acts as a SOAP server, a SOAP-aware service that can accept requests from SOAP clients and create appropriate responses.</span></span> <span data-ttu-id="f40ed-113">此服务器处理请求并将经过编码的响应发回到客户端。</span><span class="sxs-lookup"><span data-stu-id="f40ed-113">The server handles the requests and sends encoded responses back to the client.</span></span>  
  
 <span data-ttu-id="f40ed-114">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 中的 SOAP 消息采取许多不同的形式，具体取决于客户端发出的请求类型。</span><span class="sxs-lookup"><span data-stu-id="f40ed-114">SOAP messages in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] take many different forms, depending on the type of request made by the client.</span></span> <span data-ttu-id="f40ed-115">以下示例表示一个简单 SOAP 客户端请求，它请求从报表服务器数据库中删除某个项。</span><span class="sxs-lookup"><span data-stu-id="f40ed-115">The following example represents a simple SOAP client request to remove an item from the report server database.</span></span>  
  
```  
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
    <soap:Body>  
        <DeleteItem xmlns="https://www.microsoft.com/sql/ReportingServer">  
            <item>/Samples/Report1</item>  
        </DeleteItem>  
    </soap:Body>  
</soap:Envelope>  
```  
  
 <span data-ttu-id="f40ed-116">SOAP 自身要求将消息放到 `Envelope` 元素中，并且将消息的主体放入 `Body` 元素内。</span><span class="sxs-lookup"><span data-stu-id="f40ed-116">The SOAP itself requires that messages be put into an `Envelope` element, with the bulk of the message inside a `Body` element.</span></span> <span data-ttu-id="f40ed-117">在本示例中，主体包含对于 <xref:ReportService2010.ReportingService2010.DeleteItem%2A> 方法的调用，该方法采用一个表示待删除项的路径的字符串参数。</span><span class="sxs-lookup"><span data-stu-id="f40ed-117">In this example, the body contains a call to the <xref:ReportService2010.ReportingService2010.DeleteItem%2A> method, which takes a string parameter representing the path of the item to delete.</span></span> <span data-ttu-id="f40ed-118">您可以创建一个 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 客户端代理类，该类将所有 SOAP 操作封装到方法中。</span><span class="sxs-lookup"><span data-stu-id="f40ed-118">You can create a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] client proxy class that encapsulates all SOAP operations into methods.</span></span> <span data-ttu-id="f40ed-119">以下 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)] 方法表示前面给出的 SOAP 示例。</span><span class="sxs-lookup"><span data-stu-id="f40ed-119">The following [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)] method represents the SOAP example given earlier.</span></span>  
  
```  
public void DeleteItem(string item);  
```  
  
 <span data-ttu-id="f40ed-120">来自服务器的响应可能如下所示：</span><span class="sxs-lookup"><span data-stu-id="f40ed-120">The response from the server might look like the following:</span></span>  
  
```  
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
    <soap:Body>  
        <DeleteItemResponse xmlns="https://www.microsoft.com/sql/ReportingServer" />  
    </soap:Body>  
</soap:Envelope>  
```  
  
 <span data-ttu-id="f40ed-121"><xref:ReportService2010.ReportingService2010.DeleteItem%2A> 方法不具备返回值，因此返回空响应。</span><span class="sxs-lookup"><span data-stu-id="f40ed-121">The <xref:ReportService2010.ReportingService2010.DeleteItem%2A> method has no return value, so an empty response is returned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f40ed-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f40ed-122">See Also</span></span>  
 <span data-ttu-id="f40ed-123">[访问 SOAP API](accessing-the-soap-api.md) </span><span class="sxs-lookup"><span data-stu-id="f40ed-123">[Accessing the SOAP API](accessing-the-soap-api.md) </span></span>  
 <span data-ttu-id="f40ed-124">[报表管理器（SSRS 本机模式）](../report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="f40ed-124">[Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="f40ed-125">[Reporting Services 报表服务器](../reporting-services-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="f40ed-125">[Reporting Services Report Server](../reporting-services-report-server.md) </span></span>  
 [<span data-ttu-id="f40ed-126">报表服务器 Web 服务</span><span class="sxs-lookup"><span data-stu-id="f40ed-126">Report Server Web Service</span></span>](report-server-web-service.md)  
  
  
