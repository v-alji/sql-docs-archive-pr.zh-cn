---
title: Reporting Services 中的身份验证 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- security [Reporting Services], authentication
- forms-based authentication [Reporting Services]
- authentication [Reporting Services]
- custom authentication [Reporting Services]
ms.assetid: 103ce1f9-31d8-44bb-b540-2752e4dcf60b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 59e97ba6ef849d8b4bfddfd6953c85826e351d6e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587224"
---
# <a name="authentication-in-reporting-services"></a><span data-ttu-id="f6d8e-102">Reporting Services 中的身份验证</span><span class="sxs-lookup"><span data-stu-id="f6d8e-102">Authentication in Reporting Services</span></span>
  <span data-ttu-id="f6d8e-103">身份验证是确立用户对某一身份的权限的过程。</span><span class="sxs-lookup"><span data-stu-id="f6d8e-103">Authentication is the process of establishing a user's right to an identity.</span></span> <span data-ttu-id="f6d8e-104">您可以使用多种方法来验证某一用户的身份。</span><span class="sxs-lookup"><span data-stu-id="f6d8e-104">There are many techniques that you can use to authenticate a user.</span></span> <span data-ttu-id="f6d8e-105">最常见的方法是使用密码。</span><span class="sxs-lookup"><span data-stu-id="f6d8e-105">The most common way is to use passwords.</span></span> <span data-ttu-id="f6d8e-106">例如，在实现窗体身份验证时，您希望某一实现查询用户的凭据（通常通过请求提供登录名和密码的某些界面），然后根据数据存储区（例如数据库表或配置文件）验证用户。</span><span class="sxs-lookup"><span data-stu-id="f6d8e-106">When you implement Forms Authentication, for example, you want an implementation that queries users for credentials (usually by some interface that requests a login name and password) and then validates users against a data store, such as a database table or configuration file.</span></span> <span data-ttu-id="f6d8e-107">如果无法验证凭据，该身份验证过程将失败，并且用户将假定匿名身份。</span><span class="sxs-lookup"><span data-stu-id="f6d8e-107">If the credentials can't be validated, the authentication process fails and the user will assume an anonymous identity.</span></span>  
  
## <a name="custom-authentication-in-reporting-services"></a><span data-ttu-id="f6d8e-108">Reporting Services 中的自定义身份验证</span><span class="sxs-lookup"><span data-stu-id="f6d8e-108">Custom Authentication in Reporting Services</span></span>  
 <span data-ttu-id="f6d8e-109">在 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中，Windows 操作系统通过集成的安全性或通过用户凭据的显式接受和验证，处理用户的身份验证。</span><span class="sxs-lookup"><span data-stu-id="f6d8e-109">In [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], the Windows operating system handles the authentication of users either through integrated security or through the explicit reception and validation of user credentials.</span></span> <span data-ttu-id="f6d8e-110">可以在 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中开发自定义身份验证，以支持附加的身份验证架构。</span><span class="sxs-lookup"><span data-stu-id="f6d8e-110">Custom authentication can be developed in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] to support additional authentication schemes.</span></span> <span data-ttu-id="f6d8e-111">这可以通过安全扩展插件接口 <xref:Microsoft.ReportingServices.Interfaces.IAuthenticationExtension> 实现。</span><span class="sxs-lookup"><span data-stu-id="f6d8e-111">This is made possible through the security extension interface <xref:Microsoft.ReportingServices.Interfaces.IAuthenticationExtension>.</span></span> <span data-ttu-id="f6d8e-112">所有扩展插件都继承自报表服务器部署和使用的任何扩展插件的 <xref:Microsoft.ReportingServices.Interfaces.IExtension> 基接口。</span><span class="sxs-lookup"><span data-stu-id="f6d8e-112">All extensions inherit from the <xref:Microsoft.ReportingServices.Interfaces.IExtension> base interface for any extension deployed and used by the report server.</span></span> <span data-ttu-id="f6d8e-113"><xref:Microsoft.ReportingServices.Interfaces.IExtension> 以及 <xref:Microsoft.ReportingServices.Interfaces.IAuthenticationExtension> 是 <xref:Microsoft.ReportingServices.Interfaces> 命名空间的成员。</span><span class="sxs-lookup"><span data-stu-id="f6d8e-113"><xref:Microsoft.ReportingServices.Interfaces.IExtension>, as well as <xref:Microsoft.ReportingServices.Interfaces.IAuthenticationExtension>, are members of the <xref:Microsoft.ReportingServices.Interfaces> namespace.</span></span>  
  
 <span data-ttu-id="f6d8e-114">在 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中对报表服务器进行身份验证的主要方式是 <xref:ReportService2010.ReportingService2010.LogonUser%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="f6d8e-114">The primary way to authenticate against a report server in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] is the <xref:ReportService2010.ReportingService2010.LogonUser%2A> method.</span></span> <span data-ttu-id="f6d8e-115">此 Reporting Services Web 服务成员可用于将用户凭据传递到某一报表服务器以进行验证。</span><span class="sxs-lookup"><span data-stu-id="f6d8e-115">This member of the Reporting Services Web service can be used to pass user credentials to a report server for validation.</span></span> <span data-ttu-id="f6d8e-116">基础安全扩展插件实现包含自定义身份验证代码的**IAuthenticationExtension。**</span><span class="sxs-lookup"><span data-stu-id="f6d8e-116">Your underlying security extension implements **IAuthenticationExtension.LogonUser** which contains your custom authentication code.</span></span> <span data-ttu-id="f6d8e-117">在窗体身份验证示例 LogonUser 中，对提供的凭据和数据库中的自定义用户存储执行身份验证检查  。</span><span class="sxs-lookup"><span data-stu-id="f6d8e-117">In the Forms Authentication sample, **LogonUser**, which performs an authentication check against the supplied credentials and a custom user store in a database.</span></span> <span data-ttu-id="f6d8e-118">LogonUser 的实现的示例如下  ：</span><span class="sxs-lookup"><span data-stu-id="f6d8e-118">An example of an implementation of **LogonUser** looks like this:</span></span>  
  
```  
public bool LogonUser(string userName, string password, string authority)  
{  
   return AuthenticationUtilities.VerifyPassword(userName, password);  
}  
  
```  
  
 <span data-ttu-id="f6d8e-119">以下示例函数用于验证提供的凭据：</span><span class="sxs-lookup"><span data-stu-id="f6d8e-119">The following sample function is used to verify the supplied credentials:</span></span>  
  
```  
  
internal static bool VerifyPassword(string suppliedUserName,  
   string suppliedPassword)  
{   
   bool passwordMatch = false;  
   // Get the salt and pwd from the database based on the user name.  
   // See "How To: Use DPAPI (Machine Store) from ASP.NET," "How To:  
   // Use DPAPI (User Store) from Enterprise Services," and "How To:  
   // Create a DPAPI Library" for more information about how to use  
   // DPAPI to securely store connection strings.  
   SqlConnection conn = new SqlConnection(  
      "Server=localhost;" +   
      "Integrated Security=SSPI;" +  
      "database=UserAccounts");  
   SqlCommand cmd = new SqlCommand("LookupUser", conn);  
   cmd.CommandType = CommandType.StoredProcedure;  
  
   SqlParameter sqlParam = cmd.Parameters.Add("@userName",  
       SqlDbType.VarChar,  
       255);  
   sqlParam.Value = suppliedUserName;  
   try  
   {  
      conn.Open();  
      SqlDataReader reader = cmd.ExecuteReader();  
      reader.Read(); // Advance to the one and only row  
      // Return output parameters from returned data stream  
      string dbPasswordHash = reader.GetString(0);  
      string salt = reader.GetString(1);  
      reader.Close();  
      // Now take the salt and the password entered by the user  
      // and concatenate them together.  
      string passwordAndSalt = String.Concat(suppliedPassword, salt);  
      // Now hash them  
      string hashedPasswordAndSalt =  
         FormsAuthentication.HashPasswordForStoringInConfigFile(  
         passwordAndSalt,  
         "SHA1");  
      // Now verify them. Returns true if they are equal.  
      passwordMatch = hashedPasswordAndSalt.Equals(dbPasswordHash);  
   }  
   catch (Exception ex)  
   {  
       throw new Exception("Exception verifying password. " +  
          ex.Message);  
   }  
   finally  
   {  
       conn.Close();  
   }  
   return passwordMatch;  
}  
```  
  
## <a name="authentication-flow"></a><span data-ttu-id="f6d8e-120">身份验证流程</span><span class="sxs-lookup"><span data-stu-id="f6d8e-120">Authentication Flow</span></span>  
 <span data-ttu-id="f6d8e-121">Reporting Services Web 服务提供自定义身份验证扩展插件，以便支持通过报表管理器和报表服务器进行窗体身份验证。</span><span class="sxs-lookup"><span data-stu-id="f6d8e-121">The Reporting Services Web service provides custom authentication extensions to enable Forms Authentication by Report Manager and the report server.</span></span>  
  
 <span data-ttu-id="f6d8e-122">Reporting Services Web 服务的 <xref:ReportService2010.ReportingService2010.LogonUser%2A> 方法用于将凭据提交到报表服务器以供身份验证。</span><span class="sxs-lookup"><span data-stu-id="f6d8e-122">The <xref:ReportService2010.ReportingService2010.LogonUser%2A> method of the Reporting Services Web service is used to submit credentials to the report server for authentication.</span></span> <span data-ttu-id="f6d8e-123">该 Web 服务使用 HTTP 标头将身份验证票证（通称为“cookie”）从服务器传递到客户端，以便用于已验证的登录请求。</span><span class="sxs-lookup"><span data-stu-id="f6d8e-123">The Web service uses HTTP headers to pass an authentication ticket (known as a "cookie") from the server to the client for validated logon requests.</span></span>  
  
 <span data-ttu-id="f6d8e-124">下图描述了在您使用配置为使用自定义身份验证扩展插件的报表服务器部署应用程序时，向该 Web 服务验证用户身份的方法。</span><span class="sxs-lookup"><span data-stu-id="f6d8e-124">The following illustration depicts the method of authenticating users to the Web service when your application is deployed with a report server configured to use a custom authentication extension.</span></span>  
  
 <span data-ttu-id="f6d8e-125">![Reporting Services 安全身份验证流程](../../media/rosettasecurityextensionauthenticationflow.gif "Reporting Services 安全身份验证流程")</span><span class="sxs-lookup"><span data-stu-id="f6d8e-125">![Reporting Services security authentication flow](../../media/rosettasecurityextensionauthenticationflow.gif "Reporting Services security authentication flow")</span></span>  
  
 <span data-ttu-id="f6d8e-126">如图 2 中所示，该身份验证流程如下：</span><span class="sxs-lookup"><span data-stu-id="f6d8e-126">As shown in Figure 2, the authentication process is as follows:</span></span>  
  
1.  <span data-ttu-id="f6d8e-127">客户端应用程序调用 Web 服务 <xref:ReportService2010.ReportingService2010.LogonUser%2A> 方法以便验证某一用户的身份。</span><span class="sxs-lookup"><span data-stu-id="f6d8e-127">A client application calls the Web service <xref:ReportService2010.ReportingService2010.LogonUser%2A> method to authenticate a user.</span></span>  
  
2.  <span data-ttu-id="f6d8e-128">Web 服务调用 <xref:ReportService2010.ReportingService2010.LogonUser%2A> 安全扩展插件的方法，具体而言，就是实现**IAuthenticationExtension**的类。</span><span class="sxs-lookup"><span data-stu-id="f6d8e-128">The Web service makes a call to the <xref:ReportService2010.ReportingService2010.LogonUser%2A> method of your security extension, specifically, the class that implements **IAuthenticationExtension**.</span></span>  
  
3.  <span data-ttu-id="f6d8e-129">您的 <xref:ReportService2010.ReportingService2010.LogonUser%2A> 实现验证用户存储或安全机构中的用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="f6d8e-129">Your implementation of <xref:ReportService2010.ReportingService2010.LogonUser%2A> validates the user name and password in the user store or security authority.</span></span>  
  
4.  <span data-ttu-id="f6d8e-130">在成功进行身份验证后，该 Web 服务将创建一个 cookie 并为会话管理它。</span><span class="sxs-lookup"><span data-stu-id="f6d8e-130">Upon successful authentication, the Web service creates a cookie and manages it for the session.</span></span>  
  
5.  <span data-ttu-id="f6d8e-131">该 Web 服务将该身份验证票证返回到调用应用程序的 HTTP 标头上。</span><span class="sxs-lookup"><span data-stu-id="f6d8e-131">The Web service returns the authentication ticket to the calling application on the HTTP header.</span></span>  
  
 <span data-ttu-id="f6d8e-132">在该 Web 服务成功通过安全扩展插件验证用户身份后，它将生成用于后续请求的 cookie。</span><span class="sxs-lookup"><span data-stu-id="f6d8e-132">When the Web service successfully authenticates a user through the security extension, it generates a cookie that is used for subsequent requests.</span></span> <span data-ttu-id="f6d8e-133">该 cookie 可能不会在自定义安全机构内持久化，因为报表服务器不拥有该安全机构。</span><span class="sxs-lookup"><span data-stu-id="f6d8e-133">The cookie may not persist within the custom security authority because the report server does not own the security authority.</span></span> <span data-ttu-id="f6d8e-134">该 cookie 从 <xref:ReportService2010.ReportingService2010.LogonUser%2A> Web 服务方法返回并且用于后续的 Web 服务方法调用和 URL 访问中。</span><span class="sxs-lookup"><span data-stu-id="f6d8e-134">The cookie is returned from the <xref:ReportService2010.ReportingService2010.LogonUser%2A> Web service method and is used in subsequent Web service method calls and in URL access.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f6d8e-135">为了避免在传输期间损坏 cookie，从 <xref:ReportService2010.ReportingService2010.LogonUser%2A> 返回的身份验证 cookie 应使用安全套接字层 (SSL) 加密安全地传输。</span><span class="sxs-lookup"><span data-stu-id="f6d8e-135">In order to avoid compromising the cookie during transmission, authentication cookies returned from <xref:ReportService2010.ReportingService2010.LogonUser%2A> should be transmitted securely using Secure Sockets Layer (SSL) encryption.</span></span>  
  
 <span data-ttu-id="f6d8e-136">如果您在安装自定义安全扩展插件时通过 URL 访问报表服务器，则 Internet 信息服务 (IIS) 和 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 将自动管理身份验证票证的传输。</span><span class="sxs-lookup"><span data-stu-id="f6d8e-136">If you access the report server through URL access when a custom security extension is installed, Internet Information Services (IIS) and [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] automatically manage the transmission of the authentication ticket.</span></span> <span data-ttu-id="f6d8e-137">如果您在通过 SOAP API 访问报表服务器，则您的代理类的实现必须包括用于管理身份验证票证的附加支持。</span><span class="sxs-lookup"><span data-stu-id="f6d8e-137">If you are accessing the report server through the SOAP API, your implementation of the proxy class must include additional support for managing the authentication ticket.</span></span> <span data-ttu-id="f6d8e-138">有关使用 SOAP API 和管理身份验证票证的详细信息，请参阅“使用具有自定义安全性的 Web 服务”。</span><span class="sxs-lookup"><span data-stu-id="f6d8e-138">For more information about using the SOAP API and managing the authentication ticket, see "Using the Web Service with Custom Security."</span></span>  
  
## <a name="forms-authentication"></a><span data-ttu-id="f6d8e-139">窗体身份验证</span><span class="sxs-lookup"><span data-stu-id="f6d8e-139">Forms Authentication</span></span>  
 <span data-ttu-id="f6d8e-140">窗体身份验证是一种 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 身份验证，其中，未经身份验证的用户定向到某一 HTML 窗体。</span><span class="sxs-lookup"><span data-stu-id="f6d8e-140">Forms Authentication is a type of [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] authentication in which an unauthenticated user is directed to an HTML form.</span></span> <span data-ttu-id="f6d8e-141">一旦用户提供凭据后，系统将发出包含身份验证票证的 cookie。</span><span class="sxs-lookup"><span data-stu-id="f6d8e-141">Once the user provides credentials, the system issues a cookie containing an authentication ticket.</span></span> <span data-ttu-id="f6d8e-142">对于以后的请求，系统首先检查 cookie 以确定报表服务器是否已验证用户的身份。</span><span class="sxs-lookup"><span data-stu-id="f6d8e-142">On later requests, the system first checks the cookie to see if the user was already authenticated by the report server.</span></span>  
  
 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="f6d8e-143">可以扩展，以便使用可通过 Reporting Services API 提供的安全可扩展接口支持窗体身份验证。</span><span class="sxs-lookup"><span data-stu-id="f6d8e-143">can be extended to support Forms Authentication using the security extensibility interfaces available through the Reporting Services API.</span></span> <span data-ttu-id="f6d8e-144">如果您扩展 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 以使用窗体身份验证，则将安全套接字层 (SSL) 用于与报表服务器的全部通信，以便防止恶意用户获取对其他用户的 cookie 的访问。</span><span class="sxs-lookup"><span data-stu-id="f6d8e-144">If you extend [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] to use Forms Authentication, use Secure Sockets Layer (SSL) for all communications with the report server to prevent malicious users from gaining access to another user's cookie.</span></span> <span data-ttu-id="f6d8e-145">SSL 使客户端和报表服务器能够彼此进行身份验证，并且确保没有其他计算机可以读取两台计算机之间的通信内容。</span><span class="sxs-lookup"><span data-stu-id="f6d8e-145">SSL enables clients and a report server to authenticate each other and to ensure that no other computers can read the contents of communications between the two computers.</span></span> <span data-ttu-id="f6d8e-146">通过 SSL 连接从客户端传送的所有数据都进行加密，以便恶意用户无法截获发送给报表服务器的密码或数据。</span><span class="sxs-lookup"><span data-stu-id="f6d8e-146">All data sent from a client through an SSL connection is encrypted so that malicious users cannot intercept passwords or data sent to a report server.</span></span>  
  
 <span data-ttu-id="f6d8e-147">实现窗体身份验证通常是为了支持针对非 Windows 的其他平台的帐户和身份验证。</span><span class="sxs-lookup"><span data-stu-id="f6d8e-147">Forms Authentication is generally implemented to support accounts and authentication for platforms other than Windows.</span></span> <span data-ttu-id="f6d8e-148">向请求对某一报表服务器的访问的用户提供一个图形界面，并且提供的凭据将提交到安全机构以便进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="f6d8e-148">A graphical interface is presented to a user who requests access to a report server, and the supplied credentials are submitted to a security authority for authentication.</span></span>  
  
 <span data-ttu-id="f6d8e-149">窗体身份验证要求某一人输入凭据。</span><span class="sxs-lookup"><span data-stu-id="f6d8e-149">Forms Authentication requires that a person is present to enter credentials.</span></span> <span data-ttu-id="f6d8e-150">对于直接与 Reporting Services Web service 服务通信的无人参与应用程序，窗体身份验证必须与自定义身份验证架构相结合。</span><span class="sxs-lookup"><span data-stu-id="f6d8e-150">For unattended applications that communicate directly with the Reporting Services Web service, Forms Authentication must be combined with a custom authentication scheme.</span></span>  
  
 <span data-ttu-id="f6d8e-151">在以下情况下窗体身份验证适用于 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]：</span><span class="sxs-lookup"><span data-stu-id="f6d8e-151">Forms Authentication is appropriate for [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] when:</span></span>  
  
-   <span data-ttu-id="f6d8e-152">您需要存储不具有 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows 帐户的用户并验证其身份，并且</span><span class="sxs-lookup"><span data-stu-id="f6d8e-152">You need to store and authenticate users that do not have [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows accounts, and</span></span>  
  
-   <span data-ttu-id="f6d8e-153">您需要提供您自己的用户界面窗体作为某一网站上不同页之间的登录页。</span><span class="sxs-lookup"><span data-stu-id="f6d8e-153">You need to provide your own user interface form as a logon page between different pages on a Web site.</span></span>  
  
 <span data-ttu-id="f6d8e-154">在编写支持窗体身份验证的自定义安全扩展插件时，应注意以下事项：</span><span class="sxs-lookup"><span data-stu-id="f6d8e-154">Consider the following when writing a custom security extension that supports Forms Authentication:</span></span>  
  
-   <span data-ttu-id="f6d8e-155">如果您使用窗体身份验证，则必须在 Internet 信息服务 (IIS) 的报表服务器虚拟目录上启用匿名访问。</span><span class="sxs-lookup"><span data-stu-id="f6d8e-155">If you use Forms Authentication, anonymous access must be enabled on the report server virtual directory in Internet Information Services (IIS).</span></span>  
  
-   [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] <span data-ttu-id="f6d8e-156">身份验证必须设置为“窗体”。</span><span class="sxs-lookup"><span data-stu-id="f6d8e-156">authentication must be set to Forms.</span></span> <span data-ttu-id="f6d8e-157">在报表服务器的 Web.config 文件中配置 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 身份验证。</span><span class="sxs-lookup"><span data-stu-id="f6d8e-157">You configure [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] authentication in the Web.config file for the report server.</span></span>  
  
-   [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="f6d8e-158">在验证用户的身份并为其授权时，既可以使用 Windows 身份验证，也可以使用自定义身份验证，但不能同时使用二者。</span><span class="sxs-lookup"><span data-stu-id="f6d8e-158">can authenticate and authorize users with either Windows Authentication or custom authentication, but not both.</span></span> [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="f6d8e-159">不支持同时使用多个安全扩展插件。</span><span class="sxs-lookup"><span data-stu-id="f6d8e-159">does not support simultaneous use of multiple security extensions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6d8e-160">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f6d8e-160">See Also</span></span>  
 [<span data-ttu-id="f6d8e-161">实现安全扩展插件</span><span class="sxs-lookup"><span data-stu-id="f6d8e-161">Implementing a Security Extension</span></span>](../security-extension/implementing-a-security-extension.md)  
  
  
