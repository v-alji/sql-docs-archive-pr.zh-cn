---
title: 在报表服务器上配置 Windows 身份验证 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Windows authentication [Reporting Services]
- Reporting Services, configuration
ms.assetid: 4de9c3dd-0ee7-49b3-88bb-209465ca9d86
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 879c036977f9a34528dbf38e42fa080e72617a14
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689279"
---
# <a name="configure-windows-authentication-on-the-report-server"></a><span data-ttu-id="582ef-102">在报表服务器上配置 Windows 身份验证</span><span class="sxs-lookup"><span data-stu-id="582ef-102">Configure Windows Authentication on the Report Server</span></span>
  <span data-ttu-id="582ef-103">默认情况下， [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 接受指定 Negotiate 或 NTLM 身份验证的请求。</span><span class="sxs-lookup"><span data-stu-id="582ef-103">By default, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] accepts requests that specify Negotiate or NTLM authentication.</span></span> <span data-ttu-id="582ef-104">如果部署中包括使用这些安全提供程序的客户端应用程序和浏览器，则可以使用这些默认值，而无需附加配置。</span><span class="sxs-lookup"><span data-stu-id="582ef-104">If your deployment includes client applications and browsers that use these security providers, you can use the default values without additional configuration.</span></span> <span data-ttu-id="582ef-105">如果要使用不同的安全提供程序来获取 Windows 集成安全性（例如，如果要直接使用 Kerberos）或者修改了默认值并且要还原原始设置，则可以使用本主题中的信息来指定报表服务器上的身份验证设置。</span><span class="sxs-lookup"><span data-stu-id="582ef-105">If you want to use a different security provider for Windows integrated security (for example, if you want to use Kerberos directly), or if you modified the default values and want to restore the original settings, you can use the information in this topic to specify authentication settings on the report server.</span></span>  
  
 <span data-ttu-id="582ef-106">若要使用 Windows 集成安全性，则每个需要访问报表服务器的用户都必须拥有有效的 Windows 本地或域用户帐户，或者必须是 Windows 本地或域组帐户的成员。</span><span class="sxs-lookup"><span data-stu-id="582ef-106">To use Windows integrated security, each user who requires access to a report server must have a valid Windows local or domain user account or be a member of a Windows local or domain group account.</span></span> <span data-ttu-id="582ef-107">对于其他域，只要这些域可信，您也可以包括其中的帐户。</span><span class="sxs-lookup"><span data-stu-id="582ef-107">You can include accounts from other domains as long as those domains are trusted.</span></span> <span data-ttu-id="582ef-108">这些帐户必须具有报表服务器计算机的访问权，并且必须随后分配给相应的角色以便获得特定报表服务器操作的访问权。</span><span class="sxs-lookup"><span data-stu-id="582ef-108">The accounts must have access to the report server computer, and must be subsequently assigned to roles in order to gain access to specific report server operations.</span></span>  
  
 <span data-ttu-id="582ef-109">同时，必须满足下列附加要求：</span><span class="sxs-lookup"><span data-stu-id="582ef-109">The following additional requirements must also be met:</span></span>  
  
-   <span data-ttu-id="582ef-110">RSeportServer.config 文件必须具有设置为 `AuthenticationType`、`RSWindowsNegotiate` 或 `RSWindowsKerberos` 的 `RSWindowsNTLM`。</span><span class="sxs-lookup"><span data-stu-id="582ef-110">The RSeportServer.config files must have `AuthenticationType` set to `RSWindowsNegotiate`, `RSWindowsKerberos`, or `RSWindowsNTLM`.</span></span> <span data-ttu-id="582ef-111">默认情况下，如果报表服务器服务帐户是 NetworkService 或 LocalSystem，则 RSReportServer.config 文件包含 `RSWindowsNegotiate` 设置；否则使用 `RSWindowsNTLM` 设置。</span><span class="sxs-lookup"><span data-stu-id="582ef-111">By default, the RSReportServer.config file includes the `RSWindowsNegotiate` setting if the Report Server service account is either NetworkService or LocalSystem; otherwise, the `RSWindowsNTLM` setting is used.</span></span> <span data-ttu-id="582ef-112">如果拥有仅使用 Kerberos 身份验证的应用程序，则可以添加 `RSWindowsKerberos`。</span><span class="sxs-lookup"><span data-stu-id="582ef-112">You can add `RSWindowsKerberos` if you have applications that only use Kerberos authentication.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="582ef-113">如果将报表服务器服务配置为在域用户帐户下运行，并且没有为该帐户注册服务主体名称 (SPN)，则使用 `RSWindowsNegotiate` 将产生 Kerberos 身份验证错误。</span><span class="sxs-lookup"><span data-stu-id="582ef-113">Using `RSWindowsNegotiate` will result in a Kerberos authentication error if you configured the Report Server service to run under a domain user account and you did not register a Service Principal Name (SPN) for the account.</span></span> <span data-ttu-id="582ef-114">有关详细信息，请参阅本主题中的 [连接到报表服务器时纠正 Kerberos 身份验证错误](#proxyfirewallRSWindowsNegotiate) 。</span><span class="sxs-lookup"><span data-stu-id="582ef-114">For more information, see [Resolving Kerberos Authentication Errors When Connecting to a report server](#proxyfirewallRSWindowsNegotiate) in this topic.</span></span>  
  
-   [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] <span data-ttu-id="582ef-115">。</span><span class="sxs-lookup"><span data-stu-id="582ef-115">must be configured for Windows Authentication.</span></span> <span data-ttu-id="582ef-116">默认情况下，报表服务器 Web 服务和报表管理器的 Web.config 文件包括 \<authentication mode="Windows"> 设置。</span><span class="sxs-lookup"><span data-stu-id="582ef-116">By default, the Web.config files for the Report Server Web service and Report Manager include the \<authentication mode="Windows"> setting.</span></span> <span data-ttu-id="582ef-117">如果将其更改为 \<authentication mode="Forms"> ，则的 Windows 身份验证 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 将失败。</span><span class="sxs-lookup"><span data-stu-id="582ef-117">If you change it to \<authentication mode="Forms">, the Windows Authentication for [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] will fail.</span></span>  
  
-   <span data-ttu-id="582ef-118">报表服务器 Web 服务和报表管理器的 Web.config 文件必须具有 \<identity impersonate= "true" /> 。</span><span class="sxs-lookup"><span data-stu-id="582ef-118">The Web.config files for the Report Server Web service and Report Manager must have \<identity impersonate= "true" />.</span></span>  
  
-   <span data-ttu-id="582ef-119">客户端应用程序或浏览器必须支持 Windows 集成安全性。</span><span class="sxs-lookup"><span data-stu-id="582ef-119">The client application or browser must support Windows integrated security.</span></span>  
  
 <span data-ttu-id="582ef-120">若要更改报表服务器身份验证设置，需要在 RSReportServer.config 文件中编辑 XML 元素和值。</span><span class="sxs-lookup"><span data-stu-id="582ef-120">To change the report server authentication settings, edit the XML elements and values in the RSReportServer.config file.</span></span> <span data-ttu-id="582ef-121">可以复制并粘贴本主题中的示例来实现特定的组合。</span><span class="sxs-lookup"><span data-stu-id="582ef-121">You can copy and paste the examples in this topic to implement specific combinations.</span></span>  
  
 <span data-ttu-id="582ef-122">如果所有客户端计算机和服务器计算机均位于相同的域或某个可信域中，并且报表服务器是针对企业防火墙之后的 Intranet 访问而部署的，则默认设置将达到最佳效果。</span><span class="sxs-lookup"><span data-stu-id="582ef-122">The default settings work best if all client and server computers are in the same domain or in a trusted domain and the report server is deployed for intranet access behind a corporate firewall.</span></span> <span data-ttu-id="582ef-123">可信域和单个域是传递 Windows 凭据所必需的。</span><span class="sxs-lookup"><span data-stu-id="582ef-123">Trusted and single domains are a requirement for passing Windows credentials.</span></span> <span data-ttu-id="582ef-124">如果为服务器启用 Kerberos 版本 5 协议，则可以多次传递凭据。</span><span class="sxs-lookup"><span data-stu-id="582ef-124">Credentials can be passed more than one time if you enable the Kerberos version 5 protocol for your servers.</span></span> <span data-ttu-id="582ef-125">否则，凭据在过期之前只能传递一次。</span><span class="sxs-lookup"><span data-stu-id="582ef-125">Otherwise, credentials can be passed only one time before they expire.</span></span> <span data-ttu-id="582ef-126">有关为多计算机连接配置凭据的详细信息，请参阅 [指定报表数据源的凭据和连接信息](../report-data/specify-credential-and-connection-information-for-report-data-sources.md)。</span><span class="sxs-lookup"><span data-stu-id="582ef-126">For more information about configuring credentials for multiple computer connections, see [Specify Credential and Connection Information for Report Data Sources](../report-data/specify-credential-and-connection-information-for-report-data-sources.md).</span></span>  
  
 <span data-ttu-id="582ef-127">以下说明针对本机模式报表服务器。</span><span class="sxs-lookup"><span data-stu-id="582ef-127">The following instructions are intended for a native mode report server.</span></span> <span data-ttu-id="582ef-128">如果在 SharePoint 集成模式下部署报表服务器，则必须使用指定 Windows 集成安全性的默认身份验证设置。</span><span class="sxs-lookup"><span data-stu-id="582ef-128">If the report server is deployed in SharePoint integrated mode, you must use the default authentication settings that specify Windows integrated security.</span></span> <span data-ttu-id="582ef-129">报表服务器使用默认 Windows 身份验证扩展插件中的内部功能支持 SharePoint 集成模式下的报表服务器。</span><span class="sxs-lookup"><span data-stu-id="582ef-129">The report server uses internal features in the default Windows Authentication extension to support report servers in SharePoint integrated mode.</span></span>  
  
## <a name="extended-protection-for-authentication"></a><span data-ttu-id="582ef-130">身份验证的扩展保护</span><span class="sxs-lookup"><span data-stu-id="582ef-130">Extended Protection for Authentication</span></span>  
 <span data-ttu-id="582ef-131">自 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]开始，提供了对针对验证的扩展保护的支持。</span><span class="sxs-lookup"><span data-stu-id="582ef-131">Beginning with [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], support for Extended Protection for Authentication is available.</span></span> <span data-ttu-id="582ef-132">此 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 功能支持使用渠道绑定和服务绑定来加强对身份验证的保护。</span><span class="sxs-lookup"><span data-stu-id="582ef-132">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] feature supports the use of channel binding and service binding to enhance protection of authentication.</span></span> <span data-ttu-id="582ef-133">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 功能需要用于支持扩展保护的操作系统。</span><span class="sxs-lookup"><span data-stu-id="582ef-133">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] features need to be used with an operating system that supports Extended Protection.</span></span> [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="582ef-134">配置由 RSReportServer.config 文件中的设置确定。</span><span class="sxs-lookup"><span data-stu-id="582ef-134">configuration for extended protection is determined by settings in the RSReportServer.config file.</span></span> <span data-ttu-id="582ef-135">可以通过编辑此文件或使用 WMI API 来更新此文件。</span><span class="sxs-lookup"><span data-stu-id="582ef-135">The file can be updated by either editing the file or using WMI APIs.</span></span> <span data-ttu-id="582ef-136">有关详细信息，请参阅 [Extended Protection for Authentication with Reporting Services](extended-protection-for-authentication-with-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="582ef-136">For more information, see [Extended Protection for Authentication with Reporting Services](extended-protection-for-authentication-with-reporting-services.md).</span></span>  
  
### <a name="to-configure-a-report-server-to-use-windows-integrated-security"></a><span data-ttu-id="582ef-137">将报表服务器配置为使用 Windows 集成安全性</span><span class="sxs-lookup"><span data-stu-id="582ef-137">To configure a report server to use Windows integrated security</span></span>  
  
1.  <span data-ttu-id="582ef-138">在文本编辑器中打开 RSReportServer.config。</span><span class="sxs-lookup"><span data-stu-id="582ef-138">Open RSReportServer.config in a text editor.</span></span>  
  
2.  <span data-ttu-id="582ef-139">查找 <`Authentication`>。</span><span class="sxs-lookup"><span data-stu-id="582ef-139">Find <`Authentication`>.</span></span>  
  
3.  <span data-ttu-id="582ef-140">复制以下最能满足您需要的一个 XML 结构。</span><span class="sxs-lookup"><span data-stu-id="582ef-140">Copy one of the following XML structures that best fits your needs.</span></span> <span data-ttu-id="582ef-141">可以按任意顺序指定 `RSWindowsNegotiate`、`RSWindowsNTLM` 和 `RSWindowsKerberos`。</span><span class="sxs-lookup"><span data-stu-id="582ef-141">You can specify `RSWindowsNegotiate`, `RSWindowsNTLM`, and `RSWindowsKerberos` in any order.</span></span> <span data-ttu-id="582ef-142">如果要对连接而非每一单个请求进行身份验证，则应启用身份验证持久性。</span><span class="sxs-lookup"><span data-stu-id="582ef-142">You should enable authentication persistence if you want to authenticate the connection rather than each individual request.</span></span> <span data-ttu-id="582ef-143">在身份验证持久性下，在连接期间将允许所有要求身份验证的请求。</span><span class="sxs-lookup"><span data-stu-id="582ef-143">Under authentication persistence, all requests that require authentication will be allowed for the duration of the connection.</span></span>  
  
     <span data-ttu-id="582ef-144">当报表服务器服务帐户是 NetworkService 或 LocalSystem 时，第一个 XML 结构是默认配置：</span><span class="sxs-lookup"><span data-stu-id="582ef-144">The first XML structure is the default configuration when the Report Server service account is either NetworkService or LocalSystem:</span></span>  
  
    ```  
    <Authentication>  
          <AuthenticationTypes>  
                 <RSWindowsNegotiate />  
          </AuthenticationTypes>  
          <EnableAuthPersistence>true</EnableAuthPersistence>  
    </Authentication>  
    ```  
  
     <span data-ttu-id="582ef-145">当报表服务器服务帐户不是 NetworkService 或 LocalSystem 时，第二个 XML 结构是默认配置：</span><span class="sxs-lookup"><span data-stu-id="582ef-145">The second XML structure is the default configuration when the Report Server service account is not NetworkService or LocalSystem:</span></span>  
  
    ```  
    <Authentication>  
          <AuthenticationTypes>  
                 <RSWindowsNTLM />  
          </AuthenticationTypes>  
          <EnableAuthPersistence>true</EnableAuthPersistence>  
    ```  
  
     \</Authentication>  
  
     <span data-ttu-id="582ef-146">第三个 XML 结构指定 Windows 集成安全性中使用的所有安全包：</span><span class="sxs-lookup"><span data-stu-id="582ef-146">The third XML structure specifies all of the security packages that are used in Windows integrated security:</span></span>  
  
    ```  
          <AuthenticationTypes>  
                 <RSWindowsNegotiate />  
                 <RSWindowsKerberos />  
                 <RSWindowsNTLM />  
          </AuthenticationTypes>  
    ```  
  
     <span data-ttu-id="582ef-147">第四个 XML 结构仅为不支持 Kerberos 的部署指定 NTLM，或解决 Kerberos 身份验证错误：</span><span class="sxs-lookup"><span data-stu-id="582ef-147">The fourth XML structure specifies NTLM only for deployments that do not support Kerberos or to work around Kerberos authentication errors:</span></span>  
  
    ```  
          <AuthenticationTypes>  
                 <RSWindowsNTLM />  
          </AuthenticationTypes>  
    ```  
  
4.  <span data-ttu-id="582ef-148">将其粘贴到 <> 的现有条目上 `Authentication` 。</span><span class="sxs-lookup"><span data-stu-id="582ef-148">Paste it over the existing entries for <`Authentication`>.</span></span>  
  
     <span data-ttu-id="582ef-149">注意，不能将 `Custom` 与 `RSWindows` 类型一起使用。</span><span class="sxs-lookup"><span data-stu-id="582ef-149">Note that you cannot use `Custom` with the `RSWindows` types.</span></span>  
  
5.  <span data-ttu-id="582ef-150">根据需要适当修改扩展保护的设置。</span><span class="sxs-lookup"><span data-stu-id="582ef-150">Modify as appropriate the settings for extended protection.</span></span> <span data-ttu-id="582ef-151">默认情况下，扩展保护处于禁用状态。</span><span class="sxs-lookup"><span data-stu-id="582ef-151">Extended protection is disabled by default.</span></span>  <span data-ttu-id="582ef-152">如果这些条目不存在，则当前计算机运行的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 版本可能不支持扩展保护。</span><span class="sxs-lookup"><span data-stu-id="582ef-152">If these entries are not present, the current computer may not be running a version of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] which supports extended protection.</span></span> <span data-ttu-id="582ef-153">有关详细信息，请参阅 [Extended Protection for Authentication with Reporting Services](extended-protection-for-authentication-with-reporting-services.md)</span><span class="sxs-lookup"><span data-stu-id="582ef-153">For more information, see [Extended Protection for Authentication with Reporting Services](extended-protection-for-authentication-with-reporting-services.md)</span></span>  
  
    ```  
          <RSWindowsExtendedProtectionLevel>Allow</RSWindowsExtendedProtectionLevel>  
          <RSWindowsExtendedProtectionScenario>Proxy</RSWindowsExtendedProtectionScenario>  
    ```  
  
6.  <span data-ttu-id="582ef-154">保存文件。</span><span class="sxs-lookup"><span data-stu-id="582ef-154">Save the file.</span></span>  
  
7.  <span data-ttu-id="582ef-155">如果配置了扩展部署，请对该部署中的其他报表服务器重复这些步骤。</span><span class="sxs-lookup"><span data-stu-id="582ef-155">If you configured a scale-out deployment, repeat these steps for other report servers in the deployment.</span></span>  
  
8.  <span data-ttu-id="582ef-156">重新启动报表服务器以清除当前打开的任何会话。</span><span class="sxs-lookup"><span data-stu-id="582ef-156">Restart the report server to clear any sessions that are currently open.</span></span>  
  
##  <a name="resolving-kerberos-authentication-errors-when-connecting-to-a-report-server"></a><a name="proxyfirewallRSWindowsNegotiate"></a> <span data-ttu-id="582ef-157">连接到报表服务器时解决 Kerberos 身份验证错误</span><span class="sxs-lookup"><span data-stu-id="582ef-157">Resolving Kerberos Authentication Errors When Connecting to a Report Server</span></span>  
 <span data-ttu-id="582ef-158">在为 Negotiate 或 Kerberos 身份验证配置的报表服务器上，如果出现 Kerberos 身份验证错误，则客户端与报表服务器的连接将失败。</span><span class="sxs-lookup"><span data-stu-id="582ef-158">On a report server that is configured for Negotiate or Kerberos authentication, a client connection to the report server will fail if there is a Kerberos authentication error.</span></span> <span data-ttu-id="582ef-159">已知在以下情况下会出现 Kerberos 身份验证错误：</span><span class="sxs-lookup"><span data-stu-id="582ef-159">Kerberos authentication errors are known to occur when:</span></span>  
  
-   <span data-ttu-id="582ef-160">报表服务器服务作为 Windows 域用户帐户运行并且您没有为该帐户注册服务主体名称 (SPN)。</span><span class="sxs-lookup"><span data-stu-id="582ef-160">The Report Server service runs as a Windows domain user account and you did not register a Service Principal Name (SPN) for the account.</span></span>  
  
-   <span data-ttu-id="582ef-161">报表服务器是使用 `RSWindowsNegotiate` 设置配置的。</span><span class="sxs-lookup"><span data-stu-id="582ef-161">The report server is configured with the `RSWindowsNegotiate` setting.</span></span>  
  
-   <span data-ttu-id="582ef-162">浏览器选择它发送给报表服务器的请求的身份验证标头中 NTLM 上的 Kerberos。</span><span class="sxs-lookup"><span data-stu-id="582ef-162">The browser chooses Kerberos over NTLM in the authentication header in the request it sends to the report server.</span></span>  
  
 <span data-ttu-id="582ef-163">如果启用了 Kerberos 日志记录，则可以检测到该错误。</span><span class="sxs-lookup"><span data-stu-id="582ef-163">You can detect the error if you enabled Kerberos logging.</span></span> <span data-ttu-id="582ef-164">另一错误症状是多次提示您输入凭据，然后您看到一个空的浏览器窗口。</span><span class="sxs-lookup"><span data-stu-id="582ef-164">Another symptom of the error is that you are prompted for credentials multiple times and then see an empty browser window.</span></span>  
  
 <span data-ttu-id="582ef-165">你可以通过 `RSWindowsNegotiate` 从配置文件中删除 </> 并意义连接来确认你遇到了 Kerberos 身份验证错误。</span><span class="sxs-lookup"><span data-stu-id="582ef-165">You can confirm that you are encountering a Kerberos authentication error by removing < `RSWindowsNegotiate` /> from your configuration file and reattempting the connection.</span></span>  
  
 <span data-ttu-id="582ef-166">确认遇到该问题之后，可以采用下列方法解决它：</span><span class="sxs-lookup"><span data-stu-id="582ef-166">After you confirm the problem, you can address it in the following ways:</span></span>  
  
-   <span data-ttu-id="582ef-167">在域用户帐户下为报表服务器服务注册 SPN。</span><span class="sxs-lookup"><span data-stu-id="582ef-167">Register an SPN for the Report Server service under the domain user account.</span></span> <span data-ttu-id="582ef-168">有关详细信息，请参阅[为报表服务器注册服务主体名称 (SPN)](../report-server/register-a-service-principal-name-spn-for-a-report-server.md)。</span><span class="sxs-lookup"><span data-stu-id="582ef-168">For more information, see [Register a Service Principal Name &#40;SPN&#41; for a Report Server](../report-server/register-a-service-principal-name-spn-for-a-report-server.md).</span></span>  
  
-   <span data-ttu-id="582ef-169">将服务帐户更改为在网络服务等内置帐户下运行。</span><span class="sxs-lookup"><span data-stu-id="582ef-169">Change the service account to run under a built-in account such as Network Service.</span></span> <span data-ttu-id="582ef-170">内置帐户将 HTTP SPN 映射到将计算机联网时定义的 Host SPN。</span><span class="sxs-lookup"><span data-stu-id="582ef-170">Built-in accounts map HTTP SPN to the Host SPN, which is defined when you join a computer to your network.</span></span> <span data-ttu-id="582ef-171">有关详细信息，请参阅[配置服务帐户（SSRS 配置管理器）](../../sql-server/install/configure-a-service-account-ssrs-configuration-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="582ef-171">For more information, see [Configure a Service Account &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-service-account-ssrs-configuration-manager.md).</span></span>  
  
-   <span data-ttu-id="582ef-172">使用 NTLM。</span><span class="sxs-lookup"><span data-stu-id="582ef-172">Use NTLM.</span></span> <span data-ttu-id="582ef-173">通常，NTLM 将在 Kerberos 身份验证失败时发挥作用。</span><span class="sxs-lookup"><span data-stu-id="582ef-173">NTLM will generally work in cases where Kerberos authentication fails.</span></span> <span data-ttu-id="582ef-174">若要使用 NTLM，从 RSReportServer.config 文件中删除 `RSWindowsNegotiate` 并验证仅指定了 `RSWindowsNTLM`。</span><span class="sxs-lookup"><span data-stu-id="582ef-174">To use NTLM, remove `RSWindowsNegotiate` from the RSReportServer.config file and verify that only `RSWindowsNTLM` is specified.</span></span> <span data-ttu-id="582ef-175">如果选择此方法，则可以继续将域用户帐户用于报表服务器服务（即使没有为其定义 SPN）。</span><span class="sxs-lookup"><span data-stu-id="582ef-175">If you choose this approach, you can continue to use a domain user account for the Report Server service even if you do not define an SPN for it.</span></span>  
  
#### <a name="logging-information"></a><span data-ttu-id="582ef-176">日志记录信息</span><span class="sxs-lookup"><span data-stu-id="582ef-176">Logging information</span></span>  
 <span data-ttu-id="582ef-177">多种日志记录信息源可以帮助解决与 Kerberos 相关的问题。</span><span class="sxs-lookup"><span data-stu-id="582ef-177">There are several sources of logging information that can help resolve Kerberos related issues.</span></span>  
  
##### <a name="user-account-control-attribute"></a><span data-ttu-id="582ef-178">用户-帐户-控制属性</span><span class="sxs-lookup"><span data-stu-id="582ef-178">User-Account-Control Attribute</span></span>  
 <span data-ttu-id="582ef-179">确定 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服务帐户在 Active Directory 中是否具有足够的属性集。</span><span class="sxs-lookup"><span data-stu-id="582ef-179">Determine if the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service account has the sufficient attribute set in Active Directory.</span></span> <span data-ttu-id="582ef-180">检查 Reporting Services 服务跟踪日志文件，以找到为 UserAccountControl 属性记录的值。</span><span class="sxs-lookup"><span data-stu-id="582ef-180">Review the reporting services service trace log file to find the value logged for the UserAccountControl attribute.</span></span> <span data-ttu-id="582ef-181">记录的值为十进制格式。</span><span class="sxs-lookup"><span data-stu-id="582ef-181">The value logged is in decimal form.</span></span> <span data-ttu-id="582ef-182">您需要将十进制值转换为十六进制格式，然后在描述用户-帐户-控制属性的 MSDN 主题中找到该值。</span><span class="sxs-lookup"><span data-stu-id="582ef-182">You need to convert the decimal value to hexadecimal form and then find that value in the MSDN topic describing User-Account-Control Attribute.</span></span>  
  
-   <span data-ttu-id="582ef-183">Reporting Services 服务跟踪日志条目类似于以下内容：</span><span class="sxs-lookup"><span data-stu-id="582ef-183">The reporting services service trace log entry will look similar to the following:</span></span>  
  
    ```  
    appdomainmanager!DefaultDomain!8f8!01/14/2010-14:42:28:: i INFO: The UserAccountControl value for the service account is 590336  
    ```  
  
-   <span data-ttu-id="582ef-184">用于将十进制值转换为十六进制格式的一个选项是使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 计算器。</span><span class="sxs-lookup"><span data-stu-id="582ef-184">One option for converting the value Decimal value to hexadecimal form is to us the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Calculator.</span></span> <span data-ttu-id="582ef-185">Windows 计算器支持多种显示“十进制”选项和“十六进制”选项的模式。</span><span class="sxs-lookup"><span data-stu-id="582ef-185">Windows Calculator supports several modes that show the 'Dec' option and 'Hex' options.</span></span> <span data-ttu-id="582ef-186">选择“十进制”选项，粘贴或键入在日志文件中找到的十进制值，然后选择“十六进制”选项。</span><span class="sxs-lookup"><span data-stu-id="582ef-186">Select the 'Dec' option, paste or type in the decimal value you found in the log file and then select the 'Hex' option.</span></span>  
  
-   <span data-ttu-id="582ef-187">然后，参阅主题 [用户-帐户-控制属性](https://go.microsoft.com/fwlink/?LinkId=183366) 以获得服务帐户的属性。</span><span class="sxs-lookup"><span data-stu-id="582ef-187">Then refer to the topic [User-Account-Control Attribute](https://go.microsoft.com/fwlink/?LinkId=183366) to derive the attribute for the service account.</span></span>  
  
##### <a name="spns-configured-in-active-directory-for-the-reporting-services-service-account"></a><span data-ttu-id="582ef-188">在 Active Directory 中为 Reporting Services 服务帐户配置的 SPN。</span><span class="sxs-lookup"><span data-stu-id="582ef-188">SPNs Configured in Active Directory for the Reporting Services service account.</span></span>  
 <span data-ttu-id="582ef-189">若要在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服务跟踪日志文件中记录 SPN，可以临时启用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 扩展保护功能。</span><span class="sxs-lookup"><span data-stu-id="582ef-189">To log the SPNs in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service trace log file, you can enable the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Extended Protection feature temporarily.</span></span>  
  
-   <span data-ttu-id="582ef-190">通过设置以下内容修改配置文件 `rsreportserver.config`：</span><span class="sxs-lookup"><span data-stu-id="582ef-190">Modify the configuration file `rsreportserver.config` by setting the following:</span></span>  
  
    ```  
    <RSWindowsExtendedProtectionLevel>Allow</RSWindowsExtendedProtectionLevel>   
    <RSWindowsExtendedProtectionScenario>Any</RSWindowsExtendedProtectionScenario>  
    ```  
  
-   <span data-ttu-id="582ef-191">重新启动 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服务。</span><span class="sxs-lookup"><span data-stu-id="582ef-191">Restart the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service.</span></span>

 <span data-ttu-id="582ef-192">如果不希望继续使用扩展保护，则将配置值重新设置为默认值，然后重新启动 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服务帐户。</span><span class="sxs-lookup"><span data-stu-id="582ef-192">If you do not want continue using Extended Protection, then set the configuration values back to defaults and restart the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Service account.</span></span>  
  
```  
<RSWindowsExtendedProtectionLevel>Off</RSWindowsExtendedProtectionLevel>  
<RSWindowsExtendedProtectionScenario>Proxy</RSWindowsExtendedProtectionScenario>  
```  
  
 <span data-ttu-id="582ef-193">有关详细信息，请参阅[与 Reporting Services 针对验证的扩展保护](extended-protection-for-authentication-with-reporting-services.md)</span><span class="sxs-lookup"><span data-stu-id="582ef-193">For more information see, [Extended Protection for Authentication with Reporting Services](extended-protection-for-authentication-with-reporting-services.md)</span></span>  
  
#### <a name="how-the-browser-chooses-negotiated-kerberos-or-negotiated-ntlm"></a><span data-ttu-id="582ef-194">浏览器如何选择协商 Kerberos 或协商 NTLM</span><span class="sxs-lookup"><span data-stu-id="582ef-194">How the Browser Chooses Negotiated Kerberos or Negotiated NTLM</span></span>  
 <span data-ttu-id="582ef-195">使用 Internet Explorer 连接到报表服务器时，它将在身份验证标头中指定协商 Kerberos 或 NTLM。</span><span class="sxs-lookup"><span data-stu-id="582ef-195">When you use Internet Explorer to connect to the report server, it specifies either Negotiated Kerberos or NTLM on the authentication header.</span></span> <span data-ttu-id="582ef-196">在以下情况下，使用 NTLM 而非 Kerberos：</span><span class="sxs-lookup"><span data-stu-id="582ef-196">NTLM is used instead of Kerberos when:</span></span>  
  
-   <span data-ttu-id="582ef-197">将请求发送到本地报表服务器。</span><span class="sxs-lookup"><span data-stu-id="582ef-197">The request is sent to a local report server.</span></span>  
  
-   <span data-ttu-id="582ef-198">将请求发送到报表服务器计算机的 IP 地址而非主机标头或服务器名称。</span><span class="sxs-lookup"><span data-stu-id="582ef-198">The request is sent to an IP address of the report server computer rather than a host header or server name.</span></span>  
  
-   <span data-ttu-id="582ef-199">防火墙软件阻塞了用于 Kerberos 身份验证的端口。</span><span class="sxs-lookup"><span data-stu-id="582ef-199">Firewall software blocks ports used for Kerberos authentication.</span></span>  
  
-   <span data-ttu-id="582ef-200">特定服务器的操作系统不启用 Kerberos。</span><span class="sxs-lookup"><span data-stu-id="582ef-200">The operating system of a particular server does not have Kerberos enabled.</span></span>  
  
-   <span data-ttu-id="582ef-201">域中包括旧版 Windows 客户端和服务器操作系统，不支持新版操作系统中内置的 Kerberos 功能。</span><span class="sxs-lookup"><span data-stu-id="582ef-201">The domain includes older versions of Windows client and server operating systems that do not support the Kerberos authentication feature built into newer versions of the operating system.</span></span>  
  
 <span data-ttu-id="582ef-202">此外，Internet Explorer 还可能选择协商 Kerberos 或 NTLM，这取决于您如何配置的 URL、LAN 和代理设置。</span><span class="sxs-lookup"><span data-stu-id="582ef-202">In addition, Internet Explorer might choose either Negotiated Kerberos or NTLM depending on how you configured URL, LAN, and proxy settings.</span></span>  
  
###### <a name="report-server-url"></a><span data-ttu-id="582ef-203">报表服务器 URL</span><span class="sxs-lookup"><span data-stu-id="582ef-203">Report Server URL</span></span>  
 <span data-ttu-id="582ef-204">如果该 URL 包括完全限定域名，则 Internet Explorer 将选择 NTLM。</span><span class="sxs-lookup"><span data-stu-id="582ef-204">If the URL includes a fully qualified domain name, Internet Explorer selects NTLM.</span></span> <span data-ttu-id="582ef-205">如果该 URL 指定本地主机，则 Internet Explorer 选择 NTLM。</span><span class="sxs-lookup"><span data-stu-id="582ef-205">If the URL specifies localhost, Internet Explorer selects NTLM.</span></span> <span data-ttu-id="582ef-206">如果该 URL 指定计算机的网络名称，则 Internet Explorer 将选择协商，这将会成功或失败，取决于报表服务器服务帐户是否存在 SPN。</span><span class="sxs-lookup"><span data-stu-id="582ef-206">If the URL specifies the network name of the computer, Internet Explorer selects Negotiate, which will succeed or fail depending on whether an SPN exists for the Report Server service account.</span></span>  
  
###### <a name="lan-and-proxy-settings-on-the-client"></a><span data-ttu-id="582ef-207">客户端上的 LAN 和代理设置</span><span class="sxs-lookup"><span data-stu-id="582ef-207">LAN and Proxy Settings on the Client</span></span>  
 <span data-ttu-id="582ef-208">在 Internet Explorer 中设置的 LAN 和代理设置可以确定是否在 Kerberos 上选择 NTLM。</span><span class="sxs-lookup"><span data-stu-id="582ef-208">LAN and proxy settings that you set in Internet Explorer can determine whether NTLM is chosen over Kerberos.</span></span> <span data-ttu-id="582ef-209">但是，由于各组织的 LAN 和代理设置会有所不同，因此不可能准确确定造成 Kerberos 身份验证错误的设置。</span><span class="sxs-lookup"><span data-stu-id="582ef-209">However, because LAN and proxy settings vary across organizations, it is not possible to precisely determine the exact settings that contribute to Kerberos authentication errors.</span></span> <span data-ttu-id="582ef-210">例如，您的组织可能会强制实施将 URL 从 Intranet URL 转换为通过 Internet 连接解析的完全限定域名 URL 的代理设置。</span><span class="sxs-lookup"><span data-stu-id="582ef-210">For example, your organization might enforce proxy settings that transform URLs from intranet URLs to fully-qualified domain name URLs that resolve over Internet connections.</span></span> <span data-ttu-id="582ef-211">如果将不同的身份验证提供程序用于不同类型的 URL，则您可能会发现原本预计会失败的某些连接竟然成功了。</span><span class="sxs-lookup"><span data-stu-id="582ef-211">If different authentication providers are used for different types of URLs, you might find that some connections succeed when you would have expected them to fail.</span></span>  
  
 <span data-ttu-id="582ef-212">如果遇到您认为因身份验证失败而引起的连接错误，则可以尝试其他 LAN 与代理设置的组合来隔离该问题。</span><span class="sxs-lookup"><span data-stu-id="582ef-212">If you encounter connection errors that you think are due to authentication failures, you can try different combinations of LAN and proxy settings to isolate the problem.</span></span> <span data-ttu-id="582ef-213">在 Internet Explorer 中，LAN 和代理设置位于“局域网 (LAN) 设置”\*\*\*\* 对话框中，可以通过单击“Internet 选项”\*\*\*\* 的“连接”\*\*\*\* 选项卡上的“LAN 设置”\*\*\*\* 打开该对话框。</span><span class="sxs-lookup"><span data-stu-id="582ef-213">In Internet Explorer, LAN and proxy settings are on the **Local Area Network (LAN) Settings** dialog box, which you open by clicking **LAN settings** on the **Connection** tab of **Internet Options**.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="582ef-214">外部资源</span><span class="sxs-lookup"><span data-stu-id="582ef-214">External resources</span></span>  
  
-   <span data-ttu-id="582ef-215">有关 Kerberos 和报表服务器的更多信息，请参阅 [Deploying a Business Intelligence Solution Using SharePoint, Reporting Services, and PerformancePoint Monitoring Server with Kerberos](https://go.microsoft.com/fwlink/?LinkID=177751)（通过 Kerberos 部署使用 SharePoint、Reporting Services 和 PerformancePoint Monitoring Server 的商业智能解决方案）。</span><span class="sxs-lookup"><span data-stu-id="582ef-215">For additional information regarding Kerberos and report servers, see [Deploying a Business Intelligence Solution Using SharePoint, Reporting Services, and PerformancePoint Monitoring Server with Kerberos.](https://go.microsoft.com/fwlink/?LinkID=177751)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="582ef-216">另请参阅</span><span class="sxs-lookup"><span data-stu-id="582ef-216">See Also</span></span>  
 <span data-ttu-id="582ef-217">[针对报表服务器的身份验证](authentication-with-the-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="582ef-217">[Authentication with the Report Server](authentication-with-the-report-server.md) </span></span>  
 <span data-ttu-id="582ef-218">[授予对本机模式报表服务器的权限](granting-permissions-on-a-native-mode-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="582ef-218">[Granting Permissions on a Native Mode Report Server](granting-permissions-on-a-native-mode-report-server.md) </span></span>  
 <span data-ttu-id="582ef-219">[Rsreportserver.config 配置文件](../report-server/rsreportserver-config-configuration-file.md) </span><span class="sxs-lookup"><span data-stu-id="582ef-219">[RSReportServer Configuration File](../report-server/rsreportserver-config-configuration-file.md) </span></span>  
 <span data-ttu-id="582ef-220">[在报表服务器上配置基本身份验证](configure-basic-authentication-on-the-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="582ef-220">[Configure Basic Authentication on the Report Server](configure-basic-authentication-on-the-report-server.md) </span></span>  
 <span data-ttu-id="582ef-221">[在报表服务器上配置自定义身份验证或窗体身份验证](configure-custom-or-forms-authentication-on-the-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="582ef-221">[Configure Custom or Forms Authentication on the Report Server](configure-custom-or-forms-authentication-on-the-report-server.md) </span></span>  
 [<span data-ttu-id="582ef-222">Reporting Services 针对验证的扩展保护</span><span class="sxs-lookup"><span data-stu-id="582ef-222">Extended Protection for Authentication with Reporting Services</span></span>](extended-protection-for-authentication-with-reporting-services.md)  
  
  
