---
title: 合并复制的 Web 同步 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication synchronization [SQL Server replication]
- Internet [SQL Server replication], synchronization
- synchronization [SQL Server replication], Web Synchronization
- Web publishing [SQL Server replication], synchronization
- Web synchronization, about
- Web synchronization
ms.assetid: 84785aba-b2c1-4821-9e9d-a363c73dcb37
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ef7bf5a6f77d593a90508a0b69d02f8c0db04407
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590170"
---
# <a name="web-synchronization-for-merge-replication"></a><span data-ttu-id="14964-102">合并复制的 Web 同步</span><span class="sxs-lookup"><span data-stu-id="14964-102">Web Synchronization for Merge Replication</span></span>
  <span data-ttu-id="14964-103">对过进行合并复制的 Web 同步，可以使用 HTTPS 协议复制数据，这对于以下情况非常有用：</span><span class="sxs-lookup"><span data-stu-id="14964-103">Web synchronization for merge replication lets you replicate data by using the HTTPS protocol, and is useful for the following scenarios:</span></span>

-   <span data-ttu-id="14964-104">通过 Internet 同步移动用户数据。</span><span class="sxs-lookup"><span data-stu-id="14964-104">Synchronizing data from mobile users over the Internet.</span></span>

-   <span data-ttu-id="14964-105">跨企业防火墙在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库之间同步数据。</span><span class="sxs-lookup"><span data-stu-id="14964-105">Synchronizing data between [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases across a corporate firewall.</span></span>

 <span data-ttu-id="14964-106">例如，正在出差的销售代表可以使用 Web 同步。</span><span class="sxs-lookup"><span data-stu-id="14964-106">For example, a traveling sales representative can use Web synchronization.</span></span> <span data-ttu-id="14964-107">[!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)]公司的销售代表们要去所在区域的不同商店和供应商那里出差。</span><span class="sxs-lookup"><span data-stu-id="14964-107">The company, [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)], has sales representatives that travel to various stores and suppliers throughout their regions.</span></span> <span data-ttu-id="14964-108">如果出差时间较长，销售代表们会住在宾馆里，这就需要一种方便的方法，能够在每天结束时上载销售数据，下载产品更新信息。</span><span class="sxs-lookup"><span data-stu-id="14964-108">On longer trips the representatives stay in hotels and need a convenient way to upload sales data and download any product updates at the end of each day.</span></span>

 <span data-ttu-id="14964-109">因此， [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] 的 IT 部门为每台便携式计算机配置了 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，并启用了合并复制以便使用 Web 同步。</span><span class="sxs-lookup"><span data-stu-id="14964-109">The [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] IT department has configured each portable computer with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and has enabled merge replication to use Web synchronization.</span></span> <span data-ttu-id="14964-110">每台便携式计算机上的合并代理都有一个 Internet URL，它指向运行 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet 信息服务 (IIS) 的计算机上所安装的复制组件。</span><span class="sxs-lookup"><span data-stu-id="14964-110">The Merge Agent on each portable computer has an Internet URL that points to the replication components that are installed on a computer that is running [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Information Services (IIS).</span></span> <span data-ttu-id="14964-111">这些组件用于使订阅服务器与发布服务器同步。</span><span class="sxs-lookup"><span data-stu-id="14964-111">These components synchronize the Subscriber with the Publisher.</span></span> <span data-ttu-id="14964-112">现在，每个代表能够通过任何可用的 Internet 连接进行连接而无须使用远程拨号，能够上载和下载合适的数据。</span><span class="sxs-lookup"><span data-stu-id="14964-112">Each representative can now connect through any available Internet connection without using a remote dial-up connection, and can upload and download the appropriate data.</span></span> <span data-ttu-id="14964-113">Internet 连接使用安全套接字层 (SSL)，所以不需要虚拟专用网络 (VPN)。</span><span class="sxs-lookup"><span data-stu-id="14964-113">The Internet connection uses Secure Sockets Layer (SSL); therefore, a virtual private network (VPN) is not required.</span></span>

 <span data-ttu-id="14964-114">有关如何配置 Web 同步所需的组件的信息，请参阅[配置 Web 同步](configure-web-synchronization.md)、[配置 IIS 以实现 Web 同步](configure-iis-for-web-synchronization.md)和[配置 IIS 7 以实现 Web 同步](configure-iis-7-for-web-synchronization.md)。</span><span class="sxs-lookup"><span data-stu-id="14964-114">For information about how to configure the components that are required for Web synchronization, see [Configure Web Synchronization](configure-web-synchronization.md), [Configure IIS for Web Synchronization](configure-iis-for-web-synchronization.md), and [Configure IIS 7 for Web Synchronization](configure-iis-7-for-web-synchronization.md).</span></span>

> [!NOTE]
>  <span data-ttu-id="14964-115">Web 同步的设计目的是为了与便携式计算机、手持设备以及其他客户端同步数据，</span><span class="sxs-lookup"><span data-stu-id="14964-115">Web synchronization is designed for synchronizing data with portable computers, handheld devices, and other clients.</span></span> <span data-ttu-id="14964-116">Web 同步并不适于大容量服务器对服务器应用程序。</span><span class="sxs-lookup"><span data-stu-id="14964-116">Web synchronization is not intended for high-volume server-to-server applications.</span></span>

## <a name="overview-of-how-web-synchronization-works"></a><span data-ttu-id="14964-117">Web 同步的工作机制概述</span><span class="sxs-lookup"><span data-stu-id="14964-117">Overview of How Web Synchronization Works</span></span>
 <span data-ttu-id="14964-118">使用 Web 同步时，借助 HTTPS 协议，将订阅服务器上的更新按 XML 消息打包并发送给运行 IIS 服务器的计算机。</span><span class="sxs-lookup"><span data-stu-id="14964-118">When Web synchronization is used, updates at the Subscriber are packaged and sent as an XML message to the computer that is running IIS by using the HTTPS protocol.</span></span> <span data-ttu-id="14964-119">然后，运行 IIS 的计算机将命令以二进制格式发送给发布服务器（通常使用 TCP/IP）。</span><span class="sxs-lookup"><span data-stu-id="14964-119">The computer that is running IIS then sends the commands to the Publisher in a binary format, typically by using TCP/IP.</span></span> <span data-ttu-id="14964-120">发布服务器上的更新将被发送给运行 IIS 的计算机，然后按 XML 消息打包，以便传递给订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="14964-120">Updates at the Publisher are sent to the computer that is running IIS and then packaged as an XML message for delivery to the Subscriber.</span></span>

 <span data-ttu-id="14964-121">下图显示了合并复制的 Web 同步中涉及的一些组件。</span><span class="sxs-lookup"><span data-stu-id="14964-121">The following illustration shows some of the components that are involved in Web synchronization for merge replication.</span></span>

 <span data-ttu-id="14964-122">![Web 同步组件和数据流](media/web-sync01.gif "Web 同步组件和数据流")</span><span class="sxs-lookup"><span data-stu-id="14964-122">![Web synchronization components and data flow](media/web-sync01.gif "Web synchronization components and data flow")</span></span>

 <span data-ttu-id="14964-123">Web 同步选项仅适用于请求订阅；所以，合并代理始终在订阅服务器上运行。</span><span class="sxs-lookup"><span data-stu-id="14964-123">Web synchronization is an option only for pull subscriptions; therefore, a Merge Agent will always run on the Subscriber.</span></span> <span data-ttu-id="14964-124">此合并代理可以是标准合并代理、合并代理 ActiveX 控件或者通过复制管理对象 (RMO) 提供同步的应用程序。</span><span class="sxs-lookup"><span data-stu-id="14964-124">This Merge Agent can be the standard Merge Agent, the Merge Agent ActiveX control, or an application that provides synchronization through Replication Management Objects (RMO).</span></span> <span data-ttu-id="14964-125">若要指定运行 IIS 的计算机的位置，请使用合并代理的 **-InternetUrl**参数。</span><span class="sxs-lookup"><span data-stu-id="14964-125">To specify the location of the computer that is running IIS, use the **-InternetUrl** parameter for the Merge Agent.</span></span>

 <span data-ttu-id="14964-126">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 复制侦听器 (Replisapi.dll) 在运行 IIS 的计算机上配置，负责处理从发布服务器和订阅服务器发送给服务器的消息。</span><span class="sxs-lookup"><span data-stu-id="14964-126">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Replication Listener (Replisapi.dll) is configured on the computer that is running IIS and is responsible for handling messages that are sent to the server from the Publisher and Subscribers.</span></span> <span data-ttu-id="14964-127">拓扑中的每个节点都使用合并复制协调器 (Replrec.dll) 处理 XML 数据流。</span><span class="sxs-lookup"><span data-stu-id="14964-127">Each node in the topology handles the XML data stream by using the Merge Replication Reconciler (Replrec.dll).</span></span>

 <span data-ttu-id="14964-128">对于所有参与 Web 同步的计算机，均需要[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="14964-128">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] or a later version is required for all computers that participate in Web synchronization.</span></span>

### <a name="synchronization-process"></a><span data-ttu-id="14964-129">同步过程</span><span class="sxs-lookup"><span data-stu-id="14964-129">Synchronization Process</span></span>
 <span data-ttu-id="14964-130">同步过程包括以下步骤：</span><span class="sxs-lookup"><span data-stu-id="14964-130">The following steps occur during synchronization:</span></span>

1.  <span data-ttu-id="14964-131">合并代理在订阅服务器上启动。</span><span class="sxs-lookup"><span data-stu-id="14964-131">The Merge Agent is started at the Subscriber.</span></span> <span data-ttu-id="14964-132">该代理将执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="14964-132">The agent does the following:</span></span>

    1.  <span data-ttu-id="14964-133">与订阅数据库建立 SQL 连接。</span><span class="sxs-lookup"><span data-stu-id="14964-133">Makes an SQL connection to the subscription database.</span></span>

    2.  <span data-ttu-id="14964-134">从数据库中提取任何更改。</span><span class="sxs-lookup"><span data-stu-id="14964-134">Extracts any changes from the database.</span></span>

    3.  <span data-ttu-id="14964-135">向运行 IIS 的计算机发出 HTTPS 请求。</span><span class="sxs-lookup"><span data-stu-id="14964-135">Makes an HTTPS request to the computer that is running IIS.</span></span>

    4.  <span data-ttu-id="14964-136">将数据更改作为 XML 消息上载。</span><span class="sxs-lookup"><span data-stu-id="14964-136">Uploads data changes as an XML message.</span></span>

2.  <span data-ttu-id="14964-137">运行 IIS 的计算机中所承载的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 复制侦听器和合并复制协调器将执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="14964-137">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Replication Listener and Merge Replication Reconciler that are hosted on the computer that is running IIS do the following:</span></span>

    1.  <span data-ttu-id="14964-138">对 HTTPS 请求做出响应。</span><span class="sxs-lookup"><span data-stu-id="14964-138">Respond to the HTTPS request.</span></span>

    2.  <span data-ttu-id="14964-139">与发布数据库建立 SQL 连接。</span><span class="sxs-lookup"><span data-stu-id="14964-139">Make an SQL connection to the publication database.</span></span>

    3.  <span data-ttu-id="14964-140">将上载更改应用于发布数据库。</span><span class="sxs-lookup"><span data-stu-id="14964-140">Apply the upload changes to the publication database.</span></span>

    4.  <span data-ttu-id="14964-141">为订阅服务器提取下载更改。</span><span class="sxs-lookup"><span data-stu-id="14964-141">Extract the download changes for the Subscriber.</span></span>

    5.  <span data-ttu-id="14964-142">将 HTTPS 响应发送回合并代理。</span><span class="sxs-lookup"><span data-stu-id="14964-142">Send an HTTPS response back to the Merge Agent.</span></span>

3.  <span data-ttu-id="14964-143">然后，订阅服务器上的合并代理将接受 HTTPS 响应，并将下载更改应用于订阅数据库。</span><span class="sxs-lookup"><span data-stu-id="14964-143">The Merge Agent at the Subscriber then accepts the HTTPS response and applies the download changes to the subscription database.</span></span>

## <a name="see-also"></a><span data-ttu-id="14964-144">另请参阅</span><span class="sxs-lookup"><span data-stu-id="14964-144">See Also</span></span>
 <span data-ttu-id="14964-145">[为 Web 同步](topologies-for-web-synchronization.md)[配置 web 同步](configure-web-synchronization.md)拓扑</span><span class="sxs-lookup"><span data-stu-id="14964-145">[Configure Web Synchronization](configure-web-synchronization.md) [Topologies for Web Synchronization](topologies-for-web-synchronization.md)</span></span>


