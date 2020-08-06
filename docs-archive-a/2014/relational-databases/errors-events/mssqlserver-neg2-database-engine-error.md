---
title: MSSQLSERVER_-2 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "2"
helpviewer_keywords:
- -2 (Database Engine error)
ms.assetid: f37a7b7d-26e1-4b9e-bcb4-57f7805393d2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5d39b4a11387a60056bba3f87adffcb2653b60f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689918"
---
# <a name="mssqlserver_-2"></a><span data-ttu-id="2e995-102">MSSQLSERVER_-2</span><span class="sxs-lookup"><span data-stu-id="2e995-102">MSSQLSERVER_-2</span></span>
    
## <a name="details"></a><span data-ttu-id="2e995-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="2e995-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2e995-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="2e995-104">Product Name</span></span>|<span data-ttu-id="2e995-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="2e995-105">SQL Server</span></span>|  
|<span data-ttu-id="2e995-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="2e995-106">Event ID</span></span>|<span data-ttu-id="2e995-107">-2</span><span class="sxs-lookup"><span data-stu-id="2e995-107">-2</span></span>|  
|<span data-ttu-id="2e995-108">事件源</span><span class="sxs-lookup"><span data-stu-id="2e995-108">Event Source</span></span>|<span data-ttu-id="2e995-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="2e995-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="2e995-110">组件</span><span class="sxs-lookup"><span data-stu-id="2e995-110">Component</span></span>|<span data-ttu-id="2e995-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="2e995-111">SQLEngine</span></span>|  
|<span data-ttu-id="2e995-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="2e995-112">Symbolic Name</span></span>||  
|<span data-ttu-id="2e995-113">消息正文</span><span class="sxs-lookup"><span data-stu-id="2e995-113">Message Text</span></span>|<span data-ttu-id="2e995-114">超时时间已到。</span><span class="sxs-lookup"><span data-stu-id="2e995-114">Timeout expired.</span></span>  <span data-ttu-id="2e995-115">超时时间在操作完成或服务器没有响应之前已过。</span><span class="sxs-lookup"><span data-stu-id="2e995-115">The timeout period elapsed prior to completion of the operation or the server is not responding.</span></span> <span data-ttu-id="2e995-116">（Microsoft SQL Server，错误: -2）</span><span class="sxs-lookup"><span data-stu-id="2e995-116">(Microsoft SQL Server, Error: -2)</span></span>|   
  
## <a name="explanation"></a><span data-ttu-id="2e995-117">说明</span><span class="sxs-lookup"><span data-stu-id="2e995-117">Explanation</span></span>  
 <span data-ttu-id="2e995-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 客户端无法连接到服务器。</span><span class="sxs-lookup"><span data-stu-id="2e995-118">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client cannot connect to the server.</span></span> <span data-ttu-id="2e995-119">发生此错误的原因可能是服务器上的防火墙拒绝此连接。</span><span class="sxs-lookup"><span data-stu-id="2e995-119">This error could occur because the firewall on the server has refused the connection.</span></span> 
  
## <a name="user-action"></a><span data-ttu-id="2e995-120">用户操作</span><span class="sxs-lookup"><span data-stu-id="2e995-120">User Action</span></span>  
 <span data-ttu-id="2e995-121">确保 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务器实例上的防火墙已配置为接受连接。</span><span class="sxs-lookup"><span data-stu-id="2e995-121">Make sure that you have configured the firewall on the server instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to accept connections.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e995-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2e995-122">See Also</span></span>  
 <span data-ttu-id="2e995-123">[将 Windows 防火墙配置为允许 SQL Server 访问](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md) </span><span class="sxs-lookup"><span data-stu-id="2e995-123">[Configure the Windows Firewall to Allow SQL Server Access](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md) </span></span>  
 <span data-ttu-id="2e995-124">[为数据库引擎访问配置 Windows 防火墙](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md) </span><span class="sxs-lookup"><span data-stu-id="2e995-124">[Configure a Windows Firewall for Database Engine Access](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md) </span></span>  
 <span data-ttu-id="2e995-125">[配置客户端协议](../../database-engine/configure-windows/configure-client-protocols.md) </span><span class="sxs-lookup"><span data-stu-id="2e995-125">[Configure Client Protocols](../../database-engine/configure-windows/configure-client-protocols.md) </span></span>  
 <span data-ttu-id="2e995-126">[网络协议和网络库](../../sql-server/install/network-protocols-and-network-libraries.md) </span><span class="sxs-lookup"><span data-stu-id="2e995-126">[Network Protocols and Network Libraries](../../sql-server/install/network-protocols-and-network-libraries.md) </span></span>  
 <span data-ttu-id="2e995-127">[客户端网络配置](../../database-engine/configure-windows/client-network-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="2e995-127">[Client Network Configuration](../../database-engine/configure-windows/client-network-configuration.md) </span></span>  
 <span data-ttu-id="2e995-128">[配置客户端协议](../../database-engine/configure-windows/configure-client-protocols.md) </span><span class="sxs-lookup"><span data-stu-id="2e995-128">[Configure Client Protocols](../../database-engine/configure-windows/configure-client-protocols.md) </span></span>  
 [<span data-ttu-id="2e995-129">启用或禁用服务器网络协议</span><span class="sxs-lookup"><span data-stu-id="2e995-129">Enable or Disable a Server Network Protocol</span></span>](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)  
  
