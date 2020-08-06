---
title: 客户端协议-TCP 和 IP 属性 (协议选项卡) |Microsoft Docs
description: 了解如何在 Microsoft SQL Server Configuration Manager 中指定 TCP/IP 选项，如 keep-alive 参数和默认端口号。
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- TCP/IP [SQL Server], client protocols
- client protocols [SQL Server]
ms.assetid: d04f1bce-069c-4a02-b561-c87c3282be36
author: rothja
ms.author: jroth
ms.openlocfilehash: dfcf0348dc863970384a40cc9e773481adeedb35
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692065"
---
# <a name="client-protocols---tcp-and-ip-properties-protocol-tab"></a><span data-ttu-id="28dff-103">客户端协议 - TCP 和 IP 属性（“协议”选项卡）</span><span class="sxs-lookup"><span data-stu-id="28dff-103">Client Protocols - TCP and IP Properties (Protocol Tab)</span></span>
  <span data-ttu-id="28dff-104">在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器中，可以使用“TCP/IP 属性”\*\*\*\* 对话框的“协议”\*\*\*\* 选项卡查看或指定下列选项。</span><span class="sxs-lookup"><span data-stu-id="28dff-104">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, use the **Protocol** tab on the **TCP/IP Properties** dialog box to view or specify the following options.</span></span> <span data-ttu-id="28dff-105">若要连接到另一个端口，可以在 **“默认端口”** 框中键入端口号。</span><span class="sxs-lookup"><span data-stu-id="28dff-105">To connect to a different port, type the port number in the **Default Port** box.</span></span> <span data-ttu-id="28dff-106">有关连接字符串的详细信息，请参阅 [使用 TCP IP 创建有效的连接字符串](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md)。</span><span class="sxs-lookup"><span data-stu-id="28dff-106">For more information about connection strings, see [Creating a Valid Connection String Using TCP IP](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="28dff-107">选项</span><span class="sxs-lookup"><span data-stu-id="28dff-107">Options</span></span>  
 <span data-ttu-id="28dff-108">**“默认端口”**</span><span class="sxs-lookup"><span data-stu-id="28dff-108">**Default Port**</span></span>  
 <span data-ttu-id="28dff-109">指定 TCP/IP Net-library 在尝试连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的目标实例时将使用的端口。</span><span class="sxs-lookup"><span data-stu-id="28dff-109">Specifies the port that the TCP/IP Net-library will use to attempt to connect to the target instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="28dff-110">默认值端口为 1433。</span><span class="sxs-lookup"><span data-stu-id="28dff-110">The default value port is 1433.</span></span>  
  
 <span data-ttu-id="28dff-111">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的默认实例时，客户端将使用此值。</span><span class="sxs-lookup"><span data-stu-id="28dff-111">When connecting to a default instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)], the client uses this value.</span></span> <span data-ttu-id="28dff-112">如果已经将默认实例配置为侦听另一个端口，则要将此值更改为该端口号。</span><span class="sxs-lookup"><span data-stu-id="28dff-112">If a default instance has been configured to listen on a different port, change this value to that port number.</span></span>  
  
 <span data-ttu-id="28dff-113">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的命名实例时，客户端将尝试从在服务器上运行的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 服务获取端口号。</span><span class="sxs-lookup"><span data-stu-id="28dff-113">When connecting to a named instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)], the client will attempt to obtain the port number from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser Service running on the server computer.</span></span> <span data-ttu-id="28dff-114">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 服务没有运行，则必须通过此设置或作为连接字符串的一部分提供端口号。</span><span class="sxs-lookup"><span data-stu-id="28dff-114">If the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser Service is not running, the port number must be provided through this setting, or as part of the connection string.</span></span>  
  
 <span data-ttu-id="28dff-115">**已启用**</span><span class="sxs-lookup"><span data-stu-id="28dff-115">**Enabled**</span></span>  
 <span data-ttu-id="28dff-116">可能的值为**Yes**和**No**。</span><span class="sxs-lookup"><span data-stu-id="28dff-116">Possible values are **Yes** and **No**.</span></span>  
  
 <span data-ttu-id="28dff-117">**保持活动状态**</span><span class="sxs-lookup"><span data-stu-id="28dff-117">**Keep Alive**</span></span>  
 <span data-ttu-id="28dff-118">此参数（毫秒）控制 TCP 通过发送 **KEEPALIVE** 包尝试验证空闲连接是否仍保持原样的频率。</span><span class="sxs-lookup"><span data-stu-id="28dff-118">This parameter (in milliseconds) controls how often TCP attempts to verify that an idle connection is still intact by sending a **KEEPALIVE** packet.</span></span> <span data-ttu-id="28dff-119">默认值为 30000 毫秒。</span><span class="sxs-lookup"><span data-stu-id="28dff-119">The default is 30000 milliseconds.</span></span>  
  
 <span data-ttu-id="28dff-120">**保持活动状态的间隔**</span><span class="sxs-lookup"><span data-stu-id="28dff-120">**Keep Alive Interval**</span></span>  
 <span data-ttu-id="28dff-121">此参数（毫秒）确定重新传输 **KEEPALIVE** 直到接收到响应的间隔。</span><span class="sxs-lookup"><span data-stu-id="28dff-121">This parameter (in milliseconds) determines the interval separating **KEEPALIVE** retransmissions until a response is received.</span></span> <span data-ttu-id="28dff-122">默认值为 1000 毫秒。</span><span class="sxs-lookup"><span data-stu-id="28dff-122">The default is 1000 milliseconds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28dff-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="28dff-123">See Also</span></span>  
 <span data-ttu-id="28dff-124">[选择网络协议](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md) </span><span class="sxs-lookup"><span data-stu-id="28dff-124">[Choosing a Network Protocol](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md) </span></span>  
 <span data-ttu-id="28dff-125">[新别名 &#40;别名选项卡&#41;](../../../2014/tools/configuration-manager/new-alias-alias-tab.md) </span><span class="sxs-lookup"><span data-stu-id="28dff-125">[New Alias &#40;Alias Tab&#41;](../../../2014/tools/configuration-manager/new-alias-alias-tab.md) </span></span>  
 [<span data-ttu-id="28dff-126"><别名>属性（“别名”选项卡）</span><span class="sxs-lookup"><span data-stu-id="28dff-126">&#60;Alias&#62; Properties &#40;Alias Tab&#41;</span></span>](../../../2014/tools/configuration-manager/alias-properties-alias-tab.md)  
  
  
