---
title: 使用 Named Pipes 创建有效的连接字符串 |Microsoft Docs
description: 了解如何在使用 named pipes 协议连接到 SQL Server 实例时创建有效的连接字符串。 查看有效管道名称的示例。
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- connection strings [Database Engine], named pipes
- pipes [SQL Server]
- pipes [SQL Server], connecting to
- aliases [SQL Server], named pipes
- Named Pipes [SQL Server], connection strings
ms.assetid: 90930ff2-143b-4651-8ae3-297103600e4f
author: rothja
ms.author: jroth
ms.openlocfilehash: 10f3e1d01e9e5b7b1d1c0d1bb822bf233ceee636
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586042"
---
# <a name="creating-a-valid-connection-string-using-named-pipes"></a><span data-ttu-id="77f3f-104">使用 Named Pipes 创建有效的连接字符串</span><span class="sxs-lookup"><span data-stu-id="77f3f-104">Creating a Valid Connection String Using Named Pipes</span></span>
  <span data-ttu-id="77f3f-105">除非用户进行了更改，否则当的默认实例 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 侦听 named pipes 协议时，它将使用 `\\.\pipe\sql\query` 作为管道名称。</span><span class="sxs-lookup"><span data-stu-id="77f3f-105">Unless changed by the user, when the default instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] listens on the named pipes protocol, it uses `\\.\pipe\sql\query` as the pipe name.</span></span> <span data-ttu-id="77f3f-106">句点指示该计算机是本地计算机， `pipe` 指示该连接是命名管道， `sql\query` 是管道的名称。</span><span class="sxs-lookup"><span data-stu-id="77f3f-106">The period indicates that the computer is the local computer, `pipe` indicates that the connection is a named pipe, and `sql\query` is the name of the pipe.</span></span> <span data-ttu-id="77f3f-107">若要连接到默认管道，别名必须使用 `\\<computer_name>\pipe\sql\query` 作为管道名称。</span><span class="sxs-lookup"><span data-stu-id="77f3f-107">To connect to the default pipe, the alias must have `\\<computer_name>\pipe\sql\query` as the pipe name.</span></span> <span data-ttu-id="77f3f-108">如果已将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置为侦听其他管道，则管道名称必须使用该管道。</span><span class="sxs-lookup"><span data-stu-id="77f3f-108">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has been configured to listen on a different pipe, the pipe name must use that pipe.</span></span> <span data-ttu-id="77f3f-109">例如，如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用 `\\.\pipe\unit\app` 作为管道，则别名必须使用 `\\<computer_name>\pipe\unit\app` 作为管道名称。</span><span class="sxs-lookup"><span data-stu-id="77f3f-109">For instance, if [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is using `\\.\pipe\unit\app` as the pipe, the alias must use `\\<computer_name>\pipe\unit\app` as the pipe name.</span></span>  
  
 <span data-ttu-id="77f3f-110">若要创建一个有效的管道名称，必须执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="77f3f-110">To create a valid pipe name, you must:</span></span>  
  
-   <span data-ttu-id="77f3f-111">指定 **“别名”**。</span><span class="sxs-lookup"><span data-stu-id="77f3f-111">Specify an **Alias Name**.</span></span>  
  
-   <span data-ttu-id="77f3f-112">选择 "**命名管道**" 作为**协议**。</span><span class="sxs-lookup"><span data-stu-id="77f3f-112">Select **Named Pipes** as the **Protocol**.</span></span>  
  
-   <span data-ttu-id="77f3f-113">输入**管道名称**。</span><span class="sxs-lookup"><span data-stu-id="77f3f-113">Enter the **Pipe Name**.</span></span> <span data-ttu-id="77f3f-114">或者，你可以将 "**管道名称**" 留空，在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 指定**协议**和**服务器**后 Configuration Manager 将完成相应的管道名称</span><span class="sxs-lookup"><span data-stu-id="77f3f-114">Alternatively, you can leave **Pipe Name** blank and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager will complete the appropriate pipe name after you specify the **Protocol** and **Server**</span></span>  
  
-   <span data-ttu-id="77f3f-115">指定**服务器**。</span><span class="sxs-lookup"><span data-stu-id="77f3f-115">Specify a **Server**.</span></span> <span data-ttu-id="77f3f-116">对于命名实例，可以提供服务器名称和实例名称。</span><span class="sxs-lookup"><span data-stu-id="77f3f-116">For a named instance you can provide a server name and instance name.</span></span>  
  
 <span data-ttu-id="77f3f-117">连接时， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 组件将从注册表中读取指定别名的服务器、协议和管道名称值，并创建格式为或的管道名称 `np:\\<computer_name>\pipe\<pipename>` `np:\\<IPAddress>\pipe\<pipename>` 。对于命名实例，默认管道名称为 `\\<computer_name>\pipe\MSSQL$<instance_name>\sql\query` 。</span><span class="sxs-lookup"><span data-stu-id="77f3f-117">At the time of connection, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client component reads the server, protocol, and pipe name values from the registry for the specified alias name, and creates a pipe name in the format `np:\\<computer_name>\pipe\<pipename>` or `np:\\<IPAddress>\pipe\<pipename>`.For a named instance, the default pipe name is `\\<computer_name>\pipe\MSSQL$<instance_name>\sql\query`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="77f3f-118">默认情况下，[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 防火墙关闭端口 445。</span><span class="sxs-lookup"><span data-stu-id="77f3f-118">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Firewall closes port 445 by default.</span></span> <span data-ttu-id="77f3f-119">因为 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 通过端口 445 进行通信，所以，如果将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置为使用命名管道侦听传入客户端连接，则必须重新打开该端口。</span><span class="sxs-lookup"><span data-stu-id="77f3f-119">Because [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] communicates over port 445, you must reopen the port if [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is configured to listen for incoming client connections using named pipes.</span></span> <span data-ttu-id="77f3f-120">有关配置防火墙的信息，请参阅 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 联机丛书中的“如何将防火墙配置为允许 SQL Server 访问”，或者查阅防火墙文档。</span><span class="sxs-lookup"><span data-stu-id="77f3f-120">For information on configuring a firewall, see "How to: Configure a Firewall for SQL Server Access" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online or review your firewall documentation.</span></span>  
  
## <a name="connecting-to-the-local-server"></a><span data-ttu-id="77f3f-121">连接到本地服务器</span><span class="sxs-lookup"><span data-stu-id="77f3f-121">Connecting to the Local Server</span></span>  
 <span data-ttu-id="77f3f-122">当连接与客户端运行在同一台计算机上的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 时，可以使用 `(local)` 作为服务器名称。</span><span class="sxs-lookup"><span data-stu-id="77f3f-122">When connecting to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] running on the same computer as the client, you can use `(local)`as the server name.</span></span> <span data-ttu-id="77f3f-123">由于上述方法不明确，因此不建议使用 `(local)`，但是当客户端运行在已知的计算机上时，该方法还是有用的。</span><span class="sxs-lookup"><span data-stu-id="77f3f-123">Using `(local)` is not encouraged because it leads to ambiguity; however it can be useful when the client is known to be running on the intended computer.</span></span> <span data-ttu-id="77f3f-124">例如，当为断开连接的移动用户（如销售人员，其 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将运行在便携式计算机上并存储相应的项目数据）创建应用程序时，连接到 (local) 的客户端就可以始终与运行在便携式计算机上的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 保持连接。</span><span class="sxs-lookup"><span data-stu-id="77f3f-124">For instance, when creating an application for mobile disconnected users, such as a sales force, where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will run on laptop computers and store project data, a client connecting to (local) would always connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] running on the laptop.</span></span> <span data-ttu-id="77f3f-125">可以使用词语 `localhost` 或句点 (.) 来取代 `(local)`。</span><span class="sxs-lookup"><span data-stu-id="77f3f-125">The word `localhost` or a period (.) can be used in place of `(local)`.</span></span>  
  
## <a name="verifying-your-connection-protocol"></a><span data-ttu-id="77f3f-126">验证连接协议</span><span class="sxs-lookup"><span data-stu-id="77f3f-126">Verifying Your Connection Protocol</span></span>  
 <span data-ttu-id="77f3f-127">以下查询将返回当前连接所使用的协议。</span><span class="sxs-lookup"><span data-stu-id="77f3f-127">The following query will return the protocol used for the current connection.</span></span>  
  
```  
SELECT net_transport   
FROM sys.dm_exec_connections   
WHERE session_id = @@SPID;  
  
```  
  
## <a name="examples"></a><span data-ttu-id="77f3f-128">示例</span><span class="sxs-lookup"><span data-stu-id="77f3f-128">Examples</span></span>  
 <span data-ttu-id="77f3f-129">通过服务器名称连接到默认管道：</span><span class="sxs-lookup"><span data-stu-id="77f3f-129">Connecting by server name to the default pipe:</span></span>  
  
```  
Alias Name         <serveralias>  
Pipe Name          <blank>  
Protocol           Named Pipes  
Server             <servername>  
  
```  
  
 <span data-ttu-id="77f3f-130">通过 IP 地址连接到默认管道：</span><span class="sxs-lookup"><span data-stu-id="77f3f-130">Connecting by IP Address to the default pipe:</span></span>  
  
```  
Alias Name         <serveralias>  
Pipe Name          <leave blank>  
Protocol           Named Pipes  
Server             <IPAddress>  
  
```  
  
 <span data-ttu-id="77f3f-131">通过服务器名称连接到非默认管道：</span><span class="sxs-lookup"><span data-stu-id="77f3f-131">Connecting by server name to a non-default pipe:</span></span>  
  
```  
Alias Name         <serveralias>  
Pipe Name          \\<servername>\pipe\unit\app  
Protocol           Named Pipes  
Server             <servername>  
  
```  
  
 <span data-ttu-id="77f3f-132">通过服务器名称连接到已命名的实例：</span><span class="sxs-lookup"><span data-stu-id="77f3f-132">Connecting by server name to a named instance:</span></span>  
  
```  
Alias Name         <serveralias>  
Pipe Name          \\<servername>\pipe\MSSQL$<instancename>\SQL\query  
Protocol           Named Pipes  
Server             <servername>  
  
```  
  
 <span data-ttu-id="77f3f-133">使用 `localhost`连接到本地计算机：</span><span class="sxs-lookup"><span data-stu-id="77f3f-133">Connecting to the local computer using `localhost`:</span></span>  
  
```  
Alias Name         <serveralias>  
Pipe Name          <blank>  
Protocol           Named Pipes  
Server             localhost  
  
```  
  
 <span data-ttu-id="77f3f-134">使用句点连接到本地计算机：</span><span class="sxs-lookup"><span data-stu-id="77f3f-134">Connecting to the local computer using a period:</span></span>  
  
```  
Alias Name         <serveralias>  
Pipe Name          <left blank>  
Protocol           Named Pipes  
Server             .  
  
```  
  
> [!NOTE]  
>  <span data-ttu-id="77f3f-135">若要将网络协议指定为**sqlcmd**参数，请参阅联机丛书中的 "如何使用 sqlcmd.exe 连接到数据库引擎" [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="77f3f-135">To specify the network protocol as a **sqlcmd** parameter, see "How to: Connect to the Database Engine Using sqlcmd.exe" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77f3f-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="77f3f-136">See Also</span></span>  
 <span data-ttu-id="77f3f-137">[使用 Shared Memory 协议创建有效的连接字符串](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-shared-memory-protocol.md) </span><span class="sxs-lookup"><span data-stu-id="77f3f-137">[Creating a Valid Connection String Using Shared Memory Protocol](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-shared-memory-protocol.md) </span></span>  
 <span data-ttu-id="77f3f-138">[使用 TCP IP 创建有效的连接字符串](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md) </span><span class="sxs-lookup"><span data-stu-id="77f3f-138">[Creating a Valid Connection String Using TCP IP](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md) </span></span>  
 [<span data-ttu-id="77f3f-139">选择网络协议</span><span class="sxs-lookup"><span data-stu-id="77f3f-139">Choosing a Network Protocol</span></span>](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md)  
  
  
