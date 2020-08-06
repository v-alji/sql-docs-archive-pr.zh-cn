---
title: Reporting Services 安全性和保护 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- security [Reporting Services]
- Reporting Services, security
ms.assetid: 270075c5-bf12-4467-a775-abbda3d954a5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0f8c7a4186c5236260fb27d8de107ce8c97bd363
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590562"
---
# <a name="reporting-services-security-and-protection"></a><span data-ttu-id="ea4a1-102">Reporting Services 安全性和保护</span><span class="sxs-lookup"><span data-stu-id="ea4a1-102">Reporting Services Security and Protection</span></span>
  <span data-ttu-id="ea4a1-103">你可使用本节中的信息来了解 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]的安全功能。</span><span class="sxs-lookup"><span data-stu-id="ea4a1-103">You can use information in this section to learn about the security features of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="ea4a1-104">本节还将说明 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]中支持的授权模型和身份验证提供程序。</span><span class="sxs-lookup"><span data-stu-id="ea4a1-104">This section also explains the authorization models and authentication providers supported in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
## <a name="extended-protection-for-authentication"></a><span data-ttu-id="ea4a1-105">身份验证的扩展保护</span><span class="sxs-lookup"><span data-stu-id="ea4a1-105">Extended Protection for Authentication</span></span>  
 <span data-ttu-id="ea4a1-106">自 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]开始，提供了对针对验证的扩展保护的支持。</span><span class="sxs-lookup"><span data-stu-id="ea4a1-106">Beginning with [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], support for Extended Protection for Authentication is available.</span></span> <span data-ttu-id="ea4a1-107">此 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 功能支持使用渠道绑定和服务绑定来加强对身份验证的保护。</span><span class="sxs-lookup"><span data-stu-id="ea4a1-107">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] feature supports the use of channel binding and service binding to enhance protection of authentication.</span></span> <span data-ttu-id="ea4a1-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 功能需要用于支持扩展保护的操作系统。</span><span class="sxs-lookup"><span data-stu-id="ea4a1-108">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] features need to be used with an operating system that supports Extended Protection.</span></span> <span data-ttu-id="ea4a1-109">有关详细信息，请参阅 [Extended Protection for Authentication with Reporting Services](extended-protection-for-authentication-with-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="ea4a1-109">For more information, see [Extended Protection for Authentication with Reporting Services](extended-protection-for-authentication-with-reporting-services.md).</span></span>  
  
## <a name="authentication-and-authorization"></a><span data-ttu-id="ea4a1-110">身份验证和授权</span><span class="sxs-lookup"><span data-stu-id="ea4a1-110">Authentication and Authorization</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="ea4a1-111">提供不同的身份验证类型以便用户和客户端应用程序对报表服务器进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="ea4a1-111">provides different authentication types for users and client applications to authenticate with the report server.</span></span> <span data-ttu-id="ea4a1-112">通过为您的报表服务器使用正确的身份验证类型，您的组织可以实现所需的适当安全级别。</span><span class="sxs-lookup"><span data-stu-id="ea4a1-112">Using the right authentication type for your report server enables your organization to achieve the appropriate level of security required by your organization.</span></span> <span data-ttu-id="ea4a1-113">有关详细信息，请参阅 [Authentication with the Report Server](authentication-with-the-report-server.md)。</span><span class="sxs-lookup"><span data-stu-id="ea4a1-113">For more information, see [Authentication with the Report Server](authentication-with-the-report-server.md).</span></span>  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="ea4a1-114">还采用角色和权限来控制用户对报表服务器目录中的内容的访问（换言之，可以控制访问的人员、访问的内容以及访问的方式）。</span><span class="sxs-lookup"><span data-stu-id="ea4a1-114">also employs roles and permissions to control user access to content in the report server catalog (in other words, who can access what, and how s/he can access it).</span></span> <span data-ttu-id="ea4a1-115">有关详细信息，请参阅[角色和权限 (Reporting Services)](roles-and-permissions-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="ea4a1-115">For more information, see [Roles and Permissions &#40;Reporting Services&#41;](roles-and-permissions-reporting-services.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="ea4a1-116">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="ea4a1-116">Related Tasks</span></span>  
  
|<span data-ttu-id="ea4a1-117">任务说明</span><span class="sxs-lookup"><span data-stu-id="ea4a1-117">Task Descriptions</span></span>|<span data-ttu-id="ea4a1-118">链接</span><span class="sxs-lookup"><span data-stu-id="ea4a1-118">Links</span></span>|  
|-----------------------|-----------|  
|<span data-ttu-id="ea4a1-119">配置安全套接字层 (SSL) 以便确保与报表服务器的客户端连接的安全。</span><span class="sxs-lookup"><span data-stu-id="ea4a1-119">Configure the Secure Socket Layer (SSL) to secure client connections to the report server.</span></span>|[<span data-ttu-id="ea4a1-120">配置本机模式报表服务器上的 SSL 连接</span><span class="sxs-lookup"><span data-stu-id="ea4a1-120">Configure SSL Connections on a Native Mode Report Server</span></span>](configure-ssl-connections-on-a-native-mode-report-server.md)|  
  
  
