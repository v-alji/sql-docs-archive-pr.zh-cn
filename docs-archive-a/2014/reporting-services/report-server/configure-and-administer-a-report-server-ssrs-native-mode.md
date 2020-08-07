---
title: 配置和管理报表服务器（SSRS 本机模式）| Microsoft Docs
ms.custom: ''
ms.date: 08/10/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Reporting Services, components
- deploying [Reporting Services], component options
- report servers [Reporting Services], component options
- configuration options [Reporting Services]
- administering Reporting Services
- components [Reporting Services], configuring
- configuring servers [Reporting Services]
ms.assetid: cfec012b-56f1-4346-9814-247acf22351c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5164fd2f9170cb092a45394f64f06d7622253f2b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588296"
---
# <a name="configure-and-administer-a-report-server-ssrs-native-mode"></a><span data-ttu-id="29d6e-102">配置和管理报表服务器（SSRS 本机模式）</span><span class="sxs-lookup"><span data-stu-id="29d6e-102">Configure and Administer a Report Server (SSRS Native Mode)</span></span>
  <span data-ttu-id="29d6e-103">本主题总结了可用于配置 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]的方法。</span><span class="sxs-lookup"><span data-stu-id="29d6e-103">This topic summarizes the approaches that you can use to configure [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="29d6e-104">它还包含一个主题列表，其中所列的主题说明了如何配置特定的组件、功能或服务器功能。</span><span class="sxs-lookup"><span data-stu-id="29d6e-104">It also includes a list of topics that explain how to configure specific components, features, or server capabilities.</span></span> <span data-ttu-id="29d6e-105">若要配置 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]，您可以：</span><span class="sxs-lookup"><span data-stu-id="29d6e-105">To configure [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], you can:</span></span>  
  
-   <span data-ttu-id="29d6e-106">使用 Reporting Services 配置管理器。</span><span class="sxs-lookup"><span data-stu-id="29d6e-106">Use the Reporting Services Configuration Manager.</span></span> <span data-ttu-id="29d6e-107">本节中的许多主题均包含有关如何通过该工具配置特定功能的信息。</span><span class="sxs-lookup"><span data-stu-id="29d6e-107">Many of the topics in this section contain information about how to configure specific features through this tool.</span></span>  
  
-   <span data-ttu-id="29d6e-108">使用 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 可自定义服务器属性，启用“我的报表”，启用跟踪日志和设置站点范围的默认值。</span><span class="sxs-lookup"><span data-stu-id="29d6e-108">Use [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] to customize server properties, enable My Reports, enable trace logs, and set site-wide defaults.</span></span> <span data-ttu-id="29d6e-109">有关站点设置的详细信息，请参阅 Management studio 的 [Reporting Services 报表服务器（本机模式）](reporting-services-report-server-native-mode.md) 。</span><span class="sxs-lookup"><span data-stu-id="29d6e-109">For more information about site settings, see [Reporting Services Report Server &#40;Native Mode&#41;](reporting-services-report-server-native-mode.md) for Management Studio.</span></span> <span data-ttu-id="29d6e-110">请注意，可以创建并运行通过编程方式设置服务器属性的脚本。</span><span class="sxs-lookup"><span data-stu-id="29d6e-110">Note that you can create and run script that sets server properties programmatically.</span></span> <span data-ttu-id="29d6e-111">有关详细信息，请参阅 [为部署和管理任务编写脚本](../tools/script-deployment-and-administrative-tasks.md) 和 [报表服务器系统属性](../report-server-web-service/net-framework/reporting-services-properties-report-server-system-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="29d6e-111">For more information, see [Script Deployment and Administrative Tasks](../tools/script-deployment-and-administrative-tasks.md) and [Report Server System Properties](../report-server-web-service/net-framework/reporting-services-properties-report-server-system-properties.md).</span></span>  
  
-   <span data-ttu-id="29d6e-112">使用报表管理器授予访问报表服务器的权限。</span><span class="sxs-lookup"><span data-stu-id="29d6e-112">Use Report Manager to grant permissions to access the report server.</span></span> <span data-ttu-id="29d6e-113">权限通过为每个用户帐户或组帐户定义的角色分配进行传送。</span><span class="sxs-lookup"><span data-stu-id="29d6e-113">Permissions are conveyed through role assignments that you define for each user or group account.</span></span> <span data-ttu-id="29d6e-114">有关详细信息，请参阅[角色和权限 (Reporting Services)](../security/roles-and-permissions-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="29d6e-114">For more information, see [Roles and Permissions &#40;Reporting Services&#41;](../security/roles-and-permissions-reporting-services.md).</span></span>  
  
-   <span data-ttu-id="29d6e-115">也可以修改配置文件以更改应用程序设置。</span><span class="sxs-lookup"><span data-stu-id="29d6e-115">Optionally, modify configuration files to change application settings.</span></span> <span data-ttu-id="29d6e-116">有关每个文件的详细信息以及这些文件的修改指南，请参阅 [Reporting Services Configuration Files](reporting-services-configuration-files.md)。</span><span class="sxs-lookup"><span data-stu-id="29d6e-116">For more information about each file and guidelines for modifying them, see [Reporting Services Configuration Files](reporting-services-configuration-files.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="29d6e-117">本节内容</span><span class="sxs-lookup"><span data-stu-id="29d6e-117">In This Section</span></span>  
 [<span data-ttu-id="29d6e-118">配置报表服务器 URL（SSRS 配置管理器）</span><span class="sxs-lookup"><span data-stu-id="29d6e-118">Configure Report Server URLs  &#40;SSRS Configuration Manager&#41;</span></span>](../install-windows/configure-report-server-urls-ssrs-configuration-manager.md)  
 <span data-ttu-id="29d6e-119">介绍如何定义用来访问报表服务器和报表管理器的 URL。</span><span class="sxs-lookup"><span data-stu-id="29d6e-119">Describes how to define the URLs used to access the report server and Report Manager.</span></span>  
  
 [<span data-ttu-id="29d6e-120">配置报表服务器服务帐户（SSRS 配置管理器）</span><span class="sxs-lookup"><span data-stu-id="29d6e-120">Configure the Report Server Service Account &#40;SSRS Configuration Manager&#41;</span></span>](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)  
 <span data-ttu-id="29d6e-121">为如何修改服务帐户和密码提供建议和步骤。</span><span class="sxs-lookup"><span data-stu-id="29d6e-121">Provides recommendations and steps on how to modify service account and password.</span></span>  
  
 [<span data-ttu-id="29d6e-122">创建报表服务器数据库（SSRS 配置管理器）</span><span class="sxs-lookup"><span data-stu-id="29d6e-122">Create a Report Server Database  &#40;SSRS Configuration Manager&#41;</span></span>](../../sql-server/install/create-a-report-server-database-ssrs-configuration-manager.md)  
 <span data-ttu-id="29d6e-123">介绍如何创建存储服务器元数据和对象所必需的报表服务器数据库。</span><span class="sxs-lookup"><span data-stu-id="29d6e-123">Describes how to create a report server database, required for storing server metadata and objects.</span></span>  
  
 [<span data-ttu-id="29d6e-124">配置报表服务器数据库连接（SSRS 配置管理器）</span><span class="sxs-lookup"><span data-stu-id="29d6e-124">Configure a Report Server Database Connection  &#40;SSRS Configuration Manager&#41;</span></span>](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)  
 <span data-ttu-id="29d6e-125">介绍如何修改报表服务器用于连接到报表服务器数据库的连接字符串。</span><span class="sxs-lookup"><span data-stu-id="29d6e-125">Describes how to modify the connection string used by the report server to connect to the report server database.</span></span>  
  
 [<span data-ttu-id="29d6e-126">配置报表服务器，以便 &#40;SSRS Configuration Manager 发送电子邮件&#41;</span><span class="sxs-lookup"><span data-stu-id="29d6e-126">Configure a Report Server for E-Mail Delivery &#40;SSRS Configuration Manager&#41;</span></span>](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)  
 <span data-ttu-id="29d6e-127">介绍如何配置报表服务器，以便通过电子邮件来分发报表。</span><span class="sxs-lookup"><span data-stu-id="29d6e-127">Describes how to configure a report server to support e-mail report distribution.</span></span>  
  
 [<span data-ttu-id="29d6e-128">配置无人参与的执行帐户（SSRS 配置管理器）</span><span class="sxs-lookup"><span data-stu-id="29d6e-128">Configure the Unattended Execution Account &#40;SSRS Configuration Manager&#41;</span></span>](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)  
 <span data-ttu-id="29d6e-129">介绍如何配置用户帐户以便以无人参与的方式处理报表。</span><span class="sxs-lookup"><span data-stu-id="29d6e-129">Describes how to configure a user account to process reports in unattended mode.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29d6e-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="29d6e-130">See Also</span></span>  
 <span data-ttu-id="29d6e-131">[配置报表生成器访问](configure-report-builder-access.md) </span><span class="sxs-lookup"><span data-stu-id="29d6e-131">[Configure Report Builder Access](configure-report-builder-access.md) </span></span>  
 <span data-ttu-id="29d6e-132">[Reporting Services 配置文件](reporting-services-configuration-files.md) </span><span class="sxs-lookup"><span data-stu-id="29d6e-132">[Reporting Services Configuration Files](reporting-services-configuration-files.md) </span></span>  
 <span data-ttu-id="29d6e-133">[Reporting Services Configuration Manager（本机模式）](../../sql-server/install/reporting-services-configuration-manager-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="29d6e-133">[Reporting Services Configuration Manager &#40;Native Mode&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md) </span></span>  
 <span data-ttu-id="29d6e-134">[Reporting Services 安全和保护](../security/reporting-services-security-and-protection.md) </span><span class="sxs-lookup"><span data-stu-id="29d6e-134">[Reporting Services Security and Protection](../security/reporting-services-security-and-protection.md) </span></span>  
 [<span data-ttu-id="29d6e-135">Reporting Services 报表服务器（本机模式）</span><span class="sxs-lookup"><span data-stu-id="29d6e-135">Reporting Services Report Server &#40;Native Mode&#41;</span></span>](reporting-services-report-server-native-mode.md)  
  
  
