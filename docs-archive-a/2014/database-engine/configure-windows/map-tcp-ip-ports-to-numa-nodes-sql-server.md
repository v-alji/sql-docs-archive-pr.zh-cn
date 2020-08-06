---
title: 将 TCP IP 端口映射到 NUMA 节点 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- NUMA
- memory [SQL Server], NUMA
- affinity NUMA
- ports [SQL Server], working with NUMA
- CPU [SQL Server], NUMA support
- NUMA, How to map a port to a NUMA node
- NUMA affinity
- TCP/IP [SQL Server], NUMA support
- non-uniform memory access
ms.assetid: 07727642-0266-4cbc-8c55-3c367e4458ca
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: cf4a1bd7e02719d3884011ad3faa20a1ccc6466a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87683056"
---
# <a name="map-tcp-ip-ports-to-numa-nodes-sql-server"></a><span data-ttu-id="7d29a-102">将 TCP IP 端口映射到 NUMA 节点 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="7d29a-102">Map TCP IP Ports to NUMA Nodes (SQL Server)</span></span>
  <span data-ttu-id="7d29a-103">本主题说明如何使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器来将 TCP/IP 端口映射到非一致性内存访问 (NUMA) 节点。</span><span class="sxs-lookup"><span data-stu-id="7d29a-103">This topic describes how to map TCP/IP ports to non-uniform memory access (NUMA) nodes by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="7d29a-104">启动时， [!INCLUDE[ssDE](../../includes/ssde-md.md)] 会将节点信息写入错误日志中。</span><span class="sxs-lookup"><span data-stu-id="7d29a-104">On startup, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] writes the node information to the error log.</span></span>  
  
 <span data-ttu-id="7d29a-105">若要确定要使用的节点编号，请参阅错误日志或 **sys.dm_os_schedulers** 视图中的节点信息。</span><span class="sxs-lookup"><span data-stu-id="7d29a-105">To determine the node number of the node you want to use, either read the node information from the error log, or from the **sys.dm_os_schedulers** view.</span></span> <span data-ttu-id="7d29a-106">若要将 TCP/IP 地址和端口设置到一个或多个节点，请在端口号后用括号追加一个节点标识位图（关联掩码）。</span><span class="sxs-lookup"><span data-stu-id="7d29a-106">To set a TCP/IP address and port to single or multiple nodes, append a node identification bitmap (an affinity mask) in brackets after the port number.</span></span> <span data-ttu-id="7d29a-107">可以按十进制格式或十六进制格式指定节点。</span><span class="sxs-lookup"><span data-stu-id="7d29a-107">Nodes can be specified in either decimal or hexadecimal format.</span></span> <span data-ttu-id="7d29a-108">若要创建位图，请先从右到左且以零开头为节点编号，例如 76543210。</span><span class="sxs-lookup"><span data-stu-id="7d29a-108">To create the bitmap, first number the nodes from right to left starting with zero, as in 76543210.</span></span> <span data-ttu-id="7d29a-109">创建节点列表的二进制表示形式，要使用的节点用 1 表示，而不使用的节点用 0 表示。</span><span class="sxs-lookup"><span data-stu-id="7d29a-109">Create a binary representation of the node list, providing 1 for nodes you want to use, and 0 for nodes you do not want to use.</span></span> <span data-ttu-id="7d29a-110">例如，若要使用 0、2 和 5 NUMA 节点，请指定 00100101。</span><span class="sxs-lookup"><span data-stu-id="7d29a-110">For example, to use NUMA nodes 0, 2, and 5, specify 00100101.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7d29a-111">NUMA 节点编号</span><span class="sxs-lookup"><span data-stu-id="7d29a-111">NUMA node number</span></span>|<span data-ttu-id="7d29a-112">76543210</span><span class="sxs-lookup"><span data-stu-id="7d29a-112">76543210</span></span>|  
|<span data-ttu-id="7d29a-113">从右边开始数起的第 0、2 和 5 个掩码</span><span class="sxs-lookup"><span data-stu-id="7d29a-113">Mask for 0, 2, and 5 counting from right</span></span>|<span data-ttu-id="7d29a-114">00100101</span><span class="sxs-lookup"><span data-stu-id="7d29a-114">00100101</span></span>|  
  
 <span data-ttu-id="7d29a-115">将二进制表示形式 (00100101) 转换为十进制 `[37]`或十六进制 `[0x25]`。</span><span class="sxs-lookup"><span data-stu-id="7d29a-115">Convert the binary representation (00100101), into decimal `[37]`, or hexadecimal `[0x25]`.</span></span> <span data-ttu-id="7d29a-116">若要侦听所有节点，则不提供任何节点标识符。</span><span class="sxs-lookup"><span data-stu-id="7d29a-116">To listen on all nodes, provide no node identifier.</span></span>  
  
 <span data-ttu-id="7d29a-117">如果一个端口映射到多个 NUMA 节点，则 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以循环的方式将连接分配到各节点，而不会试图平衡节点之间的负载。</span><span class="sxs-lookup"><span data-stu-id="7d29a-117">If a port is mapped to more than one NUMA node, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] assigns connections to nodes in a round-robin fashion without attempting to balance load across the nodes.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7d29a-118">若要允许 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 侦听每个 IP 地址的多个 TCP 端口，请参阅 [将数据库引擎配置为侦听多个 TCP 端口](configure-the-database-engine-to-listen-on-multiple-tcp-ports.md)。</span><span class="sxs-lookup"><span data-stu-id="7d29a-118">To enable [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to listen on multiple TCP ports for each IP address, see [Configure the Database Engine to Listen on Multiple TCP Ports](configure-the-database-engine-to-listen-on-multiple-tcp-ports.md).</span></span>  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> <span data-ttu-id="7d29a-119">使用 SQL Server 配置管理器</span><span class="sxs-lookup"><span data-stu-id="7d29a-119">Using SQL Server Configuration Manager</span></span>  
  
#### <a name="to-map-a-tcpip-port-to-a-numa-node"></a><span data-ttu-id="7d29a-120">将 TCP/IP 端口映射到 NUMA 节点</span><span class="sxs-lookup"><span data-stu-id="7d29a-120">To map a TCP/IP port to a NUMA node</span></span>  
  
1.  <span data-ttu-id="7d29a-121">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器中，展开“SQL Server 网络配置”，然后单击“\<instance name> 的协议” 。</span><span class="sxs-lookup"><span data-stu-id="7d29a-121">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, expand **SQL Server Network Configuration**, and then click **Protocols for** *\<instance name>*.</span></span>  
  
2.  <span data-ttu-id="7d29a-122">在详细信息窗格中，双击“TCP/IP”。</span><span class="sxs-lookup"><span data-stu-id="7d29a-122">In the details pane, double-click **TCP/IP**.</span></span>  
  
3.  <span data-ttu-id="7d29a-123">在 **“IP 地址”** 选项卡（要配置的 IP 地址的相应部分）的 **“TCP 端口”** 框中，在端口号后面的方括号里添加 NUMA 节点标识符。</span><span class="sxs-lookup"><span data-stu-id="7d29a-123">On the **IP Addresses** tab, in the section corresponding to the IP address to configure, in the **TCP Port** box, add the NUMA node identifier in brackets after the port number.</span></span> <span data-ttu-id="7d29a-124">例如，对于 TCP 端口 1500 以及节点 0、2 和 5，请使用 `1500[37]` 或 `1500[0x25]`。</span><span class="sxs-lookup"><span data-stu-id="7d29a-124">For example, for TCP port 1500 and nodes 0, 2, and 5, use `1500[37]`, or `1500[0x25]`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d29a-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7d29a-125">See Also</span></span>  
 [<span data-ttu-id="7d29a-126">将 SQL Server 配置为使用软件 NUMA &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="7d29a-126">Configure SQL Server to Use Soft-NUMA &#40;SQL Server&#41;</span></span>](soft-numa-sql-server.md)  
  
  
