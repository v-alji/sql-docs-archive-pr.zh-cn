---
title: 保护通过 Internet 进行的复制 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- security [SQL Server replication], Internet
- Internet [SQL Server replication], security
ms.assetid: 25b7af05-2721-4b24-9083-fb671e8bf4e0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 47408b2b9559d33da4563c6fc9560d20338ee01d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693241"
---
# <a name="securing-replication-over-the-internet"></a><span data-ttu-id="d2abf-102">Securing Replication Over the Internet</span><span class="sxs-lookup"><span data-stu-id="d2abf-102">Securing Replication Over the Internet</span></span>
  <span data-ttu-id="d2abf-103">Internet 上的复制非常灵活，对移动订阅方而言尤为如此，但必须适当地配置 Internet 复制以确保具有足够的安全性。</span><span class="sxs-lookup"><span data-stu-id="d2abf-103">Replication over the Internet can provide flexibility, particularly for mobile Subscribers, but you must configure Internet replication appropriately to ensure adequate security.</span></span> [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="d2abf-104">建议使用下列两种技术之一在 Internet 上安全地共享信息：</span><span class="sxs-lookup"><span data-stu-id="d2abf-104">recommends using one of two techniques for securely sharing information over the Internet:</span></span>  
  
-   <span data-ttu-id="d2abf-105">虚拟专用网络 (VPN)</span><span class="sxs-lookup"><span data-stu-id="d2abf-105">Virtual private network (VPN)</span></span>  
  
-   <span data-ttu-id="d2abf-106">合并复制的 Web 同步选项</span><span class="sxs-lookup"><span data-stu-id="d2abf-106">The Web synchronization option for merge replication</span></span>  
  
## <a name="virtual-private-network"></a><span data-ttu-id="d2abf-107">虚拟专用网络</span><span class="sxs-lookup"><span data-stu-id="d2abf-107">Virtual Private Network</span></span>  
 <span data-ttu-id="d2abf-108">虚拟专用网络为在 Internet 上复制 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 数据提供了简便安全的分层方法。</span><span class="sxs-lookup"><span data-stu-id="d2abf-108">Virtual private networks provide a simple and secure layered approach to replicating [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data over the Internet.</span></span> <span data-ttu-id="d2abf-109">Internet 上的 VPN 连接逻辑上可以像站点间的广域网 (WAN) 链接一样使用。</span><span class="sxs-lookup"><span data-stu-id="d2abf-109">The VPN connection over the Internet logically operates as a Wide Area Network (WAN) link between the sites.</span></span>  
  
 <span data-ttu-id="d2abf-110">其实现方法是允许用户使用如 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows NT 4.0 或 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows 2000 操作系统中的 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 点对点隧道协议 (PPTP) 或者 Windows 2000 操作系统中的第二层隧道协议 (L2TP)，将 Internet 或另一公用网络作为通道。</span><span class="sxs-lookup"><span data-stu-id="d2abf-110">This is achieved by allowing the user to tunnel through the Internet or another public network using a protocol such as [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Point-to-Point Tunneling Protocol (PPTP) available with the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows NT version 4.0 or [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows 2000 operating system, or Layer Two Tunneling Protocol (L2TP) available with the Windows 2000 operating system.</span></span> <span data-ttu-id="d2abf-111">此过程提供类似于专用网络中的安全性和功能。</span><span class="sxs-lookup"><span data-stu-id="d2abf-111">This process provides security and features similar to those available in a private network.</span></span>  
  
 <span data-ttu-id="d2abf-112">有关设置 VPN 的详细信息，请参阅 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows 文档。</span><span class="sxs-lookup"><span data-stu-id="d2abf-112">For more information about setting up a VPN, see the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows documentation.</span></span>  
  
## <a name="web-synchronization-through-iis"></a><span data-ttu-id="d2abf-113">通过 IIS 的 Web 同步</span><span class="sxs-lookup"><span data-stu-id="d2abf-113">Web Synchronization Through IIS</span></span>  
 <span data-ttu-id="d2abf-114">合并复制的 Web 同步选项提供了用 HTTPS 协议复制数据的功能，这是一种通过防火墙复制数据的简便方法。</span><span class="sxs-lookup"><span data-stu-id="d2abf-114">The web synchronization option for merge replication provides the ability to replicate data using the HTTPS protocol, which can be a convenient approach to replicating data through a firewall.</span></span> <span data-ttu-id="d2abf-115">有关详细信息，请参阅[配置 Web 同步](../configure-web-synchronization.md)和 [Web 同步的安全体系结构](security-architecture-for-web-synchronization.md)。</span><span class="sxs-lookup"><span data-stu-id="d2abf-115">For more information, see [Configure Web Synchronization](../configure-web-synchronization.md) and [Security Architecture for Web Synchronization](security-architecture-for-web-synchronization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2abf-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d2abf-116">See Also</span></span>  
 <span data-ttu-id="d2abf-117">[Replication Security Best Practices](replication-security-best-practices.md) </span><span class="sxs-lookup"><span data-stu-id="d2abf-117">[Replication Security Best Practices](replication-security-best-practices.md) </span></span>  
 [<span data-ttu-id="d2abf-118">SQL Server 复制安全性</span><span class="sxs-lookup"><span data-stu-id="d2abf-118">SQL Server Replication Security</span></span>](view-and-modify-replication-security-settings.md)  
  
  
