---
title: 使用 VPN 通过 Internet 发布数据 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- VPNs [SQL Server replication]
- Web publishing [SQL Server replication], VPNs
- Internet [SQL Server replication], VPNs
ms.assetid: 9ffb6546-9973-4574-aaa0-8fe0017e3601
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7a477e70031053a9563c2f3ed3740091d632febe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591267"
---
# <a name="publish-data-over-the-internet-using-vpn"></a><span data-ttu-id="c123e-102">使用 VPN 通过 Internet 发布数据</span><span class="sxs-lookup"><span data-stu-id="c123e-102">Publish Data over the Internet Using VPN</span></span>
  <span data-ttu-id="c123e-103">通过使用虚拟专用网络 (VPN) 技术，用户可以在家中、分支机构、远程客户端和其他公司通过 Internet 连接到企业网络进行工作，同时保持通信安全。</span><span class="sxs-lookup"><span data-stu-id="c123e-103">Virtual Private Networking (VPN) technology allows users working at home, branch offices, remote clients, and other companies to connect to a corporate network over the Internet, while maintaining secure communications.</span></span> <span data-ttu-id="c123e-104">用户可以像在局域网 (LAN) 上那样使用 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="c123e-104">Users can use Windows Authentication as though they were on a Local Area Network (LAN).</span></span> <span data-ttu-id="c123e-105">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 复制的所有类型都可以通过 VPN 复制数据，但如果使用的是合并复制，则应该考虑使用 Web 同步，因为 Web 同步不需要使用 VPN。</span><span class="sxs-lookup"><span data-stu-id="c123e-105">All types of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] replication can replicate data over a VPN, but consider using Web synchronization if you are using merge replication, because Web synchronization eliminates the need for a VPN.</span></span> <span data-ttu-id="c123e-106">有关详细信息，请参阅 [Web Synchronization for Merge Replication](web-synchronization-for-merge-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="c123e-106">For more information, see [Web Synchronization for Merge Replication](web-synchronization-for-merge-replication.md).</span></span>  
  
 <span data-ttu-id="c123e-107">VPN 包含客户端软件，以便计算机可以通过 Internet（特殊情况下甚至可以是 Intranet）连接到专用计算机或服务器上的软件。</span><span class="sxs-lookup"><span data-stu-id="c123e-107">A VPN includes client software so that computers connect over the Internet (or in special cases, even an intranet) to software in a dedicated computer or a server.</span></span> <span data-ttu-id="c123e-108">用户可以选择使用两端加密和用户身份验证的方法。</span><span class="sxs-lookup"><span data-stu-id="c123e-108">Optionally, encryption at both ends, as well as user authentication methods, are used.</span></span> <span data-ttu-id="c123e-109">Internet 上的 VPN 连接逻辑上可以像站点间的广域网 (WAN) 链接一样使用。</span><span class="sxs-lookup"><span data-stu-id="c123e-109">The VPN connection over the Internet logically operates as a Wide Area Network (WAN) link between the sites.</span></span>  
  
 <span data-ttu-id="c123e-110">VPN 通过一个网络连接另一个网络的组件。</span><span class="sxs-lookup"><span data-stu-id="c123e-110">A VPN connects the components of a network using another network.</span></span> <span data-ttu-id="c123e-111">为了连接，用户应以使用协议（例如 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 点对点隧道协议 [PPTP] 或第二层隧道协议 [L2TP]）的 Internet 或其他公用网络为隧道。</span><span class="sxs-lookup"><span data-stu-id="c123e-111">To connect, the user tunnels through the Internet or another public network using a protocol such as [!INCLUDE[msCoName](../../includes/msconame-md.md)] Point-to-Point Tunneling Protocol (PPTP) or Layer Two Tunneling Protocol (L2TP).</span></span> <span data-ttu-id="c123e-112">此过程提供了与以前仅在专用网络中实现的相同安全性和功能。</span><span class="sxs-lookup"><span data-stu-id="c123e-112">This process provides the same security and features previously available only in a private network.</span></span> <span data-ttu-id="c123e-113">在 Microsoft Windows NT 4.0 版和 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 2000（和更高版本）的操作系统中可以使用 PPTP；在 Windows 2000 和更高版本的操作系统中可以使用 L2TP。</span><span class="sxs-lookup"><span data-stu-id="c123e-113">PPTP is available with the Microsoft Windows NT version 4.0 and [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 2000 (and later) operating systems; L2TP is available with Windows 2000 and later.</span></span>  
  
 <span data-ttu-id="c123e-114">对于用户来说，Internet 的中间路由基础结构是不可见的，数据就好像通过专门的专用链接发送一样。</span><span class="sxs-lookup"><span data-stu-id="c123e-114">For the user, the intermediate routing infrastructure of the Internet is not visible and it appears as though the data is being sent over a dedicated private link.</span></span> <span data-ttu-id="c123e-115">就用户而言，VPN 是用户计算机和公司服务器之间的点对点连接。</span><span class="sxs-lookup"><span data-stu-id="c123e-115">As far as users are concerned, the VPN is a point-to-point connection between the user computer and a corporate server.</span></span>  
  
 <span data-ttu-id="c123e-116">将远程客户端配置为使用 VPN 进行连接，而且客户端能够访问 Internet 并已登录到公司 LAN 之后，可以像远程客户端直接连接在 LAN 上一样配置复制。</span><span class="sxs-lookup"><span data-stu-id="c123e-116">After you have your remote client configured to connect using a VPN, and the client has Internet access and is logged in to the corporate LAN, you can configure replication as though the remote client is connected directly on the LAN.</span></span> <span data-ttu-id="c123e-117">出于安全考虑，通过 VPN 连接的用户和直接连接在 LAN 上的用户可能使用不同的网络资源。</span><span class="sxs-lookup"><span data-stu-id="c123e-117">For security reasons, it is possible to have different network resources available to users connected over VPN and to those connected directly on the LAN.</span></span>  
  
 <span data-ttu-id="c123e-118">有关设置 VPN 的详细信息，请参阅 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 文档。</span><span class="sxs-lookup"><span data-stu-id="c123e-118">For more information about setting up a VPN, see the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c123e-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c123e-119">See Also</span></span>  
 [<span data-ttu-id="c123e-120">通过 Internet 复制</span><span class="sxs-lookup"><span data-stu-id="c123e-120">Replication over the Internet</span></span>](replication-over-the-internet.md)  
  
  
