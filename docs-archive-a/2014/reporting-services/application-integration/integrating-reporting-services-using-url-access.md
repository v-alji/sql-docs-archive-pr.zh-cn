---
title: 使用 URL 访问集成 Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- URL access [Reporting Services], about URL access
- integrating reports [Reporting Services]
ms.assetid: f1014f7d-fafa-4aa8-8bd2-5bdba835d9b6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fedf4ce3011d9caae9d673acf354265537115057
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691136"
---
# <a name="integrating-reporting-services-using-url-access"></a><span data-ttu-id="11032-102">使用 URL 访问集成 Reporting Services</span><span class="sxs-lookup"><span data-stu-id="11032-102">Integrating Reporting Services Using URL Access</span></span>
  <span data-ttu-id="11032-103">借助于 URL 访问，您可以通过报表服务器 URL 访问报表。</span><span class="sxs-lookup"><span data-stu-id="11032-103">With URL access, you access reports through a report server URL.</span></span> <span data-ttu-id="11032-104">使用 URL 请求，您可以访问特定的报表服务器以及报表服务器数据库中的报表、资源和其他项。</span><span class="sxs-lookup"><span data-stu-id="11032-104">A URL request enables you to access a specific report server as well as the reports, resources, and other items in the report server database.</span></span> <span data-ttu-id="11032-105">还可以为用户自定义报表查看和导航体验。</span><span class="sxs-lookup"><span data-stu-id="11032-105">You can also customize the report viewing and navigation experience for your users.</span></span> <span data-ttu-id="11032-106">URL 的查询字符串包含设备信息设置，以及针对报表和所选呈现输出的报表参数。</span><span class="sxs-lookup"><span data-stu-id="11032-106">The query string of the URL contains device information settings, as well as report parameters targeted at your report and the chosen rendering output.</span></span> <span data-ttu-id="11032-107">报表服务器处理 URL 请求的方法取决于您通过 URL 访问的项的参数、参数前缀和类型。</span><span class="sxs-lookup"><span data-stu-id="11032-107">The way the report server handles URL requests depends on the parameters, parameter prefixes, and type of item that you are accessing through the URL.</span></span>  
  
 <span data-ttu-id="11032-108">您可以使用 URL 访问在您开发的应用程序中向报表和其他报表服务器项嵌入超链接，而无论是在 Windows 还是 Web 环境中。</span><span class="sxs-lookup"><span data-stu-id="11032-108">You can use URL access to embed hyperlinks to reports and other report server items in the applications that you develop, whether in a Windows or Web environment.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="11032-109">本节中的各主题向您提供有关集成的一些基本构思。</span><span class="sxs-lookup"><span data-stu-id="11032-109">The topics in the section provide you with some basic ideas for integration.</span></span> <span data-ttu-id="11032-110">您可以使用此信息来开始设计和开发您自己的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 集成方案。</span><span class="sxs-lookup"><span data-stu-id="11032-110">You can use the information to begin to design and develop your own [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] integration scenarios.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="11032-111">本节内容</span><span class="sxs-lookup"><span data-stu-id="11032-111">In This Section</span></span>  
 [<span data-ttu-id="11032-112">在 Web 应用程序中使用 URL 访问</span><span class="sxs-lookup"><span data-stu-id="11032-112">Using URL Access in a Web Application</span></span>](integrating-reporting-services-using-url-access-web-application.md)  
 <span data-ttu-id="11032-113">介绍如何使用 URL 访问将 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 集成到 Web 环境中。</span><span class="sxs-lookup"><span data-stu-id="11032-113">Describes how to use URL access to integrate [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] into a Web environment.</span></span>  
  
 [<span data-ttu-id="11032-114">在 Windows 应用程序中使用 URL 访问</span><span class="sxs-lookup"><span data-stu-id="11032-114">Using URL Access in a Windows Application</span></span>](integrating-reporting-services-using-url-access-windows-application.md)  
 <span data-ttu-id="11032-115">介绍如何使用 URL 访问将 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 集成到 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Win32 环境中。</span><span class="sxs-lookup"><span data-stu-id="11032-115">Describes how to use URL access to integrate [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] into a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Win32 environment.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11032-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="11032-116">See Also</span></span>  
 <span data-ttu-id="11032-117">[将 Reporting Services 集成到应用程序中](../application-integration/integrating-reporting-services-into-applications.md) </span><span class="sxs-lookup"><span data-stu-id="11032-117">[Integrating Reporting Services into Applications](../application-integration/integrating-reporting-services-into-applications.md) </span></span>  
 [<span data-ttu-id="11032-118">URL 访问 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="11032-118">URL Access &#40;SSRS&#41;</span></span>](../url-access-ssrs.md)  
  
  
