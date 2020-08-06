---
title: SQL Server Service Broker | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- SQL12.SWB.SSBQUEUEPROPERTIES.GENERAL.F1
- SQL12.SWB.SSBREMSVCBINDPROPERTIES.GENERAL.F1
- SQL12.SWB.SSBMSGTYPEPROPERTIES.GENERAL.F1
- SQL12.SWB.SSBROUTEPROPERTIES.GENERAL.F1
- SQL12.SWB.SSBCONTRACTPROPERTIES.GENERAL.F1
- SQL12.SWB.SSBSERVICEPROPERTIES.GENERAL.F1
- SQL12.SWB.SSBPRIORITYPROPERTIES.GENERAL.F1
helpviewer_keywords:
- Broker See Service Broker
- SQL Server Service Broker
- Service Broker
ms.assetid: 8b8b3b57-fd46-44de-9a4e-e3a8e3999c1e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3d3877dd8311e0fe5b65bd4b1e7f9c40fbd84751
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693074"
---
# <a name="sql-server-service-broker"></a><span data-ttu-id="cf8c5-102">SQL Server Service Broker</span><span class="sxs-lookup"><span data-stu-id="cf8c5-102">SQL Server Service Broker</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="cf8c5-103">[!INCLUDE[ssSB](../../includes/sssb-md.md)]为中的消息和队列应用程序提供本机支持 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="cf8c5-103">[!INCLUDE[ssSB](../../includes/sssb-md.md)] provides native support for messaging and queuing applications in the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span> <span data-ttu-id="cf8c5-104">这使开发人员可以更轻松地创建使用 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 组件在完全不同的数据库之间进行通信的复杂应用程序。</span><span class="sxs-lookup"><span data-stu-id="cf8c5-104">This makes it easier for developers to create sophisticated applications that use the [!INCLUDE[ssDE](../../includes/ssde-md.md)] components to communicate between disparate databases.</span></span> <span data-ttu-id="cf8c5-105">开发人员可以使用 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 轻松生成可靠的分布式应用程序。</span><span class="sxs-lookup"><span data-stu-id="cf8c5-105">Developers can use [!INCLUDE[ssSB](../../includes/sssb-md.md)] to easily build distributed and reliable applications.</span></span>  
  
 <span data-ttu-id="cf8c5-106">使用 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 的应用程序开发人员无需编写复杂的内部通信和消息，即可跨多个数据库分发数据工作负荷。</span><span class="sxs-lookup"><span data-stu-id="cf8c5-106">Application developers who use [!INCLUDE[ssSB](../../includes/sssb-md.md)] can distribute data workloads across several databases without programming complex communication and messaging internals.</span></span> <span data-ttu-id="cf8c5-107">因为 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 会处理会话上下文中的通信路径，所以这就减少了开发和测试工作。</span><span class="sxs-lookup"><span data-stu-id="cf8c5-107">This reduces development and test work because [!INCLUDE[ssSB](../../includes/sssb-md.md)] handles the communication paths in the context of a conversation.</span></span> <span data-ttu-id="cf8c5-108">同时还提高了性能。</span><span class="sxs-lookup"><span data-stu-id="cf8c5-108">It also improves performance.</span></span> <span data-ttu-id="cf8c5-109">例如，支持网站的前端数据库可以记录信息，并发送处理密集型任务以便在后端数据库中进行排队。</span><span class="sxs-lookup"><span data-stu-id="cf8c5-109">For example, front-end databases supporting Web sites can record information and send process intensive tasks to queue in back-end databases.</span></span> [!INCLUDE[ssSB](../../includes/sssb-md.md)] <span data-ttu-id="cf8c5-110">确保在事务上下文中管理所有任务，以确保可靠性和技术一致性。</span><span class="sxs-lookup"><span data-stu-id="cf8c5-110">ensures that all tasks are managed in the context of transactions to assure reliability and technical consistency.</span></span>  
  
## <a name="where-is-the-documentation-for-service-broker"></a><span data-ttu-id="cf8c5-111">Service Broker 文档在哪里？</span><span class="sxs-lookup"><span data-stu-id="cf8c5-111">Where is the documentation for Service Broker?</span></span>  
 <span data-ttu-id="cf8c5-112">[!INCLUDE[ssSB](../../includes/sssb-md.md)] 的参考文档位于 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 文档中。</span><span class="sxs-lookup"><span data-stu-id="cf8c5-112">The reference documentation for [!INCLUDE[ssSB](../../includes/sssb-md.md)] is included in the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] documentation.</span></span> <span data-ttu-id="cf8c5-113">本参考文档包含以下各节：</span><span class="sxs-lookup"><span data-stu-id="cf8c5-113">This reference documentation includes the following sections:</span></span>  
  
-   <span data-ttu-id="cf8c5-114">适用于 CREATE, ALTER 和 DROP 语句的[数据定义语言 (DDL) 语句 (Transact-SQL)](/sql/odbc/reference/develop-app/ddl-statements)</span><span class="sxs-lookup"><span data-stu-id="cf8c5-114">[Data Definition Language &#40;DDL&#41; Statements &#40;Transact-SQL&#41;](/sql/odbc/reference/develop-app/ddl-statements) for CREATE, ALTER, and DROP statements</span></span>  
  
-   [<span data-ttu-id="cf8c5-115">Service Broker 目录视图 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="cf8c5-115">Service Broker Catalog Views &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/service-broker-catalog-views-transact-sql)  
  
-   [<span data-ttu-id="cf8c5-116">与 Service Broker 有关的动态管理视图 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="cf8c5-116">Service Broker Related Dynamic Management Views &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/service-broker-related-dynamic-management-views-transact-sql)  
  
-   [<span data-ttu-id="cf8c5-117">ssbdiagnose 实用工具 (Service Broker)</span><span class="sxs-lookup"><span data-stu-id="cf8c5-117">ssbdiagnose Utility &#40;Service Broker&#41;</span></span>](../../tools/ssbdiagnose/ssbdiagnose-utility-service-broker.md)  
  
 <span data-ttu-id="cf8c5-118">有关 [概念以及开发和管理任务，请参阅](https://go.microsoft.com/fwlink/?LinkId=231312) 以前发布的文档 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="cf8c5-118">See the [previously published documentation](https://go.microsoft.com/fwlink/?LinkId=231312) for [!INCLUDE[ssSB](../../includes/sssb-md.md)] concepts and for development and management tasks.</span></span> <span data-ttu-id="cf8c5-119">由于 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 的 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 中的更改数量少，因此未在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]文档中重新生成该文档。</span><span class="sxs-lookup"><span data-stu-id="cf8c5-119">This documentation is not reproduced in the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] documentation due to the small number of changes in [!INCLUDE[ssSB](../../includes/sssb-md.md)] in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
## <a name="whats-new-in-service-broker"></a><span data-ttu-id="cf8c5-120">Service Broker 新增功能</span><span class="sxs-lookup"><span data-stu-id="cf8c5-120">What's new in Service Broker</span></span>  
 <span data-ttu-id="cf8c5-121">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]未引入任何重大更改。</span><span class="sxs-lookup"><span data-stu-id="cf8c5-121">No significant changes are introduced in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  <span data-ttu-id="cf8c5-122">[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]中引入了以下更改。</span><span class="sxs-lookup"><span data-stu-id="cf8c5-122">The following changes were introduced in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].</span></span>  
  
### <a name="messages-can-be-sent-to-multiple-target-services-multicast"></a><span data-ttu-id="cf8c5-123">可以将消息发送到多个目标服务（多播）</span><span class="sxs-lookup"><span data-stu-id="cf8c5-123">Messages can be sent to multiple target services (multicast)</span></span>  
 <span data-ttu-id="cf8c5-124">通过支持多个会话句柄，扩展了 [SEND (Transact-SQL)](/sql/t-sql/statements/send-transact-sql) 语句的语法以启用多播。</span><span class="sxs-lookup"><span data-stu-id="cf8c5-124">The syntax of the [SEND &#40;Transact-SQL&#41;](/sql/t-sql/statements/send-transact-sql) statement has been extended to enable multicast by supporting multiple conversation handles.</span></span>  
  
### <a name="queues-expose-the-message-enqueued-time"></a><span data-ttu-id="cf8c5-125">队列将公开此消息排队时间</span><span class="sxs-lookup"><span data-stu-id="cf8c5-125">Queues expose the message enqueued time</span></span>  
 <span data-ttu-id="cf8c5-126">队列具有一个新列 **message_enqueue_time**，用于显示消息已在队列中待了多少时间。</span><span class="sxs-lookup"><span data-stu-id="cf8c5-126">Queues have a new column, **message_enqueue_time**, that shows how long a message has been in the queue.</span></span>  
  
### <a name="poison-message-handling-can-be-disabled"></a><span data-ttu-id="cf8c5-127">可以禁用有害消息处理</span><span class="sxs-lookup"><span data-stu-id="cf8c5-127">Poison message handling can be disabled</span></span>  
 <span data-ttu-id="cf8c5-128">现在，[CREATE QUEUE (Transact-SQL)](/sql/t-sql/statements/create-queue-transact-sql) 和 [ALTER QUEUE (Transact-SQL)](/sql/t-sql/statements/alter-queue-transact-sql) 语句可以通过添加子句 `POISON_MESSAGE_HANDLING (STATUS = ON | OFF)` 来启用或禁用有害消息处理。</span><span class="sxs-lookup"><span data-stu-id="cf8c5-128">The [CREATE QUEUE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-queue-transact-sql) and [ALTER QUEUE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-queue-transact-sql) statements now have the ability to enable or disable poison message handling by adding the clause, `POISON_MESSAGE_HANDLING (STATUS = ON | OFF)`.</span></span> <span data-ttu-id="cf8c5-129">目录视图 **sys.service_queues** 现在具有列 **is_poison_message_handling_enabled** ，以指示是启用还是禁用有害消息。</span><span class="sxs-lookup"><span data-stu-id="cf8c5-129">The catalog view **sys.service_queues** now has the column **is_poison_message_handling_enabled** to indicate whether poison message is enabled or disabled.</span></span>  
  
### <a name="alwayson-support-in-service-broker"></a><span data-ttu-id="cf8c5-130">Service Broker 中的 AlwaysOn 支持</span><span class="sxs-lookup"><span data-stu-id="cf8c5-130">AlwaysOn support in Service Broker</span></span>  
 <span data-ttu-id="cf8c5-131">有关详细信息，请参阅：[Service Broker 与 AlwaysOn 可用性组 (SQL Server)](../availability-groups/windows/service-broker-with-always-on-availability-groups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="cf8c5-131">For more information, see [Service Broker with AlwaysOn Availability Groups &#40;SQL Server&#41;](../availability-groups/windows/service-broker-with-always-on-availability-groups-sql-server.md).</span></span>  
  
  
