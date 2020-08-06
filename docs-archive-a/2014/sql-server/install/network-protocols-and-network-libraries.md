---
title: 网络协议和网络库 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- protocols [SQL Server]
- configuration options [SQL Server], protocols
- network libraries [SQL Server]
- protocols [SQL Server], about network protocols
- pipes [SQL Server]
- network protocols [SQL Server]
- default SQL Server configurations
- library [SQL Server]
- network protocols [SQL Server], about network protocols
- configuration options [SQL Server], libraries
ms.assetid: 8cd437f6-9af1-44ce-9cb0-4d10c83da9ce
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8be012ea2bc9499a99ca7763446c6f26cf219a18
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590523"
---
# <a name="network-protocols-and-network-libraries"></a><span data-ttu-id="24398-102">网络协议和网络库</span><span class="sxs-lookup"><span data-stu-id="24398-102">Network Protocols and Network Libraries</span></span>
  <span data-ttu-id="24398-103">服务器可以同时监听或监视多个网络协议。</span><span class="sxs-lookup"><span data-stu-id="24398-103">A server can listen on, or monitor, multiple network protocols at one time.</span></span> <span data-ttu-id="24398-104">但必须对每个协议都进行配置。</span><span class="sxs-lookup"><span data-stu-id="24398-104">However, each protocol must be configured.</span></span> <span data-ttu-id="24398-105">如果没有配置某个协议，则服务器将无法监听该协议。</span><span class="sxs-lookup"><span data-stu-id="24398-105">If a particular protocol is not configured, the server cannot listen on that protocol.</span></span> <span data-ttu-id="24398-106">安装完成后，可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器更改这些协议配置。</span><span class="sxs-lookup"><span data-stu-id="24398-106">After installation, you can change the protocol configurations using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span>  
  
## <a name="default-sql-server-network-configuration"></a><span data-ttu-id="24398-107">默认 SQL Server 网络配置</span><span class="sxs-lookup"><span data-stu-id="24398-107">Default SQL Server Network Configuration</span></span>  
 <span data-ttu-id="24398-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的默认实例针对 TCP/IP 端口 1433 进行配置，并命名为管道 \\\\.\pipe\sql\query。</span><span class="sxs-lookup"><span data-stu-id="24398-108">A default instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is configured for TCP/IP port 1433, and named pipe \\\\.\pipe\sql\query.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="24398-109">命名实例配置为采用 TCP 动态端口，其端口号由操作系统分配。</span><span class="sxs-lookup"><span data-stu-id="24398-109">named instances are configured for TCP dynamic ports, with a port number assigned by the operating system.</span></span>  
  
 <span data-ttu-id="24398-110">如果无法使用动态端口地址（例如，当 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 连接必须通过服务器配置为要通过特定端口地址的防火墙时）。</span><span class="sxs-lookup"><span data-stu-id="24398-110">If you cannot use dynamic port addresses (for example, when [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connections must pass through a firewall server configured to pass through specific port addresses).</span></span> <span data-ttu-id="24398-111">选择一个未分配的端口号。</span><span class="sxs-lookup"><span data-stu-id="24398-111">Select an unassigned port number.</span></span> <span data-ttu-id="24398-112">Internet 号码分配机构负责管理端口号的分配，并在 [http://www.iana.org](https://go.microsoft.com/fwlink/?LinkId=48844) 上列出这些端口号。</span><span class="sxs-lookup"><span data-stu-id="24398-112">Port number assignments are managed by the Internet Assigned Numbers Authority and are listed at [http://www.iana.org](https://go.microsoft.com/fwlink/?LinkId=48844).</span></span>  
  
 <span data-ttu-id="24398-113">为了增强安全性，当安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 时不会完全启用网络连接。</span><span class="sxs-lookup"><span data-stu-id="24398-113">To enhance security, network connectivity is not fully enabled when [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed.</span></span> <span data-ttu-id="24398-114">在安装完成后，若要启用、禁用和配置网络协议，请使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 网络配置区域。</span><span class="sxs-lookup"><span data-stu-id="24398-114">To enable, disable, and configure network protocols after Setup is complete, use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Network Configuration area of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span>  
  
## <a name="server-message-block-protocol"></a><span data-ttu-id="24398-115">服务器消息块协议</span><span class="sxs-lookup"><span data-stu-id="24398-115">Server Message Block Protocol</span></span>  
 <span data-ttu-id="24398-116">周边网络中的服务器应该禁用所有不必要的协议，其中包括服务器消息块 (SMB)。</span><span class="sxs-lookup"><span data-stu-id="24398-116">Servers in the perimeter network should have all unnecessary protocols disabled, including server message block (SMB).</span></span> <span data-ttu-id="24398-117">Web 服务器和域名系统 (DNS) 服务器不需要 SMB。</span><span class="sxs-lookup"><span data-stu-id="24398-117">Web servers and Domain Name System (DNS) servers do not require SMB.</span></span> <span data-ttu-id="24398-118">为了应对用户枚举的威胁，应禁用此协议。</span><span class="sxs-lookup"><span data-stu-id="24398-118">This protocol should be disabled to counter the threat of user enumeration.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="24398-119">禁用服务器消息块将阻止 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 或 Windows 群集服务访问远程文件共享。</span><span class="sxs-lookup"><span data-stu-id="24398-119">Disabling Server Message Block will block the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or Windows Cluster service from accessing the remote file share.</span></span> <span data-ttu-id="24398-120">如果您执行或计划执行以下操作之一，请不要禁用 SMB：</span><span class="sxs-lookup"><span data-stu-id="24398-120">Do not disable SMB if you do or plan to do one of the following:</span></span>  
> 
>  -   <span data-ttu-id="24398-121">使用 Windows 群集节点和文件共享多数仲裁模式</span><span class="sxs-lookup"><span data-stu-id="24398-121">Use Windows Cluster Node and File Share Majority Quorum mode</span></span>  
> -   <span data-ttu-id="24398-122">在安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的过程中将 SMB 文件共享指定为数据目录</span><span class="sxs-lookup"><span data-stu-id="24398-122">Specify an SMB file share as the data directory during [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation</span></span>  
> -   <span data-ttu-id="24398-123">在 SMB 文件共享上创建数据库文件</span><span class="sxs-lookup"><span data-stu-id="24398-123">Create a database file on an SMB file share</span></span>  
  
#### <a name="to-disable-smb"></a><span data-ttu-id="24398-124">禁用 SMB</span><span class="sxs-lookup"><span data-stu-id="24398-124">To disable SMB</span></span>  
  
1.  <span data-ttu-id="24398-125">在“开始”  菜单中，指向“设置”  ，然后单击“网络和拨号连接”  。</span><span class="sxs-lookup"><span data-stu-id="24398-125">On the **Start** menu, point to **Settings**, and then click **Network and Dial-up Connections**.</span></span>  
  
     <span data-ttu-id="24398-126">右键单击面向 Internet 的连接，然后单击“属性”  。</span><span class="sxs-lookup"><span data-stu-id="24398-126">Right-click the Internet-facing connection, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="24398-127">选中 **“Microsoft Networks 客户端”** 复选框，然后单击 **“卸载”** 。</span><span class="sxs-lookup"><span data-stu-id="24398-127">Select the **Client for Microsoft Networks** check box, and then click **Uninstall**.</span></span>  
  
3.  <span data-ttu-id="24398-128">执行卸载步骤。</span><span class="sxs-lookup"><span data-stu-id="24398-128">Follow the uninstall steps.</span></span>  
  
4.  <span data-ttu-id="24398-129">选择 **“Microsoft Networks 文件和打印机共享”** ，然后单击 **“卸载”** 。</span><span class="sxs-lookup"><span data-stu-id="24398-129">Select **File and Printer Sharing for Microsoft Networks**, and then click **Uninstall**.</span></span>  
  
5.  <span data-ttu-id="24398-130">执行卸载步骤。</span><span class="sxs-lookup"><span data-stu-id="24398-130">Follow the uninstall steps.</span></span>  
  
#### <a name="to-disable-smb-on-servers-accessible-from-the-internet"></a><span data-ttu-id="24398-131">在可通过 Internet 访问的服务器上禁用 SMB</span><span class="sxs-lookup"><span data-stu-id="24398-131">To disable SMB on servers accessible from the Internet</span></span>  
  
-   <span data-ttu-id="24398-132">在本地连接属性中，使用“传播控制协议/Internet 协议 (TCP/IP) 属性”  对话框删除“Microsoft 网络的文件和打印共享”  和“Microsoft 网络客户端”  。</span><span class="sxs-lookup"><span data-stu-id="24398-132">In the Local Area Connection properties, use the **Transmission Control Protocol/Internet Protocol (TCP/IP) properties** dialog box to remove **File and Printer Sharing for Microsoft Networks** and **Client for Microsoft Networks**.</span></span>  
  
## <a name="endpoints"></a><span data-ttu-id="24398-133">终结点</span><span class="sxs-lookup"><span data-stu-id="24398-133">Endpoints</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="24398-134">为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 连接引入了一个新概念；在服务器端用 [!INCLUDE[tsql](../../includes/tsql-md.md)]*终结点*。</span><span class="sxs-lookup"><span data-stu-id="24398-134">introduces a new concept for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connections; the connection is represented on the server end by a [!INCLUDE[tsql](../../includes/tsql-md.md)]*endpoint*.</span></span> <span data-ttu-id="24398-135">可以对 [!INCLUDE[tsql](../../includes/tsql-md.md)] 端点授予、撤消和拒绝权限。</span><span class="sxs-lookup"><span data-stu-id="24398-135">Permissions can be granted, revoked, and denied for [!INCLUDE[tsql](../../includes/tsql-md.md)] endpoints.</span></span> <span data-ttu-id="24398-136">默认情况下，所有用户都具备访问端点的权限，除非 sysadmin 组的成员或端点所有者拒绝或撤消了此权限。</span><span class="sxs-lookup"><span data-stu-id="24398-136">By default, all users have permissions to access an endpoint unless the permissions are denied or revoked by a member of the sysadmin group or by the endpoint owner.</span></span> <span data-ttu-id="24398-137">GRANT、REVOKE 和 DENY ENDPOINT 语法使用终结点 ID，管理员必须从终结点的目录视图中获取此 ID。</span><span class="sxs-lookup"><span data-stu-id="24398-137">The GRANT, REVOKE, and DENY ENDPOINT syntax uses an endpoint ID that the administrator must get from the endpoint's catalog view.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="24398-138">安装程序将为所有支持的网络协议以及专用管理员连接创建 [!INCLUDE[tsql](../../includes/tsql-md.md)] 端点。</span><span class="sxs-lookup"><span data-stu-id="24398-138">Setup creates [!INCLUDE[tsql](../../includes/tsql-md.md)] endpoints for all supported network protocols, as well as for the dedicated administrator connection.</span></span>  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="24398-139">安装程序所创建的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 端点如下：</span><span class="sxs-lookup"><span data-stu-id="24398-139">endpoints created by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup are as follows:</span></span>  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="24398-140">本地计算机</span><span class="sxs-lookup"><span data-stu-id="24398-140">local machine</span></span>  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="24398-141">命名管道</span><span class="sxs-lookup"><span data-stu-id="24398-141">named pipes</span></span>  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="24398-142">默认 TCP</span><span class="sxs-lookup"><span data-stu-id="24398-142">default TCP</span></span>  
  
 <span data-ttu-id="24398-143">有关终结点的详细信息，请参阅[将数据库引擎配置为侦听多个 TCP 端口](../../database-engine/configure-windows/configure-the-database-engine-to-listen-on-multiple-tcp-ports.md)和[终结点目录视图 (Transact-SQL)](/sql/relational-databases/system-catalog-views/endpoints-catalog-views-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="24398-143">For more information about endpoints, see [Configure the Database Engine to Listen on Multiple TCP Ports](../../database-engine/configure-windows/configure-the-database-engine-to-listen-on-multiple-tcp-ports.md) and [Endpoints Catalog Views &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/endpoints-catalog-views-transact-sql).</span></span>  
  
 <span data-ttu-id="24398-144">有关 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 网络配置的详细信息，请参阅 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 联机丛书中的下列主题：</span><span class="sxs-lookup"><span data-stu-id="24398-144">For more information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] network configurations, see the following topic in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online:</span></span>  
  
-   [<span data-ttu-id="24398-145">服务器网络配置</span><span class="sxs-lookup"><span data-stu-id="24398-145">Server Network Configuration</span></span>](../../database-engine/configure-windows/server-network-configuration.md)  
  
## <a name="see-also"></a><span data-ttu-id="24398-146">另请参阅</span><span class="sxs-lookup"><span data-stu-id="24398-146">See Also</span></span>  
 <span data-ttu-id="24398-147">[外围应用配置器](../../relational-databases/security/surface-area-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="24398-147">[Surface Area Configuration](../../relational-databases/security/surface-area-configuration.md) </span></span>  
 <span data-ttu-id="24398-148">[安装 SQL Server 的安全注意事项](../../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md) </span><span class="sxs-lookup"><span data-stu-id="24398-148">[Security Considerations for a SQL Server Installation](../../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md) </span></span>  
 [<span data-ttu-id="24398-149">计划 SQL Server 安装</span><span class="sxs-lookup"><span data-stu-id="24398-149">Planning a SQL Server Installation</span></span>](../../../2014/sql-server/install/planning-a-sql-server-installation.md)  
  
  
