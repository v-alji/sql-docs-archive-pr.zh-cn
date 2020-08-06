---
title: TCP-IP 属性 (协议 "选项卡) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- TCP/IP [SQL Server], configuration options
ms.assetid: 007638fc-3a24-4460-adbe-545ded5d6f88
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1d5bc28faddae9a86a6636b56b907b57a2d8711a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577988"
---
# <a name="tcp---ip-properties-protocols-tab"></a><span data-ttu-id="fdfa7-102">TCP-IP 属性 (协议 "选项卡) </span><span class="sxs-lookup"><span data-stu-id="fdfa7-102">TCP - IP Properties (Protocols Tab)</span></span>
  <span data-ttu-id="fdfa7-103">使用“TCP/IP 属性”  对话框可以配置 TCP/IP 协议的选项。</span><span class="sxs-lookup"><span data-stu-id="fdfa7-103">Use the **TCP/IP Properties** dialog box to configure the options for the TCP/IP protocol.</span></span> <span data-ttu-id="fdfa7-104">在左窗格中单击 **TCP/IP** 以在详细信息窗格中显示单个 IP 地址配置。</span><span class="sxs-lookup"><span data-stu-id="fdfa7-104">Click **TCP/IP** in the left pane, to show individual IP address configurations in the details pane.</span></span>  
  
 <span data-ttu-id="fdfa7-105">必须重新启动 Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，更改才会生效。</span><span class="sxs-lookup"><span data-stu-id="fdfa7-105">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must be restarted before the changes take effect.</span></span>  
  
## <a name="options"></a><span data-ttu-id="fdfa7-106">选项</span><span class="sxs-lookup"><span data-stu-id="fdfa7-106">Options</span></span>  
 <span data-ttu-id="fdfa7-107">**已启用**</span><span class="sxs-lookup"><span data-stu-id="fdfa7-107">**Enabled**</span></span>  
 <span data-ttu-id="fdfa7-108">可能的值为“是”  和“否”  。</span><span class="sxs-lookup"><span data-stu-id="fdfa7-108">Possible values are **Yes** and **No**.</span></span>  
  
 <span data-ttu-id="fdfa7-109">**Keep Alive**</span><span class="sxs-lookup"><span data-stu-id="fdfa7-109">**Keep Alive**</span></span>  
 <span data-ttu-id="fdfa7-110">指定传输保持活动状态的数据包的时间间隔（毫秒），以检查位于连接远端的计算机是否仍可用。</span><span class="sxs-lookup"><span data-stu-id="fdfa7-110">Specify the interval (milliseconds) in which keep-alive packets are transmitted to verify that the computer at the remote end of a connection is still available.</span></span>  
  
 <span data-ttu-id="fdfa7-111">**Listen All**</span><span class="sxs-lookup"><span data-stu-id="fdfa7-111">**Listen All**</span></span>  
 <span data-ttu-id="fdfa7-112">指定 SQL Server 是否侦听所有绑定到计算机网卡的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="fdfa7-112">Specify whether SQL Server will listen on all the IP addresses that are bound to network cards on the computer.</span></span> <span data-ttu-id="fdfa7-113">如果设置为“否”  ，则使用每个 IP 地址的各自属性对话框分别对每个 IP 地址进行配置。</span><span class="sxs-lookup"><span data-stu-id="fdfa7-113">If set to **No**, configure each IP address separately using the properties dialog box for each IP address.</span></span> <span data-ttu-id="fdfa7-114">如果设置为“是”  ，则 **IPAll** 属性框的设置将应用到所有的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="fdfa7-114">If set to **Yes**, the settings of the **IPAll** properties box will apply to all IP addresses.</span></span> <span data-ttu-id="fdfa7-115">默认值为“是”  。</span><span class="sxs-lookup"><span data-stu-id="fdfa7-115">Default value is **Yes**.</span></span>  
  
 <span data-ttu-id="fdfa7-116">**No Delay**</span><span class="sxs-lookup"><span data-stu-id="fdfa7-116">**No Delay**</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="fdfa7-117">不会实施对此属性的更改。</span><span class="sxs-lookup"><span data-stu-id="fdfa7-117">does not implement changes to this property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdfa7-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fdfa7-118">See Also</span></span>  
 <span data-ttu-id="fdfa7-119">[选择网络协议](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md) </span><span class="sxs-lookup"><span data-stu-id="fdfa7-119">[Choosing a Network Protocol](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md) </span></span>  
 [<span data-ttu-id="fdfa7-120">使用 TCP IP 创建有效的连接字符串</span><span class="sxs-lookup"><span data-stu-id="fdfa7-120">Creating a Valid Connection String Using TCP IP</span></span>](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md)  
  
  
