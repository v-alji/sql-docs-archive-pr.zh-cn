---
title: MSSQLSERVER_233 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "233"
helpviewer_keywords:
- 233 (Database Engine error)
ms.assetid: 201665dc-7ac8-4c19-90d3-33354c5caa72
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8c51fac7c0af16c520d7cf5538e512912e62cf87
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688929"
---
# <a name="mssqlserver_233"></a><span data-ttu-id="534ac-102">MSSQLSERVER_233</span><span class="sxs-lookup"><span data-stu-id="534ac-102">MSSQLSERVER_233</span></span>
    
## <a name="details"></a><span data-ttu-id="534ac-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="534ac-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="534ac-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="534ac-104">Product Name</span></span>|<span data-ttu-id="534ac-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="534ac-105">SQL Server</span></span>|  
|<span data-ttu-id="534ac-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="534ac-106">Event ID</span></span>|<span data-ttu-id="534ac-107">233</span><span class="sxs-lookup"><span data-stu-id="534ac-107">233</span></span>|  
|<span data-ttu-id="534ac-108">事件源</span><span class="sxs-lookup"><span data-stu-id="534ac-108">Event Source</span></span>|<span data-ttu-id="534ac-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="534ac-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="534ac-110">组件</span><span class="sxs-lookup"><span data-stu-id="534ac-110">Component</span></span>|<span data-ttu-id="534ac-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="534ac-111">SQLEngine</span></span>|  
|<span data-ttu-id="534ac-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="534ac-112">Symbolic Name</span></span>||  
|<span data-ttu-id="534ac-113">消息正文</span><span class="sxs-lookup"><span data-stu-id="534ac-113">Message Text</span></span>|<span data-ttu-id="534ac-114">已成功与服务器建立连接，但是在登录过程中发生错误。</span><span class="sxs-lookup"><span data-stu-id="534ac-114">A connection was successfully established with the server, but then an error occurred during the login process.</span></span> <span data-ttu-id="534ac-115">（提供程序：共享内存提供程序，错误: 0 - 在管道的另一端没有进程。) (Microsoft SQL Server，错误: 233)</span><span class="sxs-lookup"><span data-stu-id="534ac-115">(provider: Shared Memory Provider, error: 0 - No process is on the other end of the pipe.) (Microsoft SQL Server, Error: 233)</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="534ac-116">说明</span><span class="sxs-lookup"><span data-stu-id="534ac-116">Explanation</span></span>  
 <span data-ttu-id="534ac-117">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 客户端无法连接到服务器。</span><span class="sxs-lookup"><span data-stu-id="534ac-117">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client cannot connect to the server.</span></span> <span data-ttu-id="534ac-118">发生此错误的原因可能是服务器未配置为接受远程连接。</span><span class="sxs-lookup"><span data-stu-id="534ac-118">This error could occur because the server is not configured to accept remote connections.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="534ac-119">用户操作</span><span class="sxs-lookup"><span data-stu-id="534ac-119">User Action</span></span>  
 <span data-ttu-id="534ac-120">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器工具使 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 接受远程连接。</span><span class="sxs-lookup"><span data-stu-id="534ac-120">Use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager tool to allow [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to accept remote connections.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="534ac-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="534ac-121">See Also</span></span>  
 <span data-ttu-id="534ac-122">[网络协议和网络库](../../sql-server/install/network-protocols-and-network-libraries.md) </span><span class="sxs-lookup"><span data-stu-id="534ac-122">[Network Protocols and Network Libraries](../../sql-server/install/network-protocols-and-network-libraries.md) </span></span>  
 <span data-ttu-id="534ac-123">[客户端网络配置](../../database-engine/configure-windows/client-network-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="534ac-123">[Client Network Configuration](../../database-engine/configure-windows/client-network-configuration.md) </span></span>  
 <span data-ttu-id="534ac-124">[配置客户端协议](../../database-engine/configure-windows/configure-client-protocols.md) </span><span class="sxs-lookup"><span data-stu-id="534ac-124">[Configure Client Protocols](../../database-engine/configure-windows/configure-client-protocols.md) </span></span>  
 [<span data-ttu-id="534ac-125">启用或禁用服务器网络协议</span><span class="sxs-lookup"><span data-stu-id="534ac-125">Enable or Disable a Server Network Protocol</span></span>](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)  
  
  
