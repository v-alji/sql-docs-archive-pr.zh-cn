---
title: Broker 事件类别 | Microsoft Docs
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- SQL Server event classes, Broker event category
- Broker event category [SQL Server]
- event classes [SQL Server], Broker event category
ms.assetid: 470dc93c-0dda-4d89-829b-937738d59b31
author: stevestein
ms.author: sstein
ms.openlocfilehash: 23f839416e3404bfdf0a7e61d1b1e8dbbb90ec95
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578260"
---
# <a name="broker-event-category"></a><span data-ttu-id="abe85-102">Broker 事件类别</span><span class="sxs-lookup"><span data-stu-id="abe85-102">Broker Event Category</span></span>
  <span data-ttu-id="abe85-103">**Broker** 事件类别包含一般的 Service Broker 事件。</span><span class="sxs-lookup"><span data-stu-id="abe85-103">The **Broker** event category contains general Service Broker events.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="abe85-104">本节内容</span><span class="sxs-lookup"><span data-stu-id="abe85-104">In This Section</span></span>  
  
|<span data-ttu-id="abe85-105">主题</span><span class="sxs-lookup"><span data-stu-id="abe85-105">Topic</span></span>|<span data-ttu-id="abe85-106">说明</span><span class="sxs-lookup"><span data-stu-id="abe85-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="abe85-107">Broker:Activation 事件类</span><span class="sxs-lookup"><span data-stu-id="abe85-107">Broker:Activation Event Class</span></span>](broker-activation-event-class.md)|<span data-ttu-id="abe85-108">队列监视器启动激活存储过程时生成的事件。</span><span class="sxs-lookup"><span data-stu-id="abe85-108">An event generated when a queue monitor starts an activation stored procedure.</span></span>|  
|[<span data-ttu-id="abe85-109">Broker:Connection 事件类</span><span class="sxs-lookup"><span data-stu-id="abe85-109">Broker:Connection Event Class</span></span>](broker-connection-event-class.md)|<span data-ttu-id="abe85-110">为报告 Service Broker 所管理的传输连接的状态而生成的事件。</span><span class="sxs-lookup"><span data-stu-id="abe85-110">An event generated to report the status of a transport connection managed by Service Broker.</span></span>|  
|[<span data-ttu-id="abe85-111">Broker:Conversation 事件类</span><span class="sxs-lookup"><span data-stu-id="abe85-111">Broker:Conversation Event Class</span></span>](broker-conversation-event-class.md)|<span data-ttu-id="abe85-112">为报告会话进度而生成的事件。</span><span class="sxs-lookup"><span data-stu-id="abe85-112">An event generated to report the progress of a conversation.</span></span>|  
|[<span data-ttu-id="abe85-113">Broker:Conversation Group 事件类</span><span class="sxs-lookup"><span data-stu-id="abe85-113">Broker:Conversation Group Event Class</span></span>](broker-conversation-group-event-class.md)|<span data-ttu-id="abe85-114">数据库创建或删除会话组时生成的事件。</span><span class="sxs-lookup"><span data-stu-id="abe85-114">An event generated when the database creates or drops a conversation group.</span></span>|  
|[<span data-ttu-id="abe85-115">Broker:Corrupted Message 事件类</span><span class="sxs-lookup"><span data-stu-id="abe85-115">Broker:Corrupted Message Event Class</span></span>](broker-corrupted-message-event-class.md)|<span data-ttu-id="abe85-116">为报告数据库接收到损坏的消息而生成的事件。</span><span class="sxs-lookup"><span data-stu-id="abe85-116">An event generated to report that the database has received a corrupt message.</span></span>|  
|[<span data-ttu-id="abe85-117">Broker:Forwarded Message Dropped 事件类</span><span class="sxs-lookup"><span data-stu-id="abe85-117">Broker:Forwarded Message Dropped Event Class</span></span>](broker-forwarded-message-dropped-event-class.md)|<span data-ttu-id="abe85-118">SQL Server 删除本应已转发的 Service Broker 消息时生成的事件。</span><span class="sxs-lookup"><span data-stu-id="abe85-118">An event generated when SQL Server drops a Service Broker message that was to have been forwarded.</span></span>|  
|[<span data-ttu-id="abe85-119">Broker:Forwarded Message Sent 事件类</span><span class="sxs-lookup"><span data-stu-id="abe85-119">Broker:Forwarded Message Sent Event Class</span></span>](broker-forwarded-message-sent-event-class.md)|<span data-ttu-id="abe85-120">SQL Server 转发 Service Broker 消息时生成的事件。</span><span class="sxs-lookup"><span data-stu-id="abe85-120">An event generated when SQL Server forwards a Service Broker message.</span></span>|  
|[<span data-ttu-id="abe85-121">Broker:Message Classify 事件类</span><span class="sxs-lookup"><span data-stu-id="abe85-121">Broker:Message Classify Event Class</span></span>](broker-message-classify-event-class.md)|<span data-ttu-id="abe85-122">Service Broker 确定消息的路由时生成的事件。</span><span class="sxs-lookup"><span data-stu-id="abe85-122">An event generated when Service Broker determines the routing for a message.</span></span>|  
|[<span data-ttu-id="abe85-123">Broker:Message Drop 事件类</span><span class="sxs-lookup"><span data-stu-id="abe85-123">Broker:Message Drop Event Class</span></span>](broker-message-drop-event-class.md)|<span data-ttu-id="abe85-124">当 Service Broker 无法保留已收到的应传递给此实例中某个服务的消息时生成的事件。</span><span class="sxs-lookup"><span data-stu-id="abe85-124">An event generated when Service Broker is unable to retain a received message that should have been delivered to a service in this instance</span></span>|  
|[<span data-ttu-id="abe85-125">Broker:Remote Message Ack 事件类</span><span class="sxs-lookup"><span data-stu-id="abe85-125">Broker:Remote Message Ack Event Class</span></span>](broker-remote-message-ack-event-class.md)|<span data-ttu-id="abe85-126">Service Broker 发送或接收消息确认时生成的事件。</span><span class="sxs-lookup"><span data-stu-id="abe85-126">An event generated when Service Broker sends or receives a message acknowledgement.</span></span>|  
  
 <span data-ttu-id="abe85-127">还为 Service Broker 提供了两个安全审核事件。</span><span class="sxs-lookup"><span data-stu-id="abe85-127">Two security audit events are also provided for Service Broker.</span></span> <span data-ttu-id="abe85-128">有关这些事件的详细信息，请参阅 [Audit Broker Login 事件类](audit-broker-login-event-class.md) 和 [Audit Broker Conversation 事件类](audit-broker-conversation-event-class.md)。</span><span class="sxs-lookup"><span data-stu-id="abe85-128">For more information on those events, see [Audit Broker Login Event Class](audit-broker-login-event-class.md) and [Audit Broker Conversation Event Class](audit-broker-conversation-event-class.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abe85-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="abe85-129">See Also</span></span>  
 [<span data-ttu-id="abe85-130">“安全审核”事件类别</span><span class="sxs-lookup"><span data-stu-id="abe85-130">Security Audit Event Category</span></span>](https://docs.microsoft.com/bi-reference/trace-events/security-audit-event-category)  
  
  
