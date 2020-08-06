---
title: 在报表服务器上配置自定义身份验证或窗体身份验证 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Forms authentication, configuring
- custom authentication [Reporting Services]
ms.assetid: e8601a8f-e66d-4649-8e4d-a46ca20ec7d0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1447e1e695f0e59dbc07b7e19f4df335a1220a97
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579459"
---
# <a name="configure-custom-or-forms-authentication-on-the-report-server"></a><span data-ttu-id="76234-102">在报表服务器上配置自定义身份验证或窗体身份验证</span><span class="sxs-lookup"><span data-stu-id="76234-102">Configure Custom or Forms Authentication on the Report Server</span></span>
  <span data-ttu-id="76234-103">Reporting Services 提供了可扩展的体系结构，该体系结构允许您插入自定义的或基于窗体的身份验证模块。</span><span class="sxs-lookup"><span data-stu-id="76234-103">Reporting Services provides an extensible architecture that allows you to plug in custom or forms-based authentication modules.</span></span> <span data-ttu-id="76234-104">如果部署要求不包含 Windows 集成安全性或基本身份验证，则可考虑实现自定义的身份验证扩展插件。</span><span class="sxs-lookup"><span data-stu-id="76234-104">You might consider implementing a custom authentication extension if deployment requirements do not include Windows integrated security or Basic authentication.</span></span> <span data-ttu-id="76234-105">使用自定义身份验证的最常见情形是支持对 Web 应用程序的 Internet 或 Extranet 访问。</span><span class="sxs-lookup"><span data-stu-id="76234-105">The most common scenario for using custom authentication is to support Internet or extranet access to a Web application.</span></span> <span data-ttu-id="76234-106">使用自定义身份验证扩展插件替换默认的 Windows 身份验证扩展插件，可更好地控制如何授予外部用户访问报表服务器的权限。</span><span class="sxs-lookup"><span data-stu-id="76234-106">Replacing the default Windows Authentication extension with a custom authentication extension gives you more control over how external users are granted access to the report server.</span></span>  
  
 <span data-ttu-id="76234-107">实际上，部署自定义身份验证扩展插件需要执行多个步骤，包括复制程序集和应用程序文件，修改配置文件以及测试。</span><span class="sxs-lookup"><span data-stu-id="76234-107">In practice, deploying a custom authentication extension requires multiple steps that include copying assemblies and application files, modifying configuration files, and testing.</span></span> <span data-ttu-id="76234-108">本主题仅重点介绍您要在配置文件中指定的身份验证设置。</span><span class="sxs-lookup"><span data-stu-id="76234-108">This topic focuses on just the authentication settings that you specify in the configuration files.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="76234-109">若要创建自定义身份验证扩展插件，需要自定义代码并掌握 [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] 安全性方面的专业知识。</span><span class="sxs-lookup"><span data-stu-id="76234-109">Creating a custom authentication extension requires custom code and expertise in [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] security.</span></span> <span data-ttu-id="76234-110">如果您不希望创建自定义身份验证扩展插件，则可以使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Active Directory 组和帐户，但应大幅减小报表服务器部署的范围。</span><span class="sxs-lookup"><span data-stu-id="76234-110">If you do not want to create a custom authentication extension, you can use [!INCLUDE[msCoName](../../includes/msconame-md.md)] Active Directory groups and accounts, but you should greatly reduce the scope of a report server deployment.</span></span> <span data-ttu-id="76234-111">有关自定义身份验证的详细信息，请参阅 [Implementing a Security Extension](../extensions/security-extension/implementing-a-security-extension.md)。</span><span class="sxs-lookup"><span data-stu-id="76234-111">For more information about custom authentication, see [Implementing a Security Extension](../extensions/security-extension/implementing-a-security-extension.md).</span></span>  
  
 <span data-ttu-id="76234-112">此外，如果希望在与 SharePoint 产品集成的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 环境中使用窗体身份验证或自定义身份验证扩展插件，则必须将 SharePoint 站点配置为使用您所选的身份验证方法。</span><span class="sxs-lookup"><span data-stu-id="76234-112">Additionally, if you want to use Forms authentication or a custom authentication extension in a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] environment that is integrated with a SharePoint product, you must configure the SharePoint site to use the authentication method that you choose.</span></span> <span data-ttu-id="76234-113">有关在 SharePoint 中配置身份验证的详细信息，请参阅 [Developer Network (MSDN) 上的](https://go.microsoft.com/fwlink/?LinkId=115575) Authentication Samples [!INCLUDE[msCoName](../../includes/msconame-md.md)] 身份验证示例。</span><span class="sxs-lookup"><span data-stu-id="76234-113">For more information about configuring authentication in SharePoint, see [Authentication Samples](https://go.microsoft.com/fwlink/?LinkId=115575) on [!INCLUDE[msCoName](../../includes/msconame-md.md)] Developer Network (MSDN).</span></span>  
  
### <a name="to-configure-a-report-server-to-use-custom-authentication"></a><span data-ttu-id="76234-114">将报表服务器配置为使用自定义身份验证</span><span class="sxs-lookup"><span data-stu-id="76234-114">To configure a report server to use Custom authentication</span></span>  
  
1.  <span data-ttu-id="76234-115">在文本编辑器中打开 RSReportServer.config。</span><span class="sxs-lookup"><span data-stu-id="76234-115">Open RSReportServer.config in a text editor.</span></span>  
  
2.  <span data-ttu-id="76234-116">查找 <`Authentication`>。</span><span class="sxs-lookup"><span data-stu-id="76234-116">Find <`Authentication`>.</span></span>  
  
3.  <span data-ttu-id="76234-117">复制以下 XML 结构：</span><span class="sxs-lookup"><span data-stu-id="76234-117">Copy the following XML structure:</span></span>  
  
    ```  
    <Authentication>  
          <AuthenticationTypes>  
                 <Custom />  
          </AuthenticationTypes>  
          <EnableAuthPersistence>true</EnableAuthPersistence>  
    </Authentication>  
    ```  
  
4.  <span data-ttu-id="76234-118">将其粘贴到 <> 的现有条目上 `Authentication` 。</span><span class="sxs-lookup"><span data-stu-id="76234-118">Paste it over the existing entries for <`Authentication`>.</span></span>  
  
     <span data-ttu-id="76234-119">请注意，不能将 `Custom` 与其他身份验证类型一起使用。</span><span class="sxs-lookup"><span data-stu-id="76234-119">Note that you cannot use `Custom` with other authentication types.</span></span>  
  
5.  <span data-ttu-id="76234-120">保存文件。</span><span class="sxs-lookup"><span data-stu-id="76234-120">Save the file.</span></span>  
  
6.  <span data-ttu-id="76234-121">打开报表服务器的 Web.config 文件。</span><span class="sxs-lookup"><span data-stu-id="76234-121">Open the Web.config file for the report server.</span></span> <span data-ttu-id="76234-122">默认情况下，该文件位于 \Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\ReportServer 下。</span><span class="sxs-lookup"><span data-stu-id="76234-122">By default, it is located at \Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\ReportServer.</span></span>  
  
7.  <span data-ttu-id="76234-123">找到 `authentication mode` 并设置它 `Forms` 。</span><span class="sxs-lookup"><span data-stu-id="76234-123">Find `authentication mode` and set it `Forms`.</span></span>  
  
    ```  
    <authentication mode = "Forms" />  
    ```  
  
8.  <span data-ttu-id="76234-124">查找 `identity impersonate` 并将其设置为 `False`。</span><span class="sxs-lookup"><span data-stu-id="76234-124">Find `identity impersonate` and set it to `False`.</span></span>  
  
    ```  
    <identity impersonate = "false" />  
    ```  
  
9. <span data-ttu-id="76234-125">打开报表管理器的 Web.config 文件。</span><span class="sxs-lookup"><span data-stu-id="76234-125">Open the Web.config file for Report Manager.</span></span> <span data-ttu-id="76234-126">默认情况下，该文件位于 \Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\ReportManager 下。</span><span class="sxs-lookup"><span data-stu-id="76234-126">By default, it is located at \Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\ReportManager.</span></span>  
  
10. <span data-ttu-id="76234-127">找到 `authentication mode` 并设置它 `Forms` 。</span><span class="sxs-lookup"><span data-stu-id="76234-127">Find `authentication mode` and set it `Forms`.</span></span>  
  
    ```  
    <authentication mode = "Forms" />  
    ```  
  
11. <span data-ttu-id="76234-128">查找 `identity impersonate` 并将其设置为 `False`。</span><span class="sxs-lookup"><span data-stu-id="76234-128">Find `identity impersonate` and set it to `False`.</span></span>  
  
    ```  
    <identity impersonate = "false" />  
    ```  
  
12. <span data-ttu-id="76234-129">将 `PassThroughCookies` 元素结构添加到配置文件中。</span><span class="sxs-lookup"><span data-stu-id="76234-129">Add the `PassThroughCookies` element structure to the configuration file.</span></span> <span data-ttu-id="76234-130">有关详细信息，请参阅 [配置报表管理器以便传递自定义身份验证 Cookie](configure-the-web-portal-to-pass-custom-authentication-cookies.md)。</span><span class="sxs-lookup"><span data-stu-id="76234-130">For more information, see [Configure Report Manager to Pass Custom Authentication Cookies](configure-the-web-portal-to-pass-custom-authentication-cookies.md).</span></span>  
  
13. <span data-ttu-id="76234-131">保存文件。</span><span class="sxs-lookup"><span data-stu-id="76234-131">Save the file.</span></span>  
  
14. <span data-ttu-id="76234-132">如果配置了扩展部署，请对该部署中的其他报表服务器重复以上所有步骤。</span><span class="sxs-lookup"><span data-stu-id="76234-132">If you configured a scale-out deployment, repeat all of the previous steps for other report servers in the deployment.</span></span>  
  
15. <span data-ttu-id="76234-133">重新启动报表服务器以清除当前打开的任何会话。</span><span class="sxs-lookup"><span data-stu-id="76234-133">Restart the report server to clear any sessions that are currently open.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76234-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="76234-134">See Also</span></span>  
 <span data-ttu-id="76234-135">[实现安全扩展插件](../extensions/security-extension/implementing-a-security-extension.md) </span><span class="sxs-lookup"><span data-stu-id="76234-135">[Implementing a Security Extension](../extensions/security-extension/implementing-a-security-extension.md) </span></span>  
 <span data-ttu-id="76234-136">[针对报表服务器的身份验证](authentication-with-the-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="76234-136">[Authentication with the Report Server](authentication-with-the-report-server.md) </span></span>  
 <span data-ttu-id="76234-137">[Rsreportserver.config 配置文件](../report-server/rsreportserver-config-configuration-file.md) </span><span class="sxs-lookup"><span data-stu-id="76234-137">[RSReportServer Configuration File](../report-server/rsreportserver-config-configuration-file.md) </span></span>  
 <span data-ttu-id="76234-138">[在报表服务器上配置基本身份验证](configure-basic-authentication-on-the-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="76234-138">[Configure Basic Authentication on the Report Server](configure-basic-authentication-on-the-report-server.md) </span></span>  
 [<span data-ttu-id="76234-139">在报表服务器上配置 Windows 身份验证</span><span class="sxs-lookup"><span data-stu-id="76234-139">Configure Windows Authentication on the Report Server</span></span>](configure-windows-authentication-on-the-report-server.md)  
  
  
