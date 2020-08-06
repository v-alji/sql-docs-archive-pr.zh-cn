---
title: 实现事件通知 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- event notifications [SQL Server], target service
- target service [SQL Server]
- event notifications [SQL Server], creating
ms.assetid: 29ac8f68-a28a-4a77-b67b-a8663001308c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6a89c66ca5c3b420fff14c087bd604b16c641369
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587305"
---
# <a name="implement-event-notifications"></a><span data-ttu-id="80430-102">实现事件通知</span><span class="sxs-lookup"><span data-stu-id="80430-102">Implement Event Notifications</span></span>
  <span data-ttu-id="80430-103">若要实现事件通知，必须先创建目标服务以接收事件通知，然后再创建事件通知。</span><span class="sxs-lookup"><span data-stu-id="80430-103">To implement an event notification, you must first create a target service to receive event notifications, and then create the event notification.</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssSB](../../includes/sssb-md.md)] <span data-ttu-id="80430-104">对话安全模式。</span><span class="sxs-lookup"><span data-stu-id="80430-104">dialog security should be configured for event notifications that send messages to a service broker on a remote server.</span></span> <span data-ttu-id="80430-105">必须根据完全安全模式手动配置对话安全设置。</span><span class="sxs-lookup"><span data-stu-id="80430-105">Dialog security must be configured manually according to the full security model.</span></span>  
  
## <a name="creating-the-target-service"></a><span data-ttu-id="80430-106">创建目标服务</span><span class="sxs-lookup"><span data-stu-id="80430-106">Creating the Target Service</span></span>  
 <span data-ttu-id="80430-107">无需创建 [!INCLUDE[ssSB](../../includes/sssb-md.md)]启动服务，因为 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 包含以下特定的事件通知消息类型和约定：</span><span class="sxs-lookup"><span data-stu-id="80430-107">You do not have to create a [!INCLUDE[ssSB](../../includes/sssb-md.md)]-initiating service because [!INCLUDE[ssSB](../../includes/sssb-md.md)] includes the following specific message type and contract for event notifications:</span></span>  
  
```  
https://schemas.microsoft.com/SQL/Notifications/PostEventNotification  
```  
  
 <span data-ttu-id="80430-108">接收事件通知的目标服务必须使用此预先存在的约定。</span><span class="sxs-lookup"><span data-stu-id="80430-108">The target service that receives event notifications must honor this preexisting contract.</span></span>  
  
 <span data-ttu-id="80430-109">**创建目标服务**：</span><span class="sxs-lookup"><span data-stu-id="80430-109">**To create a target service**:</span></span>  
  
1.  <span data-ttu-id="80430-110">创建队列以接收消息。</span><span class="sxs-lookup"><span data-stu-id="80430-110">Create a queue to receive messages.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="80430-111">队列接收下列消息类型： `https://schemas.microsoft.com/SQL/Notifications/QueryNotification`。</span><span class="sxs-lookup"><span data-stu-id="80430-111">The queue receives the following message type: `https://schemas.microsoft.com/SQL/Notifications/QueryNotification`.</span></span>  
  
2.  <span data-ttu-id="80430-112">在引用事件通知约定的队列上创建服务。</span><span class="sxs-lookup"><span data-stu-id="80430-112">Create a service on the queue that references the event notifications contract.</span></span>  
  
3.  <span data-ttu-id="80430-113">创建服务路由，以定义 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 将服务消息发送到的地址。</span><span class="sxs-lookup"><span data-stu-id="80430-113">Create a route on the service to define the address to which [!INCLUDE[ssSB](../../includes/sssb-md.md)] sends messages for the service.</span></span> <span data-ttu-id="80430-114">对于指向同一数据库中的服务的事件通知，请指定 `ADDRESS = 'LOCAL'`。</span><span class="sxs-lookup"><span data-stu-id="80430-114">For event notifications that target a service in the same database, specify `ADDRESS = 'LOCAL'`.</span></span>  
  
    > [!NOTE]  
    >  [!INCLUDE[ssSB](../../includes/sssb-md.md)] <span data-ttu-id="80430-115">路由确定接收通知消息的服务。</span><span class="sxs-lookup"><span data-stu-id="80430-115">routing determines the service that receives the notification messages.</span></span> <span data-ttu-id="80430-116">如果事件通知指向远程服务器中的服务，则源服务器和目标服务器必须都定义了路由，确保实现双向通信。</span><span class="sxs-lookup"><span data-stu-id="80430-116">If the event notification targets a service on a remote server, both the source server and the target server must have routes defined on them to make sure that two-way communication occurs.</span></span>  
  
 <span data-ttu-id="80430-117">下面的示例将创建队列、队列服务以及服务路由，以便依据事件通知约定处理消息。</span><span class="sxs-lookup"><span data-stu-id="80430-117">The following example creates a queue, a service on the queue, and a route on the service to handle messages from the event notification contract.</span></span>  
  
```  
CREATE QUEUE NotifyQueue ;  
GO  
CREATE SERVICE NotifyService  
ON QUEUE NotifyQueue  
(  
[https://schemas.microsoft.com/SQL/Notifications/PostEventNotification]  
);  
GO  
CREATE ROUTE NotifyRoute  
WITH SERVICE_NAME = 'NotifyService',  
ADDRESS = 'LOCAL';  
GO  
```  
  
## <a name="creating-the-event-notification"></a><span data-ttu-id="80430-118">创建事件通知</span><span class="sxs-lookup"><span data-stu-id="80430-118">Creating the Event Notification</span></span>  
 <span data-ttu-id="80430-119">事件通知使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE EVENT NOTIFICATION 语句创建，使用 DROP EVENT NOTIFICATION STATEMENT 删除。</span><span class="sxs-lookup"><span data-stu-id="80430-119">Event notifications are created by using the [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE EVENT NOTIFICATION statement, and are dropped by using the DROP EVENT NOTIFICATION STATEMENT.</span></span> <span data-ttu-id="80430-120">若要修改事件通知，必须先删除事件通知，然后再重新创建。</span><span class="sxs-lookup"><span data-stu-id="80430-120">To modify an event notification, you must drop and re-create the event notification.</span></span>  
  
 <span data-ttu-id="80430-121">下面的示例将创建事件通知 `CreateDatabaseNotification`。</span><span class="sxs-lookup"><span data-stu-id="80430-121">The following example creates the event notification `CreateDatabaseNotification`.</span></span> <span data-ttu-id="80430-122">该通知将服务器中发生的 `CREATE_DATABASE` 事件的相关消息发送到先前创建的 `NotifyService` 服务。</span><span class="sxs-lookup"><span data-stu-id="80430-122">This notification sends a message about any `CREATE_DATABASE` event that occurs on the server to the `NotifyService` service that was previously created.</span></span>  
  
```  
CREATE EVENT NOTIFICATION CreateDatabaseNotification  
ON SERVER  
FOR CREATE_DATABASE  
TO SERVICE 'NotifyService', '8140a771-3c4b-4479-8ac0-81008ab17984' ;  
```  
  
> [!CAUTION]  
>  <span data-ttu-id="80430-123">事件通知将 CREATE_SCHEMA 事件和 CREATE SCHEMA 语句的 <schema_element> 定义识别为不同的事件。</span><span class="sxs-lookup"><span data-stu-id="80430-123">Event notifications recognize CREATE_SCHEMA events and the <schema_element> definitions of CREATE SCHEMA statements as separate events.</span></span> <span data-ttu-id="80430-124">例如，针对 CREATE_SCHEMA 和 CREATE_TABLE 事件创建事件通知，然后便可运行以下批处理。</span><span class="sxs-lookup"><span data-stu-id="80430-124">For example, an event notification is created on both the CREATE_SCHEMA and CREATE_TABLE events, and you run the following batch.</span></span>  
>   
>  `CREATE SCHEMA s`  
>   
>  `CREATE TABLE t1 (col1 int)`  
>   
>  <span data-ttu-id="80430-125">在此情况下，事件通知会引发两次：一次是在 CREATE_SCHEMA 事件发生时，另一次是在 CREATE_TABLE 事件发生时。</span><span class="sxs-lookup"><span data-stu-id="80430-125">In this case, the event notification is raised two times: Onne time when the CREATE_SCHEMA event occurs, and again when the CREATE_TABLE event occurs.</span></span> <span data-ttu-id="80430-126">建议您避免针对 CREATE_SCHEMA 事件和任何相应 CREATE SCHEMA 定义的 <schema_element> 文本创建事件通知，也不要将逻辑置入应用程序中以免捕获不需要的事件数据。</span><span class="sxs-lookup"><span data-stu-id="80430-126">We recommend that you either avoid creating event notifications on both the CREATE_SCHEMA events and the <schema_element> texts of any corresponding CREATE SCHEMA definitions, or build logic into your application to avoid capturing unwanted event data.</span></span>  
  
 <span data-ttu-id="80430-127">**创建事件通知**</span><span class="sxs-lookup"><span data-stu-id="80430-127">**To create an event notification**</span></span>  
  
-   [<span data-ttu-id="80430-128">CREATE EVENT NOTIFICATION (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="80430-128">CREATE EVENT NOTIFICATION &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-event-notification-transact-sql)  
  
 <span data-ttu-id="80430-129">**删除事件通知**</span><span class="sxs-lookup"><span data-stu-id="80430-129">**To drop an event notification**</span></span>  
  
-   [<span data-ttu-id="80430-130">DROP EVENT NOTIFICATION (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="80430-130">DROP EVENT NOTIFICATION &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-event-notification-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="80430-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="80430-131">See Also</span></span>  
 <span data-ttu-id="80430-132">[获取有关事件通知的信息](event-notifications.md) </span><span class="sxs-lookup"><span data-stu-id="80430-132">[Get Information About Event Notifications](event-notifications.md) </span></span>  
 [<span data-ttu-id="80430-133">EVENTDATA (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="80430-133">EVENTDATA &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/eventdata-transact-sql)  
  
  
