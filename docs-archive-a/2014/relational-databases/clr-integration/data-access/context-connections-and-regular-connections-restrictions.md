---
title: 常规连接和上下文连接的限制 |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- context connections [CLR integration]
- regular connections [CLR integration]
ms.assetid: 0c6fe4cb-d846-40b5-8884-35a9c770f5e8
author: rothja
ms.author: jroth
ms.openlocfilehash: 52f50347a27cdaffe83b252d86c56382b5ef4f31
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587865"
---
# <a name="restrictions-on-regular-and-context-connections"></a><span data-ttu-id="91d57-102">对常规连接和上下文连接的限制</span><span class="sxs-lookup"><span data-stu-id="91d57-102">Restrictions on Regular and Context Connections</span></span>
  <span data-ttu-id="91d57-103">本主题讨论 [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)] 通过上下文和常规连接在进程中执行的代码的限制。</span><span class="sxs-lookup"><span data-stu-id="91d57-103">This topic discusses the restrictions associated with code executing in the [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)] process through context and regular connections.</span></span>  
  
## <a name="restrictions-on-context-connections"></a><span data-ttu-id="91d57-104">对上下文连接的限制</span><span class="sxs-lookup"><span data-stu-id="91d57-104">Restrictions on Context Connections</span></span>  
 <span data-ttu-id="91d57-105">开发应用程序时，请考虑应用于上下文连接的以下限制：</span><span class="sxs-lookup"><span data-stu-id="91d57-105">When developing your application, take into account the following restrictions that apply to context connections:</span></span>  
  
-   <span data-ttu-id="91d57-106">对于给定的连接，在给定的时间，您只能打开一个上下文连接。</span><span class="sxs-lookup"><span data-stu-id="91d57-106">You can have only one context connection open at a given time for a given connection.</span></span> <span data-ttu-id="91d57-107">如果有多个语句并发运行在单独的连接中，则其中的每个语句都可以获得自己的上下文连接。</span><span class="sxs-lookup"><span data-stu-id="91d57-107">If you have multiple statements running concurrently in separate connections, each one of them can get their own context connection.</span></span> <span data-ttu-id="91d57-108">此限制不影响来自不同连接的并发请求；它只影响对给定连接的给定请求。</span><span class="sxs-lookup"><span data-stu-id="91d57-108">The restriction does not affect concurrent requests from different connections; it only affects a given request on a given connection.</span></span>  
  
-   <span data-ttu-id="91d57-109">上下文连接中不支持多个活动结果集 (MARS)。</span><span class="sxs-lookup"><span data-stu-id="91d57-109">Multiple Active Result Sets (MARS) is not supported in a context connection.</span></span>  
  
-   <span data-ttu-id="91d57-110">`SqlBulkCopy` 类不能在上下文连接中工作。</span><span class="sxs-lookup"><span data-stu-id="91d57-110">The `SqlBulkCopy` class does not operate in a context connection.</span></span>  
  
-   <span data-ttu-id="91d57-111">不支持上下文连接中的更新批处理</span><span class="sxs-lookup"><span data-stu-id="91d57-111">Update batching in a context connection is not supported</span></span>  
  
-   <span data-ttu-id="91d57-112">`SqlNotificationRequest` 不能用于对上下文连接执行的命令。</span><span class="sxs-lookup"><span data-stu-id="91d57-112">`SqlNotificationRequest` cannot be used with commands that execute against a context connection.</span></span>  
  
-   <span data-ttu-id="91d57-113">不支持取消正在对上下文连接运行的命令。</span><span class="sxs-lookup"><span data-stu-id="91d57-113">Canceling commands that are running against the context connection is not supported.</span></span> <span data-ttu-id="91d57-114">`SqlCommand.Cancel` 方法会自行忽略请求。</span><span class="sxs-lookup"><span data-stu-id="91d57-114">The `SqlCommand.Cancel` method silently ignores the request.</span></span>  
  
-   <span data-ttu-id="91d57-115">使用“context connection=true”时，不能使用任何其他连接字符串关键字。</span><span class="sxs-lookup"><span data-stu-id="91d57-115">No other connection string keywords can be used when you use "context connection=true".</span></span>  
  
-   <span data-ttu-id="91d57-116">如果 `SqlConnection.DataSource` 的连接字符串为“context connection=true”，则 `SqlConnection` 属性返回 Null，而不是 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例的名称。</span><span class="sxs-lookup"><span data-stu-id="91d57-116">The `SqlConnection.DataSource` property returns null if the connection string for the `SqlConnection` is "context connection=true", instead of the name of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="91d57-117">对上下文连接执行命令时，设置 `SqlCommand.CommandTimeout` 属性无效。</span><span class="sxs-lookup"><span data-stu-id="91d57-117">Setting the `SqlCommand.CommandTimeout` property has no effect when the command is executed against a context connection.</span></span>  
  
## <a name="restrictions-on-regular-connections"></a><span data-ttu-id="91d57-118">对常规连接的限制</span><span class="sxs-lookup"><span data-stu-id="91d57-118">Restrictions on Regular Connections</span></span>  
 <span data-ttu-id="91d57-119">开发应用程序时，请考虑应用于常规连接的以下限制：</span><span class="sxs-lookup"><span data-stu-id="91d57-119">When developing your application, take into account the following restrictions that apply to regular connections:</span></span>  
  
-   <span data-ttu-id="91d57-120">不支持对内部服务器异步执行命令。</span><span class="sxs-lookup"><span data-stu-id="91d57-120">Asynchronous command execution against internal servers is not supported.</span></span> <span data-ttu-id="91d57-121">如果在命令的连接字符串中包括“async=true”，然后执行命令，将导致引发 `System.NotSupportedException`。</span><span class="sxs-lookup"><span data-stu-id="91d57-121">Including "async=true" in the connection string of a command, and then executing the command, results in `System.NotSupportedException` being thrown.</span></span> <span data-ttu-id="91d57-122">将出现此消息：“在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 进程内运行时，不支持异步处理。”</span><span class="sxs-lookup"><span data-stu-id="91d57-122">This message appears: "Asynchronous processing is not supported when running inside the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] process."</span></span>  
  
-   <span data-ttu-id="91d57-123">不支持 `SqlDependency` 对象。</span><span class="sxs-lookup"><span data-stu-id="91d57-123">`SqlDependency` object is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91d57-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="91d57-124">See Also</span></span>  
 [<span data-ttu-id="91d57-125">上下文连接</span><span class="sxs-lookup"><span data-stu-id="91d57-125">Context Connection</span></span>](context-connection.md)  
  
  
