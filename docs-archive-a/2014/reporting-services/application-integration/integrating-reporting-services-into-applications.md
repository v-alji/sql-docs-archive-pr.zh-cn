---
title: 将 Reporting Services 集成到应用程序中 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- integrating reports [Reporting Services]
- custom applications [SSRS]
- Reporting Services, application integration
- application integration [Reporting Services]
- reports [Reporting Services], integrating
ms.assetid: 49eb539c-d89b-4291-839a-0ec1a65cd270
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3ab92008c5beb4d931e8e781857d766bb56a1efd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577409"
---
# <a name="integrating-reporting-services-into-applications"></a><span data-ttu-id="f2ef7-102">将 Reporting Services 集成到应用程序中</span><span class="sxs-lookup"><span data-stu-id="f2ef7-102">Integrating Reporting Services into Applications</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="f2ef7-103">是一个开放和可扩展的报表平台，设计用于向开发人员提供一整套用于开发解决方案的 API。</span><span class="sxs-lookup"><span data-stu-id="f2ef7-103">is an open and extensible reporting platform designed to provide developers with a comprehensive set of APIs for developing solutions.</span></span>  
  
 <span data-ttu-id="f2ef7-104">有三个选项可用于集成 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 到自定义应用程序中：报表服务器 Web 服务（也称为 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SOAP API）、用于的 ReportViewer 控件 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)] 和 URL 访问。</span><span class="sxs-lookup"><span data-stu-id="f2ef7-104">There are three options for integrating [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] into custom applications: the Report Server Web service, also known as the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SOAP API, the ReportViewer controls for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)], and URL access.</span></span> <span data-ttu-id="f2ef7-105">每个选项都提供一个不同的方法来将 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 集成到应用程序中。</span><span class="sxs-lookup"><span data-stu-id="f2ef7-105">Each option provides a different approach for integrating [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] into your applications.</span></span>  
  
## <a name="report-server-web-service"></a><span data-ttu-id="f2ef7-106">报表服务器 Web 服务</span><span class="sxs-lookup"><span data-stu-id="f2ef7-106">Report Server Web Service</span></span>  
 <span data-ttu-id="f2ef7-107">报表服务器 Web 服务是针对 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 进行开发的主接口。</span><span class="sxs-lookup"><span data-stu-id="f2ef7-107">The Report Server Web service is the primary interface for developing against [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="f2ef7-108">无论您是开发代码以管理报表目录，还是开发代码以便用支持的格式呈现报表，该 Web 服务都公开所有必需的方法以便将 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 集成到您的应用程序中。</span><span class="sxs-lookup"><span data-stu-id="f2ef7-108">Whether you are developing code to manage your report catalog or developing code to render reports to a supported format, the Web service exposes all the necessary methods to integrate [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] into your applications.</span></span> <span data-ttu-id="f2ef7-109">报表管理器就是此类应用程序的一个示例，报表管理器随 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 一起提供，它使用该 Web 服务管理报表服务器数据库。</span><span class="sxs-lookup"><span data-stu-id="f2ef7-109">An example of one such application is Report Manager, which is included with [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]; it uses the Web service to manage the report server database.</span></span>  
  
## <a name="reportviewer-controls-for-visual-studio"></a><span data-ttu-id="f2ef7-110">用于 Visual Studio 的 ReportViewer 控件</span><span class="sxs-lookup"><span data-stu-id="f2ef7-110">ReportViewer Controls for Visual Studio</span></span>  
 <span data-ttu-id="f2ef7-111">[!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)] 随附的 ReportViewer 控件用于将报表查看集成到您的应用程序中。</span><span class="sxs-lookup"><span data-stu-id="f2ef7-111">The ReportViewer controls included with [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)] are used for integrating report viewing into your applications.</span></span> <span data-ttu-id="f2ef7-112">存在两个此类控件：一个用于基于 Windows 窗体的应用程序，另一个用于 Web 窗体应用程序。</span><span class="sxs-lookup"><span data-stu-id="f2ef7-112">There are two controls: one for Windows Forms-based applications and one for Web Forms applications.</span></span> <span data-ttu-id="f2ef7-113">每个控件都提供查看已部署到报表服务器的报表的功能以及呈现在尚未安装报表服务器的环境中存在的报表的功能。</span><span class="sxs-lookup"><span data-stu-id="f2ef7-113">Each control provides the capability for viewing reports that have been deployed to a report server as well as the ability to render reports that exist in an environment where a report server has not been installed.</span></span>  
  
## <a name="url-access"></a><span data-ttu-id="f2ef7-114">URL 访问</span><span class="sxs-lookup"><span data-stu-id="f2ef7-114">URL Access</span></span>  
 <span data-ttu-id="f2ef7-115">URL 访问是用于将报表查看集成到您的应用程序中的另一个选项（如果无法选择 ReportViewer 控件）。</span><span class="sxs-lookup"><span data-stu-id="f2ef7-115">URL access is another option for integrating report viewing into your applications if the ReportViewer controls are not an option.</span></span> <span data-ttu-id="f2ef7-116">此外，URL 访问还用于通过电子邮件将指向报表的链接发送给用户。</span><span class="sxs-lookup"><span data-stu-id="f2ef7-116">In addition, URL access is useful for sending links to reports to users via e-mail.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f2ef7-117">本节内容</span><span class="sxs-lookup"><span data-stu-id="f2ef7-117">In This Section</span></span>  
 [<span data-ttu-id="f2ef7-118">使用 SOAP 集成 Reporting Services</span><span class="sxs-lookup"><span data-stu-id="f2ef7-118">Integrating Reporting Services Using SOAP</span></span>](../application-integration/integrating-reporting-services-using-soap.md)  
 <span data-ttu-id="f2ef7-119">说明如何使用报表服务器 Web 服务将 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 报表导航和管理集成到您的现有业务应用程序中。</span><span class="sxs-lookup"><span data-stu-id="f2ef7-119">Describes how to integrate [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report navigation and management into your existing business applications using the Report Server Web service.</span></span>  
  
 [<span data-ttu-id="f2ef7-120">使用 ReportViewer 控件集成 Reporting Services</span><span class="sxs-lookup"><span data-stu-id="f2ef7-120">Integrating Reporting Services Using the ReportViewer Controls</span></span>](../application-integration/integrating-reporting-services-using-reportviewer-controls.md)  
 <span data-ttu-id="f2ef7-121">说明如何使用 ReportViewer 控件将报表查看集成到您的现有应用程序中。</span><span class="sxs-lookup"><span data-stu-id="f2ef7-121">Describes how to integrate report viewing into your existing applications using the ReportViewer controls.</span></span>  
  
 [<span data-ttu-id="f2ef7-122">使用 URL 访问集成 Reporting Services</span><span class="sxs-lookup"><span data-stu-id="f2ef7-122">Integrating Reporting Services Using URL Access</span></span>](../application-integration/integrating-reporting-services-using-url-access.md)  
 <span data-ttu-id="f2ef7-123">说明如何使用 URL 访问将 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 报表导航集成到您的现有业务应用程序中。</span><span class="sxs-lookup"><span data-stu-id="f2ef7-123">Describes how to integrate [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report navigation into your existing business applications using URL access.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2ef7-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f2ef7-124">See Also</span></span>  
 <span data-ttu-id="f2ef7-125">[报表管理器（SSRS 本机模式）](../../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="f2ef7-125">[Report Manager  &#40;SSRS Native Mode&#41;](../../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="f2ef7-126">[在 URL 访问和 SOAP 之间选择](../../../2014/reporting-services/application-integration/choosing-between-url-access-and-soap.md) </span><span class="sxs-lookup"><span data-stu-id="f2ef7-126">[Choosing Between URL Access and SOAP](../../../2014/reporting-services/application-integration/choosing-between-url-access-and-soap.md) </span></span>  
 <span data-ttu-id="f2ef7-127">[SSRS&#41;&#40;技术参考](../../../2014/reporting-services/technical-reference-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f2ef7-127">[Technical Reference &#40;SSRS&#41;](../../../2014/reporting-services/technical-reference-ssrs.md) </span></span>  
 [<span data-ttu-id="f2ef7-128">报表服务器 Web 服务</span><span class="sxs-lookup"><span data-stu-id="f2ef7-128">Report Server Web Service</span></span>](../report-server-web-service/report-server-web-service.md)  
  
  
