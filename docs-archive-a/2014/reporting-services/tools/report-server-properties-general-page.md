---
title: 服务器属性（“常规”页）| Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.serverproperties.general.f1
ms.assetid: 23537d52-4356-450f-a671-5921cef2431f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 66199e35c180790cba5120cb839be67e43052be6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694251"
---
# <a name="server-properties-general-page"></a><span data-ttu-id="7b1eb-102">服务器属性（“常规”页）</span><span class="sxs-lookup"><span data-stu-id="7b1eb-102">Server Properties (General Page)</span></span>
  <span data-ttu-id="7b1eb-103">使用此页可以查看或修改报表管理器中所使用的标题，启用或禁用“我的报表”，为“我的报表”安全性选择角色定义以及启用或禁用客户端打印控件。</span><span class="sxs-lookup"><span data-stu-id="7b1eb-103">Use this page to view or modify the title used in Report Manager, enable or disable My Reports, select a role definition for My Reports security, and enable or disable the client print control.</span></span>  
  
 <span data-ttu-id="7b1eb-104">若要打开此页，请启动 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，连接到 Report Server 实例，右键单击 Report Server 名称，然后选择 "**属性**"。</span><span class="sxs-lookup"><span data-stu-id="7b1eb-104">To open this page, start [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to a report server instance, right-click the report server name, and then select **Properties**.</span></span>  
  
 <span data-ttu-id="7b1eb-105">服务器模式决定可以设置哪些服务器属性。</span><span class="sxs-lookup"><span data-stu-id="7b1eb-105">The server mode determines which server properties you can set.</span></span> <span data-ttu-id="7b1eb-106">如果要管理配置为 SharePoint 集成模式的报表服务器，则不能启用“我的报表”，也不能为报表管理器设置应用程序标题。</span><span class="sxs-lookup"><span data-stu-id="7b1eb-106">If you are managing a report server that is configured for SharePoint integrated mode, you cannot enable My Reports or set the application title for Report Manager.</span></span>  
  
## <a name="options"></a><span data-ttu-id="7b1eb-107">选项</span><span class="sxs-lookup"><span data-stu-id="7b1eb-107">Options</span></span>  
 <span data-ttu-id="7b1eb-108">**名称**</span><span class="sxs-lookup"><span data-stu-id="7b1eb-108">**Name**</span></span>  
 <span data-ttu-id="7b1eb-109">键入将显示在报表管理器中的应用程序名称。</span><span class="sxs-lookup"><span data-stu-id="7b1eb-109">Type an application name that appears in Report Manager.</span></span> <span data-ttu-id="7b1eb-110">此值默认为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="7b1eb-110">By default, this value is [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="7b1eb-111">指定的名称仅显示在报表管理器中。</span><span class="sxs-lookup"><span data-stu-id="7b1eb-111">The name that you specify appears only in Report Manager.</span></span>  
  
 <span data-ttu-id="7b1eb-112">**Version**</span><span class="sxs-lookup"><span data-stu-id="7b1eb-112">**Version**</span></span>  
 <span data-ttu-id="7b1eb-113">此属性是只读的。</span><span class="sxs-lookup"><span data-stu-id="7b1eb-113">This property is read-only.</span></span> <span data-ttu-id="7b1eb-114">指定正在使用的的版本 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="7b1eb-114">Specifies the version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] that you are using.</span></span>  
  
 <span data-ttu-id="7b1eb-115">**版本**</span><span class="sxs-lookup"><span data-stu-id="7b1eb-115">**Edition**</span></span>  
 <span data-ttu-id="7b1eb-116">此属性为只读。</span><span class="sxs-lookup"><span data-stu-id="7b1eb-116">This property is read-only.</span></span> <span data-ttu-id="7b1eb-117">指定当前报表服务器实例。</span><span class="sxs-lookup"><span data-stu-id="7b1eb-117">Specifies the current report server instance.</span></span> <span data-ttu-id="7b1eb-118">并非 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的每个版本都提供报表管理器。</span><span class="sxs-lookup"><span data-stu-id="7b1eb-118">Report Manager is not available in every edition of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="7b1eb-119">有关各个版本支持的功能列表 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，请参阅 SQL Server 2014 的各个[版本支持的功能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="7b1eb-119">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
 <span data-ttu-id="7b1eb-120">**身份验证模式**</span><span class="sxs-lookup"><span data-stu-id="7b1eb-120">**Authentication Mode**</span></span>  
 <span data-ttu-id="7b1eb-121">此属性是只读的。</span><span class="sxs-lookup"><span data-stu-id="7b1eb-121">This property is read-only.</span></span> <span data-ttu-id="7b1eb-122">它标识报表服务器实例所接受的身份验证请求的类型。</span><span class="sxs-lookup"><span data-stu-id="7b1eb-122">It identifies the types of authentication requests accepted by the report server instance.</span></span> <span data-ttu-id="7b1eb-123">若要更改身份验证模式，必须编辑 RSReportServer.config 文件。</span><span class="sxs-lookup"><span data-stu-id="7b1eb-123">To change the authentication mode, you must edit the RSReportServer.config file.</span></span> <span data-ttu-id="7b1eb-124">有关详细信息，请参阅 [Authentication with the Report Server](../security/authentication-with-the-report-server.md)。</span><span class="sxs-lookup"><span data-stu-id="7b1eb-124">For more information, see [Authentication with the Report Server](../security/authentication-with-the-report-server.md).</span></span>  
  
 <span data-ttu-id="7b1eb-125">**URL**</span><span class="sxs-lookup"><span data-stu-id="7b1eb-125">**URL**</span></span>  
 <span data-ttu-id="7b1eb-126">此属性是只读的。</span><span class="sxs-lookup"><span data-stu-id="7b1eb-126">This property is read-only.</span></span> <span data-ttu-id="7b1eb-127">指定报表服务器 Web 服务的 URL。</span><span class="sxs-lookup"><span data-stu-id="7b1eb-127">Specifies the URL to the Report Server Web service.</span></span> <span data-ttu-id="7b1eb-128">可在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 配置工具中指定此值。</span><span class="sxs-lookup"><span data-stu-id="7b1eb-128">This value is specified in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool.</span></span> <span data-ttu-id="7b1eb-129">有关详细信息，请参阅[配置 URL（SSRS 配置管理器）](../install-windows/configure-a-url-ssrs-configuration-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="7b1eb-129">For more information, see [Configure a URL  &#40;SSRS Configuration Manager&#41;](../install-windows/configure-a-url-ssrs-configuration-manager.md).</span></span>  
  
 <span data-ttu-id="7b1eb-130">**为每个用户启用“我的报表”文件夹**</span><span class="sxs-lookup"><span data-stu-id="7b1eb-130">**Enable a My Reports folder for each user**</span></span>  
 <span data-ttu-id="7b1eb-131">使“我的报表”可供用户使用。</span><span class="sxs-lookup"><span data-stu-id="7b1eb-131">Make My Reports available to users.</span></span> <span data-ttu-id="7b1eb-132">此选项仅适用于处于本机模式的报表服务器。</span><span class="sxs-lookup"><span data-stu-id="7b1eb-132">This option is only available for native mode report servers.</span></span>  
  
 <span data-ttu-id="7b1eb-133">**选择应用于每个“我的报表”文件夹的角色**</span><span class="sxs-lookup"><span data-stu-id="7b1eb-133">**Select the role to apply to each My Reports folder**</span></span>  
 <span data-ttu-id="7b1eb-134">指定要用于“我的报表”安全性的角色定义。</span><span class="sxs-lookup"><span data-stu-id="7b1eb-134">Specify a role definition to use for My Reports security.</span></span> <span data-ttu-id="7b1eb-135">角色定义标识在每个“我的报表”文件夹中都支持的任务集。</span><span class="sxs-lookup"><span data-stu-id="7b1eb-135">The role definition identifies the set of tasks that are supported in each My Reports folder.</span></span>  
  
 <span data-ttu-id="7b1eb-136">**允许下载 ActiveX 客户端打印控件**</span><span class="sxs-lookup"><span data-stu-id="7b1eb-136">**Enable download for the ActiveX client print control**</span></span>  
 <span data-ttu-id="7b1eb-137">设置 `EnableClientPrinting` 报表服务器系统属性。</span><span class="sxs-lookup"><span data-stu-id="7b1eb-137">Sets the `EnableClientPrinting` report server system property.</span></span> <span data-ttu-id="7b1eb-138">如果启用客户端打印，则具有本地管理员权限的用户可以选择下载已签名的 ActiveX 控件来打印 HTML 报表。</span><span class="sxs-lookup"><span data-stu-id="7b1eb-138">If you enable client printing, users who have local administrator permissions have the option of downloading a signed ActiveX control for printing HTML reports.</span></span> <span data-ttu-id="7b1eb-139">有关详细信息，请参阅 [启用和禁用 Reporting Services 的客户端打印](../report-server/enable-and-disable-client-side-printing-for-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="7b1eb-139">For more information, see [Enable and Disable Client-Side Printing for Reporting Services](../report-server/enable-and-disable-client-side-printing-for-reporting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b1eb-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7b1eb-140">See Also</span></span>  
 <span data-ttu-id="7b1eb-141">[设置报表服务器属性 &#40;Management Studio&#41;](set-report-server-properties-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="7b1eb-141">[Set Report Server Properties &#40;Management Studio&#41;](set-report-server-properties-management-studio.md) </span></span>  
 <span data-ttu-id="7b1eb-142">[在 Management Studio 中连接到报表服务器](connect-to-a-report-server-in-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="7b1eb-142">[Connect to a Report Server in Management Studio](connect-to-a-report-server-in-management-studio.md) </span></span>  
 <span data-ttu-id="7b1eb-143">[启用和禁用我的报表](../report-server/enable-and-disable-my-reports.md) </span><span class="sxs-lookup"><span data-stu-id="7b1eb-143">[Enable and Disable My Reports](../report-server/enable-and-disable-my-reports.md) </span></span>  
 <span data-ttu-id="7b1eb-144">[Management Studio F1 帮助中的报表服务器](report-server-in-management-studio-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="7b1eb-144">[Report Server in Management Studio F1 Help](report-server-in-management-studio-f1-help.md) </span></span>  
 [<span data-ttu-id="7b1eb-145">保护“我的报表”</span><span class="sxs-lookup"><span data-stu-id="7b1eb-145">Secure My Reports</span></span>](../security/secure-my-reports.md)  
  
  
