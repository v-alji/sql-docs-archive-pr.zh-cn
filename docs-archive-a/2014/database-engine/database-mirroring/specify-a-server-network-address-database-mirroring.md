---
title: 指定服务器网络地址（数据库镜像）| Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], deployment
- database mirroring [SQL Server], endpoint
- endpoints [SQL Server], database mirroring
- server network addresses [SQL Server]
ms.assetid: a64d4b6b-9016-4f1e-a310-b1df181dd0c6
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5c7db7ee6d321229205248059ce09a86f1da101f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587579"
---
# <a name="specify-a-server-network-address-database-mirroring"></a><span data-ttu-id="3e5a7-102">指定服务器网络地址（数据库镜像）</span><span class="sxs-lookup"><span data-stu-id="3e5a7-102">Specify a Server Network Address (Database Mirroring)</span></span>
  <span data-ttu-id="3e5a7-103">设置数据库镜像会话要求每个服务器实例都有一个服务器网络地址。</span><span class="sxs-lookup"><span data-stu-id="3e5a7-103">Setting up a database mirroring session requires a server network address for each of the server instances.</span></span> <span data-ttu-id="3e5a7-104">服务器实例的服务器网络地址必须通过提供系统地址和实例侦听的端口号来明确标识该实例。</span><span class="sxs-lookup"><span data-stu-id="3e5a7-104">The server network address of a server instance must unambiguously identify the instance by providing a system address and the number of the port on which the instance is listening.</span></span>  
  
 <span data-ttu-id="3e5a7-105">在服务器网络地址中指定一个端口之前，服务器实例上必须具有数据库镜像端点。</span><span class="sxs-lookup"><span data-stu-id="3e5a7-105">Before you can specify a port in a server network address, the database mirroring endpoint must exist on the server instance.</span></span> <span data-ttu-id="3e5a7-106">有关详细信息，请参阅 [为 Windows 身份验证创建数据库镜像终结点 (Transact-SQL)](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="3e5a7-106">For more information, see [Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md).</span></span>  
  
  
  
##  <a name="syntax-for-a-server-network-address"></a><a name="Syntax"></a> <span data-ttu-id="3e5a7-107">服务器网络地址的语法</span><span class="sxs-lookup"><span data-stu-id="3e5a7-107">Syntax for a Server Network Address</span></span>  
 <span data-ttu-id="3e5a7-108">服务器网络地址的语法格式如下：</span><span class="sxs-lookup"><span data-stu-id="3e5a7-108">The syntax for a server network address is of the form:</span></span>  
  
 <span data-ttu-id="3e5a7-109">TCP：<strong>//</strong> *\<system-address>* <strong> ：<strong>*\<port>*</span><span class="sxs-lookup"><span data-stu-id="3e5a7-109">TCP<strong>://</strong>*\<system-address>*<strong>:<strong>*\<port>*</span></span> 
  
 <span data-ttu-id="3e5a7-110">其中</span><span class="sxs-lookup"><span data-stu-id="3e5a7-110">where</span></span>  
  
-   <span data-ttu-id="3e5a7-111">\<system-address> 是明确标识目标计算机系统的字符串。</span><span class="sxs-lookup"><span data-stu-id="3e5a7-111">*\<system-address>* is a string that unambiguously identifies the destination computer system.</span></span> <span data-ttu-id="3e5a7-112">通常，服务器地址是系统名称（如果各系统都在同一个域中）、完全限定域名或 IP 地址：</span><span class="sxs-lookup"><span data-stu-id="3e5a7-112">Typically, the server address is a system name (if the systems are in the same domain), a fully qualified domain name, or an IP address:</span></span>  
  
    -   <span data-ttu-id="3e5a7-113">如果各系统都在同一个域中，则可以使用计算机系统的名称；例如， `SYSTEM46`。</span><span class="sxs-lookup"><span data-stu-id="3e5a7-113">If the systems are the same domain, you can use the name of the computer system; for example, `SYSTEM46`.</span></span>  
  
    -   <span data-ttu-id="3e5a7-114">若要使用 IP 地址，则该地址在您环境中必须是唯一的。</span><span class="sxs-lookup"><span data-stu-id="3e5a7-114">To use an IP address, it must be unique in your environment.</span></span> <span data-ttu-id="3e5a7-115">建议只使用静态的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="3e5a7-115">We recommend that you use an IP address only if it is static.</span></span> <span data-ttu-id="3e5a7-116">IP 地址可以是 IP 版本 4 (IPv4) 或 IP 版本 6 (IPv6)。</span><span class="sxs-lookup"><span data-stu-id="3e5a7-116">The IP address can be IP Version 4 (IPv4) or IP Version 6 (IPv6).</span></span> <span data-ttu-id="3e5a7-117">必须用方括号将 IPv6 地址括起，例如： **[** _<IPv6_address>_ **]** 。</span><span class="sxs-lookup"><span data-stu-id="3e5a7-117">An IPv6 address must be enclosed within square brackets, for example: **[**_<IPv6_address>_**]**.</span></span>  
  
         <span data-ttu-id="3e5a7-118">若要了解系统的 IP 地址，则在 Windows 命令提示符处，输入 **ipconfig** 命令。</span><span class="sxs-lookup"><span data-stu-id="3e5a7-118">To learn the IP address of a system, at the Windows command prompt, enter the **ipconfig** command.</span></span>  
  
    -   <span data-ttu-id="3e5a7-119">保证完全限定域名的有效性。</span><span class="sxs-lookup"><span data-stu-id="3e5a7-119">The fully qualified domain name is guaranteed to work.</span></span> <span data-ttu-id="3e5a7-120">它是在不同位置具有不同形式的本地定义的地址字符串。</span><span class="sxs-lookup"><span data-stu-id="3e5a7-120">This is a locally defined address string that different forms in different places.</span></span> <span data-ttu-id="3e5a7-121">通常（但并不总是），完全限定域名是一个复合名称，包含计算机名称和一系列句点分隔的域段，其格式为：</span><span class="sxs-lookup"><span data-stu-id="3e5a7-121">Often, but not always, a fully qualified domain name is a compound name that includes the computer name and a series of period-separated domain segments of the form:</span></span>  
  
         <span data-ttu-id="3e5a7-122">computer_name .</span><span class="sxs-lookup"><span data-stu-id="3e5a7-122">_computer_name_ **.**</span></span> <span data-ttu-id="3e5a7-123">_domain_segment_[... **.** _domain_segment_]</span><span class="sxs-lookup"><span data-stu-id="3e5a7-123">_domain_segment_[...**.**_domain_segment_]</span></span>  
  
         <span data-ttu-id="3e5a7-124">其中， *computer_name*是运行服务器实例的计算机的网络名称， *domain_segment*[... **.** _domain_segment_] 是服务器的其余域信息；例如： `localinfo.corp.Adventure-Works.com`。</span><span class="sxs-lookup"><span data-stu-id="3e5a7-124">where *computer_name i*s the network name of the computer running the server instance, and *domain_segment*[...**.**_domain_segment_] is the remaining domain information of the server; for example: `localinfo.corp.Adventure-Works.com`.</span></span>  
  
         <span data-ttu-id="3e5a7-125">在公司或组织内确定域段的内容和数量。</span><span class="sxs-lookup"><span data-stu-id="3e5a7-125">The content and number of domain segments are determined within the company or organization.</span></span> <span data-ttu-id="3e5a7-126">如果您不知道服务器的完全限定域名，请与系统管理员联系。</span><span class="sxs-lookup"><span data-stu-id="3e5a7-126">If you do not know the fully qualified domain name for your server, see your system administrator.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="3e5a7-127">有关如何查找完全限定域名的信息，请参阅本主题后面的“查找完全限定域名”。</span><span class="sxs-lookup"><span data-stu-id="3e5a7-127">For information about how to find a fully qualified domain name, see "Finding the Fully Qualified Domain Name," later in this topic.</span></span>  
  
-   <span data-ttu-id="3e5a7-128">\<port> 是伙伴服务器实例的镜像终结点所用的端口号。</span><span class="sxs-lookup"><span data-stu-id="3e5a7-128">*\<port>* is the port number used by the mirroring endpoint of the partner server instance.</span></span> <span data-ttu-id="3e5a7-129">有关指定终结点的信息，请参阅 [为 Windows 身份验证创建数据库镜像终结点 (Transact-SQL)](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="3e5a7-129">For information about specifying an endpoint, see [Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md).</span></span>  
  
     <span data-ttu-id="3e5a7-130">数据库镜像端点可以使用计算机系统上的任意可用端口。</span><span class="sxs-lookup"><span data-stu-id="3e5a7-130">A database mirroring endpoint can use any available port on the computer system.</span></span> <span data-ttu-id="3e5a7-131">计算机系统上的每个端口号只能与一个端点相关联，而每个端点与一个服务器实例相关联；这样，同一服务器上的不同服务器实例便可使用不同端口来侦听各个端点。</span><span class="sxs-lookup"><span data-stu-id="3e5a7-131">Each port number on a computer system must be associated with only one endpoint, and each endpoint is associated with a single server instance; thus, different server instances on the same server listen on different endpoints with different ports.</span></span> <span data-ttu-id="3e5a7-132">因此，设置数据库镜像会话时在服务器网络地址中指定的端口会始终将会话定向到其端点与该端口关联的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="3e5a7-132">Therefore, the port you specify in the server network address when you set up a database mirroring session will always direct the session to the server instance whose endpoint is associated with that port.</span></span>  
  
     <span data-ttu-id="3e5a7-133">在服务器实例的服务器网络地址中，只有通过与其镜像端点关联的端口号才能将实例与计算机上的所有其他实例区分开来。</span><span class="sxs-lookup"><span data-stu-id="3e5a7-133">In the server network address of a server instance, only the number of the port associated with its mirroring endpoint distinguishes that instance from any other instances on the computer.</span></span> <span data-ttu-id="3e5a7-134">下图显示了一台计算机上两个服务器实例的服务器网络地址。</span><span class="sxs-lookup"><span data-stu-id="3e5a7-134">The following figure illustrates the server network addresses of two server instances on a single computer.</span></span> <span data-ttu-id="3e5a7-135">默认实例使用端口 `7022` ，命名实例使用端口 `7033`。</span><span class="sxs-lookup"><span data-stu-id="3e5a7-135">The default instance uses port `7022` and the named instance uses port `7033`.</span></span> <span data-ttu-id="3e5a7-136">这两个服务器实例的服务器网络地址分别为： `TCP://MYSYSTEM.Adventure-works.MyDomain.com:7022` 和 `TCP://MYSYSTEM.Adventure-works.MyDomain.com:7033`。</span><span class="sxs-lookup"><span data-stu-id="3e5a7-136">The server network address for these two server instances are, respectively: `TCP://MYSYSTEM.Adventure-works.MyDomain.com:7022` and `TCP://MYSYSTEM.Adventure-works.MyDomain.com:7033`.</span></span> <span data-ttu-id="3e5a7-137">请注意，地址中不包含服务器实例名。</span><span class="sxs-lookup"><span data-stu-id="3e5a7-137">Note that the address does not contain the name of the server instance.</span></span>  
  
     <span data-ttu-id="3e5a7-138">![默认实例的服务器网络地址](../media/dbm-2-instances-ports-1-system.gif "默认实例的服务器网络地址")</span><span class="sxs-lookup"><span data-stu-id="3e5a7-138">![Server network addresses of a default instance](../media/dbm-2-instances-ports-1-system.gif "Server network addresses of a default instance")</span></span>  
  
     <span data-ttu-id="3e5a7-139">若要标识当前与服务器实例的数据库镜像端点关联的端口，请使用以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句：</span><span class="sxs-lookup"><span data-stu-id="3e5a7-139">To identify the port currently associated with database mirroring endpoint of a server instance, use the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement:</span></span>  
  
    ```  
    SELECT type_desc, port FROM sys.tcp_endpoints  
    ```  
  
     <span data-ttu-id="3e5a7-140">找到 **type_desc** 值为“DATABASE_MIRRORING”的行，然后使用对应的端口号。</span><span class="sxs-lookup"><span data-stu-id="3e5a7-140">Find the row whose **type_desc** value is "DATABASE_MIRRORING," and use the corresponding port number.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="3e5a7-141">示例</span><span class="sxs-lookup"><span data-stu-id="3e5a7-141">Examples</span></span>  
  
#### <a name="a-using-a-system-name"></a><span data-ttu-id="3e5a7-142">A.</span><span class="sxs-lookup"><span data-stu-id="3e5a7-142">A.</span></span> <span data-ttu-id="3e5a7-143">使用系统名称</span><span class="sxs-lookup"><span data-stu-id="3e5a7-143">Using a system name</span></span>  
 <span data-ttu-id="3e5a7-144">以下服务器网络地址指定系统名称 `SYSTEM46`和端口 `7022`。</span><span class="sxs-lookup"><span data-stu-id="3e5a7-144">The following server network address specifies a system name, `SYSTEM46`, and port `7022`.</span></span>  
  
```  
ALTER DATABASE AdventureWorks SET PARTNER ='tcp://SYSTEM46:7022';  
```  
  
#### <a name="b-using-a-fully-qualified-domain-name"></a><span data-ttu-id="3e5a7-145">B.</span><span class="sxs-lookup"><span data-stu-id="3e5a7-145">B.</span></span> <span data-ttu-id="3e5a7-146">使用完全限定域名</span><span class="sxs-lookup"><span data-stu-id="3e5a7-146">Using a fully qualified domain name</span></span>  
 <span data-ttu-id="3e5a7-147">以下服务器网络地址指定完全限定域名 `DBSERVER8.manufacturing.Adventure-Works.com`和端口 `7024`。</span><span class="sxs-lookup"><span data-stu-id="3e5a7-147">The following server network address specifies a fully qualified domain name, `DBSERVER8.manufacturing.Adventure-Works.com`, and port `7024`.</span></span>  
  
```  
ALTER DATABASE AdventureWorks SET PARTNER ='tcp://DBSERVER8.manufacturing.Adventure-Works.com:7024';  
```  
  
#### <a name="c-using-ipv4"></a><span data-ttu-id="3e5a7-148">C.</span><span class="sxs-lookup"><span data-stu-id="3e5a7-148">C.</span></span> <span data-ttu-id="3e5a7-149">使用 IPv4</span><span class="sxs-lookup"><span data-stu-id="3e5a7-149">Using IPv4</span></span>  
 <span data-ttu-id="3e5a7-150">以下服务器网络地址指定 IPv4 地址 `10.193.9.134`和端口 `7023`。</span><span class="sxs-lookup"><span data-stu-id="3e5a7-150">The following server network address specifies an IPv4 address, `10.193.9.134`, and port `7023`.</span></span>  
  
```  
ALTER DATABASE AdventureWorks SET PARTNER ='tcp://10.193.9.134:7023';  
```  
  
#### <a name="d-using-ipv6"></a><span data-ttu-id="3e5a7-151">D.</span><span class="sxs-lookup"><span data-stu-id="3e5a7-151">D.</span></span> <span data-ttu-id="3e5a7-152">使用 IPv6</span><span class="sxs-lookup"><span data-stu-id="3e5a7-152">Using IPv6</span></span>  
 <span data-ttu-id="3e5a7-153">以下服务器网络地址包含 IPv6 地址 `2001:4898:23:1002:20f:1fff:feff:b3a3`和端口 `7022`。</span><span class="sxs-lookup"><span data-stu-id="3e5a7-153">The following server network address contains an IPv6 address, `2001:4898:23:1002:20f:1fff:feff:b3a3`, and port `7022`.</span></span>  
  
```  
ALTER DATABASE AdventureWorks SET PARTNER ='tcp://[2001:4898:23:1002:20f:1fff:feff:b3a3]:7022';  
```  
  
## <a name="finding-the-fully-qualified-domain-name"></a><span data-ttu-id="3e5a7-154">查找完全限定域名</span><span class="sxs-lookup"><span data-stu-id="3e5a7-154">Finding the Fully Qualified Domain Name</span></span>  
 <span data-ttu-id="3e5a7-155">若要查找系统的完全限定域名，请在该系统的 Windows 命令提示符下，输入：</span><span class="sxs-lookup"><span data-stu-id="3e5a7-155">To find the fully qualified domain name of a system, at the Windows command prompt on that system, enter:</span></span>  
  
 <span data-ttu-id="3e5a7-156">**IPCONFIG /ALL**</span><span class="sxs-lookup"><span data-stu-id="3e5a7-156">**IPCONFIG /ALL**</span></span>  
  
 <span data-ttu-id="3e5a7-157">若要形成完全限定的域名，请将 *<host_name>* 和 *<Primary_Dns_Suffix>* 的值连接一起，如下所示：</span><span class="sxs-lookup"><span data-stu-id="3e5a7-157">To form the fully qualified domain name, concatenate the values of *<host_name>* and *<Primary_Dns_Suffix>* as follows:</span></span>  
  
 <span data-ttu-id="3e5a7-158"><host_name> .</span><span class="sxs-lookup"><span data-stu-id="3e5a7-158">_<host_name>_ **.**</span></span> <span data-ttu-id="3e5a7-159">_<Primary_Dns_Suffix>_</span><span class="sxs-lookup"><span data-stu-id="3e5a7-159">_<Primary_Dns_Suffix>_</span></span>  
  
 <span data-ttu-id="3e5a7-160">例如，IP 配置</span><span class="sxs-lookup"><span data-stu-id="3e5a7-160">For example, the IP configuration</span></span>  
  
 `Host Name  .  .  .  .  .  .  : MYSERVER`  
  
 `Primary Dns Suffix  .  .  .  : mydomain.Adventure-Works.com`  
  
 <span data-ttu-id="3e5a7-161">等同于以下完全限定域名：</span><span class="sxs-lookup"><span data-stu-id="3e5a7-161">equates to the following fully qualified domain name:</span></span>  
  
 `MYSERVER.mydomain.Adventure-Works.com`  
  
##  <a name="examples"></a><a name="Examples"></a> <span data-ttu-id="3e5a7-162">示例</span><span class="sxs-lookup"><span data-stu-id="3e5a7-162">Examples</span></span>  
 <span data-ttu-id="3e5a7-163">以下示例显示了其他域中名为 `REMOTESYSTEM3` 的计算机系统上的某个服务器实例的服务器网络地址。</span><span class="sxs-lookup"><span data-stu-id="3e5a7-163">The following example shows the server network address for a server instance on a computer system named `REMOTESYSTEM3` in another domain.</span></span> <span data-ttu-id="3e5a7-164">域信息为 `NORTHWEST.ADVENTURE-WORKS.COM`，数据库镜像端点的端口为 `7025`。</span><span class="sxs-lookup"><span data-stu-id="3e5a7-164">The domain information is `NORTHWEST.ADVENTURE-WORKS.COM`, and the port of the database mirroring endpoint is `7025`.</span></span> <span data-ttu-id="3e5a7-165">假设具有这些示例组件，则服务器网络地址将为：</span><span class="sxs-lookup"><span data-stu-id="3e5a7-165">Given these example components, the server network address is.</span></span>  
  
 `TCP://REMOTESYSTEM3.NORTHWEST.ADVENTURE-WORKS.COM:7025`  
  
 <span data-ttu-id="3e5a7-166">以下示例显示了名为 `DBSERVER1`的计算机系统上的某个服务器实例的服务器网络地址。</span><span class="sxs-lookup"><span data-stu-id="3e5a7-166">The following example shows the server network address for a server instance on a computer system named `DBSERVER1`.</span></span> <span data-ttu-id="3e5a7-167">此系统位于本地域中，并由其系统名称明确标识。</span><span class="sxs-lookup"><span data-stu-id="3e5a7-167">This system is in the local domain and is unambiguously identified by its system name.</span></span> <span data-ttu-id="3e5a7-168">数据库镜像端点的端口为 `7022`。</span><span class="sxs-lookup"><span data-stu-id="3e5a7-168">The port of the database mirroring endpoint is `7022`.</span></span>  
  
 `TCP://DBSERVER1:7022`  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="3e5a7-169">相关任务</span><span class="sxs-lookup"><span data-stu-id="3e5a7-169">Related Tasks</span></span>  
  
-   [<span data-ttu-id="3e5a7-170">为 Windows 身份验证创建数据库镜像终结点 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="3e5a7-170">Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;</span></span>](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="3e5a7-171">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3e5a7-171">See Also</span></span>  
 <span data-ttu-id="3e5a7-172">[数据库镜像 (SQL Server)](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="3e5a7-172">[Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="3e5a7-173">数据库镜像终结点 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="3e5a7-173">The Database Mirroring Endpoint &#40;SQL Server&#41;</span></span>](the-database-mirroring-endpoint-sql-server.md)  
  
  
