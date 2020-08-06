---
title: 为 Kerberos 连接注册服务主体名称 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- connections [SQL Server], SPNs
- network connections [SQL Server], SPNs
- registering SPNs
- Server Principal Names
- SPNs [SQL Server]
ms.assetid: e38d5ce4-e538-4ab9-be67-7046e0d9504e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f4db1e8b86fca057acbce29491be9c2be91f0748
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589876"
---
# <a name="register-a-service-principal-name-for-kerberos-connections"></a><span data-ttu-id="f4b20-102">为 Kerberos 连接注册服务主体名称</span><span class="sxs-lookup"><span data-stu-id="f4b20-102">Register a Service Principal Name for Kerberos Connections</span></span>
  <span data-ttu-id="f4b20-103">若要将 Kerberos 身份验证用于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，则以下两个条件都必须得到满足：</span><span class="sxs-lookup"><span data-stu-id="f4b20-103">To use Kerberos authentication with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] requires both the following conditions to be true:</span></span>  
  
-   <span data-ttu-id="f4b20-104">客户端计算机和服务器计算机必须属于同一 Windows 域或在可信域中。</span><span class="sxs-lookup"><span data-stu-id="f4b20-104">The client and server computers must be part of the same Windows domain, or in trusted domains.</span></span>  
  
-   <span data-ttu-id="f4b20-105">服务主体名称 (SPN) 必须在 Active Directory 中进行注册，后者在 Windows 域中起到密钥分发中心的作用。</span><span class="sxs-lookup"><span data-stu-id="f4b20-105">A Service Principal Name (SPN) must be registered with Active Directory, which assumes the role of the Key Distribution Center in a Windows domain.</span></span> <span data-ttu-id="f4b20-106">SPN 在注册后会映射到启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例服务的 Windows 帐户。</span><span class="sxs-lookup"><span data-stu-id="f4b20-106">The SPN, after it is registered, maps to the Windows account that started the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance service.</span></span> <span data-ttu-id="f4b20-107">如果未进行 SPN 注册或注册失败，则 Windows 安全层无法确定与 SPN 关联的帐户，因而无法使用 Kerberos 身份验证。</span><span class="sxs-lookup"><span data-stu-id="f4b20-107">If the SPN registration has not been performed or fails, the Windows security layer cannot determine the account associated with the SPN, and Kerberos authentication will not be used.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f4b20-108">如果服务器无法自动注册 SPN，则必须手动注册 SPN。</span><span class="sxs-lookup"><span data-stu-id="f4b20-108">If the server cannot automatically register the SPN, the SPN must be registered manually.</span></span> <span data-ttu-id="f4b20-109">请参阅 [手动注册 SPN](#Manual)。</span><span class="sxs-lookup"><span data-stu-id="f4b20-109">See [Manual SPN Registration](#Manual).</span></span>  
  
 <span data-ttu-id="f4b20-110">可以通过查询 sys.dm_exec_connections 动态管理视图来验证连接使用的是否为 Kerberos。</span><span class="sxs-lookup"><span data-stu-id="f4b20-110">You can verify that a connection is using Kerberos by querying the sys.dm_exec_connections dynamic management view.</span></span> <span data-ttu-id="f4b20-111">请运行下面的查询并检查 auth_scheme 列的值，如果 Kerberos 已启用，该值应为“KERBEROS”。</span><span class="sxs-lookup"><span data-stu-id="f4b20-111">Run the following query and check the value of the auth_scheme column, which will be "KERBEROS" if Kerberos is enabled.</span></span>  
  
```  
SELECT auth_scheme FROM sys.dm_exec_connections WHERE session_id = @@spid ;  
```  
  
> [!TIP]  
>  <span data-ttu-id="f4b20-112">**[!INCLUDE[msCoName](../../includes/msconame-md.md)] Kerberos Configuration Manager for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]** 是一款诊断工具，可帮助解决与 Kerberos Configuration Manager for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]相关的连接问题。</span><span class="sxs-lookup"><span data-stu-id="f4b20-112">**[!INCLUDE[msCoName](../../includes/msconame-md.md)] Kerberos Configuration Manager for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]** is a diagnostic tool that helps troubleshoot Kerberos related connectivity issues with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="f4b20-113">有关详细信息，请参阅 [Microsoft Kerberos Configuration Manager for SQL Server](https://www.microsoft.com/download/details.aspx?id=39046)。</span><span class="sxs-lookup"><span data-stu-id="f4b20-113">For more information, see [Microsoft Kerberos Configuration Manager for SQL Server](https://www.microsoft.com/download/details.aspx?id=39046).</span></span>  
  
##  <a name="the-role-of-the-spn-in-authentication"></a><a name="Role"></a> <span data-ttu-id="f4b20-114">SPN 在身份验证过程中所起的作用</span><span class="sxs-lookup"><span data-stu-id="f4b20-114">The Role of the SPN in Authentication</span></span>  
 <span data-ttu-id="f4b20-115">当应用程序打开一个连接并使用 Windows 身份验证时， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 会传递 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 计算机名、实例名和 SPN（可选）。</span><span class="sxs-lookup"><span data-stu-id="f4b20-115">When an application opens a connection and uses Windows Authentication, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client passes the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] computer name, instance name and, optionally, an SPN.</span></span> <span data-ttu-id="f4b20-116">如果该连接传递了 SPN，则使用它时不对它做任何更改。</span><span class="sxs-lookup"><span data-stu-id="f4b20-116">If the connection passes an SPN it is used without any changes.</span></span>  
  
 <span data-ttu-id="f4b20-117">如果该连接未传递 SPN，则将根据所使用的协议、服务器名和实例名构造一个默认的 SPN。</span><span class="sxs-lookup"><span data-stu-id="f4b20-117">If the connection does not pass an SPN, a default SPN is constructed based on the protocol used, server name, and the instance name.</span></span>  
  
 <span data-ttu-id="f4b20-118">在上面这两种情况下，都会将 SPN 发送到密钥分发中心以获取用于对连接进行身份验证的安全标记。</span><span class="sxs-lookup"><span data-stu-id="f4b20-118">In both of the preceding scenarios, the SPN is sent to the Key Distribution Center to obtain a security token for authenticating the connection.</span></span> <span data-ttu-id="f4b20-119">如果无法获取安全标记，则身份验证采用 NTLM。</span><span class="sxs-lookup"><span data-stu-id="f4b20-119">If a security token cannot be obtained, authentication uses NTLM.</span></span>  
  
 <span data-ttu-id="f4b20-120">服务主体名称 (SPN) 是客户端用来唯一标识服务实例的名称。</span><span class="sxs-lookup"><span data-stu-id="f4b20-120">A service principal name (SPN) is the name by which a client uniquely identifies an instance of a service.</span></span> <span data-ttu-id="f4b20-121">Kerberos 身份验证服务可以使用 SPN 对服务进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="f4b20-121">The Kerberos authentication service can use an SPN to authenticate a service.</span></span> <span data-ttu-id="f4b20-122">当客户端想要连接到某个服务时，它将查找该服务的实例，并为该实例编写 SPN，然后连接到该服务并显示该服务的 SPN 以进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="f4b20-122">When a client wants to connect to a service, it locates an instance of the service, composes an SPN for that instance, connects to the service, and presents the SPN for the service to authenticate.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f4b20-123">本主题中提供的信息还适用于使用聚类分析的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置。</span><span class="sxs-lookup"><span data-stu-id="f4b20-123">The information that is provided in this topic also applies to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] configurations that use clustering.</span></span>  
  
 <span data-ttu-id="f4b20-124">Windows 身份验证是向 SQL Server 验证用户身份的首选方法。</span><span class="sxs-lookup"><span data-stu-id="f4b20-124">Windows Authentication is the preferred method for users to authenticate to SQL Server.</span></span> <span data-ttu-id="f4b20-125">使用 Windows 身份验证的客户端通过 NTLM 或 Kerberos 进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="f4b20-125">Clients that use Windows Authentication are authenticated by either using NTLM or Kerberos.</span></span> <span data-ttu-id="f4b20-126">在 Active Directory 环境中，始终首先尝试 Kerberos 身份验证。</span><span class="sxs-lookup"><span data-stu-id="f4b20-126">In an Active Directory environment, Kerberos authentication is always attempted first.</span></span> <span data-ttu-id="f4b20-127">Kerberos 身份验证不可用于使用命名管道的 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 客户端。</span><span class="sxs-lookup"><span data-stu-id="f4b20-127">Kerberos authentication is not available for [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] clients using named pipes.</span></span>  
  
##  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="f4b20-128">权限</span><span class="sxs-lookup"><span data-stu-id="f4b20-128">Permissions</span></span>  
 <span data-ttu-id="f4b20-129">当启动 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 服务时，它将尝试注册服务主体名称 (SPN)。</span><span class="sxs-lookup"><span data-stu-id="f4b20-129">When the [!INCLUDE[ssDE](../../includes/ssde-md.md)] service starts, it attempts to register the Service Principal Name (SPN).</span></span> <span data-ttu-id="f4b20-130">如果启动 SQL Server 的帐户没有在 Active Directory 域服务中注册 SPN 的权限，则此调用将失败，并将在应用程序事件日志以及 SQL Server 错误日志中记录一条警告消息。</span><span class="sxs-lookup"><span data-stu-id="f4b20-130">If the account starting SQL Server doesn't have permission to register a SPN in Active Directory Domain Services, this call will fail and a warning message will be logged in the Application event log as well as the SQL Server error log.</span></span> <span data-ttu-id="f4b20-131">若要注册 SPN，必须在内置帐户（如 Local System（建议不要使用）或 NETWORK SERVICE）或有权注册 SPN 的帐户（如域管理员帐户）下运行 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="f4b20-131">To register the SPN, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] must be running under a built-in account, such as Local System (not recommended), or NETWORK SERVICE, or an account that has permission to register an SPN, such as a domain administrator account.</span></span> <span data-ttu-id="f4b20-132">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 或  [!INCLUDE[win7](../../includes/win7-md.md)] 操作系统上运行  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] 时，可以使用虚拟帐户或托管服务帐户 (MSA) 运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="f4b20-132">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running on the  [!INCLUDE[win7](../../includes/win7-md.md)] or  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] operating system, you can run [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using a virtual account or a managed service account (MSA).</span></span> <span data-ttu-id="f4b20-133">虚拟帐户和 MSA 都可以注册 SPN。</span><span class="sxs-lookup"><span data-stu-id="f4b20-133">Both virtual accounts and MSA's can register an SPN.</span></span> <span data-ttu-id="f4b20-134">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 不在上述任一帐户下运行，则启动时不会注册 SPN，此时，域管理员必须手动注册 SPN。</span><span class="sxs-lookup"><span data-stu-id="f4b20-134">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is not running under one of these accounts, the SPN is not registered at startup and the domain administrator must register the SPN manually.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f4b20-135">将 Windows 域配置为在低于 [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] Windows Server 2008 R2 功能级别的级别上运行时，托管服务帐户将不具有注册 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 服务的 SPN 所需的权限。</span><span class="sxs-lookup"><span data-stu-id="f4b20-135">When the Windows domain is configured to run at less than the [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] Windows Server 2008 R2 functional level, then the Managed Service Account will not have the necessary permissions to register the SPNs for the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] service.</span></span> <span data-ttu-id="f4b20-136">如果需要进行 Kerberos 身份验证，域管理员应手动在托管服务帐户上注册 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SPN。</span><span class="sxs-lookup"><span data-stu-id="f4b20-136">If Kerberos authentication is required, the Domain Administrator should manually register the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SPNs on the Managed Service Account.</span></span>  
  
 <span data-ttu-id="f4b20-137">知识库文章 [How to use Kerberos authentication in SQL Server](https://support.microsoft.com/kb/319723)（如何在 SQL Server 中使用 Kerberos 身份验证）包含有关如何向非域管理员帐户授予 SPN 读或写权限的信息。</span><span class="sxs-lookup"><span data-stu-id="f4b20-137">The KB article, [How to use Kerberos authentication in SQL Server](https://support.microsoft.com/kb/319723), contains information about how to grant read or write permission to an SPN for an account that is not a Domain Administrator.</span></span>  
  
 <span data-ttu-id="f4b20-138">有关其他信息，请参阅 [How to Implement Kerberos Constrained Delegation with SQL Server 2008](https://technet.microsoft.com/library/ee191523.aspx)（如何使用 SQL Server 2008 实现 Kerberos 约束委派）</span><span class="sxs-lookup"><span data-stu-id="f4b20-138">Additional information is available at [How to Implement Kerberos Constrained Delegation with SQL Server 2008](https://technet.microsoft.com/library/ee191523.aspx)</span></span>  
  
##  <a name="spn-formats"></a><a name="Formats"></a> <span data-ttu-id="f4b20-139">SPN 格式</span><span class="sxs-lookup"><span data-stu-id="f4b20-139">SPN Formats</span></span>  
 <span data-ttu-id="f4b20-140">自 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]开始，SPN 格式已发生更改，目的是为了支持对 TCP/IP、Named Pipes 和 Shared Memory 进行 Kerberos 身份验证。</span><span class="sxs-lookup"><span data-stu-id="f4b20-140">Beginning with [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], the SPN format is changed in order to support Kerberos authentication on TCP/IP, named pipes, and shared memory.</span></span> <span data-ttu-id="f4b20-141">所支持的命名实例和默认实例的 SPN 格式如下所示。</span><span class="sxs-lookup"><span data-stu-id="f4b20-141">The supported SPN formats for named and default instances are as follows.</span></span>  
  
 <span data-ttu-id="f4b20-142">**命名实例**</span><span class="sxs-lookup"><span data-stu-id="f4b20-142">**Named instance**</span></span>  
  
-   <span data-ttu-id="f4b20-143">*MSSQLSvc/FQDN*:[_port_**|**_instancename_]，其中：</span><span class="sxs-lookup"><span data-stu-id="f4b20-143">*MSSQLSvc/FQDN*:[_port_**|**_instancename_], where:</span></span>  
  
    -   <span data-ttu-id="f4b20-144">*MSSQLSvc* 是要注册的服务。</span><span class="sxs-lookup"><span data-stu-id="f4b20-144">*MSSQLSvc* is the service that is being registered.</span></span>  
  
    -   <span data-ttu-id="f4b20-145">*FQDN*是服务器的完全限定的域名。</span><span class="sxs-lookup"><span data-stu-id="f4b20-145">*FQDN* is the fully qualified domain name of the server.</span></span>  
  
    -   <span data-ttu-id="f4b20-146">*port*是 TCP 端口号。</span><span class="sxs-lookup"><span data-stu-id="f4b20-146">*port* is the TCP port number.</span></span>  
  
    -   <span data-ttu-id="f4b20-147">*instancename*是实例的名称 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="f4b20-147">*instancename* is the name of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span>  
  
 <span data-ttu-id="f4b20-148">**默认实例**</span><span class="sxs-lookup"><span data-stu-id="f4b20-148">**Default instance**</span></span>  
  
-   <span data-ttu-id="f4b20-149">*MSSQLSvc/fqdn*：_port_ **|** _MSSQLSvc/fqdn_，其中：</span><span class="sxs-lookup"><span data-stu-id="f4b20-149">*MSSQLSvc/FQDN*:_port_**|**_MSSQLSvc/FQDN_, where:</span></span>  
  
    -   <span data-ttu-id="f4b20-150">*MSSQLSvc* 是要注册的服务。</span><span class="sxs-lookup"><span data-stu-id="f4b20-150">*MSSQLSvc* is the service that is being registered.</span></span>  
  
    -   <span data-ttu-id="f4b20-151">*FQDN*是服务器的完全限定的域名。</span><span class="sxs-lookup"><span data-stu-id="f4b20-151">*FQDN* is the fully qualified domain name of the server.</span></span>  
  
    -   <span data-ttu-id="f4b20-152">*port*是 TCP 端口号。</span><span class="sxs-lookup"><span data-stu-id="f4b20-152">*port* is the TCP port number.</span></span>  
  
 <span data-ttu-id="f4b20-153">新 SPN 格式不需要端口号。</span><span class="sxs-lookup"><span data-stu-id="f4b20-153">The new SPN format does not require a port number.</span></span> <span data-ttu-id="f4b20-154">这意味着，多端口服务器或不使用端口号的协议都可以使用 Kerberos 身份验证。</span><span class="sxs-lookup"><span data-stu-id="f4b20-154">This means that a multiple-port server or a protocol that does not use port numbers can use Kerberos authentication.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f4b20-155">对于 TCP/IP 连接，由于 SPN 中包括 TCP 端口，因此 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 必须启用 TCP 协议，以便用户使用 Kerberos 身份验证进行连接。</span><span class="sxs-lookup"><span data-stu-id="f4b20-155">In the case of a TCP/IP connection, where the TCP port is included in the SPN, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must enable the TCP protocol for a user to connect by using Kerberos authentication.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f4b20-156">MSSQLSvc/*fqdn：端口*</span><span class="sxs-lookup"><span data-stu-id="f4b20-156">MSSQLSvc/*fqdn:port*</span></span>|<span data-ttu-id="f4b20-157">使用 TCP 时访问接口生成的默认 SPN。</span><span class="sxs-lookup"><span data-stu-id="f4b20-157">The provider-generated, default SPN when TCP is used.</span></span> <span data-ttu-id="f4b20-158">*port* 是 TCP 端口号。</span><span class="sxs-lookup"><span data-stu-id="f4b20-158">*port* is a TCP port number.</span></span>|  
|<span data-ttu-id="f4b20-159">MSSQLSvc/*fqdn*</span><span class="sxs-lookup"><span data-stu-id="f4b20-159">MSSQLSvc/*fqdn*</span></span>|<span data-ttu-id="f4b20-160">使用除 TCP 之外的协议时访问接口生成的用于默认实例的默认 SPN。</span><span class="sxs-lookup"><span data-stu-id="f4b20-160">The provider-generated, default SPN for a default instance when a protocol other than TCP is used.</span></span> <span data-ttu-id="f4b20-161">*fqdn*为完全限定的域名。</span><span class="sxs-lookup"><span data-stu-id="f4b20-161">*fqdn* is a fully-qualified domain name.</span></span>|  
|<span data-ttu-id="f4b20-162">MSSQLSvc/*fqdn： InstanceName*</span><span class="sxs-lookup"><span data-stu-id="f4b20-162">MSSQLSvc/*fqdn:InstanceName*</span></span>|<span data-ttu-id="f4b20-163">使用除 TCP 之外的协议时访问接口生成的用于命名实例的默认 SPN。</span><span class="sxs-lookup"><span data-stu-id="f4b20-163">The provider-generated, default SPN for a named instance when a protocol other than TCP is used.</span></span> <span data-ttu-id="f4b20-164">*InstanceName*是实例的名称 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="f4b20-164">*InstanceName* is the name of an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|  
  
##  <a name="automatic-spn-registration"></a><a name="Auto"></a> <span data-ttu-id="f4b20-165">自动注册 SPN</span><span class="sxs-lookup"><span data-stu-id="f4b20-165">Automatic SPN Registration</span></span>  
 <span data-ttu-id="f4b20-166">当 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 的实例启动时， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将尝试为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务注册 SPN。</span><span class="sxs-lookup"><span data-stu-id="f4b20-166">When an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] starts, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tries to register the SPN for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span> <span data-ttu-id="f4b20-167">实例停止时， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将尝试取消此 SPN 的注册。</span><span class="sxs-lookup"><span data-stu-id="f4b20-167">When the instance is stopped, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tries to unregister the SPN.</span></span> <span data-ttu-id="f4b20-168">对于 TCP/IP 连接，注册 SPN 时使用的格式为 MSSQLSvc/\<FQDN>:\<tcpport>。命名实例和默认实例均注册为 MSSQLSvc，根据 \<tcpport> 值来区分这些实例   。</span><span class="sxs-lookup"><span data-stu-id="f4b20-168">For a TCP/IP connection the SPN is registered in the format *MSSQLSvc/\<FQDN>*:*\<tcpport>*.Both named instances and the default instance are registered as *MSSQLSvc*, relying on the *\<tcpport>* value to differentiate the instances.</span></span>  
  
 <span data-ttu-id="f4b20-169">对于支持 Kerberos 的其他连接，为命名实例注册 SPN 时使用的格式为\*MSSQLSvc/ \<FQDN> \*： *\<instancename>* 。</span><span class="sxs-lookup"><span data-stu-id="f4b20-169">For other connections that support Kerberos the SPN is registered in the format *MSSQLSvc/\<FQDN>*:*\<instancename>* for a named instance.</span></span> <span data-ttu-id="f4b20-170">注册默认实例的格式为 MSSQLSvc/\<FQDN>。</span><span class="sxs-lookup"><span data-stu-id="f4b20-170">The format for registering the default instance is *MSSQLSvc/\<FQDN>*.</span></span>  
  
 <span data-ttu-id="f4b20-171">如果服务帐户缺少执行这些操作所需的权限，在注册或取消注册 SPN 时可能需要进行手动干预。</span><span class="sxs-lookup"><span data-stu-id="f4b20-171">Manual intervention might be required to register or unregister the SPN if the service account lacks the permissions that are required for these actions.</span></span>  
  
##  <a name="manual-spn-registration"></a><a name="Manual"></a> <span data-ttu-id="f4b20-172">手动注册 SPN</span><span class="sxs-lookup"><span data-stu-id="f4b20-172">Manual SPN Registration</span></span>  
 <span data-ttu-id="f4b20-173">若要手动注册 SPN，管理员必须使用随 Microsoft [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] 支持工具提供的 Setspn.exe 工具。</span><span class="sxs-lookup"><span data-stu-id="f4b20-173">To register the SPN manually, the administrator must use the Setspn.exe tool that is provided with the Microsoft [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] Support Tools.</span></span> <span data-ttu-id="f4b20-174">有关详细信息，请参阅 [Windows Server 2003 Service Pack 1 Support Tools](https://support.microsoft.com/kb/892777) （Windows Server 2003 Service Pack 1 支持工具）知识库文章。</span><span class="sxs-lookup"><span data-stu-id="f4b20-174">For more information, see the [Windows Server 2003 Service Pack 1 Support Tools](https://support.microsoft.com/kb/892777) KB article.</span></span>  
  
 <span data-ttu-id="f4b20-175">Setspn.exe 是一个命令行工具，您可通过该工具读取、修改和删除服务主体名称 (SPN) 目录属性。</span><span class="sxs-lookup"><span data-stu-id="f4b20-175">Setspn.exe is a command line tool that enables you to read, modify, and delete the Service Principal Names (SPN) directory property.</span></span> <span data-ttu-id="f4b20-176">您还可借助此工具查看当前 SPN、重置帐户的默认 SPN 以及添加或删除补充 SPN。</span><span class="sxs-lookup"><span data-stu-id="f4b20-176">This tool also enables you to view the current SPNs, reset the account's default SPNs, and add or delete supplemental SPNs.</span></span>  
  
 <span data-ttu-id="f4b20-177">以下示例说明了用于为 TCP/IP 连接手动注册 SPN 的语法：</span><span class="sxs-lookup"><span data-stu-id="f4b20-177">The following example illustrates the syntax used to register manually register an SPN for a TCP/IP connection.</span></span>  
  
```  
setspn -A MSSQLSvc/myhost.redmond.microsoft.com:1433 accountname  
```  
  
 <span data-ttu-id="f4b20-178">**注意** 如果 SPN 已存在，则必须在重新注册该 SPN 之前将其删除。</span><span class="sxs-lookup"><span data-stu-id="f4b20-178">**Note** If an SPN already exists, it must be deleted before it can be reregistered.</span></span> <span data-ttu-id="f4b20-179">可以使用带有 `setspn` 开关的 `-D` 命令实现此操作。</span><span class="sxs-lookup"><span data-stu-id="f4b20-179">You do this by using the `setspn` command together with the `-D` switch.</span></span> <span data-ttu-id="f4b20-180">以下示例说明如何手动注册基于新实例的 SPN。</span><span class="sxs-lookup"><span data-stu-id="f4b20-180">The following examples illustrate how to manually register a new instance-based SPN.</span></span> <span data-ttu-id="f4b20-181">对于默认实例，请使用：</span><span class="sxs-lookup"><span data-stu-id="f4b20-181">For a default instance, use:</span></span>  
  
```  
setspn -A MSSQLSvc/myhost.redmond.microsoft.com accountname  
```  
  
 <span data-ttu-id="f4b20-182">对于命名实例，请使用：</span><span class="sxs-lookup"><span data-stu-id="f4b20-182">For a named instance, use:</span></span>  
  
```  
setspn -A MSSQLSvc/myhost.redmond.microsoft.com:instancename accountname  
```  
  
##  <a name="client-connections"></a><a name="Client"></a> <span data-ttu-id="f4b20-183">客户端连接</span><span class="sxs-lookup"><span data-stu-id="f4b20-183">Client Connections</span></span>  
 <span data-ttu-id="f4b20-184">客户端驱动程序支持用户指定的 SPN。</span><span class="sxs-lookup"><span data-stu-id="f4b20-184">User-specified SPNs are supported in client drivers.</span></span> <span data-ttu-id="f4b20-185">但是，如果未提供 SPN，则将根据客户端连接类型自动生成 SPN。</span><span class="sxs-lookup"><span data-stu-id="f4b20-185">However, if an SPN is not provided, it will be generated automatically based on the type of a client connection.</span></span> <span data-ttu-id="f4b20-186">对于 TCP 连接，为命名实例和默认实例使用 *MSSQLSvc*/*FQDN*:[*port*] 格式的 SPN。</span><span class="sxs-lookup"><span data-stu-id="f4b20-186">For a TCP connection, an SPN in the format *MSSQLSvc*/*FQDN*:[*port*] is used for both the named and default instances.</span></span>  
  
 <span data-ttu-id="f4b20-187">对于命名管道和共享内存连接，使用*MSSQLSvc* / *fqdn*：*instancename*格式的 SPN 作为命名实例，并使用*MSSQLSvc* / *fqdn*作为默认实例。</span><span class="sxs-lookup"><span data-stu-id="f4b20-187">For named pipes and shared memory connections, an SPN in the format *MSSQLSvc*/*FQDN*:*instancename* is used for a named instance and *MSSQLSvc*/*FQDN* is used for the default instance.</span></span>  
  
 <span data-ttu-id="f4b20-188">**将服务帐户用作 SPN**</span><span class="sxs-lookup"><span data-stu-id="f4b20-188">**Using a service account as an SPN**</span></span>  
  
 <span data-ttu-id="f4b20-189">可将服务帐户用作 SPN。</span><span class="sxs-lookup"><span data-stu-id="f4b20-189">Service accounts can be used as an SPN.</span></span> <span data-ttu-id="f4b20-190">可以通过 Kerberos 身份验证的连接属性指定服务帐户，并采用以下格式：</span><span class="sxs-lookup"><span data-stu-id="f4b20-190">They are specified through the connection attribute for the Kerberos authentication and take the following formats:</span></span>  
  
-   <span data-ttu-id="f4b20-191">**username@domain**域用户帐户的用户名或域**\ 用户名**</span><span class="sxs-lookup"><span data-stu-id="f4b20-191">**username@domain** or **domain\username** for a domain user account</span></span>  
  
-   <span data-ttu-id="f4b20-192">machine$@domain 或 host\FQDN（适用于计算机域帐户，如 Local System 或 NETWORK SERVICES）\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f4b20-192">**machine$@domain** or **host\FQDN** for a computer domain account such as Local System or NETWORK SERVICES.</span></span>  
  
 <span data-ttu-id="f4b20-193">若要确定连接的身份验证方法，请执行下面的查询。</span><span class="sxs-lookup"><span data-stu-id="f4b20-193">To determine the authentication method of a connection, execute the following query.</span></span>  
  
```sql  
SELECT net_transport, auth_scheme   
FROM sys.dm_exec_connections   
WHERE session_id = @@SPID;  
```  
  
##  <a name="authentication-defaults"></a><a name="Defaults"></a> <span data-ttu-id="f4b20-194">身份验证默认值</span><span class="sxs-lookup"><span data-stu-id="f4b20-194">Authentication Defaults</span></span>  
 <span data-ttu-id="f4b20-195">下表说明根据 SPN 注册情况所使用的身份验证默认值。</span><span class="sxs-lookup"><span data-stu-id="f4b20-195">The following table describes the authentication defaults that are used based on SPN registration scenarios.</span></span>  
  
|<span data-ttu-id="f4b20-196">场景</span><span class="sxs-lookup"><span data-stu-id="f4b20-196">Scenario</span></span>|<span data-ttu-id="f4b20-197">身份验证方法</span><span class="sxs-lookup"><span data-stu-id="f4b20-197">Authentication method</span></span>|  
|--------------|---------------------------|  
|<span data-ttu-id="f4b20-198">SPN 映射到正确的域帐户、虚拟帐户、MSA 或内置帐户。</span><span class="sxs-lookup"><span data-stu-id="f4b20-198">The SPN maps to the correct domain account, virtual account, MSA, or built-in account.</span></span> <span data-ttu-id="f4b20-199">例如 Local System 或 NETWORK SERVICE。</span><span class="sxs-lookup"><span data-stu-id="f4b20-199">For example, Local System or NETWORK SERVICE.</span></span><br /><br /> <span data-ttu-id="f4b20-200">注意：正确表示注册的 SPN 映射的帐户是 SQL Server 服务正在其下运行的帐户。</span><span class="sxs-lookup"><span data-stu-id="f4b20-200">Note: Correct means that the account mapped by the registered SPN is the account that the SQL Server service is running under.</span></span>|<span data-ttu-id="f4b20-201">本地连接使用 NTLM，远程连接使用 Kerberos。</span><span class="sxs-lookup"><span data-stu-id="f4b20-201">Local connections use NTLM, remote connections use Kerberos.</span></span>|  
|<span data-ttu-id="f4b20-202">SPN 是正确的域帐户、虚拟帐户、MSA 或内置帐户。</span><span class="sxs-lookup"><span data-stu-id="f4b20-202">The SPN is the correct domain account, virtual account, MSA, or built-in account.</span></span><br /><br /> <span data-ttu-id="f4b20-203">注意：正确表示注册的 SPN 映射的帐户是 SQL Server 服务正在其下运行的帐户。</span><span class="sxs-lookup"><span data-stu-id="f4b20-203">Note: Correct means that the account mapped by the registered SPN is the account that the SQL Server service is running under.</span></span>|<span data-ttu-id="f4b20-204">本地连接使用 NTLM，远程连接使用 Kerberos。</span><span class="sxs-lookup"><span data-stu-id="f4b20-204">Local connections use NTLM, remote connections use Kerberos.</span></span>|  
|<span data-ttu-id="f4b20-205">SPN 映射到不正确的域帐户、虚拟帐户、MSA 或内置帐户。</span><span class="sxs-lookup"><span data-stu-id="f4b20-205">The SPN maps to an incorrect domain account, virtual account, MSA, or built-in account</span></span>|<span data-ttu-id="f4b20-206">身份验证失败。</span><span class="sxs-lookup"><span data-stu-id="f4b20-206">Authentication fails.</span></span>|  
|<span data-ttu-id="f4b20-207">SPN 查找失败或未映射到正确的域帐户、虚拟帐户、MSA 或内置帐户，或者不是正确的域帐户、虚拟帐户、MSA 或内置帐户。</span><span class="sxs-lookup"><span data-stu-id="f4b20-207">The SPN lookup fails or does not map to a correct domain account, virtual account, MSA, or built-in account, or is not a correct domain account, virtual account, MSA, or built-in account.</span></span>|<span data-ttu-id="f4b20-208">本地和远程连接使用 NTLM。</span><span class="sxs-lookup"><span data-stu-id="f4b20-208">Local and remote connections use NTLM.</span></span>|  
  
##  <a name="comments"></a><a name="Comments"></a> <span data-ttu-id="f4b20-209">注释</span><span class="sxs-lookup"><span data-stu-id="f4b20-209">Comments</span></span>  
 <span data-ttu-id="f4b20-210">专用管理员连接 (DAC) 使用一个基于实例名称的 SPN。</span><span class="sxs-lookup"><span data-stu-id="f4b20-210">The Dedicated Administrator Connection (DAC) uses an instance name based SPN.</span></span> <span data-ttu-id="f4b20-211">如果成功注册 SPN，则可以将 Kerberos 身份验证用于 DAC。</span><span class="sxs-lookup"><span data-stu-id="f4b20-211">Kerberos authentication can be used with a DAC if that SPN is registered successfully.</span></span> <span data-ttu-id="f4b20-212">用户也可以选择将帐户名指定为 SPN。</span><span class="sxs-lookup"><span data-stu-id="f4b20-212">As an alternative a user can specify the account name as an SPN.</span></span>  
  
 <span data-ttu-id="f4b20-213">如果在启动过程中 SPN 注册失败，将在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误日志中记录此失败，而启动过程将继续进行。</span><span class="sxs-lookup"><span data-stu-id="f4b20-213">If SPN registration fails during startup, this failure is recorded in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log, and startup continues.</span></span>  
  
 <span data-ttu-id="f4b20-214">如果在关闭时 SPN 取消注册失败，将在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误日志中记录此失败，而关闭过程将继续进行。</span><span class="sxs-lookup"><span data-stu-id="f4b20-214">If SPN de-registration fails during shutdown, this failure is recorded in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log, and shutdown continues.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4b20-215">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f4b20-215">See Also</span></span>  
 <span data-ttu-id="f4b20-216">[客户端连接中的服务主体名称 (SPN) 支持](../../relational-databases/native-client/features/service-principal-name-spn-support-in-client-connections.md) </span><span class="sxs-lookup"><span data-stu-id="f4b20-216">[Service Principal Name &#40;SPN&#41; Support in Client Connections](../../relational-databases/native-client/features/service-principal-name-spn-support-in-client-connections.md) </span></span>  
 <span data-ttu-id="f4b20-217">[客户端连接中的服务主体名称 (SPN) (OLE DB)](../../relational-databases/native-client/ole-db/service-principal-names-spns-in-client-connections-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="f4b20-217">[Service Principal Names &#40;SPNs&#41; in Client Connections &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/service-principal-names-spns-in-client-connections-ole-db.md) </span></span>  
 <span data-ttu-id="f4b20-218">[客户端连接中的服务主体名称 (SPN) (ODBC)](../../relational-databases/native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md) </span><span class="sxs-lookup"><span data-stu-id="f4b20-218">[Service Principal Names &#40;SPNs&#41; in Client Connections &#40;ODBC&#41;](../../relational-databases/native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md) </span></span>  
 <span data-ttu-id="f4b20-219">[SQL Server Native Client 功能](../../relational-databases/native-client/features/sql-server-native-client-features.md) </span><span class="sxs-lookup"><span data-stu-id="f4b20-219">[SQL Server Native Client Features](../../relational-databases/native-client/features/sql-server-native-client-features.md) </span></span>  
 [<span data-ttu-id="f4b20-220">管理 Reporting Services 环境中的 Kerberos 身份验证问题</span><span class="sxs-lookup"><span data-stu-id="f4b20-220">Manage Kerberos Authentication Issues in a Reporting Services Environment</span></span>](https://technet.microsoft.com/library/ff679930.aspx)  
  
  
