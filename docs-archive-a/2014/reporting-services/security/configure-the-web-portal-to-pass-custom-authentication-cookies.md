---
title: 配置报表管理器以传递自定义身份验证 Cookie |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- authentication [Reporting Services]
- extensions [Reporting Services], custom security
ms.assetid: 91aeb053-149e-4562-ae4c-a688d0e1b2ba
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 90e8798fb91152ec64e7f290dc1522fc8eaa451c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579456"
---
# <a name="configure-report-manager-to-pass-custom-authentication-cookies"></a><span data-ttu-id="dd367-102">配置报表管理器以便传递自定义身份验证 Cookie</span><span class="sxs-lookup"><span data-stu-id="dd367-102">Configure Report Manager to Pass Custom Authentication Cookies</span></span>
  <span data-ttu-id="dd367-103">如果使用的是自定义身份验证扩展插件，则应配置报表管理器以传输自定义身份验证 Cookie。</span><span class="sxs-lookup"><span data-stu-id="dd367-103">If you are using a custom authentication extension, you should configure Report Manager to transmit custom authentication cookies.</span></span> <span data-ttu-id="dd367-104">否则，报表管理器通过特定的 HTTP 请求将 Cookie 传输到报表服务器。</span><span class="sxs-lookup"><span data-stu-id="dd367-104">Otherwise, Report Manager will only transmit cookies through HTTP requests specific to the report server.</span></span> <span data-ttu-id="dd367-105">如果要传输其他 Cookie，则必须修改 RSReportServer.Config 文件。</span><span class="sxs-lookup"><span data-stu-id="dd367-105">If you want to transmit additional cookies, you must modify the RSReportServer.Config file.</span></span>  
  
## <a name="modifying-the-rsreportserverconfig-file"></a><span data-ttu-id="dd367-106">修改 RSReportServer.Config 文件</span><span class="sxs-lookup"><span data-stu-id="dd367-106">Modifying the RSReportServer.Config File</span></span>  
 <span data-ttu-id="dd367-107">可以通过将 <`PassThroughCookies`> 元素添加到报表管理器文件中的 RSReportServer.config 配置设置，使报表管理器将其他 cookie 传输到 Report Server。</span><span class="sxs-lookup"><span data-stu-id="dd367-107">You can enable Report Manager to transmit additional cookies through to the report server by adding a <`PassThroughCookies`> element to the Report Manager configuration settings in the RSReportServer.config file.</span></span> <span data-ttu-id="dd367-108">在单一登录身份验证解决方案中，传输其他 Cookie 十分有用，因为此类解决方案不仅需要报表服务器身份验证 Cookie，而且还需要第三方身份验证系统中的 Cookie。</span><span class="sxs-lookup"><span data-stu-id="dd367-108">Transmitting additional cookies is helpful in a single sign-on authentication solution that requires not only the report server authentication cookies, but also cookies from a third-party authentication system.</span></span>  
  
 <span data-ttu-id="dd367-109">使用报表服务器时，为了使其他 Cookie 可以通过 HTTP 请求进行传输，请在 RSReportServer.config 文件中设置下列元素：</span><span class="sxs-lookup"><span data-stu-id="dd367-109">To enable additional cookies to be transmitted through HTTP requests when using Report Manager, set the following elements in the RSReportServer.config file:</span></span>  
  
```  
<UI>  
   <CustomAuthenticationUI>  
      ...  
      <PassThroughCookies>  
         <PassThroughCookie>cookiename1</PassThroughCookie>  
         <PassThroughCookie>cookiename2</PassThroughCookie>  
      </PassThroughCookies>  
   </CustomAuthenticationUI>  
      ...  
</UI>  
```  
  
## <a name="see-also"></a><span data-ttu-id="dd367-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dd367-110">See Also</span></span>  
 <span data-ttu-id="dd367-111">[针对报表服务器的身份验证](authentication-with-the-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="dd367-111">[Authentication with the Report Server](authentication-with-the-report-server.md) </span></span>  
 <span data-ttu-id="dd367-112">[Rsreportserver.config 配置文件](../report-server/rsreportserver-config-configuration-file.md) </span><span class="sxs-lookup"><span data-stu-id="dd367-112">[RSReportServer Configuration File](../report-server/rsreportserver-config-configuration-file.md) </span></span>  
 <span data-ttu-id="dd367-113">[安全扩展插件概述](../extensions/security-extension/security-extensions-overview.md) </span><span class="sxs-lookup"><span data-stu-id="dd367-113">[Security Extensions Overview](../extensions/security-extension/security-extensions-overview.md) </span></span>  
 [<span data-ttu-id="dd367-114">配置和管理报表服务器（SSRS 本机模式）</span><span class="sxs-lookup"><span data-stu-id="dd367-114">Configure and Administer a Report Server &#40;SSRS Native Mode&#41;</span></span>](../report-server/configure-and-administer-a-report-server-ssrs-native-mode.md)  
  
  
