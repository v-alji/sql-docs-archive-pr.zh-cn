---
title: 安装 SQL Server 的安全注意事项 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- firewall systems [SQL Server]
- server message blocks [SQL Server]
- disabling protocols
- security [SQL Server], installations
- protocols [SQL Server], disabling
- NetBIOS [SQL Server]
- services [SQL Server], security
- SMB [SQL Server]
- isolating services [SQL Server]
- Setup [SQL Server], security
- low SQL Server installation privileges
- NTFS [SQL Server]
- physical security [SQL Server]
- file system security [SQL Server]
- installing SQL Server, security
ms.assetid: cf96155f-30a8-48b7-8d6b-24ce90dafdc7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ed0cd42d51c2b4db96778182c60f1ad3d13a098c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588835"
---
# <a name="security-considerations-for-a-sql-server-installation"></a><span data-ttu-id="c8934-102">安装 SQL Server 的安全注意事项</span><span class="sxs-lookup"><span data-stu-id="c8934-102">Security Considerations for a SQL Server Installation</span></span>
  <span data-ttu-id="c8934-103">安全对于每个产品和每家企业都很重要。</span><span class="sxs-lookup"><span data-stu-id="c8934-103">Security is important for every product and every business.</span></span> <span data-ttu-id="c8934-104">遵循简单的最佳做法，可以避免很多安全漏洞。</span><span class="sxs-lookup"><span data-stu-id="c8934-104">By following simple best practices, you can avoid many security vulnerabilities.</span></span> <span data-ttu-id="c8934-105">本主题讨论安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 前和安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]之后应考虑采用的一些最佳安全做法。</span><span class="sxs-lookup"><span data-stu-id="c8934-105">This topic discusses some security best practices that you should consider both before you install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and after you install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c8934-106">功能的参考主题中包括了特定功能的安全指南。</span><span class="sxs-lookup"><span data-stu-id="c8934-106">Security guidance for specific features is included in the reference topics for those features.</span></span>  
  
## <a name="before-installing-ssnoversion"></a><span data-ttu-id="c8934-107">安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8934-107">Before Installing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span></span>  
 <span data-ttu-id="c8934-108">设置服务器环境时，请遵循以下最佳做法：</span><span class="sxs-lookup"><span data-stu-id="c8934-108">Follow these best practices when you set up the server environment:</span></span>  
  
-   [<span data-ttu-id="c8934-109">增强物理安全性</span><span class="sxs-lookup"><span data-stu-id="c8934-109">Enhance physical security</span></span>](#physical_security)  
  
-   [<span data-ttu-id="c8934-110">使用防火墙</span><span class="sxs-lookup"><span data-stu-id="c8934-110">Use firewalls</span></span>](#firewalls)  
  
-   [<span data-ttu-id="c8934-111">隔离服务</span><span class="sxs-lookup"><span data-stu-id="c8934-111">Isolate services</span></span>](#isolated_services)  
  
-   [<span data-ttu-id="c8934-112">配置安全的文件系统</span><span class="sxs-lookup"><span data-stu-id="c8934-112">Configure a secure file system</span></span>](#sa_with_least_privileges)  
  
-   [<span data-ttu-id="c8934-113">禁用 NetBIOS 和服务器消息块</span><span class="sxs-lookup"><span data-stu-id="c8934-113">Disable NetBIOS and server message block</span></span>](#disabled_protocols)  
  
-   [<span data-ttu-id="c8934-114">在域控制器上安装 SQL Server</span><span class="sxs-lookup"><span data-stu-id="c8934-114">Installing SQL Server on a domain controller</span></span>](../../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md#Install_DC)  
  
###  <a name="enhance-physical-security"></a><a name="physical_security"></a> <span data-ttu-id="c8934-115">Enhance Physical Security</span><span class="sxs-lookup"><span data-stu-id="c8934-115">Enhance Physical Security</span></span>  
 <span data-ttu-id="c8934-116">物理和逻辑隔离是构成 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安全的基础。</span><span class="sxs-lookup"><span data-stu-id="c8934-116">Physical and logical isolation make up the foundation of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] security.</span></span> <span data-ttu-id="c8934-117">若要增强 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装的物理安全性，请执行以下任务：</span><span class="sxs-lookup"><span data-stu-id="c8934-117">To enhance the physical security of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation, do the following tasks:</span></span>  
  
-   <span data-ttu-id="c8934-118">将服务器置于专门的房间，未经授权的人员不得入内。</span><span class="sxs-lookup"><span data-stu-id="c8934-118">Place the server in a room accessible only to authorized persons.</span></span>  
  
-   <span data-ttu-id="c8934-119">将数据库的宿主计算机置于受物理保护的场所，最好是上锁的机房，房中配备水灾检测和火灾检测监视系统或灭火系统。</span><span class="sxs-lookup"><span data-stu-id="c8934-119">Place computers that host a database in a physically protected location, ideally a locked computer room with monitored flood detection and fire detection or suppression systems.</span></span>  
  
-   <span data-ttu-id="c8934-120">将数据库安装在公司 Intranet 的安全区域中，并且不得将 SQL Server 直接连接到 Internet。</span><span class="sxs-lookup"><span data-stu-id="c8934-120">Install databases in the secure zone of the corporate intranet and do not connect your SQL Servers directly to the Internet.</span></span>  
  
-   <span data-ttu-id="c8934-121">定期备份所有数据，并将备份存储在远离工作现场的安全位置。</span><span class="sxs-lookup"><span data-stu-id="c8934-121">Back up all data regularly and secure the backups in an off-site location.</span></span>  
  
###  <a name="use-firewalls"></a><a name="firewalls"></a> <span data-ttu-id="c8934-122">Use Firewalls</span><span class="sxs-lookup"><span data-stu-id="c8934-122">Use Firewalls</span></span>  
 <span data-ttu-id="c8934-123">防火墙对于协助确保 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装的安全十分重要。</span><span class="sxs-lookup"><span data-stu-id="c8934-123">Firewalls are important to help secure the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation.</span></span> <span data-ttu-id="c8934-124">如果遵循以下准则，防火墙将最为有效：</span><span class="sxs-lookup"><span data-stu-id="c8934-124">Firewalls will be most effective if you follow these guidelines:</span></span>  
  
-   <span data-ttu-id="c8934-125">在服务器和 Internet 之间放置防火墙。</span><span class="sxs-lookup"><span data-stu-id="c8934-125">Put a firewall between the server and the Internet.</span></span> <span data-ttu-id="c8934-126">启用防火墙。</span><span class="sxs-lookup"><span data-stu-id="c8934-126">Enable your firewall.</span></span> <span data-ttu-id="c8934-127">如果防火墙处于关闭状态，请将其开启。</span><span class="sxs-lookup"><span data-stu-id="c8934-127">If your firewall is turned off, turn it on.</span></span> <span data-ttu-id="c8934-128">如果防火墙处于开启状态，请不要将其关闭。</span><span class="sxs-lookup"><span data-stu-id="c8934-128">If your firewall is turned on, do not turn it off.</span></span>  
  
-   <span data-ttu-id="c8934-129">将网络分成若干安全区域，区域之间用防火墙分隔。</span><span class="sxs-lookup"><span data-stu-id="c8934-129">Divide the network into security zones separated by firewalls.</span></span> <span data-ttu-id="c8934-130">阻止所有流量，然后有选择性地仅接受所需内容。</span><span class="sxs-lookup"><span data-stu-id="c8934-130">Block all traffic, and then selectively admit only what is required.</span></span>  
  
-   <span data-ttu-id="c8934-131">在多层环境中，使用多个防火墙创建屏蔽子网。</span><span class="sxs-lookup"><span data-stu-id="c8934-131">In a multi-tier environment, use multiple firewalls to create screened subnets.</span></span>  
  
-   <span data-ttu-id="c8934-132">如果在 Windows 域内部安装服务器，请将内部防火墙配置为允许使用 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="c8934-132">When you are installing the server inside a Windows domain, configure interior firewalls to allow Windows Authentication.</span></span>  
  
-   <span data-ttu-id="c8934-133">如果应用程序使用分布式事务处理，可能必须要将防火墙配置为允许 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 分布式事务处理协调器 (MS DTC) 在不同的 MS DTC 实例之间进行通信。</span><span class="sxs-lookup"><span data-stu-id="c8934-133">If your application uses distributed transactions, you might have to configure the firewall to allow [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator (MS DTC) traffic to flow between separate MS DTC instances.</span></span> <span data-ttu-id="c8934-134">还需要将防火墙配置为允许在 MS DTC 和资源管理器（如 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]）之间进行通信。</span><span class="sxs-lookup"><span data-stu-id="c8934-134">You will also have to configure the firewall to allow traffic to flow between the MS DTC and resource managers such as [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="c8934-135">有关默认 Windows 防火墙设置的详细信息，以及有关影响 [!INCLUDE[ssDE](../../includes/ssde-md.md)]、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]和 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]的 TCP 端口的说明，请参阅 [配置 Windows 防火墙以允许 SQL Server 访问](../../../2014/sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)。</span><span class="sxs-lookup"><span data-stu-id="c8934-135">For more information about the default Windows firewall settings, and a description of the TCP ports that affect the [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], and [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], see [Configure the Windows Firewall to Allow SQL Server Access](../../../2014/sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).</span></span>  
  
###  <a name="isolate-services"></a><a name="isolated_services"></a> <span data-ttu-id="c8934-136">Isolate Services</span><span class="sxs-lookup"><span data-stu-id="c8934-136">Isolate Services</span></span>  
 <span data-ttu-id="c8934-137">隔离服务可降低一项遭到入侵的服务可能被用来危害其他服务的风险。</span><span class="sxs-lookup"><span data-stu-id="c8934-137">Isolating services reduces the risk that one compromised service could be used to compromise others.</span></span> <span data-ttu-id="c8934-138">要隔离服务，请考虑以下准则：</span><span class="sxs-lookup"><span data-stu-id="c8934-138">To isolate services, consider the following guidelines:</span></span>  
  
-   <span data-ttu-id="c8934-139">在不同的 Windows 帐户下运行各自的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务。</span><span class="sxs-lookup"><span data-stu-id="c8934-139">Run separate [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services under separate Windows accounts.</span></span> <span data-ttu-id="c8934-140">对每个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务，尽可能使用不同的低权限 Windows 或本地用户帐户。</span><span class="sxs-lookup"><span data-stu-id="c8934-140">Whenever possible, use separate, low-rights Windows or Local user accounts for each [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span> <span data-ttu-id="c8934-141">有关详细信息，请参阅 [配置 Windows 服务帐户和权限](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)预览版本升级问题的解答。</span><span class="sxs-lookup"><span data-stu-id="c8934-141">For more information, see [Configure Windows Service Accounts and Permissions](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).</span></span>  
  
###  <a name="configure-a-secure-file-system"></a><a name="sa_with_least_privileges"></a> <span data-ttu-id="c8934-142">Configure a Secure File System</span><span class="sxs-lookup"><span data-stu-id="c8934-142">Configure a Secure File System</span></span>  
 <span data-ttu-id="c8934-143">使用正确的文件系统可提高安全性。</span><span class="sxs-lookup"><span data-stu-id="c8934-143">Using the correct file system increases security.</span></span> <span data-ttu-id="c8934-144">对于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装，应执行以下几项任务：</span><span class="sxs-lookup"><span data-stu-id="c8934-144">For [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installations, you should do the following tasks:</span></span>  
  
-   <span data-ttu-id="c8934-145">使用 NTFS 文件系统 (NTFS)。</span><span class="sxs-lookup"><span data-stu-id="c8934-145">Use the NTFS file system (NTFS).</span></span> <span data-ttu-id="c8934-146">NTFS 是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装的首选文件系统，因为它比 FAT 文件系统更加稳定和更容易恢复。</span><span class="sxs-lookup"><span data-stu-id="c8934-146">NTFS is the preferred file system for installations of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] because it is more stable and recoverable than FAT file systems.</span></span> <span data-ttu-id="c8934-147">NTFS 还启用安全选项，例如文件和目录访问控制列表 (ACL) 和加密文件系统 (EFS) 文件加密。</span><span class="sxs-lookup"><span data-stu-id="c8934-147">NTFS also enables security options like file and directory access control lists (ACLs) and Encrypting File System (EFS) file encryption.</span></span> <span data-ttu-id="c8934-148">在安装期间，如果检测到 NTFS， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将对注册表项和文件设置相应的 ACL。</span><span class="sxs-lookup"><span data-stu-id="c8934-148">During installation, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will set appropriate ACLs on registry keys and files if it detects NTFS.</span></span> <span data-ttu-id="c8934-149">不应对这些权限做任何更改。</span><span class="sxs-lookup"><span data-stu-id="c8934-149">These permissions should not be changed.</span></span> <span data-ttu-id="c8934-150">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的未来版本可能不支持在具有 FAT 文件系统的计算机上进行安装。</span><span class="sxs-lookup"><span data-stu-id="c8934-150">Future releases of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] might not support installation on computers with FAT file systems.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c8934-151">如果使用 EFS，则将在运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的帐户的标识下加密数据库文件。</span><span class="sxs-lookup"><span data-stu-id="c8934-151">If you use EFS, database files will be encrypted under the identity of the account running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c8934-152">只有该帐户才能解密文件。</span><span class="sxs-lookup"><span data-stu-id="c8934-152">Only this account will be able to decrypt the files.</span></span> <span data-ttu-id="c8934-153">如果必须更改运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的帐户，则应先在旧帐户下解密文件，然后在新帐户下将文件重新加密。</span><span class="sxs-lookup"><span data-stu-id="c8934-153">If you must change the account that runs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you should first decrypt the files under the old account and then re-encrypt them under the new account.</span></span>  
  
-   <span data-ttu-id="c8934-154">对关键数据文件使用独立磁盘冗余阵列 (RAID)。</span><span class="sxs-lookup"><span data-stu-id="c8934-154">Use a redundant array of independent disks (RAID) for critical data files.</span></span>  
  
###  <a name="disable-netbios-and-server-message-block"></a><a name="disabled_protocols"></a> <span data-ttu-id="c8934-155">Disable NetBIOS and Server Message Block</span><span class="sxs-lookup"><span data-stu-id="c8934-155">Disable NetBIOS and Server Message Block</span></span>  
 <span data-ttu-id="c8934-156">外围网络中的服务器应禁用所有不必要的协议，包括 NetBIOS 和服务器消息块 (SMB)。</span><span class="sxs-lookup"><span data-stu-id="c8934-156">Servers in the perimeter network should have all unnecessary protocols disabled, including NetBIOS and server message block (SMB).</span></span>  
  
 <span data-ttu-id="c8934-157">NetBIOS 使用以下端口：</span><span class="sxs-lookup"><span data-stu-id="c8934-157">NetBIOS uses the following ports:</span></span>  
  
-   <span data-ttu-id="c8934-158">UDP/137（NetBIOS 名称服务）</span><span class="sxs-lookup"><span data-stu-id="c8934-158">UDP/137 (NetBIOS name service)</span></span>  
  
-   <span data-ttu-id="c8934-159">UDP/138（NetBIOS 数据报服务）</span><span class="sxs-lookup"><span data-stu-id="c8934-159">UDP/138 (NetBIOS datagram service)</span></span>  
  
-   <span data-ttu-id="c8934-160">TCP/139（NetBIOS 会话服务）</span><span class="sxs-lookup"><span data-stu-id="c8934-160">TCP/139 (NetBIOS session service)</span></span>  
  
 <span data-ttu-id="c8934-161">SMB 使用以下端口：</span><span class="sxs-lookup"><span data-stu-id="c8934-161">SMB uses the following ports:</span></span>  
  
-   <span data-ttu-id="c8934-162">TCP/139</span><span class="sxs-lookup"><span data-stu-id="c8934-162">TCP/139</span></span>  
  
-   <span data-ttu-id="c8934-163">TCP/445</span><span class="sxs-lookup"><span data-stu-id="c8934-163">TCP/445</span></span>  
  
 <span data-ttu-id="c8934-164">Web 服务器和域名系统 (DNS) 服务器不需要 NetBIOS 或 SMB。</span><span class="sxs-lookup"><span data-stu-id="c8934-164">Web servers and Domain Name System (DNS) servers do not require NetBIOS or SMB.</span></span> <span data-ttu-id="c8934-165">在这些服务器上，禁用这两个协议可以减轻由用户枚举带来的威胁。</span><span class="sxs-lookup"><span data-stu-id="c8934-165">On these servers, disable both protocols to reduce the threat of user enumeration.</span></span>  
  
###  <a name="installing-ssnoversion-on-a-domain-controller"></a><a name="Install_DC"></a> <span data-ttu-id="c8934-166">在域控制器上安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8934-166">Installing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on a domain controller</span></span>  
 <span data-ttu-id="c8934-167">出于安全方面的考虑，我们建议您不要将 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 安装在域控制器上。</span><span class="sxs-lookup"><span data-stu-id="c8934-167">For security reasons, we recommend that you do not install [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] on a domain controller.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="c8934-168">安装程序不会阻止在作为域控制器的计算机上进行安装，但存在以下限制：</span><span class="sxs-lookup"><span data-stu-id="c8934-168">Setup will not block installation on a computer that is a domain controller, but the following limitations apply:</span></span>  
  
-   <span data-ttu-id="c8934-169">在域控制器上，无法在本地服务帐户下运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务。</span><span class="sxs-lookup"><span data-stu-id="c8934-169">You cannot run [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services on a domain controller under a local service account.</span></span>  
  
-   <span data-ttu-id="c8934-170">将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装到计算机上之后，无法将此计算机从域成员更改为域控制器。</span><span class="sxs-lookup"><span data-stu-id="c8934-170">After [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed on a computer, you cannot change the computer from a domain member to a domain controller.</span></span> <span data-ttu-id="c8934-171">必须先卸载 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，然后才能将主机计算机更改为域控制器。</span><span class="sxs-lookup"><span data-stu-id="c8934-171">You must uninstall [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] before you change the host computer to a domain controller.</span></span>  
  
-   <span data-ttu-id="c8934-172">将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装到计算机上之后，无法将此计算机从域控制器更改为域成员。</span><span class="sxs-lookup"><span data-stu-id="c8934-172">After [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed on a computer, you cannot change the computer from a domain controller to a domain member.</span></span> <span data-ttu-id="c8934-173">必须先卸载 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，然后才能将主机计算机更改为域成员。</span><span class="sxs-lookup"><span data-stu-id="c8934-173">You must uninstall [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] before you change the host computer to a domain member.</span></span>  
  
-   <span data-ttu-id="c8934-174">在群集节点用作域控制器的情况下，不支持[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 故障转移群集实例。</span><span class="sxs-lookup"><span data-stu-id="c8934-174">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster instances are not supported where cluster nodes are domain controllers.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="c8934-175">安装程序不能在只读域控制器上创建安全组或设置 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务帐户。</span><span class="sxs-lookup"><span data-stu-id="c8934-175">Setup cannot create security groups or provision [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service accounts on a read-only domain controller.</span></span> <span data-ttu-id="c8934-176">在这种情况下，安装将失败。</span><span class="sxs-lookup"><span data-stu-id="c8934-176">In this scenario, Setup will fail.</span></span>  
  
## <a name="during-or-after-installation-of-ssnoversion"></a><span data-ttu-id="c8934-177">在安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8934-177">During or After Installation of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span></span>  
 <span data-ttu-id="c8934-178">安装完成后，若要增强所安装的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 软件的安全性，请遵循以下有关帐户和身份验证模式的最佳做法：</span><span class="sxs-lookup"><span data-stu-id="c8934-178">After installation, you can enhance the security of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation by following these best practices regarding accounts and authentication modes:</span></span>  
  
 <span data-ttu-id="c8934-179">**服务帐户**</span><span class="sxs-lookup"><span data-stu-id="c8934-179">**Service accounts**</span></span>  
  
-   <span data-ttu-id="c8934-180">使用尽可能低的权限运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务。</span><span class="sxs-lookup"><span data-stu-id="c8934-180">Run [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services by using the lowest possible permissions.</span></span>  
  
-   <span data-ttu-id="c8934-181">将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务与低特权 Windows 本地用户帐户或域用户帐户相关联。</span><span class="sxs-lookup"><span data-stu-id="c8934-181">Associate [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services with low privileged Windows local user accounts, or domain user accounts.</span></span>  
  
-   <span data-ttu-id="c8934-182">有关详细信息，请参阅 [配置 Windows 服务帐户和权限](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)预览版本升级问题的解答。</span><span class="sxs-lookup"><span data-stu-id="c8934-182">For more information, see [Configure Windows Service Accounts and Permissions](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).</span></span>  
  
 <span data-ttu-id="c8934-183">**身份验证模式**</span><span class="sxs-lookup"><span data-stu-id="c8934-183">**Authentication mode**</span></span>  
  
-   <span data-ttu-id="c8934-184">连接 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]时要求 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="c8934-184">Require Windows Authentication for connections to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="c8934-185">使用 Kerberos 身份验证。</span><span class="sxs-lookup"><span data-stu-id="c8934-185">Use Kerberos authentication.</span></span> <span data-ttu-id="c8934-186">有关详细信息，请参阅 [为 Kerberos 连接注册服务主体名称](../../database-engine/configure-windows/register-a-service-principal-name-for-kerberos-connections.md)。</span><span class="sxs-lookup"><span data-stu-id="c8934-186">For more information, see [Register a Service Principal Name for Kerberos Connections](../../database-engine/configure-windows/register-a-service-principal-name-for-kerberos-connections.md).</span></span>  
  
 <span data-ttu-id="c8934-187">**强密码**</span><span class="sxs-lookup"><span data-stu-id="c8934-187">**Strong passwords**</span></span>  
  
-   <span data-ttu-id="c8934-188">始终为 `sa` 帐户分配强密码。</span><span class="sxs-lookup"><span data-stu-id="c8934-188">Always assign a strong password to the `sa` account.</span></span>  
  
-   <span data-ttu-id="c8934-189">始终启用密码策略检查以检查密码强度和有效期。</span><span class="sxs-lookup"><span data-stu-id="c8934-189">Always enable password policy checking for password strength and expiration.</span></span>  
  
-   <span data-ttu-id="c8934-190">始终对所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名使用强密码。</span><span class="sxs-lookup"><span data-stu-id="c8934-190">Always use strong passwords for all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logins.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="c8934-191">在安装 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 过程中，为 BUILTIN\Users 组添加一个登录名。</span><span class="sxs-lookup"><span data-stu-id="c8934-191">During setup of [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] a login is added for the BUILTIN\Users group.</span></span> <span data-ttu-id="c8934-192">这可以使计算机的所有通过身份验证的用户作为 public 角色成员访问 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="c8934-192">This allows all authenticated users of the computer to access the instance of [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] as a member of the public role.</span></span> <span data-ttu-id="c8934-193">可以安全地删除 BUILTIN\Users 登录名，以限制 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 对具有单独登录名或为使用此登录名的其他 Windows 组成员的计算机用户的访问。</span><span class="sxs-lookup"><span data-stu-id="c8934-193">The BUILTIN\Users login can be safely removed to restrict [!INCLUDE[ssDE](../../includes/ssde-md.md)] access to computer users who have individual logins or are members of other Windows groups with logins.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8934-194">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c8934-194">See Also</span></span>  
 <span data-ttu-id="c8934-195">[安装 SQL Server 2014 的硬件和软件要求](hardware-and-software-requirements-for-installing-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="c8934-195">[Hardware and Software Requirements for Installing SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md) </span></span>  
 <span data-ttu-id="c8934-196">[网络协议和网络库](../../../2014/sql-server/install/network-protocols-and-network-libraries.md) </span><span class="sxs-lookup"><span data-stu-id="c8934-196">[Network Protocols and Network Libraries](../../../2014/sql-server/install/network-protocols-and-network-libraries.md) </span></span>  
 [<span data-ttu-id="c8934-197">为 Kerberos 连接注册服务主体名称</span><span class="sxs-lookup"><span data-stu-id="c8934-197">Register a Service Principal Name for Kerberos Connections</span></span>](../../database-engine/configure-windows/register-a-service-principal-name-for-kerberos-connections.md)  
  
  
