---
title: MSSQLSERVER_2 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "2"
helpviewer_keywords:
- 2 (Database Engine error)
ms.assetid: 567fb571-7cda-4ce8-a702-cdff2df5d419
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 87d19a24219fda79de2cad4c06af4f1936b37b24
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589625"
---
# <a name="mssqlserver_2"></a><span data-ttu-id="33d49-102">MSSQLSERVER_2</span><span class="sxs-lookup"><span data-stu-id="33d49-102">MSSQLSERVER_2</span></span>
    
## <a name="details"></a><span data-ttu-id="33d49-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="33d49-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="33d49-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="33d49-104">Product Name</span></span>|<span data-ttu-id="33d49-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="33d49-105">SQL Server</span></span>|  
|<span data-ttu-id="33d49-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="33d49-106">Event ID</span></span>|<span data-ttu-id="33d49-107">2</span><span class="sxs-lookup"><span data-stu-id="33d49-107">2</span></span>|  
|<span data-ttu-id="33d49-108">事件源</span><span class="sxs-lookup"><span data-stu-id="33d49-108">Event Source</span></span>|<span data-ttu-id="33d49-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="33d49-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="33d49-110">组件</span><span class="sxs-lookup"><span data-stu-id="33d49-110">Component</span></span>|<span data-ttu-id="33d49-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="33d49-111">SQLEngine</span></span>|  
|<span data-ttu-id="33d49-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="33d49-112">Symbolic Name</span></span>||  
|<span data-ttu-id="33d49-113">消息正文</span><span class="sxs-lookup"><span data-stu-id="33d49-113">Message Text</span></span>|<span data-ttu-id="33d49-114">在建立与服务器的连接时出错。</span><span class="sxs-lookup"><span data-stu-id="33d49-114">An error has occurred while establishing a connection to the server.</span></span>  <span data-ttu-id="33d49-115">在连接到 SQL Server 时，在默认的设置下 SQL Server 不允许远程连接可能会导致此失败。</span><span class="sxs-lookup"><span data-stu-id="33d49-115">When connecting to SQL Server, this failure may be caused by the fact that under the default settings SQL Server does not allow remote connections.</span></span> <span data-ttu-id="33d49-116">（提供程序：命名管道提供程序，错误: 40 - 无法打开到 SQL Server 的连接) (.Net SqlClient 数据提供程序)</span><span class="sxs-lookup"><span data-stu-id="33d49-116">(provider: Named Pipes Provider, error: 40 - Could not open a connection to SQL Server) (.Net SqlClient Data Provider)</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="33d49-117">说明</span><span class="sxs-lookup"><span data-stu-id="33d49-117">Explanation</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="33d49-118">未响应客户端请求，可能是因为尚未启动服务器。</span><span class="sxs-lookup"><span data-stu-id="33d49-118">did not respond to the client request because the server is probably not started.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="33d49-119">用户操作</span><span class="sxs-lookup"><span data-stu-id="33d49-119">User Action</span></span>  
 <span data-ttu-id="33d49-120">确保已启动服务器。</span><span class="sxs-lookup"><span data-stu-id="33d49-120">Make sure that the server is started.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33d49-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="33d49-121">See Also</span></span>  
 <span data-ttu-id="33d49-122">[管理数据库引擎服务](../../database-engine/configure-windows/manage-the-database-engine-services.md) </span><span class="sxs-lookup"><span data-stu-id="33d49-122">[Manage the Database Engine Services](../../database-engine/configure-windows/manage-the-database-engine-services.md) </span></span>  
 <span data-ttu-id="33d49-123">[配置客户端协议](../../database-engine/configure-windows/configure-client-protocols.md) </span><span class="sxs-lookup"><span data-stu-id="33d49-123">[Configure Client Protocols](../../database-engine/configure-windows/configure-client-protocols.md) </span></span>  
 <span data-ttu-id="33d49-124">[网络协议和网络库](../../sql-server/install/network-protocols-and-network-libraries.md) </span><span class="sxs-lookup"><span data-stu-id="33d49-124">[Network Protocols and Network Libraries](../../sql-server/install/network-protocols-and-network-libraries.md) </span></span>  
 <span data-ttu-id="33d49-125">[客户端网络配置](../../database-engine/configure-windows/client-network-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="33d49-125">[Client Network Configuration](../../database-engine/configure-windows/client-network-configuration.md) </span></span>  
 <span data-ttu-id="33d49-126">[配置客户端协议](../../database-engine/configure-windows/configure-client-protocols.md) </span><span class="sxs-lookup"><span data-stu-id="33d49-126">[Configure Client Protocols](../../database-engine/configure-windows/configure-client-protocols.md) </span></span>  
 [<span data-ttu-id="33d49-127">启用或禁用服务器网络协议</span><span class="sxs-lookup"><span data-stu-id="33d49-127">Enable or Disable a Server Network Protocol</span></span>](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)  
  
  
