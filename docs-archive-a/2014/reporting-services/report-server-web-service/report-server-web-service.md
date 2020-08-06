---
title: 报表服务器 Web 服务 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- SSIS, Web service
- Web service [Reporting Services]
- Reporting Services, extending
- SQL Server Reporting Services, Web service
- Reporting Services, Web service
- XML Web service [Reporting Services]
- Report Server Web service
ms.assetid: 16c21dec-6b46-4497-9a0c-1b0f2b6ab8fc
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8bb43a0fa52a243bd250f70fac16e18d949f8197
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586342"
---
# <a name="report-server-web-service"></a><span data-ttu-id="9d6b1-102">报表服务器 Web 服务</span><span class="sxs-lookup"><span data-stu-id="9d6b1-102">Report Server Web Service</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="9d6b1-103">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]通过报表服务器 Web 服务提供对 Report Server 的全部功能的访问。</span><span class="sxs-lookup"><span data-stu-id="9d6b1-103">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] provides access to the full functionality of the report server through the Report Server Web service.</span></span> <span data-ttu-id="9d6b1-104">报表服务器 Web 服务是具有 SOAP API 的 XML Web 服务。</span><span class="sxs-lookup"><span data-stu-id="9d6b1-104">The Report Server Web service is an XML Web service with a SOAP API.</span></span> <span data-ttu-id="9d6b1-105">它使用 HTTP 上的 SOAP (SOAP over HTTP)，并且充当客户端程序与报表服务器之间的通信接口。</span><span class="sxs-lookup"><span data-stu-id="9d6b1-105">It uses SOAP over HTTP and acts as a communications interface between client programs and the report server.</span></span> <span data-ttu-id="9d6b1-106">该 Web 服务提供两个端点（一个用于报表执行，一个用于报表管理）以及公开报表服务器的功能和使您能够为报表生命周期的任何部分创建自定义工具的方法。</span><span class="sxs-lookup"><span data-stu-id="9d6b1-106">The Web service provides two endpoints - one for report execution and one for report management - with methods that expose the functionality of the report server and enable you to create custom tools for any part of the report life cycle.</span></span>  
  
 <span data-ttu-id="9d6b1-107">可以通过三个主要方法基于 Web 服务开发 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 应用程序。</span><span class="sxs-lookup"><span data-stu-id="9d6b1-107">There are three primary ways to develop [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] applications based on the Web service.</span></span> <span data-ttu-id="9d6b1-108">可以：</span><span class="sxs-lookup"><span data-stu-id="9d6b1-108">You can:</span></span>  
  
-   <span data-ttu-id="9d6b1-109">使用和 SDK 开发应用程序 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="9d6b1-109">Develop applications using [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] and the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK.</span></span> <span data-ttu-id="9d6b1-110">有关使用 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 生成 Web 服务应用程序的详细信息，请参阅[使用 Web 服务和 .NET Framework 生成应用程序](../report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)。</span><span class="sxs-lookup"><span data-stu-id="9d6b1-110">For more information about using the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] to build Web service applications, see [Building Applications Using the Web Service and the .NET Framework](../report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md).</span></span>  
  
-   <span data-ttu-id="9d6b1-111">使用 **rs** 实用工具 (RS.exe)（ [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 脚本环境）开发应用程序。</span><span class="sxs-lookup"><span data-stu-id="9d6b1-111">Develop applications using the **rs** utility (RS.exe), the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] script environment.</span></span> <span data-ttu-id="9d6b1-112">使用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 和 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 脚本，可以运行任何报表服务器 Web 服务操作。</span><span class="sxs-lookup"><span data-stu-id="9d6b1-112">With [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] and [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] scripts, you can run any of the Report Server Web service operations.</span></span> <span data-ttu-id="9d6b1-113">有关 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 中脚本编写的详细信息，请参阅[使用 rs.exe 实用工具和 Web 服务编写脚本](../tools/script-with-the-rs-exe-utility-and-the-web-service.md)。</span><span class="sxs-lookup"><span data-stu-id="9d6b1-113">For more information about scripting in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], see [Script with the rs.exe Utility and the Web Service](../tools/script-with-the-rs-exe-utility-and-the-web-service.md).</span></span>  
  
-   <span data-ttu-id="9d6b1-114">使用任何支持 SOAP 的开发工具集开发应用程序。</span><span class="sxs-lookup"><span data-stu-id="9d6b1-114">Develop applications using any SOAP-enabled set of development tools.</span></span> <span data-ttu-id="9d6b1-115">有关详细信息，请参阅 [SOAP 在 Reporting Services 中的作用](../report-server-web-service/the-role-of-soap-in-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="9d6b1-115">For more information, see [The Role of SOAP in Reporting Services](../report-server-web-service/the-role-of-soap-in-reporting-services.md).</span></span>  
  
## <a name="programming-diagram"></a><span data-ttu-id="9d6b1-116">编程关系图</span><span class="sxs-lookup"><span data-stu-id="9d6b1-116">Programming Diagram</span></span>  
 <span data-ttu-id="9d6b1-117">![报表服务器 Web 服务部署选项](../../../2014/reporting-services/media/reportserviceswebserviceprog-01.gif "报表服务器 Web 服务部署选项")</span><span class="sxs-lookup"><span data-stu-id="9d6b1-117">![Report Server Web service development options](../../../2014/reporting-services/media/reportserviceswebserviceprog-01.gif "Report Server Web service development options")</span></span>  
<span data-ttu-id="9d6b1-118">Reporting Services 可用 Web 服务开发选项</span><span class="sxs-lookup"><span data-stu-id="9d6b1-118">Reporting Services available Web service development options</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9d6b1-119">本节内容</span><span class="sxs-lookup"><span data-stu-id="9d6b1-119">In This Section</span></span>  
 [<span data-ttu-id="9d6b1-120">报表服务器 Web 服务方法</span><span class="sxs-lookup"><span data-stu-id="9d6b1-120">Report Server Web Service Methods</span></span>](../report-server-web-service/methods/report-server-web-service-methods.md)  
 <span data-ttu-id="9d6b1-121">介绍每个报表服务器 Web 服务的功能和方法。</span><span class="sxs-lookup"><span data-stu-id="9d6b1-121">Describes the features and methods of each Report Server Web service.</span></span>  
  
 [<span data-ttu-id="9d6b1-122">The Role of SOAP in Reporting Services</span><span class="sxs-lookup"><span data-stu-id="9d6b1-122">The Role of SOAP in Reporting Services</span></span>](../report-server-web-service/the-role-of-soap-in-reporting-services.md)  
 <span data-ttu-id="9d6b1-123">概述 SOAP 以及如何在报表服务器 Web 服务中使用 SOAP。</span><span class="sxs-lookup"><span data-stu-id="9d6b1-123">Provides an overview of SOAP and how it is used in the Report Server Web services.</span></span>  
  
 [<span data-ttu-id="9d6b1-124">访问 SOAP API</span><span class="sxs-lookup"><span data-stu-id="9d6b1-124">Accessing the SOAP API</span></span>](../report-server-web-service/accessing-the-soap-api.md)  
 <span data-ttu-id="9d6b1-125">介绍 Web 服务描述语言 (WSDL) 并提供用于访问 Reporting Services WSDL 文件的 URL。</span><span class="sxs-lookup"><span data-stu-id="9d6b1-125">Describes the Web Service Description Language (WSDL) and provides URLs for accessing a Reporting Services WSDL file.</span></span>  
  
 [<span data-ttu-id="9d6b1-126">使用 Web 服务和 .NET Framework 生成应用程序</span><span class="sxs-lookup"><span data-stu-id="9d6b1-126">Building Applications Using the Web Service and the .NET Framework</span></span>](../report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)  
 <span data-ttu-id="9d6b1-127">包含与开发调用 Reporting Services SOAP API 的应用程序和 Web 服务有关的信息。</span><span class="sxs-lookup"><span data-stu-id="9d6b1-127">Contains information about developing applications and Web services that call the Reporting Services SOAP API.</span></span>  
  
 [<span data-ttu-id="9d6b1-128">使用 rs.exe 实用工具和 Web 服务编写脚本</span><span class="sxs-lookup"><span data-stu-id="9d6b1-128">Script with the rs.exe Utility and the Web Service</span></span>](../tools/script-with-the-rs-exe-utility-and-the-web-service.md)  
 <span data-ttu-id="9d6b1-129">概要介绍 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 脚本编写环境。</span><span class="sxs-lookup"><span data-stu-id="9d6b1-129">Provides an overview of the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] scripting environment.</span></span>  
  
 [<span data-ttu-id="9d6b1-130">技术参考 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="9d6b1-130">Technical Reference &#40;SSRS&#41;</span></span>](../../../2014/reporting-services/technical-reference-ssrs.md)  
 <span data-ttu-id="9d6b1-131">包含特定于报表服务器 Web 服务方法以及相应复杂类型的参考材料。</span><span class="sxs-lookup"><span data-stu-id="9d6b1-131">Contains reference material specific to Report Server Web services methods and corresponding complex types.</span></span>  
  
## <a name="user-requirements-for-web-service-development"></a><span data-ttu-id="9d6b1-132">针对 Web 服务开发的用户要求</span><span class="sxs-lookup"><span data-stu-id="9d6b1-132">User Requirements for Web Service Development</span></span>  
 <span data-ttu-id="9d6b1-133">若要使用报表服务器 Web 服务开发应用程序，您需要：</span><span class="sxs-lookup"><span data-stu-id="9d6b1-133">To develop applications using the Report Server Web service, you need:</span></span>  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="9d6b1-134">Internet Explorer 5.5 或更高版本安装在具有与报表服务器的 Internet 连接或能够访问报表服务器的计算机上。</span><span class="sxs-lookup"><span data-stu-id="9d6b1-134">Internet Explorer 5.5 or later installed on a computer with an Internet connection to and access to the report server.</span></span>  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="9d6b1-135">[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] 或 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]如果要使用开发和部署应用程序，请在计算机上安装 SDK [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="9d6b1-135">[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] or the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK installed on a computer if you want to develop and deploy [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] applications using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)].</span></span>  
  
-   <span data-ttu-id="9d6b1-136">深入了解 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 特性和功能。</span><span class="sxs-lookup"><span data-stu-id="9d6b1-136">An in-depth understanding of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] features and capabilities.</span></span>  
  
-   <span data-ttu-id="9d6b1-137">扎实理解 SOAP 和 [!INCLUDE[vstecwebservices](../../includes/vstecwebservices-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="9d6b1-137">A firm understanding of SOAP and [!INCLUDE[vstecwebservices](../../includes/vstecwebservices-md.md)].</span></span>  
  
-   <span data-ttu-id="9d6b1-138">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 如果你计划将用作 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 开发平台，则采用与兼容的语言（如或）的开发体验。</span><span class="sxs-lookup"><span data-stu-id="9d6b1-138">Development experience in a [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]-compatible language such as [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)] or [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)], if you plan to use the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] as your development platform.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d6b1-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9d6b1-139">See Also</span></span>  
 [<span data-ttu-id="9d6b1-140">报表服务器 Web 服务</span><span class="sxs-lookup"><span data-stu-id="9d6b1-140">Report Server Web Service</span></span>](../report-server-web-service/report-server-web-service.md)  
  
  
