---
title: “仅文件”安装 (Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- files-only installation [Reporting Services]
- installation options [Reporting Services]
ms.assetid: bdc74a8f-046c-4aa0-bfbd-4f1711dfb9ce
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3ec5c595dce3e292d37117453ccbbc6d19f8b87d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689788"
---
# <a name="files-only-installation-reporting-services"></a><span data-ttu-id="62452-102">“仅文件”安装 (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="62452-102">Files-Only Installation (Reporting Services)</span></span>
  <span data-ttu-id="62452-103">“仅文件安装”  指的是一种 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 安装模式，在该安装模式中，安装程序为 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 程序文件创建文件夹结构、将文件复制到磁盘、在本地计算机上注册报表服务器服务、配置服务帐户、向服务帐户授予文件权限以及注册 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] WMI 提供程序。</span><span class="sxs-lookup"><span data-stu-id="62452-103">*Files-only installation* refers to a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation where Setup creates the folder structure for [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] program files, copies the files to disk, registers the Report Server service on the local computer, configures the service account, grants files permissions to the service account, and registers the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] WMI provider.</span></span>  
  
 <span data-ttu-id="62452-104">“仅文件”安装包括以下 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 功能：报表服务器 Web 服务（它承载报表服务器 Web 服务、后台处理应用程序和报表管理器）、报表生成器、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 配置工具和 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 命令行实用工具（rsconfig.exe、rskeymgmt.exe 和 rs.exe）。</span><span class="sxs-lookup"><span data-stu-id="62452-104">A files-only installation includes the following [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] features: Report Server service (which hosts the Report Server Web service, background processing application, and Report Manager), Report Builder, the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool, and the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] command line utilities (rsconfig.exe, rskeymgmt.exe and rs.exe).</span></span> <span data-ttu-id="62452-105">它不适用于共享功能，如 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 或 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]。必须将此类功能指定为独立项，才能安装它们。</span><span class="sxs-lookup"><span data-stu-id="62452-105">It does not apply to shared features such as [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] or [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], which must be specified as separate items if you want to install them.</span></span>  
  
 <span data-ttu-id="62452-106">与其他安装模式不同，“仅文件”模式下安装的报表服务器在安装程序完成后不能正常工作。</span><span class="sxs-lookup"><span data-stu-id="62452-106">In contrast with other installation modes, a report server that is installed in files-only mode is not operational when Setup is finished.</span></span> <span data-ttu-id="62452-107">要使用 [Reporting Services 配置管理器（本机模式）](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)来使报表服务器联机，需要进行其他配置。</span><span class="sxs-lookup"><span data-stu-id="62452-107">Additional configuration will be required to bring the report server online by using the [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>  
  
## <a name="when-to-select-files-only-installation-mode"></a><span data-ttu-id="62452-108">何时选择“仅文件”安装模式</span><span class="sxs-lookup"><span data-stu-id="62452-108">When to Select Files-Only Installation Mode</span></span>  
 <span data-ttu-id="62452-109">在以下情况下必须执行“仅文件”安装：</span><span class="sxs-lookup"><span data-stu-id="62452-109">A files-only installation must be performed when:</span></span>  
  
-   <span data-ttu-id="62452-110">想要将报表服务器连接到远程报表服务器数据库。</span><span class="sxs-lookup"><span data-stu-id="62452-110">You want to connect the report server to a remote report server database.</span></span>  
  
-   <span data-ttu-id="62452-111">想要将报表服务器作为命名实例安装。</span><span class="sxs-lookup"><span data-stu-id="62452-111">You want to install the report server as a named instance.</span></span>  
  
-   <span data-ttu-id="62452-112">您的部署要求包括使用自定义设置或功能，并且想要完全控制服务器配置的时间和方式。</span><span class="sxs-lookup"><span data-stu-id="62452-112">You have deployment requirements that include using custom settings or functionality, and you want full control over when and how the server is configured.</span></span>  
  
-   <span data-ttu-id="62452-113">安装包括 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]故障转移群集。</span><span class="sxs-lookup"><span data-stu-id="62452-113">Installing a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster that includes [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
## <a name="how-to-perform-a-files-only-installation"></a><span data-ttu-id="62452-114">如何执行“仅文件”安装</span><span class="sxs-lookup"><span data-stu-id="62452-114">How to Perform a Files-Only Installation</span></span>  
 <span data-ttu-id="62452-115">“仅文件”安装是 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]的默认安装模式。</span><span class="sxs-lookup"><span data-stu-id="62452-115">Files-only installation is the default for [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="62452-116">可通过命令行或在安装向导中指定“仅文件”安装。</span><span class="sxs-lookup"><span data-stu-id="62452-116">You can specify a files-only installation through the command line or in the Installation wizard.</span></span> <span data-ttu-id="62452-117">以下主题提供了分步说明：</span><span class="sxs-lookup"><span data-stu-id="62452-117">The following topics provide step-by-step instructions:</span></span>  
  
-   <span data-ttu-id="62452-118">[从安装向导安装 SQL Server 2014 &#40;安装&#41;](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md)。</span><span class="sxs-lookup"><span data-stu-id="62452-118">[Install SQL Server 2014 from the Installation Wizard &#40;Setup&#41;](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md).</span></span>  
  
-   <span data-ttu-id="62452-119">[从命令提示符安装 SQL Server 2014](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)。</span><span class="sxs-lookup"><span data-stu-id="62452-119">[Install SQL Server 2014 from the Command Prompt](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md).</span></span>  
  
#### <a name="example-command-line-script"></a><span data-ttu-id="62452-120">命令行脚本示例</span><span class="sxs-lookup"><span data-stu-id="62452-120">Example Command Line Script</span></span>  
 <span data-ttu-id="62452-121">为清楚起见，该示例包括了 /RSINSTALLMODE="FilesOnlyMode"。</span><span class="sxs-lookup"><span data-stu-id="62452-121">For clarity, the example includes /RSINSTALLMODE="FilesOnlyMode".</span></span> <span data-ttu-id="62452-122">但是，由于“仅文件”模式是默认模式，因此可将其省略且仍可进行“仅文件”模式安装。</span><span class="sxs-lookup"><span data-stu-id="62452-122">However, because files-only mode is the default, you can omit this and still get a files-only mode installation.</span></span>  
  
```  
setup /q /ACTION=install /FEATURES=RS /InstanceName=MSSQLSERVER /RSSVCACCOUNT="NT AUTHORITY\NETWORK SERVICE" /RSINSTALLMODE="FilesOnlyMode"  
```  
  
#### <a name="installation-wizard"></a><span data-ttu-id="62452-123">安装向导</span><span class="sxs-lookup"><span data-stu-id="62452-123">Installation Wizard</span></span>  
 <span data-ttu-id="62452-124">在“功能选择”页中选择 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 时，安装程序将提供可用于指定安装模式的“ [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 配置”页。</span><span class="sxs-lookup"><span data-stu-id="62452-124">When you select [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in the Feature Selection page, Setup provides a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration page that enables you to specify the installation mode.</span></span> <span data-ttu-id="62452-125">要指定“仅文件”安装，请在“[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 配置”页上选择“安装但不配置报表服务器”。</span><span class="sxs-lookup"><span data-stu-id="62452-125">To specify a files-only installation, select **Install but do not configure the report server** on the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62452-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="62452-126">See Also</span></span>  
 <span data-ttu-id="62452-127">[验证 Reporting Services 安装](verify-a-reporting-services-installation.md) </span><span class="sxs-lookup"><span data-stu-id="62452-127">[Verify a Reporting Services Installation](verify-a-reporting-services-installation.md) </span></span>  
 <span data-ttu-id="62452-128">[配置报表服务器服务帐户（SSRS 配置管理器）](configure-the-report-server-service-account-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="62452-128">[Configure the Report Server Service Account &#40;SSRS Configuration Manager&#41;](configure-the-report-server-service-account-ssrs-configuration-manager.md) </span></span>  
 <span data-ttu-id="62452-129">[配置报表服务器 URL（SSRS 配置管理器）](configure-report-server-urls-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="62452-129">[Configure Report Server URLs  &#40;SSRS Configuration Manager&#41;](configure-report-server-urls-ssrs-configuration-manager.md) </span></span>  
 <span data-ttu-id="62452-130">[&#40;SSRS Configuration Manager 配置报表服务器数据库连接&#41;](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="62452-130">[Configure a Report Server Database Connection  &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md) </span></span>  
 <span data-ttu-id="62452-131">[Reporting Services sharepoint 模式安装 &#40;SharePoint 2010 和 SharePoint 2013&#41;](install-reporting-services-sharepoint-mode.md) </span><span class="sxs-lookup"><span data-stu-id="62452-131">[Reporting Services SharePoint Mode Installation &#40;SharePoint 2010 and SharePoint 2013&#41;](install-reporting-services-sharepoint-mode.md) </span></span>  
 <span data-ttu-id="62452-132">[安装 Reporting Services 本机模式报表服务器](install-reporting-services-native-mode-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="62452-132">[Install Reporting Services Native Mode Report Server](install-reporting-services-native-mode-report-server.md) </span></span>  
 [<span data-ttu-id="62452-133">Reporting Services 工具</span><span class="sxs-lookup"><span data-stu-id="62452-133">Reporting Services Tools</span></span>](../tools/reporting-services-tools.md)  
  
  
