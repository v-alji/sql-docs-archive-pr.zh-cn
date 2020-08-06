---
title: 使用 Shared Memory 协议创建有效的连接字符串 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- connection strings [Database Engine], shared memory
- aliases [SQL Server], shared memory
ms.assetid: 5fff42e8-377f-4b40-b0c8-b02393f8a1af
author: stevestein
ms.author: sstein
ms.openlocfilehash: ca97332a09a33fcfc15a3dbb2599af27dbe0e1db
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682558"
---
# <a name="creating-a-valid-connection-string-using-shared-memory-protocol"></a><span data-ttu-id="ac62d-102">使用 Shared Memory 协议创建有效的连接字符串</span><span class="sxs-lookup"><span data-stu-id="ac62d-102">Creating a Valid Connection String Using Shared Memory Protocol</span></span>
  <span data-ttu-id="ac62d-103">从运行在同一台计算机上的客户端到 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的连接使用 shared memory 协议。</span><span class="sxs-lookup"><span data-stu-id="ac62d-103">Connections to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from a client running on the same computer use the shared memory protocol.</span></span> <span data-ttu-id="ac62d-104">共享内存没有可配置的属性。</span><span class="sxs-lookup"><span data-stu-id="ac62d-104">Shared memory has no configurable properties.</span></span> <span data-ttu-id="ac62d-105">始终会先尝试使用共享内存，无法将其从 **“客户端协议属性”** 列表中 **“启用的协议”** 列表的顶部位置移开。</span><span class="sxs-lookup"><span data-stu-id="ac62d-105">Shared memory is always tried first, and cannot be moved from the top position of the **Enabled Protocols** list in the **Client Protocols Properties** list.</span></span> <span data-ttu-id="ac62d-106">可以禁用 shared memory 协议，在排除其他某个协议的故障时，这样做很有用。</span><span class="sxs-lookup"><span data-stu-id="ac62d-106">The Shared Memory protocol can be disabled, which is useful when troubleshooting one of the other protocols.</span></span>  
  
 <span data-ttu-id="ac62d-107">不能使用 shared memory 协议来创建别名，但是如果启用了共享内存，然后通过名称连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] ，就可以创建共享内存连接。</span><span class="sxs-lookup"><span data-stu-id="ac62d-107">You cannot create an alias using the shared memory protocol, but if shared memory is enabled, then connecting to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] by name, creates a shared memory connection.</span></span> <span data-ttu-id="ac62d-108">共享内存连接字符串的格式为 `lpc:<servername>[\instancename]`。</span><span class="sxs-lookup"><span data-stu-id="ac62d-108">A shared memory connection string uses the format `lpc:<servername>[\instancename]`.</span></span>  
  
## <a name="connecting-to-the-local-server"></a><span data-ttu-id="ac62d-109">连接到本地服务器</span><span class="sxs-lookup"><span data-stu-id="ac62d-109">Connecting to the Local Server</span></span>  
 <span data-ttu-id="ac62d-110">当连接到与客户端运行在同一台计算机上的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 时，可以使用“(本地)”  作为服务器名称。</span><span class="sxs-lookup"><span data-stu-id="ac62d-110">When connecting to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] running on the same computer as the client, you can use **(local)** as the server name.</span></span> <span data-ttu-id="ac62d-111">由于上述方法不明确，因此不建议使用，但是当客户端运行在已知的计算机上时，该方法还是有用的。</span><span class="sxs-lookup"><span data-stu-id="ac62d-111">This is not encouraged as it leads to ambiguity, however it can be useful when the client is known to be running on the intended computer.</span></span> <span data-ttu-id="ac62d-112">例如，当为断开连接的移动用户（如销售人员，其 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将在便携式计算机上运行并存储相应的项目数据）创建应用程序时，连接到“(本地)”  的客户端就可以始终与运行在便携式计算机上的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 保持连接。</span><span class="sxs-lookup"><span data-stu-id="ac62d-112">For instance, when creating an application for mobile disconnected users, such as a sales force, where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will run on laptop computers and store project data, a client connecting to **(local)** would always connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] running on the laptop.</span></span> <span data-ttu-id="ac62d-113">可以使用词语“本地主机”  或句点 ( **.** ) 来取代“(本地)”  。</span><span class="sxs-lookup"><span data-stu-id="ac62d-113">The word **localhost** or a period (**.**) can be used in place of **(local)**.</span></span>  
  
## <a name="verifying-your-connection-protocol"></a><span data-ttu-id="ac62d-114">验证连接协议</span><span class="sxs-lookup"><span data-stu-id="ac62d-114">Verifying your Connection Protocol</span></span>  
 <span data-ttu-id="ac62d-115">以下查询将返回当前连接所使用的协议。</span><span class="sxs-lookup"><span data-stu-id="ac62d-115">The following query will return the protocol used for the current connection.</span></span>  
  
```  
SELECT net_transport   
FROM sys.dm_exec_connections   
WHERE session_id = @@SPID;  
  
```  
  
## <a name="examples"></a><span data-ttu-id="ac62d-116">示例：</span><span class="sxs-lookup"><span data-stu-id="ac62d-116">Examples:</span></span>  
 <span data-ttu-id="ac62d-117">如果已启用 shared memory 协议，下列名称将使用该协议连接到本地计算机：</span><span class="sxs-lookup"><span data-stu-id="ac62d-117">The following names will connect to the local computer with the shared memory protocol if it is enabled:</span></span>  
  
 `<servername>`  
  
 `<servername>\<instancename>`  
  
 `(local)`  
  
 `localhost`  
  
 <span data-ttu-id="ac62d-118">不能为共享内存连接创建别名。</span><span class="sxs-lookup"><span data-stu-id="ac62d-118">You cannot create an alias for a shared memory connection.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ac62d-119">在“服务器”框中指定 IP 地址将产生 TCP/IP 连接。 </span><span class="sxs-lookup"><span data-stu-id="ac62d-119">Specifying an IP Address in the **Server** box will result in a TCP/IP connection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac62d-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ac62d-120">See Also</span></span>  
 <span data-ttu-id="ac62d-121">[使用 TCP IP 创建有效的连接字符串](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md) </span><span class="sxs-lookup"><span data-stu-id="ac62d-121">[Creating a Valid Connection String Using TCP IP](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md) </span></span>  
 <span data-ttu-id="ac62d-122">[使用命名管道创建有效的连接字符串](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-named-pipes.md) </span><span class="sxs-lookup"><span data-stu-id="ac62d-122">[Creating a Valid Connection String Using Named Pipes](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-named-pipes.md) </span></span>  
 [<span data-ttu-id="ac62d-123">选择网络协议</span><span class="sxs-lookup"><span data-stu-id="ac62d-123">Choosing a Network Protocol</span></span>](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md)  
  
  
