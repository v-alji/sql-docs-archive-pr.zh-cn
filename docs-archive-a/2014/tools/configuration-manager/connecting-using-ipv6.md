---
title: 使用 IPv6 进行连接 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- Internet Protocol
- IPv4
- IPv6
ms.assetid: 2669098c-f5f1-43da-aec6-e91003ac89f6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0f2ecd605f67446fade262cfe795f344dfb165c0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691451"
---
# <a name="connecting-using-ipv6"></a><span data-ttu-id="c3fd8-102">使用 IPv6 进行连接</span><span class="sxs-lookup"><span data-stu-id="c3fd8-102">Connecting Using IPv6</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="c3fd8-103">和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 完全支持 Internet 协议版本 4 (IPv4) 和 Internet 协议版本 6 (IPv6)。</span><span class="sxs-lookup"><span data-stu-id="c3fd8-103">and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client fully support both Internet Protocol version 4 (IPv4) and Internet Protocol version 6 (IPv6).</span></span> <span data-ttu-id="c3fd8-104">将 Windows 配置为使用 IPv6 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]时，各组件会自动识别 IPv6 的存在。</span><span class="sxs-lookup"><span data-stu-id="c3fd8-104">When Windows is configured with IPv6 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], components automatically recognize the existence of IPv6.</span></span> <span data-ttu-id="c3fd8-105">不必采用特殊的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置。</span><span class="sxs-lookup"><span data-stu-id="c3fd8-105">No special [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] configuration is necessary.</span></span>  
  
 <span data-ttu-id="c3fd8-106">支持包括但不限于下列各项：</span><span class="sxs-lookup"><span data-stu-id="c3fd8-106">Support includes but is not limited to the following:</span></span>  
  
-   <span data-ttu-id="c3fd8-107">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 和其他服务器组件可以同时侦听 IPv4 和 IPv6 地址。</span><span class="sxs-lookup"><span data-stu-id="c3fd8-107">The [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] and the other server components can listen on both IPv4 and IPv6 addresses at the same time.</span></span> <span data-ttu-id="c3fd8-108">如果同时存在 IPv4 和 IPv6，则可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器来配置 [!INCLUDE[ssDE](../../includes/ssde-md.md)] ，以便只侦听 IPv4 地址或只侦听 IPv6 地址。</span><span class="sxs-lookup"><span data-stu-id="c3fd8-108">When both IPv4 and IPv6 are present, you can use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager to configure the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to listen only on IPv4 addresses or only on IPv6 addresses.</span></span>  
  
-   <span data-ttu-id="c3fd8-109">根据 IPv4 地址对运行于支持 IPv4 和 IPv6 的计算机上的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 服务进行查询时，该服务会对 IPv4 地址及其列表中的第一个 IPv4 TCP 端口做出响应。</span><span class="sxs-lookup"><span data-stu-id="c3fd8-109">When the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service running on a machine that supports both IPv4 and IPv6 is queried on an IPv4 address, it responds with an IPv4 address and the first IPv4 TCP port in its list.</span></span> <span data-ttu-id="c3fd8-110">根据 IPv6 地址进行查询时，该服务会对 IPv6 地址及其列表中的第一个 IPv6 TCP 端口做出响应。</span><span class="sxs-lookup"><span data-stu-id="c3fd8-110">When queried on an IPv6 address, it responds with an IPv6 address and the first IPv6 TCP port in its list.</span></span> <span data-ttu-id="c3fd8-111">为了避免出现不一致，建议将 IPv4 和 IPv6 侦听器配置为侦听相同的端口。</span><span class="sxs-lookup"><span data-stu-id="c3fd8-111">To avoid inconsistency, we recommend that the IPv4 and IPv6 listeners be configured to listen to the same port.</span></span>  
  
-   <span data-ttu-id="c3fd8-112">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器等工具都接受 IPv4 和 IPv6 格式的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="c3fd8-112">Tools such as [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager accept both IPv4 and IPv6 formats for IP addresses.</span></span> <span data-ttu-id="c3fd8-113">在大多数情况下，如果 \<*computer_name*> \\ < 使用服务器主机名或完全限定的域名 (FQDN) 指定*instance_name*>，则无需修改连接字符串。</span><span class="sxs-lookup"><span data-stu-id="c3fd8-113">In most cases, the connection string does not need to be modified if the \<*computer_name*>\\<*instance_name*> is specified using server hostname or fully qualified domain name (FQDN).</span></span> <span data-ttu-id="c3fd8-114">如果服务器安装有 IPv4 和 IPv6，则其主机名或 FQDN 将会解析到多个 IP 地址，其中至少包括一个 IPv4 地址和多个 IPv6 地址。</span><span class="sxs-lookup"><span data-stu-id="c3fd8-114">If the server computer has both IPv4 and IPv6, its hostname or FQDN will be resolved into multiple IP addresses, including at least one IPv4 address and multiple IPv6 addresses.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="c3fd8-115">Native Client 会按照从 TCP/IP 接收这些 IP 地址时的顺序尝试使用它们来建立连接，并使用第一个成功建立的连接。</span><span class="sxs-lookup"><span data-stu-id="c3fd8-115">Native Client attempts to establish connections using these IP addresses in the order received from TCP/IP and uses the first connection that succeeds.</span></span> <span data-ttu-id="c3fd8-116">由于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 无法预测顺序，因此，应将顺序视为随机顺序。</span><span class="sxs-lookup"><span data-stu-id="c3fd8-116">Because the order cannot be predicted by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, this should be regarded as random order.</span></span> <span data-ttu-id="c3fd8-117">如果同时存在 IPv4 地址和 IPv6 地址，则首先尝试使用 IPv4 地址。</span><span class="sxs-lookup"><span data-stu-id="c3fd8-117">IPv4 addresses are attempted first if both IPv4 and IPv6 addresses are present.</span></span> <span data-ttu-id="c3fd8-118">这一逻辑对于 ODBC、OLE DB 或 ADO.NET 的用户是透明的。</span><span class="sxs-lookup"><span data-stu-id="c3fd8-118">This logic is transparent to the users of ODBC, OLE DB, or ADO.NET.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c3fd8-119">如果 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 未侦听 IPv4，则尝试进行 IPv4 连接之后，必须等待超时期限过后再尝试使用 IPv6 地址。</span><span class="sxs-lookup"><span data-stu-id="c3fd8-119">If the [!INCLUDE[ssDE](../../includes/ssde-md.md)] is not listening on IPv4, the attempted IPv4 connection must wait for the time-out period before the IPv6 address is attempted.</span></span> <span data-ttu-id="c3fd8-120">为了避免出现这种情况，请直接连接到 IPv6 IP 地址或使用 IPv6 地址配置客户端的别名。</span><span class="sxs-lookup"><span data-stu-id="c3fd8-120">To avoid this, connect directly to the IPv6 IP address or configure an alias on the client with the IPv6 address.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3fd8-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c3fd8-121">See Also</span></span>  
 [<span data-ttu-id="c3fd8-122">SQL Server 配置管理器</span><span class="sxs-lookup"><span data-stu-id="c3fd8-122">SQL Server Configuration Manager</span></span>](../../relational-databases/sql-server-configuration-manager.md)  
  
  
