---
title: 使用 TCP IP 创建有效的连接字符串 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- connection strings [Database Engine]
- ports [SQL Server], connecting to
- TCP/IP [SQL Server], connection strings
- connection strings [Database Engine], TCP/IP
- aliases [SQL Server], TCP/IP
ms.assetid: ee5dbc2c-1fc6-42bd-bdf5-efa792557934
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5f761fa86ec4ed09c13bf4807489754c10b979ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586040"
---
# <a name="creating-a-valid-connection-string-using-tcp-ip"></a><span data-ttu-id="e50d3-102">使用 TCP IP 创建有效的连接字符串</span><span class="sxs-lookup"><span data-stu-id="e50d3-102">Creating a Valid Connection String Using TCP IP</span></span>
  <span data-ttu-id="e50d3-103">若要使用 TCP/IP 来创建有效的连接字符串，必须执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="e50d3-103">To create a valid connection string using TCP/IP, you must:</span></span>  
  
-   <span data-ttu-id="e50d3-104">指定 **“别名”** 。</span><span class="sxs-lookup"><span data-stu-id="e50d3-104">Specify an **Alias Name**.</span></span>  
  
-   <span data-ttu-id="e50d3-105">在 **“服务器”** 框中，输入可以使用 **PING** 实用工具连接到的服务器名称或可以使用 **PING** 实用工具连接到的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="e50d3-105">For the **Server**, enter either a server name to which you can connect using the **PING** utility, or an IP address to which you can connect using the **PING** utility.</span></span> <span data-ttu-id="e50d3-106">对于命名实例，请追加实例名称。</span><span class="sxs-lookup"><span data-stu-id="e50d3-106">For a named instance append the instance name.</span></span>  
  
-   <span data-ttu-id="e50d3-107">在 **“协议”** 框中指定 **TCP/IP**。</span><span class="sxs-lookup"><span data-stu-id="e50d3-107">Specify **TCP/IP** for the **Protocol**.</span></span>  
  
-   <span data-ttu-id="e50d3-108">在 **“端口号”** 框中输入端口号（可选）。</span><span class="sxs-lookup"><span data-stu-id="e50d3-108">Optionally, enter a port number for the **Port No**.</span></span> <span data-ttu-id="e50d3-109">默认端口号为 1433，这是服务器上默认的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 实例的端口号。</span><span class="sxs-lookup"><span data-stu-id="e50d3-109">The default is 1433, which is the port number of the default instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] on a server.</span></span> <span data-ttu-id="e50d3-110">若要连接到命名实例或未侦听端口 1433 的默认实例，则必须提供端口号，或者启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 服务。</span><span class="sxs-lookup"><span data-stu-id="e50d3-110">To connect to a named instance or a default instance that is not listening on port 1433, you must provide the port number, or start the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service.</span></span> <span data-ttu-id="e50d3-111">有关配置 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 服务的信息，请参阅 [SQL Server Browser 服务](../../../2014/tools/configuration-manager/sql-server-browser-service.md)。</span><span class="sxs-lookup"><span data-stu-id="e50d3-111">For information on configuring the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service, see [SQL Server Browser Service](../../../2014/tools/configuration-manager/sql-server-browser-service.md).</span></span>  
  
 <span data-ttu-id="e50d3-112">连接时， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 组件将从指定别名的注册表中读取服务器、协议和端口的值，然后创建一个格式为 `tcp:<servername>[\<instancename>],<port>` 或 `tcp:<IPAddress>[\<instancename>],<port>`的连接字符串。</span><span class="sxs-lookup"><span data-stu-id="e50d3-112">At the time of connection, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client component reads the server, protocol, and port values from the registry for the specified alias name, and creates a connection string in the format `tcp:<servername>[\<instancename>],<port>` or `tcp:<IPAddress>[\<instancename>],<port>`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e50d3-113">默认情况下， [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 防火墙关闭端口 1433。</span><span class="sxs-lookup"><span data-stu-id="e50d3-113">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Firewall closes port 1433 by default.</span></span> <span data-ttu-id="e50d3-114">由于 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 通过端口 1433 进行通信，因此，如果你将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置为使用 TCP/IP 侦听传入客户端连接，则必须重新打开该端口。</span><span class="sxs-lookup"><span data-stu-id="e50d3-114">Because [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] communicates over port 1433, you must reopen the port if [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is configured to listen for incoming client connections using TCP/IP.</span></span> <span data-ttu-id="e50d3-115">有关配置防火墙的信息，请参阅 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 联机丛书中的“如何将防火墙配置为允许 SQL Server 访问”，或者查阅防火墙文档。</span><span class="sxs-lookup"><span data-stu-id="e50d3-115">For information on configuring a firewall, see "How to: Configure a Firewall for SQL Server Access" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online or review your firewall documentation.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="e50d3-116">和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 完全支持 Internet 协议版本 4 (IPv4) 和 Internet 协议版本 6 (IPv6)。</span><span class="sxs-lookup"><span data-stu-id="e50d3-116">and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client fully support both Internet Protocol version 4 (IPv4) and Internet Protocol version 6 (IPv6).</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="e50d3-117">配置管理器接受 IPv4 和 IPv6 格式的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="e50d3-117">Configuration Manager accepts both IPv4 and IPv6 formats for IP addresses.</span></span> <span data-ttu-id="e50d3-118">有关 IPv6 的信息，请参阅 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 联机丛书中的“使用 IPv6 进行连接”。</span><span class="sxs-lookup"><span data-stu-id="e50d3-118">For information on IPv6, see "Connecting Using IPv6" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="connecting-to-the-local-server"></a><span data-ttu-id="e50d3-119">连接到本地服务器</span><span class="sxs-lookup"><span data-stu-id="e50d3-119">Connecting to the Local Server</span></span>  
 <span data-ttu-id="e50d3-120">当连接与客户端运行在同一台计算机上的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 时，可以使用 `(local)` 作为服务器名称。</span><span class="sxs-lookup"><span data-stu-id="e50d3-120">When connecting to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] running on the same computer as the client, you can use `(local)` as the server name.</span></span> <span data-ttu-id="e50d3-121">由于上述方法不明确，因此不建议使用，但是当客户端运行在已知的计算机上时，该方法还是有用的。</span><span class="sxs-lookup"><span data-stu-id="e50d3-121">This is not encouraged as it leads to ambiguity, however it can be useful when the client is known to be running on the intended computer.</span></span> <span data-ttu-id="e50d3-122">例如，当为断开连接的移动用户（如销售人员，其 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将运行在便携式计算机上并存储相应的项目数据）创建应用程序时，连接到 `(local)` 的客户端就可以始终与运行在便携式计算机上的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 保持连接。</span><span class="sxs-lookup"><span data-stu-id="e50d3-122">For instance, when creating an application for mobile disconnected users, such as a sales force, where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will run on laptop computers and store project data, a client connecting to `(local)` would always connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] running on the laptop.</span></span> <span data-ttu-id="e50d3-123">可以使用词语 `localhost` 或句点 ( **.** ) 来取代 `(local)`。</span><span class="sxs-lookup"><span data-stu-id="e50d3-123">The word `localhost` or a period (**.**) can be used in place of `(local)`.</span></span>  
  
## <a name="verifying-your-connection-protocol"></a><span data-ttu-id="e50d3-124">验证连接协议</span><span class="sxs-lookup"><span data-stu-id="e50d3-124">Verifying Your Connection Protocol</span></span>  
 <span data-ttu-id="e50d3-125">以下查询将返回当前连接所使用的协议。</span><span class="sxs-lookup"><span data-stu-id="e50d3-125">The following query returns the protocol used for the current connection.</span></span>  
  
```  
SELECT net_transport   
FROM sys.dm_exec_connections   
WHERE session_id = @@SPID;  
  
```  
  
## <a name="examples"></a><span data-ttu-id="e50d3-126">示例</span><span class="sxs-lookup"><span data-stu-id="e50d3-126">Examples</span></span>  
 <span data-ttu-id="e50d3-127">通过服务器名称进行连接：</span><span class="sxs-lookup"><span data-stu-id="e50d3-127">Connecting by server name:</span></span>  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             <servername>  
  
```  
  
 <span data-ttu-id="e50d3-128">通过服务器名称连接到已命名的实例：</span><span class="sxs-lookup"><span data-stu-id="e50d3-128">Connecting by server name to a named instance:</span></span>  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             <servername>\<instancename>  
  
```  
  
 <span data-ttu-id="e50d3-129">通过服务器名称连接到指定的端口：</span><span class="sxs-lookup"><span data-stu-id="e50d3-129">Connecting by server name to a specified port:</span></span>  
  
```  
Alias Name         <serveralias>  
Port No            <port>  
Protocol           TCP/IP  
Server             <servername>  
  
```  
  
 <span data-ttu-id="e50d3-130">通过 IP 地址进行连接：</span><span class="sxs-lookup"><span data-stu-id="e50d3-130">Connecting by IP address:</span></span>  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             <IPAddress>  
  
```  
  
 <span data-ttu-id="e50d3-131">通过 IP 地址连接到命名实例：</span><span class="sxs-lookup"><span data-stu-id="e50d3-131">Connecting by IP address to a named instance:</span></span>  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             <IPAddress>\<instancename>  
  
```  
  
 <span data-ttu-id="e50d3-132">通过 IP 地址连接到指定的端口：</span><span class="sxs-lookup"><span data-stu-id="e50d3-132">Connecting by IP address to a specified port:</span></span>  
  
```  
Alias Name         <serveralias>  
Port No            <port number>  
Protocol           TCP/IP  
Server             <IPAddress>  
  
```  
  
 <span data-ttu-id="e50d3-133">使用 `(local)`连接到本地计算机：</span><span class="sxs-lookup"><span data-stu-id="e50d3-133">Connecting to the local computer using `(local)`:</span></span>  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             (local)  
  
```  
  
 <span data-ttu-id="e50d3-134">使用 `localhost`连接到本地计算机：</span><span class="sxs-lookup"><span data-stu-id="e50d3-134">Connecting to the local computer using `localhost`:</span></span>  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             localhost  
  
```  
  
 <span data-ttu-id="e50d3-135">连接到本地计算机 `localhost`上的命名实例：</span><span class="sxs-lookup"><span data-stu-id="e50d3-135">Connecting to a named instance on the local computer `localhost`:</span></span>  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             localhost\<instancename>  
  
```  
  
 <span data-ttu-id="e50d3-136">使用句点连接到本地计算机：</span><span class="sxs-lookup"><span data-stu-id="e50d3-136">Connecting to the local computer using a period:</span></span>  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             .  
  
```  
  
 <span data-ttu-id="e50d3-137">使用句点连接到本地计算机上的命名实例：</span><span class="sxs-lookup"><span data-stu-id="e50d3-137">Connecting to a named instance on the local computer using a period:</span></span>  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             .\<instancename>  
  
```  
  
> [!NOTE]  
>  <span data-ttu-id="e50d3-138">若要了解如何将网络协议指定为 **sqlcmd** 参数，请参阅 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 联机丛书中的“如何使用 sqlcmd.exe 连接到数据库引擎”。</span><span class="sxs-lookup"><span data-stu-id="e50d3-138">For information on specifying the network protocol as a **sqlcmd** parameter, see "How to: Connect to the Database Engine Using sqlcmd.exe" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e50d3-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e50d3-139">See Also</span></span>  
 <span data-ttu-id="e50d3-140">[使用 Shared Memory 协议创建有效的连接字符串](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-shared-memory-protocol.md) </span><span class="sxs-lookup"><span data-stu-id="e50d3-140">[Creating a Valid Connection String Using Shared Memory Protocol](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-shared-memory-protocol.md) </span></span>  
 <span data-ttu-id="e50d3-141">[使用命名管道创建有效的连接字符串](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-named-pipes.md) </span><span class="sxs-lookup"><span data-stu-id="e50d3-141">[Creating a Valid Connection String Using Named Pipes](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-named-pipes.md) </span></span>  
 [<span data-ttu-id="e50d3-142">选择网络协议</span><span class="sxs-lookup"><span data-stu-id="e50d3-142">Choosing a Network Protocol</span></span>](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md)  
  
  
