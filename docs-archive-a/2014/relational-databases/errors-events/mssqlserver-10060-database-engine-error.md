---
title: MSSQLSERVER_10060 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "10060"
helpviewer_keywords:
- 10060 (Database Engine error)
ms.assetid: 28c21277-cad8-406c-a955-07933a56982a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d634cfb06381fb916ef2e421e0677e76edb9ae02
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692430"
---
# <a name="mssqlserver_10060"></a><span data-ttu-id="101fe-102">MSSQLSERVER_10060</span><span class="sxs-lookup"><span data-stu-id="101fe-102">MSSQLSERVER_10060</span></span>
    
## <a name="details"></a><span data-ttu-id="101fe-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="101fe-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="101fe-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="101fe-104">Product Name</span></span>|<span data-ttu-id="101fe-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="101fe-105">SQL Server</span></span>|  
|<span data-ttu-id="101fe-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="101fe-106">Event ID</span></span>|<span data-ttu-id="101fe-107">10060</span><span class="sxs-lookup"><span data-stu-id="101fe-107">10060</span></span>|  
|<span data-ttu-id="101fe-108">事件源</span><span class="sxs-lookup"><span data-stu-id="101fe-108">Event Source</span></span>|<span data-ttu-id="101fe-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="101fe-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="101fe-110">组件</span><span class="sxs-lookup"><span data-stu-id="101fe-110">Component</span></span>|<span data-ttu-id="101fe-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="101fe-111">SQLEngine</span></span>|  
|<span data-ttu-id="101fe-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="101fe-112">Symbolic Name</span></span>||  
|<span data-ttu-id="101fe-113">消息正文</span><span class="sxs-lookup"><span data-stu-id="101fe-113">Message Text</span></span>|<span data-ttu-id="101fe-114">在建立与服务器的连接时出错。</span><span class="sxs-lookup"><span data-stu-id="101fe-114">An error has occurred while establishing a connection to the server.</span></span>  <span data-ttu-id="101fe-115">在连接到 SQL Server 时，在默认的设置下 SQL Server 不允许远程连接可能会导致此失败。</span><span class="sxs-lookup"><span data-stu-id="101fe-115">When connecting to SQL Server, this failure may be caused by the fact that under the default settings SQL Server does not allow remote connections.</span></span> <span data-ttu-id="101fe-116">（提供程序：TCP 提供程序，错误:0 - 由于被连接方在一段时间后未正确响应，或者连接的主机无法响应，连接尝试失败。)(Microsoft SQL Server，错误:10060)</span><span class="sxs-lookup"><span data-stu-id="101fe-116">(provider: TCP Provider, error: 0 - A connection attempt failed because the connected party did not properly respond after a period of time, or established connection failed because connected host has failed to respond.) (Microsoft SQL Server, Error: 10060)</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="101fe-117">说明</span><span class="sxs-lookup"><span data-stu-id="101fe-117">Explanation</span></span>  
 <span data-ttu-id="101fe-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 客户端无法连接到服务器。</span><span class="sxs-lookup"><span data-stu-id="101fe-118">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client cannot connect to the server.</span></span> <span data-ttu-id="101fe-119">发生此错误的原因可能是服务器上的防火墙拒绝该连接或服务器未配置为接受远程连接。</span><span class="sxs-lookup"><span data-stu-id="101fe-119">This error could occur because either the firewall on the server has refused the connection or the server is not configured to accept remote connections.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="101fe-120">用户操作</span><span class="sxs-lookup"><span data-stu-id="101fe-120">User Action</span></span>  
 <span data-ttu-id="101fe-121">若要解决此错误，请尝试执行下列操作之一：</span><span class="sxs-lookup"><span data-stu-id="101fe-121">To resolve this error, try one of the following actions:</span></span>  
  
-   <span data-ttu-id="101fe-122">确保计算机上的防火墙已配置，以便此 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例可以接受连接。</span><span class="sxs-lookup"><span data-stu-id="101fe-122">Make sure that you have configured the firewall on the computer to allow this instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to accept connections.</span></span>  
  
-   <span data-ttu-id="101fe-123">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器工具使 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 接受远程连接。</span><span class="sxs-lookup"><span data-stu-id="101fe-123">Use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager tool to allow [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to accept remote connections.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="101fe-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="101fe-124">See Also</span></span>  
 <span data-ttu-id="101fe-125">[为数据库引擎访问配置 Windows 防火墙](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md) </span><span class="sxs-lookup"><span data-stu-id="101fe-125">[Configure a Windows Firewall for Database Engine Access](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md) </span></span>  
 <span data-ttu-id="101fe-126">[配置客户端协议](../../database-engine/configure-windows/configure-client-protocols.md) </span><span class="sxs-lookup"><span data-stu-id="101fe-126">[Configure Client Protocols](../../database-engine/configure-windows/configure-client-protocols.md) </span></span>  
 <span data-ttu-id="101fe-127">[网络协议和网络库](../../sql-server/install/network-protocols-and-network-libraries.md) </span><span class="sxs-lookup"><span data-stu-id="101fe-127">[Network Protocols and Network Libraries](../../sql-server/install/network-protocols-and-network-libraries.md) </span></span>  
 <span data-ttu-id="101fe-128">[客户端网络配置](../../database-engine/configure-windows/client-network-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="101fe-128">[Client Network Configuration](../../database-engine/configure-windows/client-network-configuration.md) </span></span>  
 <span data-ttu-id="101fe-129">[配置客户端协议](../../database-engine/configure-windows/configure-client-protocols.md) </span><span class="sxs-lookup"><span data-stu-id="101fe-129">[Configure Client Protocols](../../database-engine/configure-windows/configure-client-protocols.md) </span></span>  
 [<span data-ttu-id="101fe-130">启用或禁用服务器网络协议</span><span class="sxs-lookup"><span data-stu-id="101fe-130">Enable or Disable a Server Network Protocol</span></span>](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)  
  
  
