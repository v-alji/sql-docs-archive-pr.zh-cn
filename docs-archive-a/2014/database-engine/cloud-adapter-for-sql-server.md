---
title: SQL Server 的云适配器 |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Cloud adapter
- Deploy to Azure
ms.assetid: 82ed0d0f-952d-4d49-aa36-3855a3ca9877
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: d5716435bb1db494bdabeb45ed366c1783926989
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588062"
---
# <a name="cloud-adapter-for-sql-server"></a><span data-ttu-id="c8743-102">SQL Server 的云适配器</span><span class="sxs-lookup"><span data-stu-id="c8743-102">Cloud Adapter for SQL Server</span></span>
  <span data-ttu-id="c8743-103">在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] AZURE VM 上进行预配时，会创建云适配器服务。</span><span class="sxs-lookup"><span data-stu-id="c8743-103">The Cloud Adapter service is created as part of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provisioning on an Azure VM.</span></span> <span data-ttu-id="c8743-104">云适配器服务在首次运行时生成自签名的 SSL 证书，然后作为“本地系统”\*\*\*\* 帐户运行。</span><span class="sxs-lookup"><span data-stu-id="c8743-104">The Cloud Adapter service generates a self-signed SSL certificate as part of its first run, and then runs as a **Local System** account.</span></span> <span data-ttu-id="c8743-105">它生成用于配置自身的配置文件。</span><span class="sxs-lookup"><span data-stu-id="c8743-105">It generates a configuration file that is used to configure itself.</span></span> <span data-ttu-id="c8743-106">云适配器还创建一项 Windows 防火墙规则，以允许其传入 TCP 连接在默认端口 11435 上通过。</span><span class="sxs-lookup"><span data-stu-id="c8743-106">The Cloud Adapter also creates a Windows Firewall rule to allow its incoming TCP connections at default port 11435.</span></span>  
  
 <span data-ttu-id="c8743-107">云适配器是无状态的同步服务，它从 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的本地实例接收消息。</span><span class="sxs-lookup"><span data-stu-id="c8743-107">The Cloud Adapter is a stateless, synchronous service that receives messages from the on-premise instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c8743-108">停止云适配器服务时，它停止远程访问云适配器、解除 SSL 证书的绑定并禁用 Windows 防火墙规则。</span><span class="sxs-lookup"><span data-stu-id="c8743-108">When the Cloud Adapter service is stopped, it stops the remote access Cloud Adapter, unbinds the SSL certificate, and disables the Windows Firewall rule.</span></span>  
  
## <a name="cloud-adapter-requirements"></a><span data-ttu-id="c8743-109">云适配器要求</span><span class="sxs-lookup"><span data-stu-id="c8743-109">Cloud Adapter Requirements</span></span>  
 <span data-ttu-id="c8743-110">请注意以下安装、启用和运行 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的云适配器的要求：</span><span class="sxs-lookup"><span data-stu-id="c8743-110">Note the following requirements to install, enable, and run the Cloud Adapter for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="c8743-111">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 2012 或更高版本支持云适配器。</span><span class="sxs-lookup"><span data-stu-id="c8743-111">Cloud Adapter is supported with [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 2012 and higher.</span></span> <span data-ttu-id="c8743-112">在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 2012 上， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的云适配器需要用于 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 2012 的 SQL 管理对象。</span><span class="sxs-lookup"><span data-stu-id="c8743-112">On [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 2012, the Cloud Adapter for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] requires SQL Management Objects for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 2012.</span></span>  
  
-   <span data-ttu-id="c8743-113">云适配器 Web 服务在 **Local System** 帐户下运行并在执行任何任务前验证客户端凭据。</span><span class="sxs-lookup"><span data-stu-id="c8743-113">Cloud Adapter web service runs as a **Local System** account and verifies client credentials before executing any task.</span></span> <span data-ttu-id="c8743-114">客户端提供的凭据必须属于远程计算机上本地**Administrators**组成员的使用帐户。</span><span class="sxs-lookup"><span data-stu-id="c8743-114">Credentials supplied by the client must belong to the use account that is a member of the local **Administrators** group on the remote machine.</span></span>  
  
-   <span data-ttu-id="c8743-115">云适配器仅支持 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 身份验证。</span><span class="sxs-lookup"><span data-stu-id="c8743-115">Cloud Adapter supports only [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
-   <span data-ttu-id="c8743-116">云适配器使用虚拟机本地管理员帐户（而非 sa 帐户）在本地计算机上执行命令。</span><span class="sxs-lookup"><span data-stu-id="c8743-116">Cloud Adapter uses VM local administrator account to execute commands on the local machine, not an sa account.</span></span>  
  
-   <span data-ttu-id="c8743-117">云适配器侦听 TCP/IP。</span><span class="sxs-lookup"><span data-stu-id="c8743-117">Cloud Adapter listens on TCP/IP.</span></span> <span data-ttu-id="c8743-118">默认端口为 11435。</span><span class="sxs-lookup"><span data-stu-id="c8743-118">The default port is 11435.</span></span>  
  
-   <span data-ttu-id="c8743-119">云适配器必须具有创建和修改 Windows 防火墙规则的权限。</span><span class="sxs-lookup"><span data-stu-id="c8743-119">Cloud Adapter must have permissions to create and modify Windows Firewall rules.</span></span>  
  
## <a name="cloud-adapter-configuration-settings"></a><span data-ttu-id="c8743-120">云适配器配置设置</span><span class="sxs-lookup"><span data-stu-id="c8743-120">Cloud Adapter Configuration Settings</span></span>  
 <span data-ttu-id="c8743-121">使用以下云适配器配置详细信息来修改云适配器的设置。</span><span class="sxs-lookup"><span data-stu-id="c8743-121">Use the following Cloud Adapter configuration details to modify settings for a Cloud Adapter.</span></span>  
  
-   <span data-ttu-id="c8743-122">**配置文件的默认路径**-C:\PROGRAM Files\Microsoft SQL Server\120\Tools\CloudAdapter</span><span class="sxs-lookup"><span data-stu-id="c8743-122">**Default path for the configuration file** - C:\Program Files\Microsoft SQL Server\120\Tools\CloudAdapter</span></span>\  
  
-   <span data-ttu-id="c8743-123">**配置文件参数** -</span><span class="sxs-lookup"><span data-stu-id="c8743-123">**Configuration file parameters** -</span></span>  
  
    -   \<configuration>  
  
        -   \<appSettings>  
  
            -   \<add key="WebServicePort" value="" />  
  
            -   \<add key="WebServiceCertificate" value="GUID" />  
  
            -   \<add key="ExposeExceptionDetails" value="true" />  
  
        -   \</appSettings>  
  
    -   \</configuration>  
  
-   <span data-ttu-id="c8743-124">**证书详细信息**-证书具有以下值：</span><span class="sxs-lookup"><span data-stu-id="c8743-124">**Certificate details** - The certificate has the following values:</span></span>  
  
    -   <span data-ttu-id="c8743-125">Subject-"CN = CloudAdapter \<VMName> ，dc = SQL Server，DC = Microsoft"</span><span class="sxs-lookup"><span data-stu-id="c8743-125">Subject - "CN=CloudAdapter\<VMName>, DC=SQL Server, DC=Microsoft"</span></span>  
  
    -   <span data-ttu-id="c8743-126">证书应仅启用服务器身份验证 EKU。</span><span class="sxs-lookup"><span data-stu-id="c8743-126">The certificate should have only Server Authentication EKU enabled.</span></span>  
  
    -   <span data-ttu-id="c8743-127">证书密钥长度为 2048。</span><span class="sxs-lookup"><span data-stu-id="c8743-127">The certificate key length is 2048.</span></span>  
  
 <span data-ttu-id="c8743-128">**配置文件值**：</span><span class="sxs-lookup"><span data-stu-id="c8743-128">**Configuration file values**:</span></span>  
  
|<span data-ttu-id="c8743-129">设置</span><span class="sxs-lookup"><span data-stu-id="c8743-129">Setting</span></span>|<span data-ttu-id="c8743-130">值</span><span class="sxs-lookup"><span data-stu-id="c8743-130">Values</span></span>|<span data-ttu-id="c8743-131">默认</span><span class="sxs-lookup"><span data-stu-id="c8743-131">Default</span></span>|<span data-ttu-id="c8743-132">注释</span><span class="sxs-lookup"><span data-stu-id="c8743-132">Comments</span></span>|  
|-------------|------------|-------------|--------------|  
|<span data-ttu-id="c8743-133">WebServicePort</span><span class="sxs-lookup"><span data-stu-id="c8743-133">WebServicePort</span></span>|<span data-ttu-id="c8743-134">1-65535</span><span class="sxs-lookup"><span data-stu-id="c8743-134">1-65535</span></span>|<span data-ttu-id="c8743-135">11435</span><span class="sxs-lookup"><span data-stu-id="c8743-135">11435</span></span>|<span data-ttu-id="c8743-136">如果未指定，请使用 11435。</span><span class="sxs-lookup"><span data-stu-id="c8743-136">If not specified, use 11435.</span></span>|  
|<span data-ttu-id="c8743-137">WebServiceCertificate</span><span class="sxs-lookup"><span data-stu-id="c8743-137">WebServiceCertificate</span></span>|<span data-ttu-id="c8743-138">Thumbprint</span><span class="sxs-lookup"><span data-stu-id="c8743-138">Thumbprint</span></span>|<span data-ttu-id="c8743-139">空</span><span class="sxs-lookup"><span data-stu-id="c8743-139">Empty</span></span>|<span data-ttu-id="c8743-140">如果为空，则生成新的自签名证书。</span><span class="sxs-lookup"><span data-stu-id="c8743-140">If empty, a new self-signed certificate is generated.</span></span>|  
|<span data-ttu-id="c8743-141">ExposeExceptionDetails</span><span class="sxs-lookup"><span data-stu-id="c8743-141">ExposeExceptionDetails</span></span>|<span data-ttu-id="c8743-142">True/False</span><span class="sxs-lookup"><span data-stu-id="c8743-142">True/False</span></span>|<span data-ttu-id="c8743-143">错误</span><span class="sxs-lookup"><span data-stu-id="c8743-143">False</span></span>||  
  
## <a name="cloud-adapter-troubleshooting"></a><span data-ttu-id="c8743-144">云适配器故障排除</span><span class="sxs-lookup"><span data-stu-id="c8743-144">Cloud Adapter Troubleshooting</span></span>  
 <span data-ttu-id="c8743-145">使用以下信息排除 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的云适配器的故障：</span><span class="sxs-lookup"><span data-stu-id="c8743-145">Use the following information to troubleshoot the Cloud Adapter for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="c8743-146">**错误处理和日志记录**-错误和状态消息会写入应用程序事件日志。</span><span class="sxs-lookup"><span data-stu-id="c8743-146">**Error handling and logging** - Errors and status messages are written to the Application Event Log.</span></span>  
  
-   <span data-ttu-id="c8743-147">**跟踪，事件**-将所有事件写入应用程序事件日志。</span><span class="sxs-lookup"><span data-stu-id="c8743-147">**Tracing, Events** - All events are written to the Application Event Log.</span></span>  
  
-   <span data-ttu-id="c8743-148">**控制，配置**-使用位于以下位置的配置文件： C:\PROGRAM Files\Microsoft SQL Server\120\Tools\CloudAdapter \\ 。</span><span class="sxs-lookup"><span data-stu-id="c8743-148">**Control, configuration** - Use the configuration file located in:  C:\Program Files\Microsoft SQL Server\120\Tools\CloudAdapter\\.</span></span>  
  
|<span data-ttu-id="c8743-149">错误</span><span class="sxs-lookup"><span data-stu-id="c8743-149">Error</span></span>|<span data-ttu-id="c8743-150">错误 ID</span><span class="sxs-lookup"><span data-stu-id="c8743-150">Error ID</span></span>|<span data-ttu-id="c8743-151">原因</span><span class="sxs-lookup"><span data-stu-id="c8743-151">Cause</span></span>|<span data-ttu-id="c8743-152">解决方法</span><span class="sxs-lookup"><span data-stu-id="c8743-152">Resolution</span></span>|  
|-----------|--------------|-----------|----------------|  
|<span data-ttu-id="c8743-153">将证书添加到证书存储区时出现异常。</span><span class="sxs-lookup"><span data-stu-id="c8743-153">There was an exception while adding the certificate to the certificate store.</span></span> <span data-ttu-id="c8743-154">{异常文本}。</span><span class="sxs-lookup"><span data-stu-id="c8743-154">{Exception text}.</span></span>|<span data-ttu-id="c8743-155">45560</span><span class="sxs-lookup"><span data-stu-id="c8743-155">45560</span></span>|<span data-ttu-id="c8743-156">计算机证书存储权限</span><span class="sxs-lookup"><span data-stu-id="c8743-156">Machine certificate store permissions</span></span>|<span data-ttu-id="c8743-157">确保云适配器服务有权将证书添加到计算机证书存储中。</span><span class="sxs-lookup"><span data-stu-id="c8743-157">Ensure that the Cloud Adapter service has permissions to add certificates to the machine certificate store.</span></span>|  
|<span data-ttu-id="c8743-158">尝试为端口 {端口号} 和证书 {指纹} 配置 SSL 绑定时出现异常。</span><span class="sxs-lookup"><span data-stu-id="c8743-158">There was an exception while trying to configure the SSL binding for port {Port number} and certificate {Thumbprint}.</span></span> <span data-ttu-id="c8743-159">{异常}。</span><span class="sxs-lookup"><span data-stu-id="c8743-159">{Exception}.</span></span>|<span data-ttu-id="c8743-160">45561</span><span class="sxs-lookup"><span data-stu-id="c8743-160">45561</span></span>|<span data-ttu-id="c8743-161">另一应用程序已使用该端口或将某一证书绑定到它。</span><span class="sxs-lookup"><span data-stu-id="c8743-161">Another application has already used the port or bound a certificate to it.</span></span>|<span data-ttu-id="c8743-162">在配置文件中删除现有绑定或更改云适配器端口。</span><span class="sxs-lookup"><span data-stu-id="c8743-162">Remove existing bindings or change Cloud Adapter port in the configuration file.</span></span>|  
|<span data-ttu-id="c8743-163">在证书存储区中找不到 SSL 证书 [{指纹}]。</span><span class="sxs-lookup"><span data-stu-id="c8743-163">Failed to find SSL certificate [{Thumbprint}] in the certificate store.</span></span>|<span data-ttu-id="c8743-164">45564</span><span class="sxs-lookup"><span data-stu-id="c8743-164">45564</span></span>|<span data-ttu-id="c8743-165">证书指纹在配置文件中，但是服务的个人证书存储区不包含证书。</span><span class="sxs-lookup"><span data-stu-id="c8743-165">Certificate thumbprint is in the configuration file, but personal certificate store for the service does not contain certificate.</span></span><br /><br /> <span data-ttu-id="c8743-166">权限不足。</span><span class="sxs-lookup"><span data-stu-id="c8743-166">Insufficient permissions.</span></span>|<span data-ttu-id="c8743-167">确保证书在服务的个人证书存储区中。</span><span class="sxs-lookup"><span data-stu-id="c8743-167">Make sure the certificate is in the personal certificate store for the service.</span></span><br /><br /> <span data-ttu-id="c8743-168">确保服务具有对存储区的正确权限。</span><span class="sxs-lookup"><span data-stu-id="c8743-168">Make sure the service has correct permissions for the store.</span></span>|  
|<span data-ttu-id="c8743-169">无法启动 Web 服务。</span><span class="sxs-lookup"><span data-stu-id="c8743-169">Failed to start the web service.</span></span> <span data-ttu-id="c8743-170">{异常文本}。</span><span class="sxs-lookup"><span data-stu-id="c8743-170">{Exception text}.</span></span>|<span data-ttu-id="c8743-171">45570</span><span class="sxs-lookup"><span data-stu-id="c8743-171">45570</span></span>|<span data-ttu-id="c8743-172">在异常中有描述。</span><span class="sxs-lookup"><span data-stu-id="c8743-172">Described in the exception.</span></span>|<span data-ttu-id="c8743-173">启用 ExposeExceptionDetails 并使用异常中的更多信息。</span><span class="sxs-lookup"><span data-stu-id="c8743-173">Enable ExposeExceptionDetails and use extended information from the exception.</span></span>|  
|<span data-ttu-id="c8743-174">证书 [{指纹}] 已过期。</span><span class="sxs-lookup"><span data-stu-id="c8743-174">Certificate [{Thumbprint}] has expired.</span></span>|<span data-ttu-id="c8743-175">45565</span><span class="sxs-lookup"><span data-stu-id="c8743-175">45565</span></span>|<span data-ttu-id="c8743-176">从配置文件引用了过期的证书。</span><span class="sxs-lookup"><span data-stu-id="c8743-176">Expired certificate referenced from the configuration file.</span></span>|<span data-ttu-id="c8743-177">添加有效证书并使用其指纹更新配置文件。</span><span class="sxs-lookup"><span data-stu-id="c8743-177">Add a valid certificate and update the configuration file with its thumbprint.</span></span>|  
|<span data-ttu-id="c8743-178">Web 服务错误： {0} 。</span><span class="sxs-lookup"><span data-stu-id="c8743-178">Web service error: {0}.</span></span>|<span data-ttu-id="c8743-179">45571</span><span class="sxs-lookup"><span data-stu-id="c8743-179">45571</span></span>|<span data-ttu-id="c8743-180">在异常中有描述。</span><span class="sxs-lookup"><span data-stu-id="c8743-180">Described in the exception.</span></span>|<span data-ttu-id="c8743-181">启用 ExposeExceptionDetails 并使用异常中的更多信息。</span><span class="sxs-lookup"><span data-stu-id="c8743-181">Enable ExposeExceptionDetails and use extended information from the exception.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c8743-182">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c8743-182">See Also</span></span>  
 [<span data-ttu-id="c8743-183">将 SQL Server 数据库部署到 Microsoft Azure 虚拟机</span><span class="sxs-lookup"><span data-stu-id="c8743-183">Deploy a SQL Server Database to a Microsoft Azure Virtual Machine</span></span>](../relational-databases/databases/deploy-a-sql-server-database-to-a-microsoft-azure-virtual-machine.md)  
  
  
