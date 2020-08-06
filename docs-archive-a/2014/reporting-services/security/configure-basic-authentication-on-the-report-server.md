---
title: 在报表服务器上配置基本身份验证 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Reporting Services, configuration
- Basic authentication
ms.assetid: 8faf2938-b71b-4e61-a172-46da2209ff55
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 07f860a67e02c3eb29c5af4f480d3817c55c507f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579460"
---
# <a name="configure-basic-authentication-on-the-report-server"></a><span data-ttu-id="36236-102">在报表服务器上配置基本身份验证</span><span class="sxs-lookup"><span data-stu-id="36236-102">Configure Basic Authentication on the Report Server</span></span>
  <span data-ttu-id="36236-103">默认情况下，Reporting Services 接受指定 Negotiate 和 NTLM 身份验证的请求。</span><span class="sxs-lookup"><span data-stu-id="36236-103">By default, Reporting Services accepts requests that specify Negotiate and NTLM authentication.</span></span> <span data-ttu-id="36236-104">如果部署中包括使用基本身份验证的客户端应用程序或浏览器，则必须将基本身份验证添加到支持的类型列表中。</span><span class="sxs-lookup"><span data-stu-id="36236-104">If your deployment includes client applications or browsers that use Basic authentication, you must add Basic authentication to the list of supported types.</span></span> <span data-ttu-id="36236-105">此外，若要使用报表生成器，必须启用对报表生成器文件的匿名访问。</span><span class="sxs-lookup"><span data-stu-id="36236-105">In addition, if you want to use Report Builder, you must enable Anonymous access to the Report Builder files.</span></span>  
  
 <span data-ttu-id="36236-106">若要对报表服务器配置基本身份验证，则需要在 RSReportServer.config 文件中编辑 XML 元素和值。</span><span class="sxs-lookup"><span data-stu-id="36236-106">To configure Basic authentication on the report server, you edit XML elements and values in the RSReportServer.config file.</span></span> <span data-ttu-id="36236-107">可以复制并粘贴本主题中的示例来替换默认值。</span><span class="sxs-lookup"><span data-stu-id="36236-107">You can copy and paste the examples in this topic to replace the default values.</span></span>  
  
 <span data-ttu-id="36236-108">启用基本身份验证之前，请验证您的安全基础结构是否支持。</span><span class="sxs-lookup"><span data-stu-id="36236-108">Before you enable Basic authentication, verify that your security infrastructure supports it.</span></span> <span data-ttu-id="36236-109">在基本身份验证模式下，报表服务器 Web 服务会将凭据传递给本地安全机构。</span><span class="sxs-lookup"><span data-stu-id="36236-109">Under Basic authentication, the Report Server Web service will pass credentials to the local security authority.</span></span> <span data-ttu-id="36236-110">如果凭据指定本地用户帐户，则该用户将由报表服务器计算机上的本地安全机构进行身份验证，并获取对本地资源有效的安全令牌。</span><span class="sxs-lookup"><span data-stu-id="36236-110">If the credentials specify a local user account, the user is authenticated by the local security authority on the report server computer and the user will get a security token that is valid for local resources.</span></span> <span data-ttu-id="36236-111">域用户帐户的凭据将转发给域控制器并由它进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="36236-111">Credentials for domain user accounts are forwarded to and authenticated by a domain controller.</span></span> <span data-ttu-id="36236-112">生成的票证对网络资源有效。</span><span class="sxs-lookup"><span data-stu-id="36236-112">The resulting ticket is valid for network resources.</span></span>  
  
 <span data-ttu-id="36236-113">若要在将凭据传输到网络中的域控制器时降低凭据被截获的风险，则需要通道加密，如安全套接字层 (SSL)。</span><span class="sxs-lookup"><span data-stu-id="36236-113">Channel encryption, such as Secure Sockets Layer (SSL), is required if you want to mitigate the risk of having credentials intercepted while in transit to a domain controller in your network.</span></span> <span data-ttu-id="36236-114">基本身份验证本身以明文形式传输用户名，以 Base-64 编码格式传输密码。</span><span class="sxs-lookup"><span data-stu-id="36236-114">By itself, Basic authentication transmits the user name in clear text and the password in base-64 encoding.</span></span> <span data-ttu-id="36236-115">添加信道加密会使数据包不可读。</span><span class="sxs-lookup"><span data-stu-id="36236-115">Adding channel encryption makes the packet unreadable.</span></span> <span data-ttu-id="36236-116">有关详细信息，请参阅[配置本机模式报表服务器上的 SSL 连接](configure-ssl-connections-on-a-native-mode-report-server.md)。</span><span class="sxs-lookup"><span data-stu-id="36236-116">For more information, see [Configure SSL Connections on a Native Mode Report Server](configure-ssl-connections-on-a-native-mode-report-server.md).</span></span>  
  
 <span data-ttu-id="36236-117">启用基本身份验证后，请注意在将连接属性设置为向报表提供数据的外部数据源时，用户不能选择 **“Windows 集成安全性”** 选项。</span><span class="sxs-lookup"><span data-stu-id="36236-117">After you enable Basic authentication, be aware that users cannot select the **Windows integrated security** option when setting connection properties to an external data source that provides data to a report.</span></span> <span data-ttu-id="36236-118">该选项将在数据源属性页中显示为灰色。</span><span class="sxs-lookup"><span data-stu-id="36236-118">The option will be grayed out in the data source property pages.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="36236-119">以下说明针对本机模式报表服务器。</span><span class="sxs-lookup"><span data-stu-id="36236-119">The following instructions are intended for a native mode report server.</span></span> <span data-ttu-id="36236-120">如果在 SharePoint 集成模式下部署报表服务器，则必须使用指定 Windows 集成安全性的默认身份验证设置。</span><span class="sxs-lookup"><span data-stu-id="36236-120">If the report server is deployed in SharePoint integrated mode, you must use the default authentication settings that specify Windows integrated security.</span></span> <span data-ttu-id="36236-121">报表服务器使用默认 Windows 身份验证扩展插件中的内部功能支持 SharePoint 集成模式下的报表服务器。</span><span class="sxs-lookup"><span data-stu-id="36236-121">The report server uses internal features in the default Windows Authentication extension to support report server in SharePoint integrated mode.</span></span>  
  
### <a name="to-configure-a-report-server-to-use-basic-authentication"></a><span data-ttu-id="36236-122">将报表服务器配置为使用基本身份验证</span><span class="sxs-lookup"><span data-stu-id="36236-122">To configure a report server to use Basic authentication</span></span>  
  
1.  <span data-ttu-id="36236-123">在文本编辑器中打开 RSReportServer.config。</span><span class="sxs-lookup"><span data-stu-id="36236-123">Open RSReportServer.config in a text editor.</span></span>  
  
     <span data-ttu-id="36236-124">该文件位于\* \<drive> ：\* \Program Files\Microsoft SQL Server\MSRS12。MSSQLSERVER\Reporting Services\reportserver。</span><span class="sxs-lookup"><span data-stu-id="36236-124">The file is located at *\<drive>:* \Program Files\Microsoft SQL Server\MSRS12.MSSQLSERVER\Reporting Services\ReportServer.</span></span>  
  
2.  <span data-ttu-id="36236-125">查找 <`Authentication`>。</span><span class="sxs-lookup"><span data-stu-id="36236-125">Find <`Authentication`>.</span></span>  
  
3.  <span data-ttu-id="36236-126">复制以下最能满足您需要的一个 XML 结构。</span><span class="sxs-lookup"><span data-stu-id="36236-126">Copy one of the following XML structures that best fits your needs.</span></span> <span data-ttu-id="36236-127">第一个 XML 结构提供了用于指定所有元素的占位符，将在下一部分对这些元素进行介绍：</span><span class="sxs-lookup"><span data-stu-id="36236-127">The first XML structure provides placeholders for specifying all of the elements, which are described in the next section:</span></span>  
  
    ```  
    <Authentication>  
          <AuthenticationTypes>  
                 <RSWindowsBasic>  
                       <LogonMethod>3</LogonMethod>  
                       <Realm></Realm>  
                       <DefaultDomain></DefaultDomain>  
                 </RSWindowsBasic>  
          </AuthenticationTypes>  
          <EnableAuthPersistence>true</EnableAuthPersistence>  
    </Authentication>  
    ```  
  
     <span data-ttu-id="36236-128">如果使用的是默认值，则可复制最小元素结构：</span><span class="sxs-lookup"><span data-stu-id="36236-128">If you are using default values, you can copy the minimum element structure:</span></span>  
  
    ```  
          <AuthenticationTypes>  
                 <RSWindowsBasic/>  
          </AuthenticationTypes>  
    ```  
  
4.  <span data-ttu-id="36236-129">将其粘贴到 <> 的现有条目上 `Authentication` 。</span><span class="sxs-lookup"><span data-stu-id="36236-129">Paste it over the existing entries for <`Authentication`>.</span></span>  
  
     <span data-ttu-id="36236-130">如果使用的是多个身份验证类型，则只能添加 `RSWindowsBasic` 元素，而不能删除 `RSWindowsNegotiate`、`RSWindowsNTLM` 或 `RSWindowsKerberos` 的条目。</span><span class="sxs-lookup"><span data-stu-id="36236-130">If you are using multiple authentication types, add just the `RSWindowsBasic` element but do not delete the entries for `RSWindowsNegotiate`, `RSWindowsNTLM`, or `RSWindowsKerberos`.</span></span>  
  
     <span data-ttu-id="36236-131">若要支持 Safari 浏览器，则不能将报表服务器配置为使用多个身份验证类型。</span><span class="sxs-lookup"><span data-stu-id="36236-131">To support the Safari browser, you cannot configure the report server to use multiple authentication types.</span></span> <span data-ttu-id="36236-132">必须仅指定 `RSWindowsBasic`，并删除其他条目。</span><span class="sxs-lookup"><span data-stu-id="36236-132">You must specify only `RSWindowsBasic` and delete the other entries.</span></span>  
  
     <span data-ttu-id="36236-133">请注意，不能将 `Custom` 与其他身份验证类型一起使用。</span><span class="sxs-lookup"><span data-stu-id="36236-133">Note that you cannot use `Custom` with other authentication types.</span></span>  
  
5.  <span data-ttu-id="36236-134">`Realm`将 <> 或 <> 的空值替换 `DefaultDomain` 为对环境有效的值。</span><span class="sxs-lookup"><span data-stu-id="36236-134">Replace empty values for <`Realm`> or <`DefaultDomain`> with values that are valid for your environment.</span></span>  
  
6.  <span data-ttu-id="36236-135">保存文件。</span><span class="sxs-lookup"><span data-stu-id="36236-135">Save the file.</span></span>  
  
7.  <span data-ttu-id="36236-136">如果配置了扩展部署，请对该部署中的其他报表服务器重复这些步骤。</span><span class="sxs-lookup"><span data-stu-id="36236-136">If you configured a scale-out deployment, repeat these steps for other report servers in the deployment.</span></span>  
  
8.  <span data-ttu-id="36236-137">重新启动报表服务器以清除当前打开的任何会话。</span><span class="sxs-lookup"><span data-stu-id="36236-137">Restart the report server to clear any sessions that are currently open.</span></span>  
  
## <a name="rswindowsbasic-reference"></a><span data-ttu-id="36236-138">RSWindowsBasic 引用</span><span class="sxs-lookup"><span data-stu-id="36236-138">RSWindowsBasic Reference</span></span>  
 <span data-ttu-id="36236-139">配置基本身份验证时，可以指定以下元素。</span><span class="sxs-lookup"><span data-stu-id="36236-139">The following elements can be specified when configuring Basic authentication.</span></span>  
  
|<span data-ttu-id="36236-140">元素</span><span class="sxs-lookup"><span data-stu-id="36236-140">Element</span></span>|<span data-ttu-id="36236-141">必选</span><span class="sxs-lookup"><span data-stu-id="36236-141">Required</span></span>|<span data-ttu-id="36236-142">有效值</span><span class="sxs-lookup"><span data-stu-id="36236-142">Valid Values</span></span>|  
|-------------|--------------|------------------|  
|<span data-ttu-id="36236-143">LogonMethod</span><span class="sxs-lookup"><span data-stu-id="36236-143">LogonMethod</span></span>|<span data-ttu-id="36236-144">是</span><span class="sxs-lookup"><span data-stu-id="36236-144">Yes</span></span><br /><br /> <span data-ttu-id="36236-145">如果不指定值，将使用 3。</span><span class="sxs-lookup"><span data-stu-id="36236-145">If you do not specify a value, 3 will be used.</span></span>|<span data-ttu-id="36236-146">`2` = 网络登录，针对要对纯文本密码进行身份验证的高性能服务器。</span><span class="sxs-lookup"><span data-stu-id="36236-146">`2` = Network logon, intended for high performance servers to authenticate plain text passwords.</span></span><br /><br /> <span data-ttu-id="36236-147">`3` = 明文登录，在此情况下，登录凭据保留在随各 HTTP 请求一起发送的身份验证包中，这样，该服务器在连接到网络中的其他服务器时可以模拟该用户。</span><span class="sxs-lookup"><span data-stu-id="36236-147">`3` = Cleartext logon, which preserves logon credentials in the authentication package that is sent with each HTTP request, allowing the server to impersonate the user when connecting to other servers in the network.</span></span> <span data-ttu-id="36236-148">（默认值）</span><span class="sxs-lookup"><span data-stu-id="36236-148">(Default)</span></span><br /><br /> <span data-ttu-id="36236-149">注意：值 0（针对交互登录）和 1（针对批处理登录）在 [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] 中不受支持。</span><span class="sxs-lookup"><span data-stu-id="36236-149">Note: Values 0 (for interactive logon) and 1 (for batch logon) are not supported in [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)].</span></span>|  
|<span data-ttu-id="36236-150">领域</span><span class="sxs-lookup"><span data-stu-id="36236-150">Realm</span></span>|<span data-ttu-id="36236-151">可选</span><span class="sxs-lookup"><span data-stu-id="36236-151">Optional</span></span>|<span data-ttu-id="36236-152">指定包含授权和身份验证功能的资源分区，这些功能用于控制对组织中受保护资源的访问。</span><span class="sxs-lookup"><span data-stu-id="36236-152">Specifies a resource partition that includes authorization and authentication features used to control access to protected resources in your organization.</span></span>|  
|<span data-ttu-id="36236-153">默认域</span><span class="sxs-lookup"><span data-stu-id="36236-153">DefaultDomain</span></span>|<span data-ttu-id="36236-154">可选</span><span class="sxs-lookup"><span data-stu-id="36236-154">Optional</span></span>|<span data-ttu-id="36236-155">指定服务器用来对用户进行身份验证的域。</span><span class="sxs-lookup"><span data-stu-id="36236-155">Specifies the domain used by the server to authenticate the user.</span></span> <span data-ttu-id="36236-156">此值是可选的。但如果忽略此值，报表服务器会将计算机名称用作域。</span><span class="sxs-lookup"><span data-stu-id="36236-156">This value is optional, but if you omit it the report server will use the computer name as the domain.</span></span> <span data-ttu-id="36236-157">如果计算机是域的成员，则该域是默认域。</span><span class="sxs-lookup"><span data-stu-id="36236-157">If the computer is a member of domain, that domain is the default domain.</span></span> <span data-ttu-id="36236-158">如果在域控制器上安装了报表服务器，则所用的域为该计算机控制的域。</span><span class="sxs-lookup"><span data-stu-id="36236-158">If you installed the report server on a domain controller, the domain used is the one controlled by the computer.</span></span>|  
  
## <a name="enabling-anonymous-access-to-report-builder-application-files"></a><span data-ttu-id="36236-159">启用对报表生成器应用程序文件的匿名访问</span><span class="sxs-lookup"><span data-stu-id="36236-159">Enabling Anonymous Access to Report Builder Application Files</span></span>  
 <span data-ttu-id="36236-160">报表生成器使用 ClickOnce 技术下载其应用程序文件，并在客户端计算机上安装这些文件。</span><span class="sxs-lookup"><span data-stu-id="36236-160">Report Builder uses ClickOnce technology to download and install application files on the client computer.</span></span> <span data-ttu-id="36236-161">当客户端计算机启动 ClickOnce 应用程序时，ClickOnce 应用程序启动程序将发出对报表服务器计算机上的其他应用程序文件的请求。</span><span class="sxs-lookup"><span data-stu-id="36236-161">When it starts on the client computer, the ClickOnce application launcher will make a request for additional application files on the report server computer.</span></span> <span data-ttu-id="36236-162">如果将报表服务器配置为使用基本身份验证，则 ClickOnce 应用程序启动程序将无法进行身份验证检查，因为它不支持基本身份验证。</span><span class="sxs-lookup"><span data-stu-id="36236-162">If the report server is configured for Basic authentication, the ClickOnce application launcher will fail the authentication check because it does not support Basic authentication.</span></span>  
  
 <span data-ttu-id="36236-163">可通过配置对报表生成器程序文件的匿名访问来解决此问题。</span><span class="sxs-lookup"><span data-stu-id="36236-163">To work around this issue, you can configure Anonymous access to the Report Builder program files.</span></span> <span data-ttu-id="36236-164">这样做可使 ClickOnce 在检索其文件时绕过身份验证检查。</span><span class="sxs-lookup"><span data-stu-id="36236-164">Doing so allows ClickOnce to bypass the authentication check when retrieving its files.</span></span> <span data-ttu-id="36236-165">请执行以下操作启用匿名访问：</span><span class="sxs-lookup"><span data-stu-id="36236-165">Enable Anonymous access by doing the following:</span></span>  
  
-   <span data-ttu-id="36236-166">验证报表服务器是否已配置为使用基本身份验证。</span><span class="sxs-lookup"><span data-stu-id="36236-166">Verify that the report server is configured for Basic authentication.</span></span>  
  
-   <span data-ttu-id="36236-167">在 ReportBuilder 下创建 Bin 文件夹，然后将 4 个程序集复制到文件夹中。</span><span class="sxs-lookup"><span data-stu-id="36236-167">Create a bin folder under ReportBuilder and copy four assemblies to the folder.</span></span>  
  
-   <span data-ttu-id="36236-168">将 `IsReportBuilderAnonymousAccessEnabled` 元素添加到 RSReportServer.config，并将其设置为 `True`。</span><span class="sxs-lookup"><span data-stu-id="36236-168">Add the `IsReportBuilderAnonymousAccessEnabled` element to the RSReportServer.config and set it to `True`.</span></span> <span data-ttu-id="36236-169">保存该文件后，报表服务器将创建报表生成器的新端点。</span><span class="sxs-lookup"><span data-stu-id="36236-169">After you save the file, the report server creates a new endpoint to Report Builder.</span></span> <span data-ttu-id="36236-170">该端点将内部用于访问程序文件，并且不具有可在代码中使用的编程接口。</span><span class="sxs-lookup"><span data-stu-id="36236-170">The endpoint is used internally to access program files and does not have a programmatic interface that you can use in code.</span></span> <span data-ttu-id="36236-171">具有不同的端点可使报表生成器在报表服务器服务进程边界中其自己的应用程序域中运行。</span><span class="sxs-lookup"><span data-stu-id="36236-171">Having a separate endpoint allows Report Builder to run in its own application domain within the Report Server service process boundary.</span></span>  
  
-   <span data-ttu-id="36236-172">还可以指定最低特权帐户以在与报表服务器不同的安全上下文下处理请求。</span><span class="sxs-lookup"><span data-stu-id="36236-172">Optionally, you can specify a least-privilege account to process requests under a security context that is different from the report server.</span></span> <span data-ttu-id="36236-173">此帐户将成为匿名帐户，用于访问报表服务器上的报表生成器文件。</span><span class="sxs-lookup"><span data-stu-id="36236-173">This account becomes the anonymous account for accessing Report Builder files on a report server.</span></span> <span data-ttu-id="36236-174">该帐户在 ASP.NET 工作进程中设置线程的标识。</span><span class="sxs-lookup"><span data-stu-id="36236-174">The account sets the identity of the thread in the ASP.NET worker process.</span></span> <span data-ttu-id="36236-175">该线程中运行的请求会被传递到报表服务器，而不进行身份验证检查。</span><span class="sxs-lookup"><span data-stu-id="36236-175">Requests that run in that thread are passed to the report server without an authentication check.</span></span> <span data-ttu-id="36236-176">此帐户等效于 \<machine> Internet Information Services (IIS) 中的 IUSR_ 帐户，该帐户用于在启用匿名访问和模拟时设置 ASP.NET 工作进程的安全上下文。</span><span class="sxs-lookup"><span data-stu-id="36236-176">This account is equivalent to the IUSR_\<machine> account in Internet Information Services (IIS), which is used to set the security context for ASP.NET worker processes when Anonymous access and impersonation are enabled.</span></span> <span data-ttu-id="36236-177">若要指定该帐户，需要将其添加到报表生成器 Web.config 文件中。</span><span class="sxs-lookup"><span data-stu-id="36236-177">To specify the account, you add it to a Report Builder Web.config file.</span></span>  
  
 <span data-ttu-id="36236-178">若要启用对报表生成器程序文件的匿名访问，必须将报表服务器配置为使用基本身份验证。</span><span class="sxs-lookup"><span data-stu-id="36236-178">The report server must be configured for Basic authentication if you want to enable Anonymous access to the Report Builder program files.</span></span> <span data-ttu-id="36236-179">如果未将报表服务器配置为使用基本身份验证，在尝试启用匿名访问时，将收到一个错误。</span><span class="sxs-lookup"><span data-stu-id="36236-179">If the report server is not configured for Basic authentication, you will get an error when you attempt to enable Anonymous access.</span></span>  
  
 <span data-ttu-id="36236-180">有关身份验证问题和报表生成器的详细信息，请参阅[配置报表生成器访问权限](../report-server/configure-report-builder-access.md)。</span><span class="sxs-lookup"><span data-stu-id="36236-180">For more information about authentication issues and Report Builder, see [Configure Report Builder Access](../report-server/configure-report-builder-access.md).</span></span>  
  
#### <a name="to-configure-report-builder-access-on-a-report-server-configured-for-basic-authentication"></a><span data-ttu-id="36236-181">在配置为使用基本身份验证的报表服务器上配置报表生成器访问</span><span class="sxs-lookup"><span data-stu-id="36236-181">To configure Report Builder access on a report server configured for Basic authentication</span></span>  
  
1.  <span data-ttu-id="36236-182">通过检查 RSReportServer.config 文件中的身份验证设置来验证报表服务器是否配置为使用基本身份验证。</span><span class="sxs-lookup"><span data-stu-id="36236-182">Verify the report server is configured for Basic authentication by checking the authentication settings in the RSReportServer.config file.</span></span>  
  
2.  <span data-ttu-id="36236-183">在 ReportBuilder 文件夹下创建一个 BIN 文件夹。</span><span class="sxs-lookup"><span data-stu-id="36236-183">Create a BIN folder under the ReportBuilder folder.</span></span> <span data-ttu-id="36236-184">默认情况下，该文件夹位于 \Program Files\Microsoft SQL Server\MSRS12.MSSQLSERVER\Reporting Services\ReportServer\ReportBuilder。</span><span class="sxs-lookup"><span data-stu-id="36236-184">By default, this folder is located at \Program Files\Microsoft SQL Server\MSRS12.MSSQLSERVER\Reporting Services\ReportServer\ReportBuilder.</span></span>  
  
3.  <span data-ttu-id="36236-185">将以下程序集从 ReportServer\Bin 文件夹复制到 ReportBuilder\BIN 文件夹中：</span><span class="sxs-lookup"><span data-stu-id="36236-185">Copy the following assemblies from the ReportServer\Bin folder to the ReportBuilder\BIN folder:</span></span>  
  
     <span data-ttu-id="36236-186">Microsoft.ReportingServices.Diagnostics.dll</span><span class="sxs-lookup"><span data-stu-id="36236-186">Microsoft.ReportingServices.Diagnostics.dll</span></span>  
  
     <span data-ttu-id="36236-187">Microsoft.ReportingServices.Interfaces.dll</span><span class="sxs-lookup"><span data-stu-id="36236-187">Microsoft.ReportingServices.Interfaces.dll</span></span>  
  
     <span data-ttu-id="36236-188">ReportingServicesAppDomainManager.dll</span><span class="sxs-lookup"><span data-stu-id="36236-188">ReportingServicesAppDomainManager.dll</span></span>  
  
     <span data-ttu-id="36236-189">RSHttpRuntime.dll</span><span class="sxs-lookup"><span data-stu-id="36236-189">RSHttpRuntime.dll</span></span>  
  
4.  <span data-ttu-id="36236-190">还可以创建一个 Web.config 文件以在匿名帐户下处理报表生成器请求：</span><span class="sxs-lookup"><span data-stu-id="36236-190">Optionally, create a Web.config file to process Report Builder requests under an Anonymous account:</span></span>  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
    <system.web>  
    <authentication mode="Windows" />    
    <identity impersonate="true " userName="username" password="password"/>  
    </system.web>  
    </configuration>  
    ```  
  
     <span data-ttu-id="36236-191">如果包含一个 Web.config 文件，则必须将身份验证模式设置为 `Windows`。</span><span class="sxs-lookup"><span data-stu-id="36236-191">Authentication mode must be set to `Windows` if you include a Web.config file.</span></span>  
  
     <span data-ttu-id="36236-192">`Identity impersonate` 可以是 `True` 或 `False`。</span><span class="sxs-lookup"><span data-stu-id="36236-192">`Identity impersonate` can be `True` or `False`.</span></span>  
  
    -   <span data-ttu-id="36236-193">如果不希望 ASP.NET 读取安全令牌，则将它设置为 `False`。</span><span class="sxs-lookup"><span data-stu-id="36236-193">Set it to `False` if you do not want ASP.NET to read the security token.</span></span> <span data-ttu-id="36236-194">该请求将在报表服务器服务的安全上下文中运行。</span><span class="sxs-lookup"><span data-stu-id="36236-194">The request will run in the security context of the Report Server service.</span></span>  
  
    -   <span data-ttu-id="36236-195">如果希望 ASP.NET 从宿主层读取安全令牌，则将它设置为 `True`。</span><span class="sxs-lookup"><span data-stu-id="36236-195">Set it to `True` if you want ASP.NET to read the security token from the host layer.</span></span> <span data-ttu-id="36236-196">如果设置为 `True`，还必须指定 `userName` 和 `password` 来指定一个匿名帐户。</span><span class="sxs-lookup"><span data-stu-id="36236-196">If you set it to `True`, you must also specify `userName` and `password` to designate an Anonymous account.</span></span> <span data-ttu-id="36236-197">您指定的凭据将确定发出请求时所处的安全上下文。</span><span class="sxs-lookup"><span data-stu-id="36236-197">The credentials you specify will determine the security context under which the request is issued.</span></span>  
  
5.  <span data-ttu-id="36236-198">将 Web.config 文件保存到 ReportBuilder\bin 文件夹。</span><span class="sxs-lookup"><span data-stu-id="36236-198">Save the Web.config file to the ReportBuilder\bin folder.</span></span>  
  
6.  <span data-ttu-id="36236-199">打开 RSReportServer.config 文件，在“Services”部分中查找 `IsReportManagerEnabled`，然后在其下添加以下设置：</span><span class="sxs-lookup"><span data-stu-id="36236-199">Open RSReportServer.config file, in the Services section, find `IsReportManagerEnabled` and add the following setting below it:</span></span>  
  
    ```  
    <IsReportBuilderAnonymousAccessEnabled>True</IsReportBuilderAnonymousAccessEnabled>  
    ```  
  
7.  <span data-ttu-id="36236-200">保存 RSReportServer.config 并关闭该文件。</span><span class="sxs-lookup"><span data-stu-id="36236-200">Save RSReportServer.config and close the file.</span></span>  
  
8.  <span data-ttu-id="36236-201">重新启动报表服务器。</span><span class="sxs-lookup"><span data-stu-id="36236-201">Restart the report server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36236-202">另请参阅</span><span class="sxs-lookup"><span data-stu-id="36236-202">See Also</span></span>  
 <span data-ttu-id="36236-203">[报表服务器应用程序的应用程序域](../report-server/application-domains-for-report-server-applications.md) </span><span class="sxs-lookup"><span data-stu-id="36236-203">[Application Domains for Report Server Applications](../report-server/application-domains-for-report-server-applications.md) </span></span>  
 [<span data-ttu-id="36236-204">Reporting Services 安全性和保护</span><span class="sxs-lookup"><span data-stu-id="36236-204">Reporting Services Security and Protection</span></span>](reporting-services-security-and-protection.md)  
  
  
