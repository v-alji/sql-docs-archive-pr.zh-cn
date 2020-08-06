---
title: 使用 sqlcmd 连接到数据库引擎
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- sqlcmd utility, Database Engine connections
- Named Pipes [SQL Server], sqlcmd utility
- TCP/IP [SQL Server], client protocols
- network protocols [SQL Server], sqlcmd utility
- protocols [SQL Server], sqlcmd utility
- VIA
- client protocols [SQL Server]
ms.assetid: 74b0fb71-7f8e-4171-9431-d07528532524
author: rothja
ms.author: jroth
ms.openlocfilehash: 3b409683b651e3e6508baced5eb3bc9fcc631e2c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578784"
---
# <a name="connect-to-the-database-engine-with-sqlcmd"></a><span data-ttu-id="1c25e-102">使用 sqlcmd 连接到数据库引擎</span><span class="sxs-lookup"><span data-stu-id="1c25e-102">Connect to the Database Engine With sqlcmd</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="1c25e-103">支持客户端使用 TCP/IP 网络协议（默认）和命名管道协议进行通信。</span><span class="sxs-lookup"><span data-stu-id="1c25e-103">supports client communication with the TCP/IP network protocol (the default), and the named pipes protocol.</span></span> <span data-ttu-id="1c25e-104">如果客户端正在连接到同一计算机上的[!INCLUDE[ssDE](../../includes/ssde-md.md)]实例，则还可使用 Shared Memory 协议。</span><span class="sxs-lookup"><span data-stu-id="1c25e-104">The shared memory protocol is also available if the client is connecting to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] on the same computer.</span></span> <span data-ttu-id="1c25e-105">通常有三种选择协议的方法。</span><span class="sxs-lookup"><span data-stu-id="1c25e-105">There are three common methods of selecting the protocol.</span></span> <span data-ttu-id="1c25e-106">**sqlcmd** 实用工具使用的协议按下列顺序确定：</span><span class="sxs-lookup"><span data-stu-id="1c25e-106">The protocol used by the **sqlcmd** utility is determined in the following order:</span></span>  
  
-   <span data-ttu-id="1c25e-107">**sqlcmd** 使用为连接字符串中指定的协议，如下所述。</span><span class="sxs-lookup"><span data-stu-id="1c25e-107">**sqlcmd** uses the protocol specified as part of the connection string as described below.</span></span>  
  
-   <span data-ttu-id="1c25e-108">如果连接字符串中未指定任何协议，则 **sqlcmd** 将使用连接到的别名中定义的协议。</span><span class="sxs-lookup"><span data-stu-id="1c25e-108">If no protocol is specified as part the connection string, **sqlcmd** will use the protocol defined as part of the alias that it is connecting to.</span></span> <span data-ttu-id="1c25e-109">若要将 **sqlcmd**配置为通过创建别名使用特定网络协议，请参阅[创建或删除供客户端使用的服务器别名 (SQL Server 配置管理器)](../../database-engine/configure-windows/create-or-delete-a-server-alias-for-use-by-a-client.md)。</span><span class="sxs-lookup"><span data-stu-id="1c25e-109">To configure **sqlcmd** to use a specific network protocol by creating an alias, see [Create or Delete a Server Alias for Use by a Client &#40;SQL Server Configuration Manager&#41;](../../database-engine/configure-windows/create-or-delete-a-server-alias-for-use-by-a-client.md).</span></span>  
  
-   <span data-ttu-id="1c25e-110">如果未通过其他方法指定协议， **sqlcmd** 将使用由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器中的协议顺序确定的网络协议。</span><span class="sxs-lookup"><span data-stu-id="1c25e-110">If the protocol is not specified in some other way, **sqlcmd** will use the network protocol determined by the protocol order in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span>  
  
 <span data-ttu-id="1c25e-111">下面的示例显示连接到 1433 端口上默认的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 实例以及假定侦听 1691 端口的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 命名实例的各种方法。</span><span class="sxs-lookup"><span data-stu-id="1c25e-111">The following examples show various ways of connecting to the default instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] on port 1433, and named instances of [!INCLUDE[ssDE](../../includes/ssde-md.md)] presumed to be listening on port 1691.</span></span> <span data-ttu-id="1c25e-112">其中一些示例使用环回适配器的 IP 地址 (127.0.0.1)。</span><span class="sxs-lookup"><span data-stu-id="1c25e-112">Some of these examples use the IP address of the loopback adapter (127.0.0.1).</span></span> <span data-ttu-id="1c25e-113">请使用您的计算机网络接口卡的 IP 地址进行测试。</span><span class="sxs-lookup"><span data-stu-id="1c25e-113">Test using the IP address of your computer network interface card.</span></span>  
  
 <span data-ttu-id="1c25e-114">通过指定实例名连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] ：</span><span class="sxs-lookup"><span data-stu-id="1c25e-114">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] by specifying the instance name:</span></span>  
  
```  
sqlcmd -S ComputerA  
sqlcmd -S ComputerA\instanceB  
```  
  
 <span data-ttu-id="1c25e-115">通过指定 IP 地址连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] ：</span><span class="sxs-lookup"><span data-stu-id="1c25e-115">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] by specifying the IP address:</span></span>  
  
```  
sqlcmd -S 127.0.0.1  
sqlcmd -S 127.0.0.1\instanceB  
```  
  
 <span data-ttu-id="1c25e-116">通过指定 TCP\IP 端口号连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] ：</span><span class="sxs-lookup"><span data-stu-id="1c25e-116">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] by specifying the TCP\IP port number:</span></span>  
  
```  
sqlcmd -S ComputerA,1433  
sqlcmd -S ComputerA,1691  
sqlcmd -S 127.0.0.1,1433  
sqlcmd -S 127.0.0.1,1691  
```  
  
### <a name="to-connect-using-tcpip"></a><span data-ttu-id="1c25e-117">使用 TCP/IP 进行连接</span><span class="sxs-lookup"><span data-stu-id="1c25e-117">To connect using TCP/IP</span></span>  
  
-   <span data-ttu-id="1c25e-118">使用以下常规语法进行连接：</span><span class="sxs-lookup"><span data-stu-id="1c25e-118">Connect using the following general syntax:</span></span>  
  
    ```  
    sqlcmd -S tcp:<computer name>,<port number>  
    ```  
  
-   <span data-ttu-id="1c25e-119">连接到默认实例：</span><span class="sxs-lookup"><span data-stu-id="1c25e-119">Connect to the default instance:</span></span>  
  
    ```  
    sqlcmd -S tcp:ComputerA,1433  
    sqlcmd -S tcp:127.0.0.1,1433  
    ```  
  
-   <span data-ttu-id="1c25e-120">连接到命名实例：</span><span class="sxs-lookup"><span data-stu-id="1c25e-120">Connect to a named instance:</span></span>  
  
    ```  
    sqlcmd -S tcp:ComputerA,1691  
    sqlcmd -S tcp:127.0.0.1,1691  
    ```  
  
### <a name="to-connect-using-named-pipes"></a><span data-ttu-id="1c25e-121">使用命名管道进行连接</span><span class="sxs-lookup"><span data-stu-id="1c25e-121">To connect using named pipes</span></span>  
  
-   <span data-ttu-id="1c25e-122">使用下列常规语法之一进行连接：</span><span class="sxs-lookup"><span data-stu-id="1c25e-122">Connect using one of the following general syntax:</span></span>  
  
    ```  
    sqlcmd -S np:\\<computer name>\<pipe name>  
    ```  
  
-   <span data-ttu-id="1c25e-123">连接到默认实例：</span><span class="sxs-lookup"><span data-stu-id="1c25e-123">Connect to the default instance:</span></span>  
  
    ```  
    sqlcmd -S np:\\ComputerA\pipe\sql\query  
    sqlcmd -S np:\\127.0.0.1\pipe\sql\query  
    ```  
  
-   <span data-ttu-id="1c25e-124">连接到命名实例：</span><span class="sxs-lookup"><span data-stu-id="1c25e-124">Connect to a named instance instance:</span></span>  
  
    ```  
    sqlcmd -S np:\\ComputerA\pipe\MSSQL$<instancename>\sql\query  
    sqlcmd -S np:\\127.0.0.1\pipe\MSSQL$<instancename>\sql\query  
    ```  
  
### <a name="to-connect-using-shared-memory-a-local-procedure-call-from-a-client-on-the-server"></a><span data-ttu-id="1c25e-125">在服务器上从客户端使用共享内存（本地过程调用）进行连接</span><span class="sxs-lookup"><span data-stu-id="1c25e-125">To connect using shared memory (a local procedure call) from a client on the server</span></span>  
  
-   <span data-ttu-id="1c25e-126">使用下列常规语法之一进行连接：</span><span class="sxs-lookup"><span data-stu-id="1c25e-126">Connect using one of the following general syntax:</span></span>  
  
    ```  
    sqlcmd -S lpc:<computer name>  
    ```  
  
-   <span data-ttu-id="1c25e-127">连接到默认实例：</span><span class="sxs-lookup"><span data-stu-id="1c25e-127">Connect to the default instance:</span></span>  
  
    ```  
    sqlcmd -S lpc:ComputerA  
    ```  
  
-   <span data-ttu-id="1c25e-128">连接到命名实例：</span><span class="sxs-lookup"><span data-stu-id="1c25e-128">Connect to a named instance:</span></span>  
  
    ```  
    sqlcmd -S lpc:ComputerA\<instancename>  
    ```  
  
  
