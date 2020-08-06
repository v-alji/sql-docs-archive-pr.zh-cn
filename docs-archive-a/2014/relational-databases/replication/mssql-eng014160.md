---
title: MSSQL_ENG014160 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014160 error
ms.assetid: d0f3855e-d095-4a81-a5bd-9d7ad51f2c77
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3351567a31a0a0384ab8957073ab0457ef0ea7c5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577549"
---
# <a name="mssql_eng014160"></a><span data-ttu-id="b6320-102">MSSQL_ENG014160</span><span class="sxs-lookup"><span data-stu-id="b6320-102">MSSQL_ENG014160</span></span>
    
## <a name="message-details"></a><span data-ttu-id="b6320-103">消息详细信息</span><span class="sxs-lookup"><span data-stu-id="b6320-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b6320-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="b6320-104">Product Name</span></span>|<span data-ttu-id="b6320-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="b6320-105">SQL Server</span></span>|  
|<span data-ttu-id="b6320-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="b6320-106">Event ID</span></span>|<span data-ttu-id="b6320-107">14160</span><span class="sxs-lookup"><span data-stu-id="b6320-107">14160</span></span>|  
|<span data-ttu-id="b6320-108">事件源</span><span class="sxs-lookup"><span data-stu-id="b6320-108">Event Source</span></span>|<span data-ttu-id="b6320-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="b6320-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="b6320-110">组件</span><span class="sxs-lookup"><span data-stu-id="b6320-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="b6320-111">符号名称</span><span class="sxs-lookup"><span data-stu-id="b6320-111">Symbolic Name</span></span>||  
|<span data-ttu-id="b6320-112">消息正文</span><span class="sxs-lookup"><span data-stu-id="b6320-112">Message Text</span></span>|<span data-ttu-id="b6320-113">已设置发布 [%s] 的阈值 [%s:%s]。</span><span class="sxs-lookup"><span data-stu-id="b6320-113">The threshold [%s:%s] for the publication [%s] has been set.</span></span> <span data-ttu-id="b6320-114">此发布的一个或多个订阅已过期。</span><span class="sxs-lookup"><span data-stu-id="b6320-114">One or more subscriptions to this publication have expired.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="b6320-115">说明</span><span class="sxs-lookup"><span data-stu-id="b6320-115">Explanation</span></span>  
 <span data-ttu-id="b6320-116">使用复制可以对一些情况启用警告。</span><span class="sxs-lookup"><span data-stu-id="b6320-116">Replication lets you enable warnings for several conditions.</span></span> <span data-ttu-id="b6320-117">例如，订阅即将过期时，即可以发出此警告。</span><span class="sxs-lookup"><span data-stu-id="b6320-117">This includes imminent subscription expiration.</span></span> <span data-ttu-id="b6320-118">如果在指定的“保持期” 内未同步订阅，则订阅会过期。</span><span class="sxs-lookup"><span data-stu-id="b6320-118">Subscriptions can expire if they are not synchronized within a specified *retention period*.</span></span> <span data-ttu-id="b6320-119">有关详细信息，请参阅 [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md)。</span><span class="sxs-lookup"><span data-stu-id="b6320-119">For more information, see [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md).</span></span>  
  
 <span data-ttu-id="b6320-120">使用复制监视器或 [sp_replmonitorchangepublicationthreshold](/sql/relational-databases/system-stored-procedures/sp-replmonitorchangepublicationthreshold-transact-sql)启用警告时，请指定阈值以确定何时触发警告。</span><span class="sxs-lookup"><span data-stu-id="b6320-120">When you enable a warning by using Replication Monitor or [sp_replmonitorchangepublicationthreshold](/sql/relational-databases/system-stored-procedures/sp-replmonitorchangepublicationthreshold-transact-sql), you specify a threshold that determines when a warning is triggered.</span></span> <span data-ttu-id="b6320-121">达到或超过该阈值时，复制监视器中将显示警告，并且将一个事件写入 Windows 事件日志。</span><span class="sxs-lookup"><span data-stu-id="b6320-121">When that threshold is met or exceeded, a warning is displayed in Replication Monitor, and an event is written to the Windows event log.</span></span> <span data-ttu-id="b6320-122">达到阈值还会触发 SQL Server 代理警报。</span><span class="sxs-lookup"><span data-stu-id="b6320-122">Reaching a threshold can also trigger a SQL Server Agent alert.</span></span> <span data-ttu-id="b6320-123">有关详细信息，请参阅[在复制监视器中设置阈值和警告](monitor/set-thresholds-and-warnings-in-replication-monitor.md)和[以编程方式监视复制](monitoring-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="b6320-123">For more information, see [Set Thresholds and Warnings in Replication Monitor](monitor/set-thresholds-and-warnings-in-replication-monitor.md) and [Programmatically Monitor Replication](monitoring-replication.md).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b6320-124">用户操作</span><span class="sxs-lookup"><span data-stu-id="b6320-124">User Action</span></span>  
 <span data-ttu-id="b6320-125">对此问题的解决依赖于引起警告的原因：</span><span class="sxs-lookup"><span data-stu-id="b6320-125">The resolution for this issue depends on the reason the warning was raised:</span></span>  
  
-   <span data-ttu-id="b6320-126">如果已超过阈值，但订阅尚未过期，则同步订阅。</span><span class="sxs-lookup"><span data-stu-id="b6320-126">If the threshold has been exceeded, but the subscription has not yet expired, synchronize the subscription.</span></span> <span data-ttu-id="b6320-127">有关详细信息，请参阅 [同步数据](synchronize-data.md)。</span><span class="sxs-lookup"><span data-stu-id="b6320-127">For more information, see [Synchronize Data](synchronize-data.md).</span></span>  
  
-   <span data-ttu-id="b6320-128">如果代理已经运行，但尚未正确复制更改，则会导致订阅过期。</span><span class="sxs-lookup"><span data-stu-id="b6320-128">If the agent has been running, but has not been replicating changes properly, this can cause the subscription to expire.</span></span> <span data-ttu-id="b6320-129">对于事务复制，请确保分发代理和日志读取器代理正在运行。</span><span class="sxs-lookup"><span data-stu-id="b6320-129">For transactional replication, make sure that the Distribution Agent and Log Reader Agent are running.</span></span> <span data-ttu-id="b6320-130">对于合并复制，请确保合并代理正在运行。</span><span class="sxs-lookup"><span data-stu-id="b6320-130">For merge replication, make sure the Merge Agent is running.</span></span> <span data-ttu-id="b6320-131">有关如何启动这些代理的信息，请参阅[启动和停止复制代理 (SQL Server Management Studio)](agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) 和[复制代理可执行文件概念](concepts/replication-agent-executables-concepts.md)。</span><span class="sxs-lookup"><span data-stu-id="b6320-131">For information about how to start these agents, see [Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;](agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) and [Replication Agent Executables Concepts](concepts/replication-agent-executables-concepts.md).</span></span>  
  
-   <span data-ttu-id="b6320-132">如果订阅已过期，则必须重新初始化订阅或删除然后重新创建订阅，具体取决于订阅的类型和已过期多长时间。</span><span class="sxs-lookup"><span data-stu-id="b6320-132">If the subscription has expired, it must either be reinitialized or dropped and re-created, depending on the type of subscription and how long it has been expired.</span></span> <span data-ttu-id="b6320-133">有关详细信息，请参阅 [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md)。</span><span class="sxs-lookup"><span data-stu-id="b6320-133">For more information, see [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6320-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b6320-134">See Also</span></span>  
 [<span data-ttu-id="b6320-135">错误和事件参考（复制）</span><span class="sxs-lookup"><span data-stu-id="b6320-135">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
