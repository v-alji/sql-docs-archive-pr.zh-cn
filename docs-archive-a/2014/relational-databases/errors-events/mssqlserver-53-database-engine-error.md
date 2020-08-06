---
title: MSSQLSERVER_53 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "53"
helpviewer_keywords:
- 53 (Database Engine error)
ms.assetid: 1234f5a2-b3d1-425a-b29f-480fa792305f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 85fda292fb956047f51b9c7cd1d229ac0afce6b5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587427"
---
# <a name="mssqlserver_53"></a><span data-ttu-id="29566-102">MSSQLSERVER_53</span><span class="sxs-lookup"><span data-stu-id="29566-102">MSSQLSERVER_53</span></span>
    
## <a name="details"></a><span data-ttu-id="29566-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="29566-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="29566-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="29566-104">Product Name</span></span>|<span data-ttu-id="29566-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="29566-105">SQL Server</span></span>|  
|<span data-ttu-id="29566-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="29566-106">Event ID</span></span>|<span data-ttu-id="29566-107">53</span><span class="sxs-lookup"><span data-stu-id="29566-107">53</span></span>|  
|<span data-ttu-id="29566-108">事件源</span><span class="sxs-lookup"><span data-stu-id="29566-108">Event Source</span></span>|<span data-ttu-id="29566-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="29566-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="29566-110">组件</span><span class="sxs-lookup"><span data-stu-id="29566-110">Component</span></span>|<span data-ttu-id="29566-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="29566-111">SQLEngine</span></span>|  
|<span data-ttu-id="29566-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="29566-112">Symbolic Name</span></span>||  
|<span data-ttu-id="29566-113">消息正文</span><span class="sxs-lookup"><span data-stu-id="29566-113">Message Text</span></span>|<span data-ttu-id="29566-114">在建立与服务器的连接时出错。</span><span class="sxs-lookup"><span data-stu-id="29566-114">An error has occurred while establishing a connection to the server.</span></span>  <span data-ttu-id="29566-115">在连接到 SQL Server 时，在默认的设置下 SQL Server 不允许远程连接可能会导致此失败。</span><span class="sxs-lookup"><span data-stu-id="29566-115">When connecting to SQL Server, this failure may be caused by the fact that under the default settings SQL Server does not allow remote connections.</span></span> <span data-ttu-id="29566-116">（提供程序：命名管道提供程序，错误: 40 - 无法打开到 SQL Server 的连接) (.Net SqlClient 数据提供程序)</span><span class="sxs-lookup"><span data-stu-id="29566-116">(provider: Named Pipes Provider, error: 40 - Could not open a connection to SQL Server) (.Net SqlClient Data Provider)</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="29566-117">说明</span><span class="sxs-lookup"><span data-stu-id="29566-117">Explanation</span></span>  
 <span data-ttu-id="29566-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 客户端无法连接到服务器。</span><span class="sxs-lookup"><span data-stu-id="29566-118">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client cannot connect to the server.</span></span> <span data-ttu-id="29566-119">发生此错误的原因可能是客户端无法解析服务器的名称或服务器的名称不正确。</span><span class="sxs-lookup"><span data-stu-id="29566-119">This error could occur because either the client cannot resolve the name of the server or the name of the server is incorrect.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="29566-120">用户操作</span><span class="sxs-lookup"><span data-stu-id="29566-120">User Action</span></span>  
 <span data-ttu-id="29566-121">确保已输入正确的客户端服务器名称，并且可以解析客户端服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="29566-121">Make sure that you have entered the correct server name on the client, and that you can resolve the name of the server from the client.</span></span> <span data-ttu-id="29566-122">若要检查 TCP/IP 名称解析，可以使用 Windows 操作系统中的 **ping** 命令。</span><span class="sxs-lookup"><span data-stu-id="29566-122">To check TCP/IP name resolution, you can use the **ping** command in the Windows operating system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29566-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="29566-123">See Also</span></span>  
 <span data-ttu-id="29566-124">[网络协议和网络库](../../sql-server/install/network-protocols-and-network-libraries.md) </span><span class="sxs-lookup"><span data-stu-id="29566-124">[Network Protocols and Network Libraries](../../sql-server/install/network-protocols-and-network-libraries.md) </span></span>  
 <span data-ttu-id="29566-125">[客户端网络配置](../../database-engine/configure-windows/client-network-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="29566-125">[Client Network Configuration](../../database-engine/configure-windows/client-network-configuration.md) </span></span>  
 <span data-ttu-id="29566-126">[配置客户端协议](../../database-engine/configure-windows/configure-client-protocols.md) </span><span class="sxs-lookup"><span data-stu-id="29566-126">[Configure Client Protocols](../../database-engine/configure-windows/configure-client-protocols.md) </span></span>  
 [<span data-ttu-id="29566-127">启用或禁用服务器网络协议</span><span class="sxs-lookup"><span data-stu-id="29566-127">Enable or Disable a Server Network Protocol</span></span>](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)  
  
  