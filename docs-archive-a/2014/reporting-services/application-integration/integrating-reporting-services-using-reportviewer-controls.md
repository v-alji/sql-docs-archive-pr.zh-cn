---
title: 使用 ReportViewer 控件集成 Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- ReportViewer controls
- integrating reports [Reporting Services]
ms.assetid: 3ba47fb4-73a9-4059-89fd-329adebe94a8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 18e28dbf1557bf36106b454738d0c0bfc037f2a7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577408"
---
# <a name="integrating-reporting-services-using-the-reportviewer-controls"></a><span data-ttu-id="d3da7-102">使用 ReportViewer 控件集成 Reporting Services</span><span class="sxs-lookup"><span data-stu-id="d3da7-102">Integrating Reporting Services Using the ReportViewer Controls</span></span>
  [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="d3da7-103">[!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)]提供两个 ReportViewer 控件，用于将报表查看功能集成到应用程序中。</span><span class="sxs-lookup"><span data-stu-id="d3da7-103">[!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)] provides two ReportViewer controls for integrating report viewing functionality into your applications.</span></span> <span data-ttu-id="d3da7-104">一个控件版本针对基于 Windows 窗体的应用程序，另一个版本针对 Web 窗体应用程序。</span><span class="sxs-lookup"><span data-stu-id="d3da7-104">There is a version for Windows Forms-based applications and one for Web Forms applications.</span></span> <span data-ttu-id="d3da7-105">每个控件都提供类似的功能，但分别设计为针对其各自的环境。</span><span class="sxs-lookup"><span data-stu-id="d3da7-105">Each control provides similar functionality but each is designed to target their individual environments.</span></span> <span data-ttu-id="d3da7-106">这两个控件都可以处理已部署到 Report Server (远程处理模式的报表) 或已复制到 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 未安装 (本地处理模式的计算机) 。</span><span class="sxs-lookup"><span data-stu-id="d3da7-106">Both controls can process reports that have been deployed to a report server (remote processing mode) or have been copied to a computer where [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] has not been installed (local processing mode).</span></span>  
  
 <span data-ttu-id="d3da7-107">ReportViewer 控件不包括对动态适应具有不同屏幕分辨率的不同设备的内置支持。</span><span class="sxs-lookup"><span data-stu-id="d3da7-107">The ReportViewer control does not include built-in support for dynamically adapting to different devices with different screen resolutions.</span></span>  
  
## <a name="remote-processing-mode"></a><span data-ttu-id="d3da7-108">远程处理模式</span><span class="sxs-lookup"><span data-stu-id="d3da7-108">Remote Processing Mode</span></span>  
 <span data-ttu-id="d3da7-109">远程处理模式是用于查看已部署到某一报表服务器的报表的首选方法。</span><span class="sxs-lookup"><span data-stu-id="d3da7-109">Remote processing mode is the preferred method for viewing reports that have been deployed to a report server.</span></span> <span data-ttu-id="d3da7-110">远程处理模式具备以下优点：</span><span class="sxs-lookup"><span data-stu-id="d3da7-110">Remote processing mode provides the following advantages:</span></span>  
  
-   <span data-ttu-id="d3da7-111">远程处理为运行报表提供优化的解决方案，因为报表服务器处理该报表。</span><span class="sxs-lookup"><span data-stu-id="d3da7-111">Remote processing provides an optimized solution for running reports because the report is processed by the report server.</span></span>  
  
-   <span data-ttu-id="d3da7-112">因为所有处理均由报表服务器进行，所以，报表请求可由扩展部署中的多个报表服务器或在某一扩展方案中具有多个处理器的服务器处理。</span><span class="sxs-lookup"><span data-stu-id="d3da7-112">Because all processing is handled by the report server, a report request can be processed by multiple report servers in a scale-out deployment or a server that has multiple processors in a scale-up scenario.</span></span>  
  
 <span data-ttu-id="d3da7-113">此外，在远程模式下运行的报表可利用报表服务器的全部功能，包括所有呈现和数据扩展插件。</span><span class="sxs-lookup"><span data-stu-id="d3da7-113">In addition, reports run in remote mode can utilize the full functionality of the report server including all rendering and data extensions.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d3da7-114">当该控件在远程处理模式下运行时可用于 ReportViewer 控件的扩展插件的列表取决于在报表服务器上安装的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 的版本。</span><span class="sxs-lookup"><span data-stu-id="d3da7-114">The list of extensions available to the ReportViewer control when it is running in remote processing mode depends on the edition of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] that is installed on the report server.</span></span>  
  
## <a name="local-processing-mode"></a><span data-ttu-id="d3da7-115">本地处理模式</span><span class="sxs-lookup"><span data-stu-id="d3da7-115">Local Processing Mode</span></span>  
 <span data-ttu-id="d3da7-116">本地处理模式提供在未安装 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 时用于查看和呈现报表的替代方法。</span><span class="sxs-lookup"><span data-stu-id="d3da7-116">Local processing mode provides an alternative method for viewing and rendering reports when [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is not installed.</span></span> <span data-ttu-id="d3da7-117">与远程处理不同，在该控件中只有报表服务器提供的一部分功能可用。</span><span class="sxs-lookup"><span data-stu-id="d3da7-117">Unlike remote processing only a subset of the functionality provided by the report server is available in the control.</span></span> <span data-ttu-id="d3da7-118">在本地处理模式中，数据处理不是由该控件处理的，而是由宿主应用程序实现的。</span><span class="sxs-lookup"><span data-stu-id="d3da7-118">In local processing mode, data processing is not handled by the control but rather implemented by the hosting application.</span></span> <span data-ttu-id="d3da7-119">但是，报表处理由控件本身处理。</span><span class="sxs-lookup"><span data-stu-id="d3da7-119">However report processing is handled by the control itself.</span></span> <span data-ttu-id="d3da7-120">在本地处理模式中，只有 PDF、Excel、Word 和图像呈现扩展插件才可用。</span><span class="sxs-lookup"><span data-stu-id="d3da7-120">In local processing mode, only the PDF, Excel, Word, and Image rendering extensions are available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3da7-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d3da7-121">See Also</span></span>  
 <span data-ttu-id="d3da7-122">[将 Reporting Services 集成到应用程序中](../application-integration/integrating-reporting-services-into-applications.md) </span><span class="sxs-lookup"><span data-stu-id="d3da7-122">[Integrating Reporting Services into Applications](../application-integration/integrating-reporting-services-into-applications.md) </span></span>  
 [<span data-ttu-id="d3da7-123">使用 Visual Studio 创建 SSRS 报表 (博客) </span><span class="sxs-lookup"><span data-stu-id="d3da7-123">Create SSRS Reports Using Visual Studio (Blog)</span></span>](https://jwcooney.com/2015/01/07/ssrs-basics-set-up-visual-studio-to-write-a-new-ssrs-report/)  
  
  
