---
title: 高级多网站配置 (SSRS 本机模式) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.advancedmultiplewebsiteconfig.F1
ms.assetid: af4ede43-2225-45b5-ae7e-9202411551ba
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 65061eae928227f16b1088a0fb5448b19093cb1d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586237"
---
# <a name="advanced-multiple-web-site-configuration-ssrs-native-mode"></a><span data-ttu-id="1ce8a-102">高级多网站配置（SSRS 本机模式）</span><span class="sxs-lookup"><span data-stu-id="1ce8a-102">Advanced Multiple Web Site Configuration (SSRS Native Mode)</span></span>
  <span data-ttu-id="1ce8a-103">使用此对话框可创建和管理用于访问报表服务器或报表管理器的 URL。</span><span class="sxs-lookup"><span data-stu-id="1ce8a-103">Use this dialog box to create and manage the URLs used to access a report server or Report Manager.</span></span> <span data-ttu-id="1ce8a-104">**“高级多网站配置”** 对话框用于创建附加 URL 和包含主机标头名称的自定义 URL，或者用于指定 IPv4 或 IPv6 格式的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="1ce8a-104">The **Advanced Multiple Web Site Configuration** dialog box is used to create additional URLs, custom URLs that include a host header name, or specify an IP address in the IPv4 or IPv6 format.</span></span>  
  
 [!INCLUDE[applies](../../includes/applies-md.md)]<span data-ttu-id="1ce8a-105">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]本机模式。</span><span class="sxs-lookup"><span data-stu-id="1ce8a-105">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode.</span></span>  
  
 <span data-ttu-id="1ce8a-106">如果要配置多种不同的方式来访问报表服务器，则创建多个 URL 非常有用。</span><span class="sxs-lookup"><span data-stu-id="1ce8a-106">Creating multiple URLs is useful if you want to configure different ways to access a report server.</span></span> <span data-ttu-id="1ce8a-107">例如，通过 Intranet 和 Extranet 连接访问报表服务器通常对于每种类型的连接需要具有不同的 URL。</span><span class="sxs-lookup"><span data-stu-id="1ce8a-107">For example, report server access over intranet and extranet connection typically requires that you have different URLs for each type of connection.</span></span>  
  
 <span data-ttu-id="1ce8a-108">若要打开 **“高级多网站配置”** 对话框，请单击 **配置管理器中的** “Web 服务 URL” **页或** “报表管理器 URL” **页上的** “高级” [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="1ce8a-108">To open the **Advanced Multiple Web Site Configuration** dialog box, click **Advanced** on the **Web Service URL** or the **Report Manager URL** page in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="1ce8a-109">**“高级多网站配置”** 对话框打开后，可以单击 **“添加”** 或 **“编辑”** 来定义新的 URL，或者修改或删除现有的 URL。</span><span class="sxs-lookup"><span data-stu-id="1ce8a-109">After the **Advanced Multiple Web Site Configuration** dialog box is open, you can click **Add** or **Edit** to define new URLs or modify or delete existing URLs.</span></span>  
  
 <span data-ttu-id="1ce8a-110">\*\*\*\* 单击“确定”以保存你的更改。</span><span class="sxs-lookup"><span data-stu-id="1ce8a-110">Click **OK** to save your changes.</span></span> <span data-ttu-id="1ce8a-111">如果添加或删除 URL 后，没有先单击 **“确定”** 就关闭了对话框，所做的更改将丢失。</span><span class="sxs-lookup"><span data-stu-id="1ce8a-111">If you add or remove URLs, but then close the dialog box without first clicking **OK**, your changes will be lost.</span></span>  
  
## <a name="options"></a><span data-ttu-id="1ce8a-112">选项</span><span class="sxs-lookup"><span data-stu-id="1ce8a-112">Options</span></span>  
 <span data-ttu-id="1ce8a-113">**IP 地址**</span><span class="sxs-lookup"><span data-stu-id="1ce8a-113">**IP Address**</span></span>  
 <span data-ttu-id="1ce8a-114">标识 TCP/IP 网络上的报表服务器计算机。</span><span class="sxs-lookup"><span data-stu-id="1ce8a-114">Identifies the report server computer on a TCP/IP network.</span></span> <span data-ttu-id="1ce8a-115">有效值包括：</span><span class="sxs-lookup"><span data-stu-id="1ce8a-115">Valid values include:</span></span>  
  
-   <span data-ttu-id="1ce8a-116">**“所有已分配的”** 指定分配给计算机的任何 IP 地址均可用在指向报表服务器应用程序的 URL 中。</span><span class="sxs-lookup"><span data-stu-id="1ce8a-116">**All Assigned** specifies that any of the IP addresses that are assigned to the computer can be used in a URL that points to a report server application.</span></span> <span data-ttu-id="1ce8a-117">此值还包含友好主机名（如计算机名），域名服务器可将该主机名解析为分配给该计算机的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="1ce8a-117">This value also encompasses friendly host names (such as computer names) that can be resolved by a domain name server to an IP address that is assigned to the computer.</span></span> <span data-ttu-id="1ce8a-118">此为 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] URL 的默认值。</span><span class="sxs-lookup"><span data-stu-id="1ce8a-118">This is the default value for a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] URL.</span></span>  
  
-   <span data-ttu-id="1ce8a-119">**“所有未分配的”** 指定报表服务器将接受任何未完全匹配 IP 地址或主机名的请求。</span><span class="sxs-lookup"><span data-stu-id="1ce8a-119">**All Unassigned** specifies that the report server will accept any request that does not have an exact match for the IP address or host name.</span></span> <span data-ttu-id="1ce8a-120">如果其他 Web 应用程序已在使用此值，请不要再使用它。</span><span class="sxs-lookup"><span data-stu-id="1ce8a-120">Do not use this value if another Web application is already using it.</span></span> <span data-ttu-id="1ce8a-121">如果仍使用此值，将中断其他应用程序的服务。</span><span class="sxs-lookup"><span data-stu-id="1ce8a-121">If you do so, you will disrupt service for the other application.</span></span>  
  
-   <span data-ttu-id="1ce8a-122">**127.0.0.1** 用于访问本地主机。</span><span class="sxs-lookup"><span data-stu-id="1ce8a-122">**127.0.0.1** is used to access to localhost.</span></span> <span data-ttu-id="1ce8a-123">它支持对报表服务器计算机进行本地管理。</span><span class="sxs-lookup"><span data-stu-id="1ce8a-123">It supports local administration on the report server computer.</span></span> <span data-ttu-id="1ce8a-124">如果仅选择此值，则只有在本地登录到报表服务器计算机的用户可以访问应用程序。</span><span class="sxs-lookup"><span data-stu-id="1ce8a-124">If you select only this value, only users who are logged on locally to the report server computer will have access the application.</span></span>  
  
-   <span data-ttu-id="1ce8a-125">*Nnn.nnn.nnn.nnn* 是计算机网络适配器的 IPv4 地址。</span><span class="sxs-lookup"><span data-stu-id="1ce8a-125">*Nnn.nnn.nnn.nnn* is the IPv4 address of a network adapter card on your computer.</span></span> <span data-ttu-id="1ce8a-126">如果你的网络使用 IPv6 寻址，则 IP 地址将是 8 4 字节字段的128位值，类似于以下格式： \<header> ：*nnnn： nnnn： nnnn： nnnn*。</span><span class="sxs-lookup"><span data-stu-id="1ce8a-126">If your network uses IPv6 addressing, the IP address will be a 128-bit value of 8 4-byte fields similar to the following format: \<header>:*nnnn:nnnn:nnnn:nnnn*.</span></span>  
  
     <span data-ttu-id="1ce8a-127">如果有多个网络适配器，您将看到每个网络适配器都有一个 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="1ce8a-127">If you have multiple cards, you will see an IP address for each one.</span></span> <span data-ttu-id="1ce8a-128">如果仅选择此值，它将限制对该 IP 地址（以及域名服务器映射到该地址的任何主机名）的应用程序访问。</span><span class="sxs-lookup"><span data-stu-id="1ce8a-128">If you select only this value, it will limit application access to the just the IP address (and any host name that a domain name server maps to that address).</span></span> <span data-ttu-id="1ce8a-129">您不能使用 localhost 访问报表服务器，也不能使用安装在报表服务器计算机上的其他网络适配器的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="1ce8a-129">You cannot use localhost to access a report server, and you cannot use the IP addresses of other network adapter cards that are installed on the report server computer.</span></span>  
  
 <span data-ttu-id="1ce8a-130">**Port**</span><span class="sxs-lookup"><span data-stu-id="1ce8a-130">**Port**</span></span>  
 <span data-ttu-id="1ce8a-131">指定报表服务器监视请求的端口。</span><span class="sxs-lookup"><span data-stu-id="1ce8a-131">Specifies the port that report server monitors for requests.</span></span> <span data-ttu-id="1ce8a-132">端口 80 为默认端口。</span><span class="sxs-lookup"><span data-stu-id="1ce8a-132">Port 80 is the default port.</span></span> <span data-ttu-id="1ce8a-133">如果使用端口 80，则不必将其包含在 URL 中。</span><span class="sxs-lookup"><span data-stu-id="1ce8a-133">If you use port 80, you do not have to include it in the URL.</span></span> <span data-ttu-id="1ce8a-134">如果使用其他任何端口号，则必须始终将其包含在 URL 中 (例如， http://localhost:8181/reports) 。</span><span class="sxs-lookup"><span data-stu-id="1ce8a-134">If you use any other port number, you must always include it in the URL (for example, http://localhost:8181/reports).</span></span>  
  
 <span data-ttu-id="1ce8a-135">**主机标头**</span><span class="sxs-lookup"><span data-stu-id="1ce8a-135">**Host Header**</span></span>  
 <span data-ttu-id="1ce8a-136">如果已有一个在域名服务器上定义的主机标头解析为您的计算机，则可以在为报表服务器访问配置的 URL 中指定该主机标头。</span><span class="sxs-lookup"><span data-stu-id="1ce8a-136">If you already have a host header defined on a domain name server that resolves to your computer, you can specify that host header in a URL that you configure for report server access.</span></span>  
  
 <span data-ttu-id="1ce8a-137">主机标头是允许多个网站共享一个 IP 地址和端口的唯一名称。</span><span class="sxs-lookup"><span data-stu-id="1ce8a-137">A host header is a unique name that allows multiple Web sites to share a single IP address and port.</span></span> <span data-ttu-id="1ce8a-138">主机标头名称比 IP 地址和端口号更容易记住和键入。</span><span class="sxs-lookup"><span data-stu-id="1ce8a-138">Host header names are easier to remember and type than IP address and port numbers.</span></span> <span data-ttu-id="1ce8a-139">这里有一个主机标头名称的示例： www.adventure-works.com 。</span><span class="sxs-lookup"><span data-stu-id="1ce8a-139">An example of a host header name might be www.adventure-works.com.</span></span>  
  
 <span data-ttu-id="1ce8a-140">**SSL 端口**</span><span class="sxs-lookup"><span data-stu-id="1ce8a-140">**SSL Port**</span></span>  
 <span data-ttu-id="1ce8a-141">为 SSL 连接指定端口。</span><span class="sxs-lookup"><span data-stu-id="1ce8a-141">Specifies the port for SSL connections.</span></span> <span data-ttu-id="1ce8a-142">SSL 的默认端口为 443。</span><span class="sxs-lookup"><span data-stu-id="1ce8a-142">The default port for SSL is 443.</span></span>  
  
 <span data-ttu-id="1ce8a-143">**SSL 证书**</span><span class="sxs-lookup"><span data-stu-id="1ce8a-143">**SSL Certificate**</span></span>  
 <span data-ttu-id="1ce8a-144">指定安装在此计算机上的 SSL 证书的证书名称。</span><span class="sxs-lookup"><span data-stu-id="1ce8a-144">Specifies the certificate name of an SSL certificate that you installed on this computer.</span></span> <span data-ttu-id="1ce8a-145">如果证书映射到某个通配符，则可以将其用于报表服务器连接。</span><span class="sxs-lookup"><span data-stu-id="1ce8a-145">If the certificate maps to a wildcard, you can use it for a report server connection.</span></span>  
  
 <span data-ttu-id="1ce8a-146">指定为其注册证书的完全限定的计算机名称。</span><span class="sxs-lookup"><span data-stu-id="1ce8a-146">Specifies the fully qualified computer name for which the certificate is registered.</span></span> <span data-ttu-id="1ce8a-147">指定的名称必须与为其注册证书的名称相同。</span><span class="sxs-lookup"><span data-stu-id="1ce8a-147">The name that you specify must be identical to the name for which the certificate is registered.</span></span>  
  
 <span data-ttu-id="1ce8a-148">必须先安装证书，才能使用此选项。</span><span class="sxs-lookup"><span data-stu-id="1ce8a-148">You must have a certificate installed to use this option.</span></span> <span data-ttu-id="1ce8a-149">还必须修改 RSReportServer.config 文件中的 UrlRoot 配置设置，以便指定要为其注册证书的计算机的完全限定名称。</span><span class="sxs-lookup"><span data-stu-id="1ce8a-149">You must also modify the UrlRoot configuration setting in the RSReportServer.config file so that it specifies the fully qualified name of the computer for which the certificate is registered.</span></span> <span data-ttu-id="1ce8a-150">有关详细信息，请参阅 [联机丛书中的](../../reporting-services/security/configure-ssl-connections-on-a-native-mode-report-server.md) 配置本机模式报表服务器上的 SSL 连接 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="1ce8a-150">For more information, see [Configure SSL Connections on a Native Mode Report Server](../../reporting-services/security/configure-ssl-connections-on-a-native-mode-report-server.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
 <span data-ttu-id="1ce8a-151">**发布到**</span><span class="sxs-lookup"><span data-stu-id="1ce8a-151">**Issued To**</span></span>  
 <span data-ttu-id="1ce8a-152">显示为其创建证书的计算机的名称。</span><span class="sxs-lookup"><span data-stu-id="1ce8a-152">Shows the name of the computer for which the certificate was created.</span></span>  
  
 <span data-ttu-id="1ce8a-153">**添加**</span><span class="sxs-lookup"><span data-stu-id="1ce8a-153">**Add**</span></span>  
 <span data-ttu-id="1ce8a-154">定义附加 URL。</span><span class="sxs-lookup"><span data-stu-id="1ce8a-154">Define an additional URL.</span></span>  
  
 <span data-ttu-id="1ce8a-155">**编辑**</span><span class="sxs-lookup"><span data-stu-id="1ce8a-155">**Edit**</span></span>  
 <span data-ttu-id="1ce8a-156">修改 URL 语法的任何部分。</span><span class="sxs-lookup"><span data-stu-id="1ce8a-156">Modify any part of the URL syntax.</span></span>  
  
 <span data-ttu-id="1ce8a-157">**删除**</span><span class="sxs-lookup"><span data-stu-id="1ce8a-157">**Remove**</span></span>  
 <span data-ttu-id="1ce8a-158">从列表中清除 URL 项。</span><span class="sxs-lookup"><span data-stu-id="1ce8a-158">Clear a URL entry from the list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ce8a-159">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1ce8a-159">See Also</span></span>  
 <span data-ttu-id="1ce8a-160">[Reporting Services Configuration Manager（本机模式）](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="1ce8a-160">[Reporting Services Configuration Manager &#40;Native Mode&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md) </span></span>  
 <span data-ttu-id="1ce8a-161">[&#40;SSRS Configuration Manager 配置 URL&#41;](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="1ce8a-161">[Configure a URL  &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md) </span></span>  
 [<span data-ttu-id="1ce8a-162">配置报表服务器 URL（SSRS 配置管理器）</span><span class="sxs-lookup"><span data-stu-id="1ce8a-162">Configure Report Server URLs  &#40;SSRS Configuration Manager&#41;</span></span>](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md)  
  
  
