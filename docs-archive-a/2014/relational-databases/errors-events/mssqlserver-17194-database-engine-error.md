---
title: MSSQLSERVER_17194 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "17194"
helpviewer_keywords:
- 17194 (Database Engine error)
ms.assetid: 0d03eb20-28a7-4ceb-8903-7f9420a620f7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d3f56a104841c4825bba1f60b3588fadd63555c6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581275"
---
# <a name="mssqlserver_17194"></a><span data-ttu-id="84493-102">MSSQLSERVER_17194</span><span class="sxs-lookup"><span data-stu-id="84493-102">MSSQLSERVER_17194</span></span>
    
## <a name="details"></a><span data-ttu-id="84493-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="84493-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="84493-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="84493-104">Product Name</span></span>|<span data-ttu-id="84493-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="84493-105">SQL Server</span></span>|  
|<span data-ttu-id="84493-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="84493-106">Event ID</span></span>|<span data-ttu-id="84493-107">17194</span><span class="sxs-lookup"><span data-stu-id="84493-107">17194</span></span>|  
|<span data-ttu-id="84493-108">事件源</span><span class="sxs-lookup"><span data-stu-id="84493-108">Event Source</span></span>|<span data-ttu-id="84493-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="84493-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="84493-110">组件</span><span class="sxs-lookup"><span data-stu-id="84493-110">Component</span></span>|<span data-ttu-id="84493-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="84493-111">SQLEngine</span></span>|  
|<span data-ttu-id="84493-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="84493-112">Symbolic Name</span></span>||  
|<span data-ttu-id="84493-113">消息正文</span><span class="sxs-lookup"><span data-stu-id="84493-113">Message Text</span></span>|<span data-ttu-id="84493-114">服务器无法加载登录所需的 SSL 提供程序库；连接已关闭。</span><span class="sxs-lookup"><span data-stu-id="84493-114">The server was unable to load the SSL provider library needed to log in; the connection has been closed.</span></span> <span data-ttu-id="84493-115">可以用 SSL 对登录序列或所有通信进行加密，具体取决于管理员配置服务器的方式。</span><span class="sxs-lookup"><span data-stu-id="84493-115">SSL is used to encrypt either the login sequence or all communications, depending on how the administrator has configured the server.</span></span> <span data-ttu-id="84493-116">有关错误消息 0xXXXX 的信息，请参阅联机丛书。</span><span class="sxs-lookup"><span data-stu-id="84493-116">See Books Online for information on this error message:  0xXXXX.</span></span> <span data-ttu-id="84493-117">[客户端：11.11.11.11]</span><span class="sxs-lookup"><span data-stu-id="84493-117">[CLIENT: 11.11.11.11]</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="84493-118">说明</span><span class="sxs-lookup"><span data-stu-id="84493-118">Explanation</span></span>  
 <span data-ttu-id="84493-119">此错误指示客户端已关闭连接。</span><span class="sxs-lookup"><span data-stu-id="84493-119">This error indicates that the client has closed the connection.</span></span> <span data-ttu-id="84493-120">因为连接超时时间已到，所以有可能发生此错误。</span><span class="sxs-lookup"><span data-stu-id="84493-120">This error could occur because the connection time-out has expired.</span></span> <span data-ttu-id="84493-121">该错误消息将显示操作系统返回的值，说明错误的根本问题。</span><span class="sxs-lookup"><span data-stu-id="84493-121">The error message displays a value from the operating system that describes the underlying problem.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="84493-122">用户操作</span><span class="sxs-lookup"><span data-stu-id="84493-122">User Action</span></span>  
 <span data-ttu-id="84493-123">如果错误消息中的错误代码为 0x2746（十进制值 10054），则说明客户端重置了连接,通常是因为连接超时。若要纠正此错误，请延长客户端或调用程序连接超时时间。</span><span class="sxs-lookup"><span data-stu-id="84493-123">If the error code in the message is 0x2746 (decimal value 10054), this means that the connection was reset by the client, typically because of a time-out. To resolve the error, increase the connection time-out on the client or calling program.</span></span>  
  
 <span data-ttu-id="84493-124">若要为其他错误消息值确定可能的解决方案，请使用操作系统命令 **net helpmsg**，并指定错误代码的十进制值。</span><span class="sxs-lookup"><span data-stu-id="84493-124">To determine a possible solution for other error message values, use the operating system command **net helpmsg** and specify the decimal value of the error code.</span></span>  
  
 <span data-ttu-id="84493-125">有关如何连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的详细信息，请参阅[服务器网络配置](../../database-engine/configure-windows/server-network-configuration.md)和[客户端网络配置](../../database-engine/configure-windows/client-network-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="84493-125">For more information about how to connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Server Network Configuration](../../database-engine/configure-windows/server-network-configuration.md) and [Client Network Configuration](../../database-engine/configure-windows/client-network-configuration.md).</span></span>  
  
## <a name="internal-only"></a><span data-ttu-id="84493-126">仅内部</span><span class="sxs-lookup"><span data-stu-id="84493-126">Internal-Only</span></span>  
  
