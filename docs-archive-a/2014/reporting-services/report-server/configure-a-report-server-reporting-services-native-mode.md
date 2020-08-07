---
title: 配置报表服务器（Reporting Services 本机模式）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- report server configuration
- report servers [Reporting Services], configuring
ms.assetid: ef84ce9d-9156-48e9-8073-7e0535476932
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 64c63f52c373e034f0242101de0a27ee775920ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588297"
---
# <a name="configure-a-report-server-reporting-services-native-mode"></a><span data-ttu-id="f9ff2-102">配置报表服务器（Reporting Services 本机模式）</span><span class="sxs-lookup"><span data-stu-id="f9ff2-102">Configure a Report Server (Reporting Services Native Mode)</span></span>
  <span data-ttu-id="f9ff2-103">报表服务器可能需要进行其他配置后才能使用，具体取决于安装过程中所选的选项。</span><span class="sxs-lookup"><span data-stu-id="f9ff2-103">Depending on options you selected during installation, the Report Server might require additional configuration before you can use it.</span></span> <span data-ttu-id="f9ff2-104">至少，报表服务器配置应包含以下内容：</span><span class="sxs-lookup"><span data-stu-id="f9ff2-104">At a minimum, a report server configuration consists of the following:</span></span>  
  
-   <span data-ttu-id="f9ff2-105">报表服务器服务帐户（在安装过程中配置的）。</span><span class="sxs-lookup"><span data-stu-id="f9ff2-105">A Report Server service account (configured during installation).</span></span>  
  
-   <span data-ttu-id="f9ff2-106">用于访问报表服务器的 Web 服务 URL。</span><span class="sxs-lookup"><span data-stu-id="f9ff2-106">A Web service URL that provides access to the report server.</span></span>  
  
-   <span data-ttu-id="f9ff2-107">用于存储应用程序数据、报表和其他项的报表服务器。</span><span class="sxs-lookup"><span data-stu-id="f9ff2-107">A report server database that stores application data, reports, and other items.</span></span>  
  
 <span data-ttu-id="f9ff2-108">如果选择了以下安装选项之一：本机模式默认配置或 SharePoint 集成模式默认配置，则安装程序会配置最低设置。</span><span class="sxs-lookup"><span data-stu-id="f9ff2-108">Setup configures the minimum settings if you select either of the following installation options: Native mode default configuration or SharePoint integrated mode default configuration.</span></span> <span data-ttu-id="f9ff2-109">如果在“仅文件”模式下安装报表服务器（即通过安装向导中的 **“安装但不配置”** 选项），则只需要配置服务帐户。</span><span class="sxs-lookup"><span data-stu-id="f9ff2-109">If you installed the report server in files-only mode (this is the **Install but do not configure** option in the Installation wizard), only the service account is configured.</span></span> <span data-ttu-id="f9ff2-110">完成安装之后，必须配置 Web 服务 URL 和报表服务器数据库。</span><span class="sxs-lookup"><span data-stu-id="f9ff2-110">The Web service URL and report server database must be configured after Setup is finished.</span></span>  
  
 <span data-ttu-id="f9ff2-111">报表管理器是本机模式报表服务器的可选功能，但建议您配置报表管理器，以便授予用户访问报表服务器和管理报表服务器内容的权限。</span><span class="sxs-lookup"><span data-stu-id="f9ff2-111">Report Manager is an optional feature for a native mode report server, but it is recommended that you configure Report Manager so that you can grant user access to the report server and manage report server content.</span></span> <span data-ttu-id="f9ff2-112">如果在 SharePoint 集成模式下部署报表服务器，可使用 SharePoint 服务器的 Web 前端授予访问权限。</span><span class="sxs-lookup"><span data-stu-id="f9ff2-112">If you deploy a report server in SharePoint integrated mode, use the Web front-end of a SharePoint server to grant access.</span></span>  
  
 <span data-ttu-id="f9ff2-113">可以根据需要配置其他功能，例如报表服务器电子邮件和无人参与的执行帐户。</span><span class="sxs-lookup"><span data-stu-id="f9ff2-113">Additional features, such as report server e-mail and the unattended execution account, can be configured as needed.</span></span> <span data-ttu-id="f9ff2-114">有关详细信息，请参阅 [管理 Reporting Services 本机模式报表服务器](manage-a-reporting-services-native-mode-report-server.md)。</span><span class="sxs-lookup"><span data-stu-id="f9ff2-114">For more information, see [Manage a Reporting Services Native Mode Report Server](manage-a-reporting-services-native-mode-report-server.md).</span></span>  
  
 <span data-ttu-id="f9ff2-115">若要配置报表服务器，请使用 Reporting Services 配置工具。</span><span class="sxs-lookup"><span data-stu-id="f9ff2-115">To configure a report server, use the Reporting Services Configuration tool.</span></span>  
  
### <a name="to-minimally-configure-a-report-server-installation"></a><span data-ttu-id="f9ff2-116">对报表服务器安装进行最小配置</span><span class="sxs-lookup"><span data-stu-id="f9ff2-116">To minimally configure a report server installation</span></span>  
  
1.  <span data-ttu-id="f9ff2-117">启动 Reporting Services 配置管理器，然后连接到报表服务器实例。</span><span class="sxs-lookup"><span data-stu-id="f9ff2-117">Start the Reporting Services Configuration Manager and connect to the report server instance.</span></span> <span data-ttu-id="f9ff2-118">有关说明，请参阅 [Reporting Services Configuration Manager（本机模式）](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="f9ff2-118">For instructions, see [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="f9ff2-119">单击 **“Web 服务 URL”** ，打开用于配置报表服务器 URL 的页。</span><span class="sxs-lookup"><span data-stu-id="f9ff2-119">Click **Web Service URL** to open the page for configuring a URL for the report server.</span></span> <span data-ttu-id="f9ff2-120">有关如何定义 URL 的说明，请参阅[配置 URL（SSRS 配置管理器）](../install-windows/configure-a-url-ssrs-configuration-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="f9ff2-120">For instructions on how to define the URL, see [Configure a URL  &#40;SSRS Configuration Manager&#41;](../install-windows/configure-a-url-ssrs-configuration-manager.md).</span></span>  
  
3.  <span data-ttu-id="f9ff2-121">单击 **“数据库”** 创建报表服务器数据库。</span><span class="sxs-lookup"><span data-stu-id="f9ff2-121">Click **Database** to create the report server database.</span></span> <span data-ttu-id="f9ff2-122">有关指导，请参阅[创建本机模式报表服务器数据库（SSRS 配置管理器）](../install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md)。</span><span class="sxs-lookup"><span data-stu-id="f9ff2-122">For instructions, see [Create a Native Mode Report Server Database  &#40;SSRS Configuration Manager&#41;](../install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md).</span></span>  
  
4.  <span data-ttu-id="f9ff2-123">返回到 **“Web 服务 URL”** 页，单击该 URL 以验证其是否有效。</span><span class="sxs-lookup"><span data-stu-id="f9ff2-123">Go back to the **Web Service URL** page and click the URL to verify it works.</span></span>  
  
5.  <span data-ttu-id="f9ff2-124">按照“后续步骤”中的说明完成您的部署。</span><span class="sxs-lookup"><span data-stu-id="f9ff2-124">Follow the instructions in "Next Steps" to complete your deployment.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="f9ff2-125">后续步骤</span><span class="sxs-lookup"><span data-stu-id="f9ff2-125">Next Steps</span></span>  
 <span data-ttu-id="f9ff2-126">若要完成部署，应配置报表管理器或 SharePoint 集成。</span><span class="sxs-lookup"><span data-stu-id="f9ff2-126">To complete your deployment, you should configure Report Manager or SharePoint integration.</span></span> <span data-ttu-id="f9ff2-127">有关详细信息，请参阅[配置报表管理器（本机模式）](configure-web-portal.md)。</span><span class="sxs-lookup"><span data-stu-id="f9ff2-127">For more information, see [Configure Report Manager &#40;Native Mode&#41;](configure-web-portal.md).</span></span>  
  
 <span data-ttu-id="f9ff2-128">如果 Windows 防火墙已开启，配置为报表服务器使用的端口很可能已关闭。</span><span class="sxs-lookup"><span data-stu-id="f9ff2-128">If Windows Firewall is turned on, the port that the report server is configured to use is most likely closed.</span></span> <span data-ttu-id="f9ff2-129">表明端口可能已关闭的一个迹象是在尝试从远程客户端计算机打开报表管理器时出现空白页。</span><span class="sxs-lookup"><span data-stu-id="f9ff2-129">One indication that a port might be closed is a blank page when you attempt to open Report Manager from a remote client computer.</span></span> <span data-ttu-id="f9ff2-130">有关配置防火墙的信息，请参阅 [Configure a Firewall for Report Server Access](configure-a-firewall-for-report-server-access.md)。</span><span class="sxs-lookup"><span data-stu-id="f9ff2-130">For information on configuring the firewall, see [Configure a Firewall for Report Server Access](configure-a-firewall-for-report-server-access.md).</span></span>  
  
 <span data-ttu-id="f9ff2-131">如果使用的是 Windows Vista 或 Windows Server 2008，则可能需要执行其他步骤，才能在本地打开报表管理器。</span><span class="sxs-lookup"><span data-stu-id="f9ff2-131">If you are using Windows Vista or Windows Server 2008, additional steps are required before you can open Report Manager locally.</span></span> <span data-ttu-id="f9ff2-132">有关详细信息，请参阅 [为本地管理配置本机模式报表服务器 (SSRS)](configure-a-native-mode-report-server-for-local-administration-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="f9ff2-132">For more information, see [Configure a Native Mode Report Server for Local Administration &#40;SSRS&#41;](configure-a-native-mode-report-server-for-local-administration-ssrs.md).</span></span>  
  
 <span data-ttu-id="f9ff2-133">通过创建文件夹、上载项和运行报表来验证您的安装。</span><span class="sxs-lookup"><span data-stu-id="f9ff2-133">Verify your installation by creating folders, uploading items, and running reports.</span></span> <span data-ttu-id="f9ff2-134">按照 [验证 Reporting Services 安装](../install-windows/verify-a-reporting-services-installation.md) 中的说明来验证安装。</span><span class="sxs-lookup"><span data-stu-id="f9ff2-134">Follow the instructions in [Verify a Reporting Services Installation](../install-windows/verify-a-reporting-services-installation.md) to verify your installation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9ff2-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f9ff2-135">See Also</span></span>  
 <span data-ttu-id="f9ff2-136">[管理 Reporting Services 本机模式报表服务器](manage-a-reporting-services-native-mode-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="f9ff2-136">[Manage a Reporting Services Native Mode Report Server](manage-a-reporting-services-native-mode-report-server.md) </span></span>  
 <span data-ttu-id="f9ff2-137">[将防火墙配置为允许报表服务器访问](configure-a-firewall-for-report-server-access.md) </span><span class="sxs-lookup"><span data-stu-id="f9ff2-137">[Configure a Firewall for Report Server Access](configure-a-firewall-for-report-server-access.md) </span></span>  
 <span data-ttu-id="f9ff2-138">[配置本机模式报表服务器以进行本地管理 (SSRS)](configure-a-native-mode-report-server-for-local-administration-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f9ff2-138">[Configure a Native Mode Report Server for Local Administration &#40;SSRS&#41;](configure-a-native-mode-report-server-for-local-administration-ssrs.md) </span></span>  
 <span data-ttu-id="f9ff2-139">[配置报表服务器以进行远程管理](configure-a-report-server-for-remote-administration.md) </span><span class="sxs-lookup"><span data-stu-id="f9ff2-139">[Configure a Report Server for Remote Administration](configure-a-report-server-for-remote-administration.md) </span></span>  
 [<span data-ttu-id="f9ff2-140">Reporting Services Configuration Manager（本机模式）</span><span class="sxs-lookup"><span data-stu-id="f9ff2-140">Reporting Services Configuration Manager &#40;Native Mode&#41;</span></span>](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)  
  
  
