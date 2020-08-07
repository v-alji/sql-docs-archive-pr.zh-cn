---
title: 复制安全最佳做法 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- security [SQL Server replication], best practices
- security [SQL Server replication], between domains
- authentication [SQL Server replication]
- Internet [SQL Server replication], security
ms.assetid: 1ab2635d-0992-4c99-b17d-041d02ec9a7c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8e5918bfed52a6ed1befd81d2fdb7910062060e6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576627"
---
# <a name="replication-security-best-practices"></a><span data-ttu-id="f8c0f-102">复制安全最佳实践</span><span class="sxs-lookup"><span data-stu-id="f8c0f-102">Replication Security Best Practices</span></span>
  <span data-ttu-id="f8c0f-103">复制在分布式环境（从单个域中的 Intranet 到在不受信任的域之间通过 Internet 访问数据的应用程序）中移动数据。</span><span class="sxs-lookup"><span data-stu-id="f8c0f-103">Replication moves data in distributed environments ranging from intranets on a single domain to applications that access data between untrusted domains and over the Internet.</span></span> <span data-ttu-id="f8c0f-104">理解在这些不同环境下保护复制连接的最佳方法非常重要。</span><span class="sxs-lookup"><span data-stu-id="f8c0f-104">It is important to understand the best approach for securing replication connections under these different circumstances.</span></span>  
  
 <span data-ttu-id="f8c0f-105">下面是在所有环境中均与复制相关的信息：</span><span class="sxs-lookup"><span data-stu-id="f8c0f-105">The following information is relevant to replication in all environments:</span></span>  
  
-   <span data-ttu-id="f8c0f-106">使用行业标准方法 [如虚拟专用网络 (VPN)、安全套接字层 (SSL) 或 IP 安全 (IPSEC)] 加密复制拓扑中计算机间的连接。</span><span class="sxs-lookup"><span data-stu-id="f8c0f-106">Encrypt the connections between computers in a replication topology using an industry standard method, such as Virtual Private Networks (VPN), Secure Sockets Layer (SSL), or IP Security (IPSEC).</span></span> <span data-ttu-id="f8c0f-107">有关详细信息，请参阅[启用数据库引擎的加密连接（SQL Server 配置管理器）](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="f8c0f-107">For more information, see [Enable Encrypted Connections to the Database Engine &#40;SQL Server Configuration Manager&#41;](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).</span></span> <span data-ttu-id="f8c0f-108">有关使用 VPN 和 SSL 在 Internet 上复制数据的信息，请参阅 [Securing Replication Over the Internet](securing-replication-over-the-internet.md)。</span><span class="sxs-lookup"><span data-stu-id="f8c0f-108">For information about using VPN and SSL for replicating data over the Internet, see [Securing Replication Over the Internet](securing-replication-over-the-internet.md).</span></span>  
  
     <span data-ttu-id="f8c0f-109">如果使用 SSL 来确保复制拓扑中计算机间的连接安全，请为每个复制代理的 **-EncryptionLevel** 参数指定值 **1** 或 **2** （建议指定值 **2** ）。</span><span class="sxs-lookup"><span data-stu-id="f8c0f-109">If you use SSL to secure the connections between computers in a replication topology, specify a value of **1** or **2** for the **-EncryptionLevel** parameter of each replication agent (a value of **2** is recommended).</span></span> <span data-ttu-id="f8c0f-110">值 **1** 指定使用加密，但是代理不验证 SSL 服务器证书是否由可信颁发者签名；值 **2** 指定证书要经过验证。</span><span class="sxs-lookup"><span data-stu-id="f8c0f-110">A value of **1** specifies that encryption is used, but the agent does not verify that the SSL server certificate is signed by a trusted issuer; a value of **2** specifies that the certificate is verified.</span></span> <span data-ttu-id="f8c0f-111">代理参数可以在代理配置文件和命令行中指定。</span><span class="sxs-lookup"><span data-stu-id="f8c0f-111">Agent parameters can be specified in agent profiles and on the command line.</span></span> <span data-ttu-id="f8c0f-112">有关详细信息，请参阅：</span><span class="sxs-lookup"><span data-stu-id="f8c0f-112">For more information, see:</span></span>  
  
    -   [<span data-ttu-id="f8c0f-113">处理复制代理配置文件</span><span class="sxs-lookup"><span data-stu-id="f8c0f-113">Work with Replication Agent Profiles</span></span>](../agents/replication-agent-profiles.md)  
  
    -   [<span data-ttu-id="f8c0f-114">查看和修改复制代理命令提示符参数 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="f8c0f-114">View and Modify Replication Agent Command Prompt Parameters &#40;SQL Server Management Studio&#41;</span></span>](../agents/view-and-modify-replication-agent-command-prompt-parameters.md)  
  
    -   [<span data-ttu-id="f8c0f-115">Replication Agent Executables Concepts</span><span class="sxs-lookup"><span data-stu-id="f8c0f-115">Replication Agent Executables Concepts</span></span>](../concepts/replication-agent-executables-concepts.md)  
  
-   <span data-ttu-id="f8c0f-116">以不同的 Windows 帐户运行每个复制代理，并对所有复制代理连接使用 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="f8c0f-116">Run each replication agent under a different Windows account, and use Windows Authentication for all replication agent connections.</span></span> <span data-ttu-id="f8c0f-117">有关指定帐户的详细信息，请参阅[管理复制中的登录名和密码](identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication)。</span><span class="sxs-lookup"><span data-stu-id="f8c0f-117">For more information about specifying accounts, see [Manage Logins and Passwords in Replication](identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication).</span></span>  
  
-   <span data-ttu-id="f8c0f-118">仅对每个代理授予其所需的权限。</span><span class="sxs-lookup"><span data-stu-id="f8c0f-118">Grant only the required permissions to each agent.</span></span> <span data-ttu-id="f8c0f-119">有关详细信息，请参阅 [Replication Agent Security Model](replication-agent-security-model.md)中的“代理所需权限”部分。</span><span class="sxs-lookup"><span data-stu-id="f8c0f-119">For more information, see the "Permissions Required by Agents" section of [Replication Agent Security Model](replication-agent-security-model.md).</span></span>  
  
-   <span data-ttu-id="f8c0f-120">确保所有合并代理和分发代理帐户均在发布访问列表 (PAL) 中。</span><span class="sxs-lookup"><span data-stu-id="f8c0f-120">Ensure all Merge Agent and Distribution Agent accounts are in the publication access list (PAL).</span></span> <span data-ttu-id="f8c0f-121">有关详细信息，请参阅[保护发布服务器](secure-the-publisher.md)。</span><span class="sxs-lookup"><span data-stu-id="f8c0f-121">For more information, see [Secure the Publisher](secure-the-publisher.md).</span></span>  
  
-   <span data-ttu-id="f8c0f-122">遵循最小权限原则，仅对 PAL 中的帐户授予其执行复制任务所需的权限。</span><span class="sxs-lookup"><span data-stu-id="f8c0f-122">Follow the principle of least privilege by allowing accounts in the PAL only the permissions they need to perform replication tasks.</span></span> <span data-ttu-id="f8c0f-123">不要向复制不需要的任何固定服务器角色添加登录帐户。</span><span class="sxs-lookup"><span data-stu-id="f8c0f-123">Do not add the logins to any fixed server roles that are not required for replication.</span></span>  
  
-   <span data-ttu-id="f8c0f-124">配置快照共享，以允许所有合并代理和分发代理进行读访问。</span><span class="sxs-lookup"><span data-stu-id="f8c0f-124">Configure the snapshot share to allow read access by all Merge Agents and Distribution Agents.</span></span> <span data-ttu-id="f8c0f-125">对于具有参数化筛选器的发布的快照，请确保将每个文件夹配置为仅允许相应的合并代理帐户进行访问。</span><span class="sxs-lookup"><span data-stu-id="f8c0f-125">In the case of snapshots for publications with parameterized filters, ensure that each folder is configured to allow access only to the appropriate Merge Agent accounts.</span></span>  
  
-   <span data-ttu-id="f8c0f-126">配置快照共享，以允许快照代理进行写权限。</span><span class="sxs-lookup"><span data-stu-id="f8c0f-126">Configure the snapshot share to allow write access by the Snapshot Agent.</span></span>  
  
-   <span data-ttu-id="f8c0f-127">如果使用的是请求订阅，请为快照文件夹使用网络共享，而不要使用本地路径。</span><span class="sxs-lookup"><span data-stu-id="f8c0f-127">If you use pull subscriptions, use a network share rather than a local path for the snapshot folder.</span></span>  
  
 <span data-ttu-id="f8c0f-128">如果复制拓扑中包含的计算机位于不同的域中，或位于彼此未建立信任关系的域中，则可以对代理建立的连接使用 Windows 身份验证或 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 身份验证（有关域的详细信息，请参阅 Windows 文档）。</span><span class="sxs-lookup"><span data-stu-id="f8c0f-128">If your replication topology includes computers that are not in the same domain or are in domains that do not have trust relationships with each other, you can use Windows Authentication or [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication for the connections made by agents (For more information about domains, see the Windows documentation).</span></span> <span data-ttu-id="f8c0f-129">建议使用 Windows 身份验证作为最佳安全配置。</span><span class="sxs-lookup"><span data-stu-id="f8c0f-129">It is recommended as a security best practice that you use Windows Authentication.</span></span>  
  
-   <span data-ttu-id="f8c0f-130">使用 Windows 身份验证：</span><span class="sxs-lookup"><span data-stu-id="f8c0f-130">To use Windows Authentication:</span></span>  
  
    -   <span data-ttu-id="f8c0f-131">为适当节点处的每个代理添加一个本地 Windows 帐户（而非域帐户），在每个节点都使用同一名称和密码。</span><span class="sxs-lookup"><span data-stu-id="f8c0f-131">Add a local Windows account (not a domain account) for each agent at the appropriate nodes (use the same name and password at each node).</span></span> <span data-ttu-id="f8c0f-132">例如，推送订阅的分发代理在分发服务器上运行，并与分发服务器和订阅服务器建立连接。</span><span class="sxs-lookup"><span data-stu-id="f8c0f-132">For example, the Distribution Agent for a push subscription runs at the Distributor and makes connections to the Distributor and Subscriber.</span></span> <span data-ttu-id="f8c0f-133">应将分发代理的 Windows 帐户添加到分发服务器和订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="f8c0f-133">The Windows account for the Distribution Agent should be added to the Distributor and Subscriber.</span></span>  
  
    -   <span data-ttu-id="f8c0f-134">确保给定代理（例如订阅的分发代理）在每台计算机上都以同一帐户运行。</span><span class="sxs-lookup"><span data-stu-id="f8c0f-134">Ensure that a given agent (for example the Distribution Agent for a subscription) runs under the same account at each computer.</span></span>  
  
-   <span data-ttu-id="f8c0f-135">使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 身份验证：</span><span class="sxs-lookup"><span data-stu-id="f8c0f-135">To use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication:</span></span>  
  
    -   <span data-ttu-id="f8c0f-136">为适当节点处的每个代理添加一个 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 帐户，在每个节点都使用同一名称和密码。</span><span class="sxs-lookup"><span data-stu-id="f8c0f-136">Add a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] account for each agent at the appropriate nodes (use the same account name and password at each node).</span></span> <span data-ttu-id="f8c0f-137">例如，推送订阅的分发代理在分发服务器上运行，并与分发服务器和订阅服务器建立连接。</span><span class="sxs-lookup"><span data-stu-id="f8c0f-137">For example, the Distribution Agent for a push subscription runs at the Distributor and makes connections to the Distributor and Subscriber.</span></span> <span data-ttu-id="f8c0f-138">应将分发代理的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 帐户添加到分发服务器和订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="f8c0f-138">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] account for the Distribution Agent should be added to the Distributor and Subscriber.</span></span>  
  
    -   <span data-ttu-id="f8c0f-139">确保给定代理（例如订阅的分发代理）在每台计算机上都以同一帐户建立连接。</span><span class="sxs-lookup"><span data-stu-id="f8c0f-139">Ensure that a given agent (for example the Distribution Agent for a subscription) makes connections under the same account at each computer.</span></span>  
  
    -   <span data-ttu-id="f8c0f-140">需要 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 身份验证时，UNC 快照共享通常无法访问（例如，防火墙可能阻止访问）。</span><span class="sxs-lookup"><span data-stu-id="f8c0f-140">In situations that require [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication, access to UNC snapshot shares is often not available (for example access might be blocked by a firewall).</span></span> <span data-ttu-id="f8c0f-141">在这种情况下，可以通过文件传输协议 (FTP) 将快照传输到订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="f8c0f-141">In this case, you can transfer the snapshot to Subscribers through file transfer protocol (FTP).</span></span> <span data-ttu-id="f8c0f-142">有关详细信息，请参阅[通过 FTP 传输快照](../transfer-snapshots-through-ftp.md)。</span><span class="sxs-lookup"><span data-stu-id="f8c0f-142">For more information, see [Transfer Snapshots Through FTP](../transfer-snapshots-through-ftp.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8c0f-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f8c0f-143">See Also</span></span>  
 <span data-ttu-id="f8c0f-144">[启用数据库引擎的加密连接（SQL Server 配置管理器）](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="f8c0f-144">[Enable Encrypted Connections to the Database Engine &#40;SQL Server Configuration Manager&#41;](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md) </span></span>  
 <span data-ttu-id="f8c0f-145">[通过 Internet 复制](../replication-over-the-internet.md) </span><span class="sxs-lookup"><span data-stu-id="f8c0f-145">[Replication over the Internet](../replication-over-the-internet.md) </span></span>  
 <span data-ttu-id="f8c0f-146">[保护订阅服务器](secure-the-subscriber.md) </span><span class="sxs-lookup"><span data-stu-id="f8c0f-146">[Secure the Subscriber](secure-the-subscriber.md) </span></span>  
 <span data-ttu-id="f8c0f-147">[保护分发服务器](secure-the-distributor.md) </span><span class="sxs-lookup"><span data-stu-id="f8c0f-147">[Secure the Distributor](secure-the-distributor.md) </span></span>  
 <span data-ttu-id="f8c0f-148">[保护发布服务器](secure-the-publisher.md) </span><span class="sxs-lookup"><span data-stu-id="f8c0f-148">[Secure the Publisher](secure-the-publisher.md) </span></span>  
 [<span data-ttu-id="f8c0f-149">SQL Server 复制安全性</span><span class="sxs-lookup"><span data-stu-id="f8c0f-149">SQL Server Replication Security</span></span>](view-and-modify-replication-security-settings.md)  
  
  
