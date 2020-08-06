---
title: 管理 Service Broker |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- Service Broker [SMO]
ms.assetid: b29d7432-d1e5-4bb6-b544-57b3a9430f95
author: stevestein
ms.author: sstein
ms.openlocfilehash: ce166825bb7adea241bac13defeca1a78b4f29cd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682786"
---
# <a name="managing-service-broker"></a><span data-ttu-id="4ff36-102">管理 Service Broker</span><span class="sxs-lookup"><span data-stu-id="4ff36-102">Managing Service Broker</span></span>
  <span data-ttu-id="4ff36-103">在 SMO 中，[!INCLUDE[ssSB](../../../includes/sssb-md.md)] 对象在 `Microsoft.SqlServer.Management.Smo.Broker` 命名空间中提供，该命名空间要求引用 Microsoft.SqlServer.Smo.dll。</span><span class="sxs-lookup"><span data-stu-id="4ff36-103">In SMO, the [!INCLUDE[ssSB](../../../includes/sssb-md.md)] objects are found in the `Microsoft.SqlServer.Management.Smo.Broker` namespace, which requires a reference to the Microsoft.SqlServer.Smo.dll.</span></span> <span data-ttu-id="4ff36-104">为支持类信息，还要求对 Microsoft.SqlServer.ServiceBrokerEnum.dll 的引用。</span><span class="sxs-lookup"><span data-stu-id="4ff36-104">A reference to the Microsoft.SqlServer.ServiceBrokerEnum.dll is also required for supporting class information.</span></span>  
  
 <span data-ttu-id="4ff36-105">SMO 提供一组 [!INCLUDE[ssSB](../../../includes/sssb-md.md)] 对象，这些对象允许以编程方式管理 [!INCLUDE[ssSB](../../../includes/sssb-md.md)] 的实现 (DDL)。</span><span class="sxs-lookup"><span data-stu-id="4ff36-105">SMO provides a set of [!INCLUDE[ssSB](../../../includes/sssb-md.md)] objects that permit programmatic management (DDL) of the [!INCLUDE[ssSB](../../../includes/sssb-md.md)] implementation.</span></span> <span data-ttu-id="4ff36-106">这包括定义消息类型、约定、队列和服务。</span><span class="sxs-lookup"><span data-stu-id="4ff36-106">This includes defining the message types, contracts, queues, and services.</span></span> <span data-ttu-id="4ff36-107">因为 SMO 是并不针对数据操作、发送和接收的管理工具，所以 SMO 不支持 [!INCLUDE[ssSB](../../../includes/sssb-md.md)] 消息。</span><span class="sxs-lookup"><span data-stu-id="4ff36-107">Because SMO is a management tool that is not intended for data manipulation, sending and receiving [!INCLUDE[ssSB](../../../includes/sssb-md.md)] messages is not supported by SMO.</span></span>  
  
 <span data-ttu-id="4ff36-108">在 SMO 中，<xref:Microsoft.SqlServer.Management.Smo.Database.ServiceBroker%2A> 对象是顶级类，所有 [!INCLUDE[ssSB](../../../includes/sssb-md.md)] 功能都位于其下。</span><span class="sxs-lookup"><span data-stu-id="4ff36-108">In SMO, the <xref:Microsoft.SqlServer.Management.Smo.Database.ServiceBroker%2A> object is the top-level class under which all the [!INCLUDE[ssSB](../../../includes/sssb-md.md)] functionality resides.</span></span> <span data-ttu-id="4ff36-109">[!INCLUDE[ssSB](../../../includes/sssb-md.md)] 实现是参与分布式消息处理应用程序的每个数据库所必需的。</span><span class="sxs-lookup"><span data-stu-id="4ff36-109">A [!INCLUDE[ssSB](../../../includes/sssb-md.md)] implementation is required for each database that is participating in the distributed messaging application.</span></span> <span data-ttu-id="4ff36-110">因此，<xref:Microsoft.SqlServer.Management.Smo.Broker.ServiceBroker> 对象是 <xref:Microsoft.SqlServer.Management.Smo.Database> 对象的子级。</span><span class="sxs-lookup"><span data-stu-id="4ff36-110">Therefore, the <xref:Microsoft.SqlServer.Management.Smo.Broker.ServiceBroker> object is a child of the <xref:Microsoft.SqlServer.Management.Smo.Database> object.</span></span>  
  
 <span data-ttu-id="4ff36-111"><xref:Microsoft.SqlServer.Management.Smo.Broker.ServiceBroker> 对象包含用于定义 [!INCLUDE[ssSB](../../../includes/sssb-md.md)] 实现的以下对象的集合：</span><span class="sxs-lookup"><span data-stu-id="4ff36-111">The <xref:Microsoft.SqlServer.Management.Smo.Broker.ServiceBroker> object contains collections of the following objects that are used to define the [!INCLUDE[ssSB](../../../includes/sssb-md.md)] implementation:</span></span>  
  
-   <span data-ttu-id="4ff36-112"><xref:Microsoft.SqlServer.Management.Smo.Broker.MessageType> 对象表示定义消息内容的消息类型。</span><span class="sxs-lookup"><span data-stu-id="4ff36-112"><xref:Microsoft.SqlServer.Management.Smo.Broker.MessageType> objects represent message types that define the content of messages.</span></span>  
  
-   <span data-ttu-id="4ff36-113"><xref:Microsoft.SqlServer.Management.Smo.Broker.MessageTypeMapping> 对象表示指定给定转换中消息的方向和类型的约定。</span><span class="sxs-lookup"><span data-stu-id="4ff36-113"><xref:Microsoft.SqlServer.Management.Smo.Broker.MessageTypeMapping> objects represent contracts that specify the direction and type of messages in a given conversation.</span></span>  
  
-   <span data-ttu-id="4ff36-114"><xref:Microsoft.SqlServer.Management.Smo.Broker.ServiceQueue> 对象在发送消息前和收到消息后存储消息。</span><span class="sxs-lookup"><span data-stu-id="4ff36-114"><xref:Microsoft.SqlServer.Management.Smo.Broker.ServiceQueue> objects store messages prior to sending and after they are received.</span></span> <span data-ttu-id="4ff36-115">它们提供服务间的异步通信以及其他好处，例如自动锁定同一会话组中的消息。</span><span class="sxs-lookup"><span data-stu-id="4ff36-115">They provide asynchronous communication between services, as well as other benefits, such as automatically locking messages in the same conversation group.</span></span>  
  
-   <span data-ttu-id="4ff36-116"><xref:Microsoft.SqlServer.Management.Smo.Broker.BrokerService> 对象表示 [!INCLUDE[ssSB](../../../includes/sssb-md.md)] 服务，这些服务是可寻址的会话端点。</span><span class="sxs-lookup"><span data-stu-id="4ff36-116"><xref:Microsoft.SqlServer.Management.Smo.Broker.BrokerService> objects represent [!INCLUDE[ssSB](../../../includes/sssb-md.md)] services, which are the addressable endpoints for conversations.</span></span> [!INCLUDE[ssSB](../../../includes/sssb-md.md)] <span data-ttu-id="4ff36-117">消息从一个服务发送到另一个服务。</span><span class="sxs-lookup"><span data-stu-id="4ff36-117">messages are sent from one service to another service.</span></span> <span data-ttu-id="4ff36-118">服务指定一个队列来保存消息，还指定一些约定，约定指明该服务可作为“目标”。</span><span class="sxs-lookup"><span data-stu-id="4ff36-118">A service specifies a queue to hold messages, and specifies the contracts for which the service can be the target.</span></span>  
  
-   <span data-ttu-id="4ff36-119"><xref:Microsoft.SqlServer.Management.Smo.Broker.RemoteServiceBinding> 对象表示 [!INCLUDE[ssSB](../../../includes/sssb-md.md)] 在与某一远程服务进行通信时用于安全性和身份验证的设置。</span><span class="sxs-lookup"><span data-stu-id="4ff36-119"><xref:Microsoft.SqlServer.Management.Smo.Broker.RemoteServiceBinding> objects represent the settings that [!INCLUDE[ssSB](../../../includes/sssb-md.md)] uses for security and authentication when communicating with a remote service.</span></span>  
  
-   <span data-ttu-id="4ff36-120"><xref:Microsoft.SqlServer.Management.Smo.Broker.ServiceRoute> 对象表示 [!INCLUDE[ssSB](../../../includes/sssb-md.md)] 路由，它包含所定义的服务和数据库的位置信息。</span><span class="sxs-lookup"><span data-stu-id="4ff36-120"><xref:Microsoft.SqlServer.Management.Smo.Broker.ServiceRoute> objects represents a [!INCLUDE[ssSB](../../../includes/sssb-md.md)] route, which contains the location information for the service and the database on which it is defined.</span></span> <span data-ttu-id="4ff36-121">路由是消息传递所必需的。</span><span class="sxs-lookup"><span data-stu-id="4ff36-121">A route is required for message delivery.</span></span> <span data-ttu-id="4ff36-122">默认情况下，每个数据库都包含一个路由，该路由将位置指定为 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的当前实例。</span><span class="sxs-lookup"><span data-stu-id="4ff36-122">By default, each database contains a route that specifies the location as the current instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ff36-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4ff36-123">See Also</span></span>  
 <xref:Microsoft.SqlServer.Management.Smo.Broker>   
 [<span data-ttu-id="4ff36-124">SQL Server Service Broker</span><span class="sxs-lookup"><span data-stu-id="4ff36-124">SQL Server Service Broker</span></span>](../../../database-engine/configure-windows/sql-server-service-broker.md)  
  
  
