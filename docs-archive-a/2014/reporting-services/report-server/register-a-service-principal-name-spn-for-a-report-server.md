---
title: 为报表服务器注册服务主体名称 (SPN) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: dda91d4f-77cc-4898-ad03-810ece5f8e74
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 502170f16aad66757e8f44419ccbac3017072449
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591130"
---
# <a name="register-a-service-principal-name-spn-for-a-report-server"></a><span data-ttu-id="39195-102">为报表服务器注册服务主体名称 (SPN)</span><span class="sxs-lookup"><span data-stu-id="39195-102">Register a Service Principal Name (SPN) for a Report Server</span></span>
  <span data-ttu-id="39195-103">如果要在使用 Kerberos 协议进行相互身份验证的网络中部署 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ，并且将报表服务器服务配置为以域用户帐户身份运行，则必须为报表服务器服务创建服务主体名称 (SPN)。</span><span class="sxs-lookup"><span data-stu-id="39195-103">If you are deploying [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in a network that uses the Kerberos protocol for mutual authentication, you must create a Service Principal Name (SPN) for the Report Server service if you configure it to run as a domain user account.</span></span>  
  
## <a name="about-spns"></a><span data-ttu-id="39195-104">关于 SPN</span><span class="sxs-lookup"><span data-stu-id="39195-104">About SPNs</span></span>  
 <span data-ttu-id="39195-105">SPN 是服务在使用 Kerberos 身份验证的网络上的唯一标识符。</span><span class="sxs-lookup"><span data-stu-id="39195-105">An SPN is a unique identifier for a service on a network that uses Kerberos authentication.</span></span> <span data-ttu-id="39195-106">它由服务类、主机名和端口组成。</span><span class="sxs-lookup"><span data-stu-id="39195-106">It consists of a service class, a host name, and a port.</span></span> <span data-ttu-id="39195-107">在使用 Kerberos 身份验证的网络中，必须在内置计算机帐户（如 NetworkService 或 LocalSystem）或用户帐户下为服务器注册 SPN。</span><span class="sxs-lookup"><span data-stu-id="39195-107">On a network that uses Kerberos authentication, an SPN for the server must be registered under either a built-in computer account (such as NetworkService or LocalSystem) or user account.</span></span> <span data-ttu-id="39195-108">对于内置帐户，SPN 将自动进行注册。</span><span class="sxs-lookup"><span data-stu-id="39195-108">SPNs are registered for built-in accounts automatically.</span></span> <span data-ttu-id="39195-109">但是，如果在域用户帐户下运行服务，则必须为要使用的帐户手动注册 SPN。</span><span class="sxs-lookup"><span data-stu-id="39195-109">However, when you run a service under a domain user account, you must manually register the SPN for the account you want to use.</span></span>  
  
 <span data-ttu-id="39195-110">若要创建 SPN，可以使用 **SetSPN** 命令行实用工具。</span><span class="sxs-lookup"><span data-stu-id="39195-110">To create an SPN, you can use the **SetSPN** command line utility.</span></span> <span data-ttu-id="39195-111">有关详细信息，请参阅以下主题：</span><span class="sxs-lookup"><span data-stu-id="39195-111">For more information, see the following:</span></span>  
  
-   <span data-ttu-id="39195-112">[Setspn](https://technet.microsoft.com/library/cc731241\(WS.10\).aspx) (https://technet.microsoft.com/library/cc731241(WS.10).aspx) 。</span><span class="sxs-lookup"><span data-stu-id="39195-112">[Setspn](https://technet.microsoft.com/library/cc731241\(WS.10\).aspx) (https://technet.microsoft.com/library/cc731241(WS.10).aspx).</span></span>  
  
-   <span data-ttu-id="39195-113">[服务主体名称 (spn) SetSPN 语法 ( # A0) ](https://social.technet.microsoft.com/wiki/contents/articles/717.service-principal-names-spns-setspn-syntax-setspn-exe.aspx) (https://social.technet.microsoft.com/wiki/contents/articles/717.service-principal-names-spns-setspn-syntax-setspn-exe.aspx) 。</span><span class="sxs-lookup"><span data-stu-id="39195-113">[Service Principal Names (SPNs) SetSPN Syntax (Setspn.exe)](https://social.technet.microsoft.com/wiki/contents/articles/717.service-principal-names-spns-setspn-syntax-setspn-exe.aspx) (https://social.technet.microsoft.com/wiki/contents/articles/717.service-principal-names-spns-setspn-syntax-setspn-exe.aspx).</span></span>  
  
 <span data-ttu-id="39195-114">您必须具有域管理员身份，才能在域控制器上运行该实用工具。</span><span class="sxs-lookup"><span data-stu-id="39195-114">You must be a domain administrator to run the utility on the domain controller.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39195-115">语法</span><span class="sxs-lookup"><span data-stu-id="39195-115">Syntax</span></span>  
 <span data-ttu-id="39195-116">使用 SetSPN 实用工具为报表服务器创建 SPN 的命令语法类似如下所示：</span><span class="sxs-lookup"><span data-stu-id="39195-116">The command syntax for using SetSPN utility to create an SPN for the report server resembles the following:</span></span>  
  
```  
Setspn -s http/<computername>.<domainname>:<port> <domain-user-account>  
```  
  
 <span data-ttu-id="39195-117">**SetSPN** 随 Windows Server 一起提供。</span><span class="sxs-lookup"><span data-stu-id="39195-117">**SetSPN** is available with Windows Server.</span></span> <span data-ttu-id="39195-118">`-s` 参数在验证不存在重复项后添加一个 SPN。</span><span class="sxs-lookup"><span data-stu-id="39195-118">The `-s` argument adds a SPN after validating no duplicate exists.</span></span> <span data-ttu-id="39195-119">**注意：-s** 从 Windows Server 2008 开始已在 Windows Server 中提供。</span><span class="sxs-lookup"><span data-stu-id="39195-119">**NOTE:-s** is available in Windows Server starting with Windows Server 2008.</span></span>  
  
 <span data-ttu-id="39195-120">`HTTP` 为服务类。</span><span class="sxs-lookup"><span data-stu-id="39195-120">`HTTP` is the service class.</span></span> <span data-ttu-id="39195-121">报表服务器 Web 服务在 HTTP.SYS 中运行。</span><span class="sxs-lookup"><span data-stu-id="39195-121">The Report Server Web service runs in HTTP.SYS.</span></span> <span data-ttu-id="39195-122">在为 HTTP 创建 SPN 时，将同时对在 HTTP.SYS（包括承载在 IIS 中的应用程序）中运行的位于同一台计算机上的所有 Web 应用程序授予基于该域用户帐户的票证。</span><span class="sxs-lookup"><span data-stu-id="39195-122">A by-product of creating an SPN for HTTP is that all Web applications on the same computer that run in HTTP.SYS (including applications hosted in IIS) will be granted tickets based on the domain user account.</span></span> <span data-ttu-id="39195-123">如果这些服务在其他帐户下运行，则身份验证请求将失败。</span><span class="sxs-lookup"><span data-stu-id="39195-123">If those services run under a different account, the authentication requests will fail.</span></span> <span data-ttu-id="39195-124">为避免此问题，请务必将所有 HTTP 应用程序配置为在同一帐户下运行，或考虑为每个应用程序创建主机头，然后为每个主机头单独创建一个 SPN。</span><span class="sxs-lookup"><span data-stu-id="39195-124">To avoid this problem, be sure to configure all HTTP applications to run under the same account, or consider creating host headers for each application and then creating separate SPNs for each host header.</span></span> <span data-ttu-id="39195-125">配置主机标头时，无论 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 配置如何都必须更改 DNS。</span><span class="sxs-lookup"><span data-stu-id="39195-125">When you configure host headers, DNS changes are required regardless of the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] configuration.</span></span>  
  
 <span data-ttu-id="39195-126">为、和指定的值 \<*computername*> \<*domainname*> \<*port*> 标识承载 Report Server 的计算机的唯一网络地址。</span><span class="sxs-lookup"><span data-stu-id="39195-126">The values that you specify for \<*computername*>, \<*domainname*>, and \<*port*> identify the unique network address of the computer that hosts the report server.</span></span> <span data-ttu-id="39195-127">此地址可以是本地主机名，或者完全限定的域名 (FQDN)。</span><span class="sxs-lookup"><span data-stu-id="39195-127">This can be a local host name or a fully qualified domain name (FQDN).</span></span> <span data-ttu-id="39195-128">如果只有一个域并且使用端口80，则可以在 \<*domainname*> \<*port*> 命令行中省略和。</span><span class="sxs-lookup"><span data-stu-id="39195-128">If you only have one domain and are using port 80, you can omit \<*domainname*> and \<*port*> from your command line.</span></span> <span data-ttu-id="39195-129">\<*domain-user-account*>报表服务器服务运行时所用的用户帐户以及必须注册 SPN 的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="39195-129">\<*domain-user-account*> is the user account under which the Report Server service runs and for which the SPN must be registered.</span></span>  
  
## <a name="register-an-spn-for-domain-user-account"></a><span data-ttu-id="39195-130">为域用户帐户注册 SPN</span><span class="sxs-lookup"><span data-stu-id="39195-130">Register an SPN for Domain User Account</span></span>  
  
#### <a name="to-register-an-spn-for-a-report-server-service-running-as-a-domain-user"></a><span data-ttu-id="39195-131">为以域用户身份运行的报表服务器服务注册 SPN</span><span class="sxs-lookup"><span data-stu-id="39195-131">To register an SPN for a Report Server service running as a domain user</span></span>  
  
1.  <span data-ttu-id="39195-132">安装 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 并将报表服务器服务配置为以域用户帐户身份运行。</span><span class="sxs-lookup"><span data-stu-id="39195-132">Install [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] and configure the Report Server service to run as a domain user account.</span></span> <span data-ttu-id="39195-133">请注意，直到完成以下步骤之后，用户才能连接到报表服务器。</span><span class="sxs-lookup"><span data-stu-id="39195-133">Note that users will not be able to connect to the report server until you complete the following steps.</span></span>  
  
2.  <span data-ttu-id="39195-134">以域管理员的身份登录到域控制器。</span><span class="sxs-lookup"><span data-stu-id="39195-134">Log on to the domain controller as domain administrator.</span></span>  
  
3.  <span data-ttu-id="39195-135">打开命令提示符窗口。</span><span class="sxs-lookup"><span data-stu-id="39195-135">Open a Command Prompt window.</span></span>  
  
4.  <span data-ttu-id="39195-136">复制以下命令，并用适用于您的网络的实际值替换占位符值。</span><span class="sxs-lookup"><span data-stu-id="39195-136">Copy the following command, replacing placeholder values with actual values that are valid for your network:</span></span>  
  
    ```  
    Setspn -s http/<computer-name>.<domain-name>:<port> <domain-user-account>  
    ```  
  
     <span data-ttu-id="39195-137">例如： `Setspn -s http/MyReportServer.MyDomain.com:80 MyDomainUser`</span><span class="sxs-lookup"><span data-stu-id="39195-137">For example: `Setspn -s http/MyReportServer.MyDomain.com:80 MyDomainUser`</span></span>  
  
5.  <span data-ttu-id="39195-138">运行命令。</span><span class="sxs-lookup"><span data-stu-id="39195-138">Run the command.</span></span>  
  
6.  <span data-ttu-id="39195-139">打开 **RsReportServer.config** 文件并找到 `<AuthenticationTypes>` 部分。</span><span class="sxs-lookup"><span data-stu-id="39195-139">Open the **RsReportServer.config** file and locate the `<AuthenticationTypes>` section.</span></span>  
  
7.  <span data-ttu-id="39195-140">添加 `<RSWindowsNegotiate/>` 作为该部分的第一个项，以启用 NTLM。</span><span class="sxs-lookup"><span data-stu-id="39195-140">Add `<RSWindowsNegotiate/>` as the first entry in this section to enable NTLM.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39195-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="39195-141">See Also</span></span>  
 <span data-ttu-id="39195-142">[&#40;SSRS Configuration Manager 配置服务帐户&#41;](../../sql-server/install/configure-a-service-account-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="39195-142">[Configure a Service Account &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-service-account-ssrs-configuration-manager.md) </span></span>  
 <span data-ttu-id="39195-143">[配置报表服务器服务帐户（SSRS 配置管理器）](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="39195-143">[Configure the Report Server Service Account &#40;SSRS Configuration Manager&#41;](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md) </span></span>  
 [<span data-ttu-id="39195-144">管理 Reporting Services 本机模式报表服务器</span><span class="sxs-lookup"><span data-stu-id="39195-144">Manage a Reporting Services Native Mode Report Server</span></span>](manage-a-reporting-services-native-mode-report-server.md)  
  
  
