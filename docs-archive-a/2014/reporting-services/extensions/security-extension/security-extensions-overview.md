---
title: 安全扩展插件概述 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- security [Reporting Services], extensions
ms.assetid: 24ccd795-6506-457c-93ac-6a9dd6bb9a46
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9cd6c2a1518b724a7faafecdb2926505694e9707
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587208"
---
# <a name="security-extensions-overview"></a><span data-ttu-id="f740f-102">安全扩展插件概述</span><span class="sxs-lookup"><span data-stu-id="f740f-102">Security Extensions Overview</span></span>
  <span data-ttu-id="f740f-103">利用 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 安全扩展插件，可以对用户或组进行身份验证和授权；这样，不同的用户便可登录至同一台报表服务器，并基于他们的标识执行不同的任务或操作。</span><span class="sxs-lookup"><span data-stu-id="f740f-103">A [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] security extension enables the authentication and authorization of users or groups; that is, it enables different users to log on to a report server and, based on their identities, perform different tasks or operations.</span></span> <span data-ttu-id="f740f-104">默认情况下，[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 使用基于 Windows 的身份验证扩展插件，该插件使用 Windows 帐户协议来验证声明在系统上拥有帐户的用户的标识。</span><span class="sxs-lookup"><span data-stu-id="f740f-104">By default, [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] uses a Windows-based authentication extension, which uses Windows account protocols to verify the identities of users who claim to have accounts on the system.</span></span> [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="f740f-105">使用基于角色的安全系统为用户授权。</span><span class="sxs-lookup"><span data-stu-id="f740f-105">uses a role-based security system to authorize users.</span></span> <span data-ttu-id="f740f-106">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 基于角色的安全模型与其他技术的基于角色的安全模型类似。</span><span class="sxs-lookup"><span data-stu-id="f740f-106">The [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] role-based security model is similar to the role-based security models of other technologies.</span></span>

 <span data-ttu-id="f740f-107">因为安全扩展插件基于可扩展的开放式 API，所以您可以在 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中创建新的身份验证和授权扩展插件。</span><span class="sxs-lookup"><span data-stu-id="f740f-107">Because security extensions are based on an open and extensible API, you can create new authentication and authorization extensions in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="f740f-108">下面的示例为使用基于窗体的身份验证和授权的典型安全扩展插件实现：</span><span class="sxs-lookup"><span data-stu-id="f740f-108">The following is an example of a typical security extension implementation that uses Forms-based authentication and authorization:</span></span>

 <span data-ttu-id="f740f-109">![Reporting Services 安全扩展插件进程](../../media/rosettasecurityextensionflow.gif "Reporting Services 安全扩展插件进程")</span><span class="sxs-lookup"><span data-stu-id="f740f-109">![Reporting Services security extension process](../../media/rosettasecurityextensionflow.gif "Reporting Services security extension process")</span></span>

 <span data-ttu-id="f740f-110">如图所示，身份验证和授权将按以下所示发生：</span><span class="sxs-lookup"><span data-stu-id="f740f-110">As shown in the illustration, authentication and authorization occur as follows:</span></span>

1.  <span data-ttu-id="f740f-111">用户尝试使用 URL 访问报表管理器，然后被重定向至为客户端应用程序收集用户凭据的窗体。</span><span class="sxs-lookup"><span data-stu-id="f740f-111">A user tries to access Report Manager by using a URL and is redirected to a form that collects user credentials for the client application.</span></span>

2.  <span data-ttu-id="f740f-112">用户向该窗体提交凭据。</span><span class="sxs-lookup"><span data-stu-id="f740f-112">The user submits credentials to the form.</span></span>

3.  <span data-ttu-id="f740f-113">用户凭据通过 <xref:ReportService2010.ReportingService2010.LogonUser%2A> 方法提交至 Reporting Services Web 服务。</span><span class="sxs-lookup"><span data-stu-id="f740f-113">The user credentials are submitted to the Reporting Services Web service through the <xref:ReportService2010.ReportingService2010.LogonUser%2A> method.</span></span>

4.  <span data-ttu-id="f740f-114">Web 服务调用客户提供的安全扩展插件，并验证相应的用户名称和密码是否存在于自定义安全机构中。</span><span class="sxs-lookup"><span data-stu-id="f740f-114">The Web service calls the customer-supplied security extension and verifies that the user name and password exist in the custom security authority.</span></span>

5.  <span data-ttu-id="f740f-115">进行身份验证之后，Web 服务创建一个身份验证票证（称为“cookie”），管理票证，然后为报表管理器的主页验证用户角色。</span><span class="sxs-lookup"><span data-stu-id="f740f-115">After authentication, the Web service creates an authentication ticket (known as a "cookie"), manages the ticket, and verifies the user's role for the Home page of Report Manager.</span></span>

6.  <span data-ttu-id="f740f-116">Web 服务将此 cookie 返回至浏览器，然后在报表管理器中显示相应的用户界面。</span><span class="sxs-lookup"><span data-stu-id="f740f-116">The Web service returns the cookie to the browser and displays the appropriate user interface in Report Manager.</span></span>

7.  <span data-ttu-id="f740f-117">对用户进行身份验证之后，在 HTTP 标头中传送此 cookie 的同时浏览器向报表管理器发出请求。</span><span class="sxs-lookup"><span data-stu-id="f740f-117">After the user is authenticated, the browser makes requests to Report Manager while transmitting the cookie in the HTTP header.</span></span> <span data-ttu-id="f740f-118">这些请求用于响应报表管理器应用程序中的用户操作。</span><span class="sxs-lookup"><span data-stu-id="f740f-118">These requests are in response to user actions within the Report Manager application.</span></span>

8.  <span data-ttu-id="f740f-119">此 cookie 在 HTTP 标头中与请求的用户操作一起传送至 Web 服务。</span><span class="sxs-lookup"><span data-stu-id="f740f-119">The cookie is transmitted in the HTTP header to the Web service along with the requested user operation.</span></span>

9. <span data-ttu-id="f740f-120">对此 cookie 进行验证，如果有效，则报表服务器从报表服务器数据库中返回安全描述符及与请求的操作有关的其他信息。</span><span class="sxs-lookup"><span data-stu-id="f740f-120">The cookie is validated, and if it is valid, the report server returns the security descriptor and other information relating to the requested operation from the report server database.</span></span>

10. <span data-ttu-id="f740f-121">如果此 cookie 有效，报表服务器将调用安全扩展插件检查用户是否有权执行特定操作。</span><span class="sxs-lookup"><span data-stu-id="f740f-121">If the cookie is valid, the report server makes a call to the security extension to check if the user is authorized to perform the specific operation.</span></span>

11. <span data-ttu-id="f740f-122">如果用户已有相应权限，则报表服务器将执行请求的操作，并将控制权返回调用方。</span><span class="sxs-lookup"><span data-stu-id="f740f-122">If the user is authorized, the report server performs the requested operation and returns control to the caller.</span></span>

12. <span data-ttu-id="f740f-123">用户经过身份验证后，报表服务器进行 URL 访问都会使用此 cookie。</span><span class="sxs-lookup"><span data-stu-id="f740f-123">After the user is authenticated, URL access to the report server uses the same cookie.</span></span> <span data-ttu-id="f740f-124">此 cookie 在 HTTP 标头中传送。</span><span class="sxs-lookup"><span data-stu-id="f740f-124">The cookie is transmitted in the HTTP header.</span></span>

13. <span data-ttu-id="f740f-125">用户继续请求对报表服务器的操作，直到会话结束为止。</span><span class="sxs-lookup"><span data-stu-id="f740f-125">The user continues to request operations on the report server until the session has ended.</span></span>

## <a name="when-to-implement-a-security-extension"></a><span data-ttu-id="f740f-126">使用安全扩展插件的条件</span><span class="sxs-lookup"><span data-stu-id="f740f-126">When to Implement a Security Extension</span></span>
 <span data-ttu-id="f740f-127">建议尽量使用 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="f740f-127">We recommend that you use Windows Authentication if at all possible.</span></span> <span data-ttu-id="f740f-128">不过，在下列两种情况下，可能适合使用 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 的身份验证和授权：</span><span class="sxs-lookup"><span data-stu-id="f740f-128">However, custom authentication and authorization for [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] may be appropriate in the following two cases:</span></span>

-   <span data-ttu-id="f740f-129">您具有无法使用 Windows 帐户的 Internet 或 Extranet 应用程序。</span><span class="sxs-lookup"><span data-stu-id="f740f-129">You have an Internet or extranet application that cannot use Windows accounts.</span></span>

-   <span data-ttu-id="f740f-130">您拥有自定义用户和角色并且需要在 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中提供匹配的授权方案。</span><span class="sxs-lookup"><span data-stu-id="f740f-130">You have custom-defined users and roles and need to provide a matching authorization scheme in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>

## <a name="see-also"></a><span data-ttu-id="f740f-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f740f-131">See Also</span></span>
 <span data-ttu-id="f740f-132">[实现安全扩展](../security-extension/implementing-a-security-extension.md)[将报表管理器配置为传递自定义身份验证 cookie](../../security/configure-the-web-portal-to-pass-custom-authentication-cookies.md)</span><span class="sxs-lookup"><span data-stu-id="f740f-132">[Implementing a Security Extension](../security-extension/implementing-a-security-extension.md) [Configure Report Manager to Pass Custom Authentication Cookies](../../security/configure-the-web-portal-to-pass-custom-authentication-cookies.md)</span></span>


