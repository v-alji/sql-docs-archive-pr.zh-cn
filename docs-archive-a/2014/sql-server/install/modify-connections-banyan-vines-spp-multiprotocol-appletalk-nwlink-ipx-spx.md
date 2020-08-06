---
title: 修改使用 Banyan VINES 顺序包协议 (SPP) 、多协议、AppleTalk 或 NWLink IPX SPX 网络协议的连接 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- network protocols [SQL Server], modifying connections
- SPP [SQL Server]
- NWLink IPX/SPX [SQL Server]
- connections [SQL Server]
- AppleTalk [SQL Server]
- Sequenced Packet Protocol [SQL Server]
- Multiprotocol Net-Library [SQL Server]
- Banyan VINES Sequenced Package Protocol [SQL Server]
- IPX/SPX [SQL Server]
- protocols [SQL Server], modifying connections
- RPC [SQL Server]
ms.assetid: 5c5ae453-cc5b-4898-95c7-ad34157b1f60
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 750b9c0b76ab6c3b43908ecb8454f31ac1a25b1a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693185"
---
# <a name="modify-connections-that-use-banyan-vines-sequenced-packet-protocol-spp-multiprotocol-appletalk-or-nwlink-ipx-spx-network-protocols"></a><span data-ttu-id="90879-102">修改使用 Banyan VINES 顺序包协议 (SPP)、多协议、AppleTalk 或 NWLink IPX SPX 网络协议的连接</span><span class="sxs-lookup"><span data-stu-id="90879-102">Modify connections that use Banyan VINES Sequenced Packet Protocol (SPP), Multiprotocol, AppleTalk, or NWLink IPX SPX network protocols</span></span>
  <span data-ttu-id="90879-103">升级顾问已检测到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 不支持的客户端服务器连接协议。</span><span class="sxs-lookup"><span data-stu-id="90879-103">The Upgrade Advisor has detected client server connectivity protocols that are not supported in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="90879-104">使用 Banyan VINES 顺序包协议 (SPP)、多协议 (RPC)、AppleTalk 或 NWLink IPX/SPX 网络协议的客户端应用程序必须通过支持的协议进行连接。</span><span class="sxs-lookup"><span data-stu-id="90879-104">Client applications that use Banyan VINES Sequenced Packet Protocol (SPP), Multiprotocol (RPC), AppleTalk, or NWLink IPX/SPX network protocols must connect using a supported protocol.</span></span>  
  
## <a name="component"></a><span data-ttu-id="90879-105">组件</span><span class="sxs-lookup"><span data-stu-id="90879-105">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="90879-106">说明</span><span class="sxs-lookup"><span data-stu-id="90879-106">Description</span></span>  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="90879-107">不支持 Banyan VINES 顺序包协议 (SPP)、多协议、AppleTalk 或 NWLink IPX/SPX 网络协议。</span><span class="sxs-lookup"><span data-stu-id="90879-107">does not support the Banyan VINES Sequenced Packet Protocol (SPP), Multiprotocol, AppleTalk, or NWLink IPX/SPX network protocols.</span></span> <span data-ttu-id="90879-108">以前使用这些协议连接的客户端必须选择其他协议。</span><span class="sxs-lookup"><span data-stu-id="90879-108">Clients previously connecting with these protocols must select a different protocol.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="90879-109">纠正措施</span><span class="sxs-lookup"><span data-stu-id="90879-109">Corrective Action</span></span>  
 <span data-ttu-id="90879-110">连接到服务器时，请将客户端应用程序更改为使用支持的协议。</span><span class="sxs-lookup"><span data-stu-id="90879-110">Change the client applications to use a supported protocol when connecting to the server.</span></span> <span data-ttu-id="90879-111">如果设置的别名使用了不支持的协议，则必须修改该别名，使其使用支持的协议。</span><span class="sxs-lookup"><span data-stu-id="90879-111">If you have an alias setup that uses one of the unsupported protocols then the alias must be modified to use one of the supported protocols.</span></span>  
  
 <span data-ttu-id="90879-112">如果你的应用程序连接字符串专门使用或加载其中一个协议，请为 RPC 指定 NETWORK = DBMSRPCN，NETWORK = DBMSADSN for Appletalk，或 NETWORK = DBMSVINN for Banyan VINES 属性，或使用显式前缀（如 "spx：*服务器 \ 实例*" 用于 spx，"bv：*server*" 用于 spx，"Banyan：*server" 表示*，对于多协议，则必须修改*server*应用程序以使用其中一个受支持的协议）。</span><span class="sxs-lookup"><span data-stu-id="90879-112">If your application connection string specifically uses or loads one of these protocols, by either specifying NETWORK=DBMSRPCN for RPC, NETWORK=DBMSADSN for Appletalk, or NETWORK=DBMSVINN for Banyan VINES property, or by using an explicit prefix such as "spx:*server\instance*" for SPX, "bv:*server*" for Banyan VINES, "adsp:*server*" for AppleTalk, or "rpc:*server*" for multiprotocol, then you must modify your application to use one of the supported protocols.</span></span>  
  
 <span data-ttu-id="90879-113">有关详细信息，请参阅 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 联机丛书中的“选择网络协议”。</span><span class="sxs-lookup"><span data-stu-id="90879-113">For more information, see "Choosing a Network Protocol" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90879-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="90879-114">See Also</span></span>  
 <span data-ttu-id="90879-115">[数据库引擎升级问题](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="90879-115">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="90879-116">SQL Server 2014 升级顾问 &#91;新&#93;</span><span class="sxs-lookup"><span data-stu-id="90879-116">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
