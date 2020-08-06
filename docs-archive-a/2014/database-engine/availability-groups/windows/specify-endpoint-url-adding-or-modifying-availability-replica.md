---
title: 在添加或修改可用性副本时指定终结点 URL (SQL Server) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- endpoints [SQL Server], AlwaysOn Availability Groups
- Availability Groups [SQL Server], configuring
- Availability Groups [SQL Server], endpoint
- Endpoint URLs (HADR)
ms.assetid: d7520c13-a8ee-4ddc-9e9a-54cd3d27ef1c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: da1eb2bacd4d5a2f7d0b2a623343f62b5e89597d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693487"
---
# <a name="specify-the-endpoint-url-when-adding-or-modifying-an-availability-replica-sql-server"></a><span data-ttu-id="b06a4-102">在添加或修改可用性副本时指定端点 URL (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="b06a4-102">Specify the Endpoint URL When Adding or Modifying an Availability Replica (SQL Server)</span></span>
  <span data-ttu-id="b06a4-103">若要为某一可用性组承载可用性副本，服务器实例必须拥有数据库镜像端点。</span><span class="sxs-lookup"><span data-stu-id="b06a4-103">To host an availability replica for an availability group, a server instance must possess a database mirroring endpoint.</span></span> <span data-ttu-id="b06a4-104">该服务器实例使用此端点来侦听来自其他服务器实例承载的可用性副本的 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 消息。</span><span class="sxs-lookup"><span data-stu-id="b06a4-104">The server instance uses this endpoint to listen for [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] messages from availability replicas hosted by other server instances.</span></span> <span data-ttu-id="b06a4-105">若要为某一可用性组定义可用性副本，您必须指定将承载该副本的服务器实例的端点 URL。</span><span class="sxs-lookup"><span data-stu-id="b06a4-105">To define an availability replica for an availability group, you must specify the endpoint URL of the server instance that will host the replica.</span></span> <span data-ttu-id="b06a4-106">“端点 URL”标识数据库镜像端点的传输协议 - TCP、服务器实例的系统地址以及与端点关联的端口号。</span><span class="sxs-lookup"><span data-stu-id="b06a4-106">The *endpoint URL* identifies the transport protocol of the database mirroring endpoint-TCP, the system address of the server instance, and the port number associated with the endpoint.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b06a4-107">“端点 URL”一词是“服务器网络地址”一词的同义词，由数据库镜像的用户界面和文档使用。</span><span class="sxs-lookup"><span data-stu-id="b06a4-107">The term "endpoint URL" is synonymous with the term "server network address" used by the database mirroring user interface and documentation.</span></span>  
  
-   [<span data-ttu-id="b06a4-108">终结点 URL 的语法</span><span class="sxs-lookup"><span data-stu-id="b06a4-108">Syntax for an Endpoint URL</span></span>](#SyntaxOfURL)  
  
-   [<span data-ttu-id="b06a4-109">查找系统的完全限定的域名</span><span class="sxs-lookup"><span data-stu-id="b06a4-109">Finding the Fully Qualified Domain Name of A System</span></span>](#Finding_FQDN)  
  
-   [<span data-ttu-id="b06a4-110">相关任务</span><span class="sxs-lookup"><span data-stu-id="b06a4-110">Related Tasks</span></span>](#RelatedTasks)  
  
-   [<span data-ttu-id="b06a4-111">相关内容</span><span class="sxs-lookup"><span data-stu-id="b06a4-111">Related Content</span></span>](#RelatedContent)  
  
##  <a name="syntax-for-an-endpoint-url"></a><a name="SyntaxOfURL"></a> <span data-ttu-id="b06a4-112">端点 URL 的语法</span><span class="sxs-lookup"><span data-stu-id="b06a4-112">Syntax for an Endpoint URL</span></span>  
 <span data-ttu-id="b06a4-113">端点 URL 的语法采用以下形式：</span><span class="sxs-lookup"><span data-stu-id="b06a4-113">The syntax for an endpoint URL is of the form:</span></span>  
  
 <span data-ttu-id="b06a4-114">TCP<strong>://</strong>\<system-address><strong>:</strong>\<port> </span><span class="sxs-lookup"><span data-stu-id="b06a4-114">TCP<strong>://</strong>*\<system-address>*<strong>:</strong>*\<port>*</span></span>  
  
 <span data-ttu-id="b06a4-115">其中</span><span class="sxs-lookup"><span data-stu-id="b06a4-115">where</span></span>  
  
-   <span data-ttu-id="b06a4-116">\<system-address> 是明确标识目标计算机系统的字符串。</span><span class="sxs-lookup"><span data-stu-id="b06a4-116">*\<system-address>* is a string that unambiguously identifies the target computer system.</span></span> <span data-ttu-id="b06a4-117">通常，服务器地址是系统名称（如果各系统都在同一个域中）、完全限定域名或 IP 地址：</span><span class="sxs-lookup"><span data-stu-id="b06a4-117">Typically, the server address is a system name (if the systems are in the same domain), a fully qualified domain name, or an IP address:</span></span>  
  
    -   <span data-ttu-id="b06a4-118">因为 Windows Server 故障转移群集 (WSFC) 群集的节点处于相同的域，所以，您可以使用计算机系统的名称，例如 `SYSTEM46`。</span><span class="sxs-lookup"><span data-stu-id="b06a4-118">Because the nodes of Windows Server Failover Clustering (WSFC) cluster are the same domain, you can use the name of the computer system; for example, `SYSTEM46`.</span></span>  
  
    -   <span data-ttu-id="b06a4-119">若要使用 IP 地址，则该地址在您环境中必须是唯一的。</span><span class="sxs-lookup"><span data-stu-id="b06a4-119">To use an IP address, it must be unique in your environment.</span></span> <span data-ttu-id="b06a4-120">建议只使用静态的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="b06a4-120">We recommend that you use an IP address only if it is static.</span></span> <span data-ttu-id="b06a4-121">IP 地址可以是 IP 版本 4 (IPv4) 或 IP 版本 6 (IPv6)。</span><span class="sxs-lookup"><span data-stu-id="b06a4-121">The IP address can be IP Version 4 (IPv4) or IP Version 6 (IPv6).</span></span> <span data-ttu-id="b06a4-122">必须用方括号将 IPv6 地址括起，例如： **[** _<IPv6_address>_ **]** 。</span><span class="sxs-lookup"><span data-stu-id="b06a4-122">An IPv6 address must be enclosed within square brackets, for example: **[**_<IPv6_address>_**]**.</span></span>  
  
         <span data-ttu-id="b06a4-123">若要了解系统的 IP 地址，则在 Windows 命令提示符处，输入 **ipconfig** 命令。</span><span class="sxs-lookup"><span data-stu-id="b06a4-123">To learn the IP address of a system, at the Windows command prompt, enter the **ipconfig** command.</span></span>  
  
    -   <span data-ttu-id="b06a4-124">保证完全限定域名的有效性。</span><span class="sxs-lookup"><span data-stu-id="b06a4-124">The fully qualified domain name is guaranteed to work.</span></span> <span data-ttu-id="b06a4-125">它是在不同位置具有不同形式的本地定义的地址字符串。</span><span class="sxs-lookup"><span data-stu-id="b06a4-125">This is a locally defined address string that takes different forms in different places.</span></span> <span data-ttu-id="b06a4-126">通常（但并不总是），完全限定域名是一个复合名称，包含计算机名称和一系列句点分隔的域段，其格式为：</span><span class="sxs-lookup"><span data-stu-id="b06a4-126">Often, but not always, a fully qualified domain name is a compound name that includes the computer name and a series of period-separated domain segments of the form:</span></span>  
  
         <span data-ttu-id="b06a4-127">computer_name .</span><span class="sxs-lookup"><span data-stu-id="b06a4-127">_computer_name_ **.**</span></span> <span data-ttu-id="b06a4-128">_domain_segment_[... **.** _domain_segment_]</span><span class="sxs-lookup"><span data-stu-id="b06a4-128">_domain_segment_[...**.**_domain_segment_]</span></span>  
  
         <span data-ttu-id="b06a4-129">其中， *computer_name*是运行服务器实例的计算机的网络名称， *domain_segment*[... **.** _domain_segment_] 是服务器的其余域信息；例如： `localinfo.corp.Adventure-Works.com`。</span><span class="sxs-lookup"><span data-stu-id="b06a4-129">where *computer_name i*s the network name of the computer running the server instance, and *domain_segment*[...**.**_domain_segment_] is the remaining domain information of the server; for example: `localinfo.corp.Adventure-Works.com`.</span></span>  
  
         <span data-ttu-id="b06a4-130">在公司或组织内确定域段的内容和数量。</span><span class="sxs-lookup"><span data-stu-id="b06a4-130">The content and number of domain segments are determined within the company or organization.</span></span> <span data-ttu-id="b06a4-131">有关详细信息，请参阅本主题后面的 [查找完全限定域名](#Finding_FQDN)。</span><span class="sxs-lookup"><span data-stu-id="b06a4-131">For more information, see [Finding the Fully Qualified Domain Name](#Finding_FQDN), later in this topic.</span></span>  
  
-   <span data-ttu-id="b06a4-132">\<port> 是伙伴服务器实例的镜像终结点所用的端口号。</span><span class="sxs-lookup"><span data-stu-id="b06a4-132">*\<port>* is the port number used by the mirroring endpoint of the partner server instance.</span></span>  
  
     <span data-ttu-id="b06a4-133">数据库镜像端点可以使用计算机系统上的任意可用端口。</span><span class="sxs-lookup"><span data-stu-id="b06a4-133">A database mirroring endpoint can use any available port on the computer system.</span></span> <span data-ttu-id="b06a4-134">每个端口号只能与一个端点相关联，而每个端点与一个服务器实例相关联；这样，同一服务器上的不同服务器实例便可使用不同端口来侦听各个端点。</span><span class="sxs-lookup"><span data-stu-id="b06a4-134">Each port number must be associated with only one endpoint, and each endpoint is associated with a single server instance; thus, different server instances on the same server listen on different endpoints with different ports.</span></span> <span data-ttu-id="b06a4-135">因此，在您指定可用性副本时在端点 URL 中指定的端口会始终将传入消息定向到其端点与该端口关联的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="b06a4-135">Therefore, the port you specify in the endpoint URL when you specify an availability replica will always direct incoming messages to the server instance whose endpoint is associated with that port.</span></span>  
  
     <span data-ttu-id="b06a4-136">在端点 URL 中，只有端口号才能标识与目标计算机上的镜像端点相关联的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="b06a4-136">IIn the endpoint URL, only the number of the port identifies the server instance that is associated with the mirroring endpoint on the target computer.</span></span> <span data-ttu-id="b06a4-137">下图显示了一台计算机上两个服务器实例的端点 URL。</span><span class="sxs-lookup"><span data-stu-id="b06a4-137">The following figure illustrates the endpoint URLs of two server instances on a single computer.</span></span> <span data-ttu-id="b06a4-138">默认实例使用端口 `7022` ，命名实例使用端口 `7033`。</span><span class="sxs-lookup"><span data-stu-id="b06a4-138">The default instance uses port `7022` and the named instance uses port `7033`.</span></span> <span data-ttu-id="b06a4-139">这两个服务器实例的端点 URL 分别为： `TCP://MYSYSTEM.Adventure-works.MyDomain.com:7022` 和 `TCP://MYSYSTEM.Adventure-works.MyDomain.com:7033`。</span><span class="sxs-lookup"><span data-stu-id="b06a4-139">The endpoint URL for these two server instances are, respectively: `TCP://MYSYSTEM.Adventure-works.MyDomain.com:7022` and `TCP://MYSYSTEM.Adventure-works.MyDomain.com:7033`.</span></span> <span data-ttu-id="b06a4-140">请注意，地址中不包含服务器实例名。</span><span class="sxs-lookup"><span data-stu-id="b06a4-140">Note that the address does not contain the name of the server instance.</span></span>  
  
     <span data-ttu-id="b06a4-141">![默认实例的服务器网络地址](../../media/dbm-2-instances-ports-1-system.gif "默认实例的服务器网络地址")</span><span class="sxs-lookup"><span data-stu-id="b06a4-141">![Server network addresses of a default instance](../../media/dbm-2-instances-ports-1-system.gif "Server network addresses of a default instance")</span></span>  
  
     <span data-ttu-id="b06a4-142">若要标识当前与服务器实例的数据库镜像端点关联的端口，请使用以下 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 语句：</span><span class="sxs-lookup"><span data-stu-id="b06a4-142">To identify the port currently associated with database mirroring endpoint of a server instance, use the following [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement:</span></span>  
  
    ```sql
    SELECT type_desc, port FROM sys.TCP_endpoints  
    ```  
  
     <span data-ttu-id="b06a4-143">找到 **type_desc** 值为“DATABASE_MIRRORING”的行，然后使用对应的端口号。</span><span class="sxs-lookup"><span data-stu-id="b06a4-143">Find the row whose **type_desc** value is "DATABASE_MIRRORING," and use the corresponding port number.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="b06a4-144">示例</span><span class="sxs-lookup"><span data-stu-id="b06a4-144">Examples</span></span>  
  
#### <a name="a-using-a-system-name"></a><span data-ttu-id="b06a4-145">A.</span><span class="sxs-lookup"><span data-stu-id="b06a4-145">A.</span></span> <span data-ttu-id="b06a4-146">使用系统名称</span><span class="sxs-lookup"><span data-stu-id="b06a4-146">Using a system name</span></span>  
 <span data-ttu-id="b06a4-147">以下端点 URL 指定系统名称 `SYSTEM46`和端口 `7022`。</span><span class="sxs-lookup"><span data-stu-id="b06a4-147">The following endpoint URL specifies a system name, `SYSTEM46`, and port `7022`.</span></span>  
  
 `TCP://SYSTEM46:7022`  
  
#### <a name="b-using-a-fully-qualified-domain-name"></a><span data-ttu-id="b06a4-148">B.</span><span class="sxs-lookup"><span data-stu-id="b06a4-148">B.</span></span> <span data-ttu-id="b06a4-149">使用完全限定域名</span><span class="sxs-lookup"><span data-stu-id="b06a4-149">Using a fully qualified domain name</span></span>  
 <span data-ttu-id="b06a4-150">以下端点 URL 指定完全限定域名 `DBSERVER8.manufacturing.Adventure-Works.com`和端口 `7024`。</span><span class="sxs-lookup"><span data-stu-id="b06a4-150">The following endpoint URL specifies a fully qualified domain name, `DBSERVER8.manufacturing.Adventure-Works.com`, and port `7024`.</span></span>  
  
 `TCP://DBSERVER8.manufacturing.Adventure-Works.com:7024`  
  
#### <a name="c-using-ipv4"></a><span data-ttu-id="b06a4-151">C.</span><span class="sxs-lookup"><span data-stu-id="b06a4-151">C.</span></span> <span data-ttu-id="b06a4-152">使用 IPv4</span><span class="sxs-lookup"><span data-stu-id="b06a4-152">Using IPv4</span></span>  
 <span data-ttu-id="b06a4-153">以下端点 URL 指定 IPv4 地址 `10.193.9.134`和端口 `7023`。</span><span class="sxs-lookup"><span data-stu-id="b06a4-153">The following endpoint URL specifies an IPv4 address, `10.193.9.134`, and port `7023`.</span></span>  
  
 `TCP://10.193.9.134:7023`  
  
#### <a name="d-using-ipv6"></a><span data-ttu-id="b06a4-154">D.</span><span class="sxs-lookup"><span data-stu-id="b06a4-154">D.</span></span> <span data-ttu-id="b06a4-155">使用 IPv6</span><span class="sxs-lookup"><span data-stu-id="b06a4-155">Using IPv6</span></span>  
 <span data-ttu-id="b06a4-156">以下端点 URL 包含 IPv6 地址 `2001:4898:23:1002:20f:1fff:feff:b3a3`和端口 `7022`。</span><span class="sxs-lookup"><span data-stu-id="b06a4-156">The following endpoint URL contains an IPv6 address, `2001:4898:23:1002:20f:1fff:feff:b3a3`, and port `7022`.</span></span>  
  
 `TCP://[2001:4898:23:1002:20f:1fff:feff:b3a3]:7022`  
  
##  <a name="finding-the-fully-qualified-domain-name-of-a-system"></a><a name="Finding_FQDN"></a> <span data-ttu-id="b06a4-157">查找系统的完全限定域名</span><span class="sxs-lookup"><span data-stu-id="b06a4-157">Finding the Fully Qualified Domain Name of A System</span></span>  
 <span data-ttu-id="b06a4-158">若要查找系统的完全限定域名，请在该系统的 Windows 命令提示符下，输入：</span><span class="sxs-lookup"><span data-stu-id="b06a4-158">To find the fully qualified domain name of a system, at the Windows command prompt on that system, enter:</span></span>  
  
 <span data-ttu-id="b06a4-159">**IPCONFIG /ALL**</span><span class="sxs-lookup"><span data-stu-id="b06a4-159">**IPCONFIG /ALL**</span></span>  
  
 <span data-ttu-id="b06a4-160">若要形成完全限定的域名，请将 *<host_name>* 和 *<Primary_Dns_Suffix>* 的值连接一起，如下所示：</span><span class="sxs-lookup"><span data-stu-id="b06a4-160">To form the fully qualified domain name, concatenate the values of *<host_name>* and *<Primary_Dns_Suffix>* as follows:</span></span>  
  
 <span data-ttu-id="b06a4-161"><host_name> .</span><span class="sxs-lookup"><span data-stu-id="b06a4-161">_<host_name>_ **.**</span></span> <span data-ttu-id="b06a4-162">_<Primary_Dns_Suffix>_</span><span class="sxs-lookup"><span data-stu-id="b06a4-162">_<Primary_Dns_Suffix>_</span></span>  
  
 <span data-ttu-id="b06a4-163">例如，IP 配置</span><span class="sxs-lookup"><span data-stu-id="b06a4-163">For example, the IP configuration</span></span>  
  
 `Host Name  .  .  .  .  .  .  : MYSERVER`  
  
 `Primary Dns Suffix  .  .  .  : mydomain.Adventure-Works.com`  
  
 <span data-ttu-id="b06a4-164">等同于以下完全限定域名：</span><span class="sxs-lookup"><span data-stu-id="b06a4-164">equates to the following fully qualified domain name:</span></span>  
  
 `MYSERVER.mydomain.Adventure-Works.com`  
  
> [!NOTE]  
>  <span data-ttu-id="b06a4-165">如果您需要与完全限定域名有关的详细信息，请与系统管理员联系。</span><span class="sxs-lookup"><span data-stu-id="b06a4-165">If you need more information about a fully qualified domain name, see your system administrator.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="b06a4-166">相关任务</span><span class="sxs-lookup"><span data-stu-id="b06a4-166">Related Tasks</span></span>  
 <span data-ttu-id="b06a4-167">**配置数据库镜像端点**</span><span class="sxs-lookup"><span data-stu-id="b06a4-167">**To Configure a Database Mirroring Endpoint**</span></span>  
  
-   [<span data-ttu-id="b06a4-168">为 AlwaysOn 可用性组 &#40;SQL Server PowerShell 创建数据库镜像端点&#41;</span><span class="sxs-lookup"><span data-stu-id="b06a4-168">Create a Database Mirroring Endpoint for AlwaysOn Availability Groups &#40;SQL Server PowerShell&#41;</span></span>](database-mirroring-always-on-availability-groups-powershell.md)  
  
-   [<span data-ttu-id="b06a4-169">为 Windows 身份验证创建数据库镜像终结点 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b06a4-169">Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [<span data-ttu-id="b06a4-170">使用数据库镜像终结点证书 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b06a4-170">Use Certificates for a Database Mirroring Endpoint &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)  
  
    -   [<span data-ttu-id="b06a4-171">允许数据库镜像终结点使用证书进行出站连接 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b06a4-171">Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/database-mirroring-use-certificates-for-outbound-connections.md)  
  
    -   [<span data-ttu-id="b06a4-172">允许数据库镜像终结点将证书用于入站连接 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b06a4-172">Allow a Database Mirroring Endpoint to Use Certificates for Inbound Connections &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/database-mirroring-use-certificates-for-inbound-connections.md)  
  
-   [<span data-ttu-id="b06a4-173">指定服务器网络地址（数据库镜像）</span><span class="sxs-lookup"><span data-stu-id="b06a4-173">Specify a Server Network Address &#40;Database Mirroring&#41;</span></span>](../../database-mirroring/specify-a-server-network-address-database-mirroring.md)  
  
-   [<span data-ttu-id="b06a4-174">&#41;删除 AlwaysOn 可用性组配置 &#40;SQL Server 的疑难解答</span><span class="sxs-lookup"><span data-stu-id="b06a4-174">Troubleshoot AlwaysOn Availability Groups Configuration &#40;SQL Server&#41;deleted</span></span>](troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
  
 <span data-ttu-id="b06a4-175">**查看有关数据库镜像端点的信息**</span><span class="sxs-lookup"><span data-stu-id="b06a4-175">**To View Information About the Database Mirroring Endpoint**</span></span>  
  
-   [<span data-ttu-id="b06a4-176">sys.database_mirroring_endpoints (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b06a4-176">sys.database_mirroring_endpoints &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql)  
  
 <span data-ttu-id="b06a4-177">**添加可用性副本**</span><span class="sxs-lookup"><span data-stu-id="b06a4-177">**To add an availability replica**</span></span>  
  
-   [<span data-ttu-id="b06a4-178">将辅助副本添加到可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="b06a4-178">Add a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="b06a4-179">将辅助副本联接到可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="b06a4-179">Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="b06a4-180">相关内容</span><span class="sxs-lookup"><span data-stu-id="b06a4-180">Related Content</span></span>  
  
-   [<span data-ttu-id="b06a4-181">用于高可用性和灾难恢复的 Microsoft SQL Server AlwaysOn 解决方案指南</span><span class="sxs-lookup"><span data-stu-id="b06a4-181">Microsoft SQL Server AlwaysOn Solutions Guide for High Availability and Disaster Recovery</span></span>](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
## <a name="see-also"></a><span data-ttu-id="b06a4-182">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b06a4-182">See Also</span></span>  
 <span data-ttu-id="b06a4-183">[创建和配置可用性组 (SQL Server)](creation-and-configuration-of-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="b06a4-183">[Creation and Configuration of Availability Groups &#40;SQL Server&#41;](creation-and-configuration-of-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="b06a4-184">[AlwaysOn 可用性组 &#40;SQL Server 概述&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="b06a4-184">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="b06a4-185">CREATE ENDPOINT (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b06a4-185">CREATE ENDPOINT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-endpoint-transact-sql)  
