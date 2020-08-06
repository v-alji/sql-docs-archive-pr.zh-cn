---
title: 常规与上下文连接 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- context connections [CLR integration]
- regular connections [CLR integration]
ms.assetid: a1dead02-be88-4b16-8cb2-db1284856764
author: rothja
ms.author: jroth
ms.openlocfilehash: ce531129099a8f4908bdc4b29920696d4ba3c505
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591402"
---
# <a name="regular-vs-context-connections"></a><span data-ttu-id="45568-102">常规连接与上下文连接</span><span class="sxs-lookup"><span data-stu-id="45568-102">Regular vs. Context Connections</span></span>
  <span data-ttu-id="45568-103">如果要连接到远程服务器，请始终使用常规连接，而不使用上下文连接。</span><span class="sxs-lookup"><span data-stu-id="45568-103">If you are connecting to a remote server, always use regular connections rather than context connections.</span></span> <span data-ttu-id="45568-104">如果您需要连接到存储过程或函数正在其上运行的同一台服务器，则在大多数情况下请使用上下文连接。</span><span class="sxs-lookup"><span data-stu-id="45568-104">If you need to connect to the same server on which the stored procedure or function is running, use the context connection in most cases.</span></span> <span data-ttu-id="45568-105">这具有一些优势，例如，在同一个事务空间中运行以及不必重新验证。</span><span class="sxs-lookup"><span data-stu-id="45568-105">This has benefits such as running in the same transaction space and not having to reauthenticate.</span></span>  
  
 <span data-ttu-id="45568-106">此外，使用上下文连接通常会导致性能更佳和占用更少的资源。</span><span class="sxs-lookup"><span data-stu-id="45568-106">Additionally, using the context connection typically results in better performance and less resource usage.</span></span> <span data-ttu-id="45568-107">上下文连接是一个仅进程内连接，因此它可以通过绕过网络协议和传输层来发送 Transact-sql 语句并接收结果，直接联系服务器。</span><span class="sxs-lookup"><span data-stu-id="45568-107">The context connection is an in-process-only connection, so it can contact the server "directly" by bypassing the network protocol and transport layers to send Transact-SQL statements and receive results.</span></span> <span data-ttu-id="45568-108">同时跳过验证过程。</span><span class="sxs-lookup"><span data-stu-id="45568-108">The authentication process is bypassed, as well.</span></span> <span data-ttu-id="45568-109">下图显示 `SqlClient` 托管提供程序的主要组件，并说明在使用常规连接和使用上下文连接时不同组件之间如何相互交互。</span><span class="sxs-lookup"><span data-stu-id="45568-109">The following figure shows the primary components of the `SqlClient` managed provider, as well as how the different components interact with each other when using a regular connection, and when using the context connection.</span></span>  
  
 <span data-ttu-id="45568-110">![上下文代码路径和常规连接代码路径。](../../../database-engine/dev-guide/media/clrintdataaccess.gif "上下文代码路径和常规连接代码路径。")</span><span class="sxs-lookup"><span data-stu-id="45568-110">![Code paths of a context and a regular connnection.](../../../database-engine/dev-guide/media/clrintdataaccess.gif "Code paths of a context and a regular connnection.")</span></span>  
  
 <span data-ttu-id="45568-111">上下文连接所采用的代码路径较短，且所涉及的组件较少，因此，您可以预计请求到达服务器和从服务器获得结果的速度将高于采用常规连接时。</span><span class="sxs-lookup"><span data-stu-id="45568-111">The context connection follows a shorter code path and involves fewer components, so you can expect requests and results to get to and from the server faster than in a regular connection.</span></span> <span data-ttu-id="45568-112">服务器上的查询执行时间对于上下文连接和常规连接是相同的。</span><span class="sxs-lookup"><span data-stu-id="45568-112">Query execution time on the server is the same for context and regular connections.</span></span>  
  
 <span data-ttu-id="45568-113">在某些情况下，您可能需要与同一台服务器之间建立单独的常规连接。</span><span class="sxs-lookup"><span data-stu-id="45568-113">There are some cases in which you may need to open a separate regular connection to the same server.</span></span> <span data-ttu-id="45568-114">例如，有关使用上下文连接的某些限制，请参阅对[常规连接和上下文连接的限制](context-connections-and-regular-connections-restrictions.md)。</span><span class="sxs-lookup"><span data-stu-id="45568-114">For example, there are certain restrictions on using the context connection, described in [Restrictions on Regular and Context Connections](context-connections-and-regular-connections-restrictions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45568-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="45568-115">See Also</span></span>  
 [<span data-ttu-id="45568-116">上下文连接</span><span class="sxs-lookup"><span data-stu-id="45568-116">Context Connection</span></span>](context-connection.md)  
  
  
