---
title: MSSQLSERVER_10061 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "10061"
helpviewer_keywords:
- 10061 (Database Engine error)
ms.assetid: 729602f3-08df-474c-8740-8dea13c1eee3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0c866bd8dce01f65036f1d508a94252a97613424
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691214"
---
# <a name="mssqlserver_10061"></a><span data-ttu-id="a61b9-102">MSSQLSERVER_10061</span><span class="sxs-lookup"><span data-stu-id="a61b9-102">MSSQLSERVER_10061</span></span>
    
## <a name="details"></a><span data-ttu-id="a61b9-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="a61b9-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a61b9-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="a61b9-104">Product Name</span></span>|<span data-ttu-id="a61b9-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="a61b9-105">SQL Server</span></span>|  
|<span data-ttu-id="a61b9-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="a61b9-106">Event ID</span></span>|<span data-ttu-id="a61b9-107">10061</span><span class="sxs-lookup"><span data-stu-id="a61b9-107">10061</span></span>|  
|<span data-ttu-id="a61b9-108">事件源</span><span class="sxs-lookup"><span data-stu-id="a61b9-108">Event Source</span></span>|<span data-ttu-id="a61b9-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="a61b9-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="a61b9-110">组件</span><span class="sxs-lookup"><span data-stu-id="a61b9-110">Component</span></span>|<span data-ttu-id="a61b9-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="a61b9-111">SQLEngine</span></span>|  
|<span data-ttu-id="a61b9-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="a61b9-112">Symbolic Name</span></span>||  
|<span data-ttu-id="a61b9-113">消息正文</span><span class="sxs-lookup"><span data-stu-id="a61b9-113">Message Text</span></span>|<span data-ttu-id="a61b9-114">在建立与服务器的连接时出错。</span><span class="sxs-lookup"><span data-stu-id="a61b9-114">An error has occurred while establishing a connection to the server.</span></span>  <span data-ttu-id="a61b9-115">在连接到 SQL Server 时，在默认的设置下 SQL Server 不允许远程连接可能会导致此失败。</span><span class="sxs-lookup"><span data-stu-id="a61b9-115">When connecting to SQL Server, this failure may be caused by the fact that under the default settings SQL Server does not allow remote connections.</span></span> <span data-ttu-id="a61b9-116">（提供程序：TCP 提供程序，错误:0 - 因目标计算机主动拒绝该连接而导致无法建立连接。) (Microsoft SQL Server，错误:10061)</span><span class="sxs-lookup"><span data-stu-id="a61b9-116">(provider: TCP Provider, error: 0 - No connection could be made because the target machine actively refused it.) (Microsoft SQL Server, Error: 10061)</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a61b9-117">说明</span><span class="sxs-lookup"><span data-stu-id="a61b9-117">Explanation</span></span>  
 <span data-ttu-id="a61b9-118">服务器未响应客户端请求。</span><span class="sxs-lookup"><span data-stu-id="a61b9-118">The server did not respond to the client request.</span></span> <span data-ttu-id="a61b9-119">发生此错误的原因可能是尚未启动服务器。</span><span class="sxs-lookup"><span data-stu-id="a61b9-119">This error could occur because the server is not started.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a61b9-120">用户操作</span><span class="sxs-lookup"><span data-stu-id="a61b9-120">User Action</span></span>  
 <span data-ttu-id="a61b9-121">确保已启动服务器。</span><span class="sxs-lookup"><span data-stu-id="a61b9-121">Make sure that the server is started.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a61b9-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a61b9-122">See Also</span></span>  
 <span data-ttu-id="a61b9-123">[管理数据库引擎服务](../../database-engine/configure-windows/manage-the-database-engine-services.md) </span><span class="sxs-lookup"><span data-stu-id="a61b9-123">[Manage the Database Engine Services](../../database-engine/configure-windows/manage-the-database-engine-services.md) </span></span>  
 <span data-ttu-id="a61b9-124">[配置客户端协议](../../database-engine/configure-windows/configure-client-protocols.md) </span><span class="sxs-lookup"><span data-stu-id="a61b9-124">[Configure Client Protocols](../../database-engine/configure-windows/configure-client-protocols.md) </span></span>  
 <span data-ttu-id="a61b9-125">[网络协议和网络库](../../sql-server/install/network-protocols-and-network-libraries.md) </span><span class="sxs-lookup"><span data-stu-id="a61b9-125">[Network Protocols and Network Libraries](../../sql-server/install/network-protocols-and-network-libraries.md) </span></span>  
 <span data-ttu-id="a61b9-126">[客户端网络配置](../../database-engine/configure-windows/client-network-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="a61b9-126">[Client Network Configuration](../../database-engine/configure-windows/client-network-configuration.md) </span></span>  
 <span data-ttu-id="a61b9-127">[配置客户端协议](../../database-engine/configure-windows/configure-client-protocols.md) </span><span class="sxs-lookup"><span data-stu-id="a61b9-127">[Configure Client Protocols](../../database-engine/configure-windows/configure-client-protocols.md) </span></span>  
 [<span data-ttu-id="a61b9-128">启用或禁用服务器网络协议</span><span class="sxs-lookup"><span data-stu-id="a61b9-128">Enable or Disable a Server Network Protocol</span></span>](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)  
  
  
