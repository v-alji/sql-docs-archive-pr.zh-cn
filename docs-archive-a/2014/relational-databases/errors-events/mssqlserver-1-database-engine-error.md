---
title: MSSQLSERVER_-1 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "-1"
helpviewer_keywords:
- -1 (Database Engine error)
ms.assetid: bad25b91-eaed-46c0-a5b7-71117a32304c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 880212b1d2e9572bbb31535a5ba68b445c7e6f35
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691217"
---
# <a name="mssqlserver_-1"></a><span data-ttu-id="41088-102">MSSQLSERVER_-1</span><span class="sxs-lookup"><span data-stu-id="41088-102">MSSQLSERVER_-1</span></span>
    
## <a name="details"></a><span data-ttu-id="41088-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="41088-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="41088-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="41088-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="41088-105">事件 ID</span><span class="sxs-lookup"><span data-stu-id="41088-105">Event ID</span></span>|<span data-ttu-id="41088-106">-1</span><span class="sxs-lookup"><span data-stu-id="41088-106">-1</span></span>|  
|<span data-ttu-id="41088-107">事件源</span><span class="sxs-lookup"><span data-stu-id="41088-107">Event Source</span></span>|<span data-ttu-id="41088-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="41088-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="41088-109">组件</span><span class="sxs-lookup"><span data-stu-id="41088-109">Component</span></span>|<span data-ttu-id="41088-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="41088-110">SQLEngine</span></span>|  
|<span data-ttu-id="41088-111">符号名称</span><span class="sxs-lookup"><span data-stu-id="41088-111">Symbolic Name</span></span>||  
|<span data-ttu-id="41088-112">消息正文</span><span class="sxs-lookup"><span data-stu-id="41088-112">Message Text</span></span>|<span data-ttu-id="41088-113">在建立与服务器的连接时出错。</span><span class="sxs-lookup"><span data-stu-id="41088-113">An error has occurred while establishing a connection to the server.</span></span>  <span data-ttu-id="41088-114">在连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 时，在默认的设置下 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 不允许进行远程连接可能会导致此失败。</span><span class="sxs-lookup"><span data-stu-id="41088-114">When connecting to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], this failure may be caused by the fact that under the default settings [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not allow remote connections.</span></span> <span data-ttu-id="41088-115">（提供程序：SQL 网络接口，错误：28 - 服务器不支持请求的协议）（Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，错误：-1）</span><span class="sxs-lookup"><span data-stu-id="41088-115">(provider: SQL Network Interfaces, error: 28 - Server doesn't support requested protocol) (Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Error: -1)</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="41088-116">说明</span><span class="sxs-lookup"><span data-stu-id="41088-116">Explanation</span></span>  
 <span data-ttu-id="41088-117">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 客户端无法连接到服务器。</span><span class="sxs-lookup"><span data-stu-id="41088-117">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client cannot connect to the server.</span></span> <span data-ttu-id="41088-118">此错误可能由以下某个原因引起：</span><span class="sxs-lookup"><span data-stu-id="41088-118">This error could be caused by one of the following reasons:</span></span>  
  
-   <span data-ttu-id="41088-119">指定的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例名称无效。</span><span class="sxs-lookup"><span data-stu-id="41088-119">A specified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance name is not valid.</span></span>  
  
-   <span data-ttu-id="41088-120">TCP 或 Named Pipes 协议未启用。</span><span class="sxs-lookup"><span data-stu-id="41088-120">The TCP, or named pipes protocols are not enabled.</span></span>  
  
-   <span data-ttu-id="41088-121">服务器上的防火墙拒绝了此连接。</span><span class="sxs-lookup"><span data-stu-id="41088-121">The firewall on the server has refused the connection.</span></span>  
  
-   <span data-ttu-id="41088-122">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 服务 (sqlbrowser) 未启动。</span><span class="sxs-lookup"><span data-stu-id="41088-122">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service (sqlbrowser) is not started.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="41088-123">用户操作</span><span class="sxs-lookup"><span data-stu-id="41088-123">User Action</span></span>  
 <span data-ttu-id="41088-124">若要解决此错误，请尝试执行下列操作之一：</span><span class="sxs-lookup"><span data-stu-id="41088-124">To resolve this error, try one of the following actions:</span></span>  
  
-   <span data-ttu-id="41088-125">检查连接字符串中指定的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例名称的拼写。</span><span class="sxs-lookup"><span data-stu-id="41088-125">Check the spelling of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance name that is specified in the connection string.</span></span>  
  
-   <span data-ttu-id="41088-126">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器工具使 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 能够通过 TCP 或 Named Pipes 协议接受远程连接。</span><span class="sxs-lookup"><span data-stu-id="41088-126">Use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager tool to enable [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to accept remote connections over the TCP or named pipes protocols.</span></span>  
  
-   <span data-ttu-id="41088-127">确保已配置 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务器实例上的防火墙，为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 打开端口并打开 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 端口 (UDP 1434)。</span><span class="sxs-lookup"><span data-stu-id="41088-127">Make sure that you have configured the firewall on the server instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to open ports for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser port (UDP 1434).</span></span>  
  
-   <span data-ttu-id="41088-128">确保 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 服务已在服务器上启动。</span><span class="sxs-lookup"><span data-stu-id="41088-128">Make sure that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service is started on the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41088-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="41088-129">See Also</span></span>  
 <span data-ttu-id="41088-130">[为数据库引擎访问配置 Windows 防火墙](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md) </span><span class="sxs-lookup"><span data-stu-id="41088-130">[Configure a Windows Firewall for Database Engine Access](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md) </span></span>  
 <span data-ttu-id="41088-131">[配置客户端协议](../../database-engine/configure-windows/configure-client-protocols.md) </span><span class="sxs-lookup"><span data-stu-id="41088-131">[Configure Client Protocols](../../database-engine/configure-windows/configure-client-protocols.md) </span></span>  
 <span data-ttu-id="41088-132">[网络协议和网络库](../../sql-server/install/network-protocols-and-network-libraries.md) </span><span class="sxs-lookup"><span data-stu-id="41088-132">[Network Protocols and Network Libraries](../../sql-server/install/network-protocols-and-network-libraries.md) </span></span>  
 <span data-ttu-id="41088-133">[客户端网络配置](../../database-engine/configure-windows/client-network-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="41088-133">[Client Network Configuration](../../database-engine/configure-windows/client-network-configuration.md) </span></span>  
 <span data-ttu-id="41088-134">[配置客户端协议](../../database-engine/configure-windows/configure-client-protocols.md) </span><span class="sxs-lookup"><span data-stu-id="41088-134">[Configure Client Protocols](../../database-engine/configure-windows/configure-client-protocols.md) </span></span>  
 [<span data-ttu-id="41088-135">启用或禁用服务器网络协议</span><span class="sxs-lookup"><span data-stu-id="41088-135">Enable or Disable a Server Network Protocol</span></span>](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)  
  
  
