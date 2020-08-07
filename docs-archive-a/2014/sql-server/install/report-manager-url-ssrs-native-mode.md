---
title: 报表管理器 URL (SSRS 本机模式) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.rsconfigtool.reportmanagervirtualdirectory.f1
ms.assetid: 45768952-23a6-45a5-b541-e7bf192b4a78
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: ec43c91bb2d24bb96cc6541d93311ce6dd234ed4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588257"
---
# <a name="report-manager-url-ssrs-native-mode"></a><span data-ttu-id="7793b-102">报表管理器 URL（SSRS 本机模式）</span><span class="sxs-lookup"><span data-stu-id="7793b-102">Report Manager URL (SSRS Native Mode)</span></span>
  <span data-ttu-id="7793b-103">使用报表管理器 URL 页可配置或修改用于访问报表管理器的 URL。</span><span class="sxs-lookup"><span data-stu-id="7793b-103">Use the Report Manager URL page to configure or modify the URL used to access Report Manager.</span></span> <span data-ttu-id="7793b-104">默认情况下，报表管理器 URL 继承报表服务器 Web 服务 URL 的前缀、IP 地址和端口。</span><span class="sxs-lookup"><span data-stu-id="7793b-104">By default, the Report Manager URL inherits the prefix, IP address, and port of the Report Server Web service URL.</span></span> <span data-ttu-id="7793b-105">这是因为报表管理器提供了对于运行在相同报表服务器服务中的 Web 服务的前端访问。</span><span class="sxs-lookup"><span data-stu-id="7793b-105">This is because Report Manager provides front-end access to the Web service that runs within the same Report Server service.</span></span> <span data-ttu-id="7793b-106">如果您正在隔离服务应用程序并使用报表管理器访问其他计算机上的报表服务器 Web 服务，则必须编辑 RSReportServer.config 文件以将报表管理器指向不同的实例。</span><span class="sxs-lookup"><span data-stu-id="7793b-106">If you are isolating the service applications and using Report Manager to access a Report Server Web service on a different computer, you must edit RSReportServer.config file to point Report Manager to a different instance.</span></span> <span data-ttu-id="7793b-107">有关配置与远程 Report Server 报表管理器连接的详细信息，请参阅[Reporting Services 配置管理器 &#40;纯模式&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="7793b-107">For more information about configuring a Report Manager connection to a remote report server, see [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>  
  
 [!INCLUDE[applies](../../includes/applies-md.md)]<span data-ttu-id="7793b-108">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]本机模式。</span><span class="sxs-lookup"><span data-stu-id="7793b-108">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode.</span></span>  
  
 <span data-ttu-id="7793b-109">如果您打算将报表服务器配置为在 SharePoint 集成模式下运行，请不要创建报表管理器 URL。</span><span class="sxs-lookup"><span data-stu-id="7793b-109">If you are configuring the report server to run in SharePoint integrated mode, do not create a Report Manager URL.</span></span> <span data-ttu-id="7793b-110">在 SharePoint 集成模式下运行的报表服务器不支持报表管理器。</span><span class="sxs-lookup"><span data-stu-id="7793b-110">Report Manager is not supported on a report server that runs in SharePoint integrated mode.</span></span> <span data-ttu-id="7793b-111">如果报表管理器已存在一个 URL，则将报表服务器配置为在 SharePoint 集成模式下运行后，该 URL 将不可用。</span><span class="sxs-lookup"><span data-stu-id="7793b-111">If a URL already exists for Report Manager, it will become unavailable after you configure the report server to run in SharePoint integrated mode.</span></span>  
  
 <span data-ttu-id="7793b-112">若要打开此页，请启动 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 配置管理器，并在导航窗格中单击 **“报表管理器 URL”** 。</span><span class="sxs-lookup"><span data-stu-id="7793b-112">To open this page, start the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager and click **Report Manager URL** in the navigation pane.</span></span> <span data-ttu-id="7793b-113">有关如何启动 Configuration Manager 的详细信息，请参阅[Reporting Services 配置管理器 &#40;本机模式&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="7793b-113">For more information about how to start the Configuration Manager, see [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7793b-114">如果报表管理器未启用，则将无法设置此页上的选项。</span><span class="sxs-lookup"><span data-stu-id="7793b-114">If Report Manager is not enabled, you cannot set options on this page.</span></span> <span data-ttu-id="7793b-115">有关启用报表管理器的详细信息，请参阅[Reporting Services 配置管理器 &#40;本机模式&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="7793b-115">For more information about enabling Report Manager, see [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="7793b-116">选项</span><span class="sxs-lookup"><span data-stu-id="7793b-116">Options</span></span>  
 <span data-ttu-id="7793b-117">**虚拟目录**</span><span class="sxs-lookup"><span data-stu-id="7793b-117">**Virtual Directory**</span></span>  
 <span data-ttu-id="7793b-118">指定报表管理器的虚拟目录名称。</span><span class="sxs-lookup"><span data-stu-id="7793b-118">Specifies the virtual directory name for Report Manager.</span></span> <span data-ttu-id="7793b-119">在同一台计算机上，每个报表管理器实例只能有一个虚拟目录名称。</span><span class="sxs-lookup"><span data-stu-id="7793b-119">You can only have one virtual directory name for each Report Manager instance on the same computer.</span></span>  
  
 <span data-ttu-id="7793b-120">**URLs**</span><span class="sxs-lookup"><span data-stu-id="7793b-120">**URLs**</span></span>  
 <span data-ttu-id="7793b-121">显示为当前报表管理器实例定义的 URL。</span><span class="sxs-lookup"><span data-stu-id="7793b-121">Displays the URL defined for the current Report Manager instance.</span></span>  
  
 <span data-ttu-id="7793b-122">**高级**</span><span class="sxs-lookup"><span data-stu-id="7793b-122">**Advanced**</span></span>  
 <span data-ttu-id="7793b-123">为当前报表管理器实例添加附加 URL。</span><span class="sxs-lookup"><span data-stu-id="7793b-123">Add an additional URL for the current Report Manager instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7793b-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7793b-124">See Also</span></span>  
 <span data-ttu-id="7793b-125">[&#40;SSRS Configuration Manager 配置 URL&#41;](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="7793b-125">[Configure a URL  &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md) </span></span>  
 <span data-ttu-id="7793b-126">[&#40;SSRS Configuration Manager 的配置文件中的 Url&#41;](../../reporting-services/install-windows/urls-in-configuration-files-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="7793b-126">[URLs in Configuration Files  &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/urls-in-configuration-files-ssrs-configuration-manager.md) </span></span>  
 [<span data-ttu-id="7793b-127">配置报表服务器 URL（SSRS 配置管理器）</span><span class="sxs-lookup"><span data-stu-id="7793b-127">Configure Report Server URLs  &#40;SSRS Configuration Manager&#41;</span></span>](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md)  
  
  
