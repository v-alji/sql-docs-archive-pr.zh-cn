---
title: 管理 Reporting Services 本机模式报表服务器 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Reporting Services Configuration tool
- configuration options [Reporting Services]
- report servers [Reporting Services], configuring
ms.assetid: 6ca03a09-d6a8-4c93-ba12-1c99dcbfb618
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0d44a9329074a20c04f878c055674ea563b297f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588276"
---
# <a name="manage-a-reporting-services-native-mode-report-server"></a><span data-ttu-id="2bc00-102">管理 Reporting Services 本机模式报表服务器</span><span class="sxs-lookup"><span data-stu-id="2bc00-102">Manage a Reporting Services Native Mode Report Server</span></span>
  <span data-ttu-id="2bc00-103">本节包含使用 Reporting Services 配置管理器配置本机模式报表服务器实例的过程。</span><span class="sxs-lookup"><span data-stu-id="2bc00-103">This section contains procedures for configuring a native mode report server instance using the Reporting Services Configuration Manager.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2bc00-104">本节内容</span><span class="sxs-lookup"><span data-stu-id="2bc00-104">In This Section</span></span>  
 <span data-ttu-id="2bc00-105">本节中的主题进行了适当分类，以便于您轻松找到所需说明。</span><span class="sxs-lookup"><span data-stu-id="2bc00-105">The topics in this section are organized into categories so that you can more easily find the instructions you want.</span></span> <span data-ttu-id="2bc00-106">第一部分包含有关本机模式的报表服务器的基本配置任务主题。</span><span class="sxs-lookup"><span data-stu-id="2bc00-106">The first section contains topics for basic configuration tasks for a native mode report server.</span></span> <span data-ttu-id="2bc00-107">第二部分包含高级配置主题。</span><span class="sxs-lookup"><span data-stu-id="2bc00-107">The second section contains advanced configuration topics.</span></span> <span data-ttu-id="2bc00-108">第三部分包含有关将报表服务器配置为以 SharePoint 集成模式运行的主题。</span><span class="sxs-lookup"><span data-stu-id="2bc00-108">The third section contains topics for configuring a report server to run in SharePoint integrated mode.</span></span>  
  
### <a name="basic-configuration"></a><span data-ttu-id="2bc00-109">基本配置</span><span class="sxs-lookup"><span data-stu-id="2bc00-109">Basic Configuration</span></span>  
 [<span data-ttu-id="2bc00-110">Reporting Services Configuration Manager（本机模式）</span><span class="sxs-lookup"><span data-stu-id="2bc00-110">Reporting Services Configuration Manager &#40;Native Mode&#41;</span></span>](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)  
 <span data-ttu-id="2bc00-111">提供启动 Reporting Services 配置工具的步骤。</span><span class="sxs-lookup"><span data-stu-id="2bc00-111">Provides steps for starting the Reporting Services Configuration tool.</span></span>  
  
 [<span data-ttu-id="2bc00-112">配置服务帐户（SSRS 配置管理器）</span><span class="sxs-lookup"><span data-stu-id="2bc00-112">Configure a Service Account &#40;SSRS Configuration Manager&#41;</span></span>](../../sql-server/install/configure-a-service-account-ssrs-configuration-manager.md)  
 <span data-ttu-id="2bc00-113">说明如何为报表服务器服务指定帐户和密码信息。</span><span class="sxs-lookup"><span data-stu-id="2bc00-113">Explains how to specify account and password information for the Report Server service.</span></span>  
  
 [<span data-ttu-id="2bc00-114">为报表服务器注册服务主体名称 (SPN)</span><span class="sxs-lookup"><span data-stu-id="2bc00-114">Register a Service Principal Name &#40;SPN&#41; for a Report Server</span></span>](register-a-service-principal-name-spn-for-a-report-server.md)  
 <span data-ttu-id="2bc00-115">说明如何为在使用 Kerberos 身份验证的网络上的域用户帐户下运行的报表服务器手动注册 SPN。</span><span class="sxs-lookup"><span data-stu-id="2bc00-115">Explains how to manually register an SPN for a report server that runs under a domain user account on a network that uses Kerberos authentication.</span></span>  
  
 [<span data-ttu-id="2bc00-116">配置 URL（SSRS 配置管理器）</span><span class="sxs-lookup"><span data-stu-id="2bc00-116">Configure a URL  &#40;SSRS Configuration Manager&#41;</span></span>](../install-windows/configure-a-url-ssrs-configuration-manager.md)  
 <span data-ttu-id="2bc00-117">说明如何建立一个或多个用于访问报表服务器 Web 服务和报表管理器的 URL。</span><span class="sxs-lookup"><span data-stu-id="2bc00-117">Explains how to establish one or more URLs used to access the Report Server Web service and Report Manager.</span></span>  
  
 [<span data-ttu-id="2bc00-118">创建本机模式报表服务器数据库（SSRS 配置管理器）</span><span class="sxs-lookup"><span data-stu-id="2bc00-118">Create a Native Mode Report Server Database  &#40;SSRS Configuration Manager&#41;</span></span>](../install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md)  
 <span data-ttu-id="2bc00-119">提供创建报表服务器数据库的步骤。</span><span class="sxs-lookup"><span data-stu-id="2bc00-119">Provides steps for creating a report server database.</span></span> <span data-ttu-id="2bc00-120">此步骤是部署 Reporting Services 安装所必需的步骤。</span><span class="sxs-lookup"><span data-stu-id="2bc00-120">This step is required for deploying a Reporting Services installation.</span></span>  
  
### <a name="advanced-or-optional-configuration"></a><span data-ttu-id="2bc00-121">高级或可选配置</span><span class="sxs-lookup"><span data-stu-id="2bc00-121">Advanced or Optional Configuration</span></span>  
 [<span data-ttu-id="2bc00-122">配置本机模式报表服务器扩展部署（SSRS 配置管理器）</span><span class="sxs-lookup"><span data-stu-id="2bc00-122">Configure a Native Mode Report Server Scale-Out Deployment &#40;SSRS Configuration Manager&#41;</span></span>](../install-windows/configure-a-native-mode-report-server-scale-out-deployment.md)  
 <span data-ttu-id="2bc00-123">提供配置多个报表服务器以共享报表服务器数据库的步骤。</span><span class="sxs-lookup"><span data-stu-id="2bc00-123">Provides steps for configuring multiple report servers to share a report server database.</span></span>  
  
 [<span data-ttu-id="2bc00-124">配置报表服务器，以便 &#40;SSRS Configuration Manager 发送电子邮件&#41;</span><span class="sxs-lookup"><span data-stu-id="2bc00-124">Configure a Report Server for E-Mail Delivery &#40;SSRS Configuration Manager&#41;</span></span>](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)  
 <span data-ttu-id="2bc00-125">提供有关配置报表服务器以进行电子邮件分发的步骤。</span><span class="sxs-lookup"><span data-stu-id="2bc00-125">Provides steps for configuring a report server for e-mail distribution.</span></span>  
  
 [<span data-ttu-id="2bc00-126">将防火墙配置为允许报表服务器访问</span><span class="sxs-lookup"><span data-stu-id="2bc00-126">Configure a Firewall for Report Server Access</span></span>](configure-a-firewall-for-report-server-access.md)  
 <span data-ttu-id="2bc00-127">说明如何打开用于报表服务器的入站请求和出站响应的端口。</span><span class="sxs-lookup"><span data-stu-id="2bc00-127">Explains how to open ports used for inbound requests and outbound responses from a report server.</span></span>  
  
 [<span data-ttu-id="2bc00-128">为本地管理配置本机模式报表服务器 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="2bc00-128">Configure a Native Mode Report Server for Local Administration &#40;SSRS&#41;</span></span>](configure-a-native-mode-report-server-for-local-administration-ssrs.md)  
 <span data-ttu-id="2bc00-129">描述使用 http://localhost 连接到报表管理器或报表服务器所需的其他步骤。</span><span class="sxs-lookup"><span data-stu-id="2bc00-129">Describes additional steps required to connect to Report Manager or a report server using http://localhost.</span></span>  
  
 [<span data-ttu-id="2bc00-130">配置报表服务器以进行远程管理</span><span class="sxs-lookup"><span data-stu-id="2bc00-130">Configure a Report Server for Remote Administration</span></span>](configure-a-report-server-for-remote-administration.md)  
 <span data-ttu-id="2bc00-131">说明如何配置远程报表服务器实例以便可以从其他计算机上连接和配置它。</span><span class="sxs-lookup"><span data-stu-id="2bc00-131">Explains how to configure a remote report server instance so that you can connect to and configure it from a different computer.</span></span>  
  
 [<span data-ttu-id="2bc00-132">打开或关闭 Reporting Services 功能</span><span class="sxs-lookup"><span data-stu-id="2bc00-132">Turn Reporting Services Features On or Off</span></span>](turn-reporting-services-features-on-or-off.md)  
 <span data-ttu-id="2bc00-133">说明如何删除 Reporting Services 安装中不使用的功能。</span><span class="sxs-lookup"><span data-stu-id="2bc00-133">Explains how to remove unused features in a Reporting Services installation.</span></span>  
  
 [<span data-ttu-id="2bc00-134">启用远程错误 (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="2bc00-134">Enable Remote Errors &#40;Reporting Services&#41;</span></span>](enable-remote-errors-reporting-services.md)  
 <span data-ttu-id="2bc00-135">说明如何将报表服务器上的服务器属性设置为返回有关出现在远程服务器上的错误条件的其他信息。</span><span class="sxs-lookup"><span data-stu-id="2bc00-135">Explains how to set server properties on a report server to return additional information about error conditions that occur on remote servers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bc00-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2bc00-136">See Also</span></span>  
 <span data-ttu-id="2bc00-137">[配置和管理报表服务器（SSRS 本机模式）](configure-and-administer-a-report-server-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="2bc00-137">[Configure and Administer a Report Server &#40;SSRS Native Mode&#41;](configure-and-administer-a-report-server-ssrs-native-mode.md) </span></span>  
 [<span data-ttu-id="2bc00-138">配置和管理报表服务器（Reporting Services SharePoint 模式）</span><span class="sxs-lookup"><span data-stu-id="2bc00-138">Configuration and Administration of a Report Server &#40;Reporting Services SharePoint Mode&#41;</span></span>](../configure-administer-report-server-reporting-services-sharepoint-mode.md)  
  
  
