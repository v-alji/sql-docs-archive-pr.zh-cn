---
title: 将 Reporting Services 配置为使用使用者可选名称 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ce458f9f-4b4f-4a58-aa75-9a90dda1e622
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0312d2d1fff8f854eb2ffb8d0dad2563212ee23b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692792"
---
# <a name="configure-reporting-services-to-use-a-subject-alternative-name"></a><span data-ttu-id="95adc-102">配置 Reporting Services 使用使用者备用名称</span><span class="sxs-lookup"><span data-stu-id="95adc-102">Configure Reporting Services to Use a Subject Alternative Name</span></span>
  <span data-ttu-id="95adc-103">本主题说明了如何通过修改 rsreportserver.config 文件和使用 Netsh.exe 工具配置 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] (SSRS) 以使用使用者可选名称 (SAN)。</span><span class="sxs-lookup"><span data-stu-id="95adc-103">This topic explains how to configure [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] (SSRS) to use a subject alternative name (SAN) by modifying the rsreportserver.config file and using the Netsh.exe tool.</span></span>

||
|-|
|<span data-ttu-id="95adc-104">**[!INCLUDE[applies](../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 本机模式</span><span class="sxs-lookup"><span data-stu-id="95adc-104">**[!INCLUDE[applies](../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Native mode</span></span>|

 <span data-ttu-id="95adc-105">该说明适用于 Reporting Service URL 以及 Web 服务 URL。</span><span class="sxs-lookup"><span data-stu-id="95adc-105">The instructions apply to the Reporting Service URL as well as a Web Service URL.</span></span>

 <span data-ttu-id="95adc-106">要使用 SAN，SSL 证书必须在服务器上注册，签名并且获得私钥。</span><span class="sxs-lookup"><span data-stu-id="95adc-106">To use a SAN, the SSL certificate must be registered on the server, signed, and have the private key.</span></span> <span data-ttu-id="95adc-107">你无法使用自签名证书。</span><span class="sxs-lookup"><span data-stu-id="95adc-107">You cannot use a self-signed certificate</span></span>

 <span data-ttu-id="95adc-108">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 中的 URL 可配置为使用 SSL 证书。</span><span class="sxs-lookup"><span data-stu-id="95adc-108">URLs in [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] can be configured to use an SSL certificate.</span></span> <span data-ttu-id="95adc-109">一个证书通常只有一个使用者名称，此名称针对一个 SSL（安全套接字层）会话只允许一个 URL。</span><span class="sxs-lookup"><span data-stu-id="95adc-109">A certificate normally has just a subject name, which allows only one URL for an SSL (Secure Sockets Layer) session.</span></span> <span data-ttu-id="95adc-110">SAN 是证书中的附加字段，允许 SSL 服务进行侦听，对许多 URL 有效，并与其他应用程序共享 SSL 端口。</span><span class="sxs-lookup"><span data-stu-id="95adc-110">The SAN is an additional field in the certificate that allows an SSL service to listen and be valid for many URLs, and to share the SSL port with other applications.</span></span> <span data-ttu-id="95adc-111">SAN 的形式如下：www.s2.com。</span><span class="sxs-lookup"><span data-stu-id="95adc-111">The SAN looks something like the following: www.s2.com.</span></span>

 <span data-ttu-id="95adc-112">有关 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]SSL 设置的详细信息，请参阅 [配置本机模式报表服务器上的 SSL 连接](security/configure-ssl-connections-on-a-native-mode-report-server.md)。</span><span class="sxs-lookup"><span data-stu-id="95adc-112">For more information about SSL settings for [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], see [Configure SSL Connections on a Native Mode Report Server](security/configure-ssl-connections-on-a-native-mode-report-server.md).</span></span>

### <a name="configure-ssrs-to-use-a-subject-alternative-name-for-web-service-url"></a><span data-ttu-id="95adc-113">将 SSRS 配置为使用适用于 Web 服务 URL 的使用者备用名称</span><span class="sxs-lookup"><span data-stu-id="95adc-113">Configure SSRS to use a subject alternative name for Web Service URL</span></span>

1.  <span data-ttu-id="95adc-114">启动 Reporting Services 配置管理器。</span><span class="sxs-lookup"><span data-stu-id="95adc-114">Start Reporting Services Configuration Manager.</span></span>

     <span data-ttu-id="95adc-115">有关详细信息，请参阅 [Reporting Services Configuration Manager（本机模式）](../sql-server/install/reporting-services-configuration-manager-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="95adc-115">For more information, see [Reporting Services Configuration Manager &#40;Native Mode&#41;](../sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>

2.  <span data-ttu-id="95adc-116">在“Web 服务 URL” \*\*\*\* 页面上，选择一个 SSL 端口和 SSL 证书。</span><span class="sxs-lookup"><span data-stu-id="95adc-116">On the **Web Service URL** page, select an SSL port and SSL Certificate.</span></span>

     <span data-ttu-id="95adc-117">![Reporting Services 配置管理器](media/reportingservices-configurationmanager.png "Reporting Services 配置管理器")</span><span class="sxs-lookup"><span data-stu-id="95adc-117">![Reporting Services Configuration Manager](media/reportingservices-configurationmanager.png "Reporting Services Configuration Manager")</span></span>

     <span data-ttu-id="95adc-118">配置管理器注册端口的 SSL 证书。</span><span class="sxs-lookup"><span data-stu-id="95adc-118">The configuration manager registers the SSL certificate for the port.</span></span>

3.  <span data-ttu-id="95adc-119">打开 rsreportserver.config 文件。</span><span class="sxs-lookup"><span data-stu-id="95adc-119">Open the rsreportserver.config file.</span></span>

     <span data-ttu-id="95adc-120">对于 SSL 本机模式，默认情况下，该文件位于以下文件夹。</span><span class="sxs-lookup"><span data-stu-id="95adc-120">For SSRS Native mode, the file is located by default in the following folder.</span></span>

    ```
    \Program Files\Microsoft SQL Server\MSRS11.MSSQLSERVER\Reporting Services\ReportServer
    ```

4.  <span data-ttu-id="95adc-121">复制 Report Server Web 服务应用程序的 URL 部分。</span><span class="sxs-lookup"><span data-stu-id="95adc-121">Copy the URL section for the Report Server Web Service application.</span></span>

     <span data-ttu-id="95adc-122">例如，以下是初始 URL 部分。</span><span class="sxs-lookup"><span data-stu-id="95adc-122">For example, the following is the original URL section.</span></span>

    ```
        <URL>
         <UrlString>https://localhost:443</UrlString>
         <AccountSid>S-1-5-20</AccountSid>
         <AccountName>NT Authority\NetworkService</AccountName>
        </URL>

    ```

     <span data-ttu-id="95adc-123">以下是修改了的 URL 部分。</span><span class="sxs-lookup"><span data-stu-id="95adc-123">The following is the modified URL section.</span></span>

    ```
    <URL>
         <UrlString>https://www.s1.com:443</UrlString>
         <AccountSid>S-1-5-20</AccountSid>
         <AccountName>NT Authority\NetworkService</AccountName>
        </URL>
        <URL>
         <UrlString>https://www.s2.com:443</UrlString>
         <AccountSid>S-1-5-20</AccountSid>
         <AccountName>NT Authority\NetworkService</AccountName>
        </URL>

    ```

5.  <span data-ttu-id="95adc-124">保存 rsreportserver.config 文件。</span><span class="sxs-lookup"><span data-stu-id="95adc-124">Save the rsreportserver.config file.</span></span>

6.  <span data-ttu-id="95adc-125">以管理员身份启动一个命令提示符并运行 Netsh.exe 工具。</span><span class="sxs-lookup"><span data-stu-id="95adc-125">Start a command prompt as an administrator, and run the Netsh.exe tool.</span></span>

    ```
    C:\windows\system32\netsh
    ```

7.  <span data-ttu-id="95adc-126">键入以下内容切换至 http 上下文。</span><span class="sxs-lookup"><span data-stu-id="95adc-126">Switch to the http context by typing the following.</span></span>

    ```
    Netsh>http
    ```

8.  <span data-ttu-id="95adc-127">键入以下内容显示现有 urlacl。</span><span class="sxs-lookup"><span data-stu-id="95adc-127">Show the existing urlacls by typing the following.</span></span>

    ```
    Netsh http>show urlacl
    ```

     <span data-ttu-id="95adc-128">出现如下条目。</span><span class="sxs-lookup"><span data-stu-id="95adc-128">An entry such as the following appears.</span></span>

    ```
    Reserved URL            : https:// www.s1.com:443/ReportServer/
        User: NT SERVICE\ReportServer
            Listen: Yes
            Delegate: No
            SDDL: D:(A;;GX;;;S-1-5-80-1234567890-123456789-123456789-123456789-1234567890)
    ```

     <span data-ttu-id="95adc-129">一个 urlacl 是一个保留的 URL 的 DACL（自由访问控制列表）。</span><span class="sxs-lookup"><span data-stu-id="95adc-129">An urlacl is a DACL (Discretionary Access Control List) for a reserved URL.</span></span>

9. <span data-ttu-id="95adc-130">通过键入以下内容，为使用者备用名称创建一个用户和 SDDL 与现有条目相同的新条目。</span><span class="sxs-lookup"><span data-stu-id="95adc-130">Create a new entry for the subject alternative name, with the same user and SDDL as the existing entry, by typing the following.</span></span>

    ```
    netsh http>add urlacl  url=https://www.s2.com:443/ReportServer  
    user="NT Service\ReportServer" sddl=D:(A;;GX;;;S-1-5-80-1234567980-12346579-123456789-123456789-1234567890)

    ```

10. <span data-ttu-id="95adc-131">在 Reporting Services 配置管理器的“报表服务器状态”  页面上单击“停止”  ，然后单击“启动”  以重启报表服务器。</span><span class="sxs-lookup"><span data-stu-id="95adc-131">On the **Report Server Status** page of the Reporting Services Configuration Manager, Click **Stop** and then click **Start** to restart the report server.</span></span>

## <a name="see-also"></a><span data-ttu-id="95adc-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="95adc-132">See Also</span></span>
 <span data-ttu-id="95adc-133">[Rsreportserver.config 配置文件](report-server/rsreportserver-config-configuration-file.md) [Reporting Services 配置管理器 &#40;本机模式下&#41;](../sql-server/install/reporting-services-configuration-manager-native-mode.md) [修改 Reporting Services 配置文件 &#40;](report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md) RSreportserver.config&#41;&#40;[SSRS Configuration Manager 配置报表服务器 url&#41;](install-windows/configure-report-server-urls-ssrs-configuration-manager.md)</span><span class="sxs-lookup"><span data-stu-id="95adc-133">[RSReportServer Configuration File](report-server/rsreportserver-config-configuration-file.md) [Reporting Services Configuration Manager &#40;Native Mode&#41;](../sql-server/install/reporting-services-configuration-manager-native-mode.md) [Modify a Reporting Services Configuration File &#40;RSreportserver.config&#41;](report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md) [Configure Report Server URLs  &#40;SSRS Configuration Manager&#41;](install-windows/configure-report-server-urls-ssrs-configuration-manager.md)</span></span>


