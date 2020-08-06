---
title: Web 同步的拓扑 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Web synchronization, topologies
- IIS server configuration [SQL Server replication]
ms.assetid: 59444faf-bcb6-4421-a3df-8715753e453b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5e28ca5a222e2286d154c16ef41d3147dc56e25a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587341"
---
# <a name="topologies-for-web-synchronization"></a><span data-ttu-id="3a924-102">Topologies for Web Synchronization</span><span class="sxs-lookup"><span data-stu-id="3a924-102">Topologies for Web Synchronization</span></span>
  <span data-ttu-id="3a924-103">可以从多种 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Web 同步复制拓扑中进行选择。</span><span class="sxs-lookup"><span data-stu-id="3a924-103">You can choose from a variety of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Web synchronization replication topologies.</span></span> <span data-ttu-id="3a924-104">配置 Web 同步的常用方法包括：</span><span class="sxs-lookup"><span data-stu-id="3a924-104">Common ways to configure Web synchronization include:</span></span>  
  
-   <span data-ttu-id="3a924-105">单个服务器</span><span class="sxs-lookup"><span data-stu-id="3a924-105">Single server</span></span>  
  
-   <span data-ttu-id="3a924-106">两台服务器</span><span class="sxs-lookup"><span data-stu-id="3a924-106">Two servers</span></span>  
  
-   <span data-ttu-id="3a924-107">多个 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet 信息服务 (IIS) 系统和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 重新发布</span><span class="sxs-lookup"><span data-stu-id="3a924-107">Multiple [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Information Services (IIS) systems and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] republishing</span></span>  
  
 <span data-ttu-id="3a924-108">有关配置 Web 同步的信息，请参阅[配置 Web 同步](configure-web-synchronization.md)。</span><span class="sxs-lookup"><span data-stu-id="3a924-108">For information about configuring Web synchronization, see [Configure Web Synchronization](configure-web-synchronization.md).</span></span>  
  
## <a name="single-server"></a><span data-ttu-id="3a924-109">单台服务器</span><span class="sxs-lookup"><span data-stu-id="3a924-109">Single Server</span></span>  
 <span data-ttu-id="3a924-110">在这种最简单的拓扑中，IIS、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 发布服务器和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 分发服务器都驻留在一台服务器中。</span><span class="sxs-lookup"><span data-stu-id="3a924-110">In the simplest topology, IIS, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Publisher, and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributor all reside on a single server.</span></span> <span data-ttu-id="3a924-111">通过连接到发布服务器中的 IIS 来同步订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="3a924-111">Subscribers synchronize by connecting to IIS on the Publisher.</span></span> <span data-ttu-id="3a924-112">发布服务器可位于防火墙后。</span><span class="sxs-lookup"><span data-stu-id="3a924-112">The Publisher can be located behind a firewall.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3a924-113">建议此配置仅用于 Intranet 方案。</span><span class="sxs-lookup"><span data-stu-id="3a924-113">This configuration is recommended only for intranet scenarios.</span></span> <span data-ttu-id="3a924-114">对于其他方案，建议 IIS 服务器和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 发布服务器/分发服务器位于不同的计算机上。</span><span class="sxs-lookup"><span data-stu-id="3a924-114">For other scenarios, it is recommended that the IIS server and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Publisher/Distributor be on separate computers.</span></span>  
  
 <span data-ttu-id="3a924-115">![使用单个服务器的 Web 同步](media/web-sync02.gif "使用单个服务器的 Web 同步")</span><span class="sxs-lookup"><span data-stu-id="3a924-115">![Web synchronization with a single server](media/web-sync02.gif "Web synchronization with a single server")</span></span>  
  
## <a name="two-servers"></a><span data-ttu-id="3a924-116">两台服务器</span><span class="sxs-lookup"><span data-stu-id="3a924-116">Two Servers</span></span>  
 <span data-ttu-id="3a924-117">可以将 IIS 放置在一台服务器中，而将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 发布服务器和分发服务器配置在另一台服务器中。</span><span class="sxs-lookup"><span data-stu-id="3a924-117">You can place IIS on one server and configure the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Publisher and Distributor on another server.</span></span> <span data-ttu-id="3a924-118">运行 IIS 的服务器可以用防火墙与 Internet 隔离。</span><span class="sxs-lookup"><span data-stu-id="3a924-118">The server running IIS can be isolated from the Internet by a firewall.</span></span> <span data-ttu-id="3a924-119">通过连接到 IIS 来同步订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="3a924-119">Subscribers synchronize by connecting to IIS.</span></span>  
  
 <span data-ttu-id="3a924-120">![使用两个服务器的 Web 同步](media/web-sync03.gif "使用两个服务器的 Web 同步")</span><span class="sxs-lookup"><span data-stu-id="3a924-120">![Web synchronization with two servers](media/web-sync03.gif "Web synchronization with two servers")</span></span>  
  
## <a name="multiple-iis-systems-and-sql-server-republishing"></a><span data-ttu-id="3a924-121">多个 IIS 系统和 SQL Server 重新发布</span><span class="sxs-lookup"><span data-stu-id="3a924-121">Multiple IIS Systems and SQL Server Republishing</span></span>  
 <span data-ttu-id="3a924-122">如果需要支持很多同时进行同步的订阅服务器，您可以将此工作分配于多台运行 IIS 的计算机。</span><span class="sxs-lookup"><span data-stu-id="3a924-122">If you need to support very large numbers of Subscribers that synchronize at the same time, you can partition the work across multiple computers running IIS.</span></span>  
  
 <span data-ttu-id="3a924-123">![使用多个 IIS 服务器的 Web 同步](media/web-sync04.gif "使用多个 IIS 服务器的 Web 同步")</span><span class="sxs-lookup"><span data-stu-id="3a924-123">![Web synchronization with multiple IIS servers](media/web-sync04.gif "Web synchronization with multiple IIS servers")</span></span>  
  
 <span data-ttu-id="3a924-124">如果运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的计算机上需要进一步的负荷平衡，您可以在多台计算机上创建重新发布层次结构。</span><span class="sxs-lookup"><span data-stu-id="3a924-124">If further load balancing is required on the computer running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you can create a republishing hierarchy on multiple computers.</span></span> <span data-ttu-id="3a924-125">顶级发布服务器将数据发布到订阅服务器，这些订阅服务器反过来重新发布来自订阅服务器的数据和负荷平衡请求。</span><span class="sxs-lookup"><span data-stu-id="3a924-125">The top-level Publisher publishes data to Subscribers, which in turn republish the data, load balancing requests from the Subscribers.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3a924-126">订阅服务器只能与特定发布服务器进行同步。</span><span class="sxs-lookup"><span data-stu-id="3a924-126">Subscribers can only synchronize with a specific Publisher.</span></span> <span data-ttu-id="3a924-127">例如，在重新发布服务器 A 不可用时，针对 A 的订阅服务器不能与重新发布服务器 B 进行同步。</span><span class="sxs-lookup"><span data-stu-id="3a924-127">For example, a Subscriber to republisher A cannot synchronize with republisher B when A is not available.</span></span>  
  
 <span data-ttu-id="3a924-128">![使用重新发布的 Web 同步](media/web-sync05.gif "使用重新发布的 Web 同步")</span><span class="sxs-lookup"><span data-stu-id="3a924-128">![Web synchronization with republishing](media/web-sync05.gif "Web synchronization with republishing")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a924-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3a924-129">See Also</span></span>  
 <span data-ttu-id="3a924-130">[Configure Web Synchronization](configure-web-synchronization.md) </span><span class="sxs-lookup"><span data-stu-id="3a924-130">[Configure Web Synchronization](configure-web-synchronization.md) </span></span>  
 [<span data-ttu-id="3a924-131">合并复制的 Web 同步</span><span class="sxs-lookup"><span data-stu-id="3a924-131">Web Synchronization for Merge Replication</span></span>](web-synchronization-for-merge-replication.md)  
  
  
