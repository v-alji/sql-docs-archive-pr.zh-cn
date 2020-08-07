---
title: MSSQLSERVER_11001 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "12001"
helpviewer_keywords:
- 11001 (Database Engine error)
ms.assetid: 53d4d63a-61e3-441f-bfe9-9d44f7a05fd4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: da7dd171d1b6a64e0cc1666eda1e3593a81eece1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589667"
---
# <a name="mssqlserver_11001"></a><span data-ttu-id="c7f5d-102">MSSQLSERVER_11001</span><span class="sxs-lookup"><span data-stu-id="c7f5d-102">MSSQLSERVER_11001</span></span>
    
## <a name="details"></a><span data-ttu-id="c7f5d-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="c7f5d-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c7f5d-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="c7f5d-104">Product Name</span></span>|<span data-ttu-id="c7f5d-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="c7f5d-105">SQL Server</span></span>|  
|<span data-ttu-id="c7f5d-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="c7f5d-106">Event ID</span></span>|<span data-ttu-id="c7f5d-107">11001</span><span class="sxs-lookup"><span data-stu-id="c7f5d-107">11001</span></span>|  
|<span data-ttu-id="c7f5d-108">事件源</span><span class="sxs-lookup"><span data-stu-id="c7f5d-108">Event Source</span></span>|<span data-ttu-id="c7f5d-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="c7f5d-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="c7f5d-110">组件</span><span class="sxs-lookup"><span data-stu-id="c7f5d-110">Component</span></span>|<span data-ttu-id="c7f5d-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="c7f5d-111">SQLEngine</span></span>|  
|<span data-ttu-id="c7f5d-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="c7f5d-112">Symbolic Name</span></span>||  
|<span data-ttu-id="c7f5d-113">消息正文</span><span class="sxs-lookup"><span data-stu-id="c7f5d-113">Message Text</span></span>|<span data-ttu-id="c7f5d-114">在建立与服务器的连接时出错。</span><span class="sxs-lookup"><span data-stu-id="c7f5d-114">An error has occurred while establishing a connection to the server.</span></span>  <span data-ttu-id="c7f5d-115">在连接到 SQL Server 时，在默认的设置下 SQL Server 不允许远程连接可能会导致此失败。</span><span class="sxs-lookup"><span data-stu-id="c7f5d-115">When connecting to SQL Server, this failure may be caused by the fact that under the default settings SQL Server does not allow remote connections.</span></span> <span data-ttu-id="c7f5d-116">（提供程序：TCP 提供程序，错误:0 - 无法识别主机。）（.Net SqlClient 数据提供程序）</span><span class="sxs-lookup"><span data-stu-id="c7f5d-116">(provider: TCP Provider, error: 0 - No such host is known.) (.Net SqlClient Data Provider)</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c7f5d-117">说明</span><span class="sxs-lookup"><span data-stu-id="c7f5d-117">Explanation</span></span>  
 <span data-ttu-id="c7f5d-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 客户端无法连接到服务器。</span><span class="sxs-lookup"><span data-stu-id="c7f5d-118">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client cannot connect to the server.</span></span> <span data-ttu-id="c7f5d-119">发生此错误的原因可能是客户端无法解析服务器的名称或服务器的名称不正确。</span><span class="sxs-lookup"><span data-stu-id="c7f5d-119">The error could occur because either the client cannot resolve the name of the server or the name of the server is incorrect.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c7f5d-120">用户操作</span><span class="sxs-lookup"><span data-stu-id="c7f5d-120">User Action</span></span>  
 <span data-ttu-id="c7f5d-121">确保已输入正确的客户端服务器名称，并且可以解析客户端服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="c7f5d-121">Make sure that you have entered the correct server name on the client, and that you can resolve the name of the server from the client.</span></span> <span data-ttu-id="c7f5d-122">若要检查 TCP/IP 名称解析，可以使用 Windows 操作系统中的 **ping** 命令。</span><span class="sxs-lookup"><span data-stu-id="c7f5d-122">To check TCP/IP name resolution, you can use the **ping** command in the Windows operating system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7f5d-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c7f5d-123">See Also</span></span>  
 <span data-ttu-id="c7f5d-124">[网络协议和网络库](../../sql-server/install/network-protocols-and-network-libraries.md) </span><span class="sxs-lookup"><span data-stu-id="c7f5d-124">[Network Protocols and Network Libraries](../../sql-server/install/network-protocols-and-network-libraries.md) </span></span>  
 <span data-ttu-id="c7f5d-125">[客户端网络配置](../../database-engine/configure-windows/client-network-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="c7f5d-125">[Client Network Configuration](../../database-engine/configure-windows/client-network-configuration.md) </span></span>  
 <span data-ttu-id="c7f5d-126">[配置客户端协议](../../database-engine/configure-windows/configure-client-protocols.md) </span><span class="sxs-lookup"><span data-stu-id="c7f5d-126">[Configure Client Protocols](../../database-engine/configure-windows/configure-client-protocols.md) </span></span>  
 [<span data-ttu-id="c7f5d-127">启用或禁用服务器网络协议</span><span class="sxs-lookup"><span data-stu-id="c7f5d-127">Enable or Disable a Server Network Protocol</span></span>](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)  
  
  
