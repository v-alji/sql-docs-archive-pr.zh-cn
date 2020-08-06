---
title: MSSQL_ENG014161 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014161 error
ms.assetid: 4b983e76-bb77-43c5-b44b-19919d3da619
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e8cf85181e444385e1a3908761ba71414b68cf3e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576659"
---
# <a name="mssql_eng014161"></a><span data-ttu-id="8f470-102">MSSQL_ENG014161</span><span class="sxs-lookup"><span data-stu-id="8f470-102">MSSQL_ENG014161</span></span>
    
## <a name="message-details"></a><span data-ttu-id="8f470-103">消息详细信息</span><span class="sxs-lookup"><span data-stu-id="8f470-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8f470-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="8f470-104">Product Name</span></span>|<span data-ttu-id="8f470-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="8f470-105">SQL Server</span></span>|  
|<span data-ttu-id="8f470-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="8f470-106">Event ID</span></span>|<span data-ttu-id="8f470-107">14161</span><span class="sxs-lookup"><span data-stu-id="8f470-107">14161</span></span>|  
|<span data-ttu-id="8f470-108">事件源</span><span class="sxs-lookup"><span data-stu-id="8f470-108">Event Source</span></span>|<span data-ttu-id="8f470-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="8f470-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="8f470-110">组件</span><span class="sxs-lookup"><span data-stu-id="8f470-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="8f470-111">符号名称</span><span class="sxs-lookup"><span data-stu-id="8f470-111">Symbolic Name</span></span>||  
|<span data-ttu-id="8f470-112">消息正文</span><span class="sxs-lookup"><span data-stu-id="8f470-112">Message Text</span></span>|<span data-ttu-id="8f470-113">已设置发布 [%s] 的阈值 [%s:%s]。</span><span class="sxs-lookup"><span data-stu-id="8f470-113">The threshold [%s:%s] for the publication [%s] has been set.</span></span> <span data-ttu-id="8f470-114">请确保日志读取器和分发代理正在运行并且可以满足滞后时间要求。</span><span class="sxs-lookup"><span data-stu-id="8f470-114">Make sure that the logreader and distribution agents are running and can match the latency requirement.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="8f470-115">说明</span><span class="sxs-lookup"><span data-stu-id="8f470-115">Explanation</span></span>  
 <span data-ttu-id="8f470-116">使用复制可以对一些情况启用警告。</span><span class="sxs-lookup"><span data-stu-id="8f470-116">Replication lets you enable warnings for several conditions.</span></span> <span data-ttu-id="8f470-117">这些情况包括超过了事务订阅的指定滞后时间。</span><span class="sxs-lookup"><span data-stu-id="8f470-117">This includes exceeding a specified latency for transactional subscriptions.</span></span> <span data-ttu-id="8f470-118">滞后时间是指在发布服务器上提交数据更改到在订阅服务器上提交相应更改之间所用的时间。</span><span class="sxs-lookup"><span data-stu-id="8f470-118">Latency is the period of time that elapses between a data change being committed at the Publisher and the corresponding change being committed at the Subscriber.</span></span>  
  
 <span data-ttu-id="8f470-119">使用复制监视器或 [sp_replmonitorchangepublicationthreshold](/sql/relational-databases/system-stored-procedures/sp-replmonitorchangepublicationthreshold-transact-sql)启用警告时，请指定阈值以确定何时触发警告。</span><span class="sxs-lookup"><span data-stu-id="8f470-119">When you enable a warning by using Replication Monitor or [sp_replmonitorchangepublicationthreshold](/sql/relational-databases/system-stored-procedures/sp-replmonitorchangepublicationthreshold-transact-sql), you specify a threshold that determines when a warning is triggered.</span></span> <span data-ttu-id="8f470-120">达到或超过该阈值时，复制监视器中将显示警告，并且将一个事件写入 Windows 事件日志。</span><span class="sxs-lookup"><span data-stu-id="8f470-120">When that threshold is met or exceeded, a warning is displayed in Replication Monitor, and an event is written to the Windows event log.</span></span> <span data-ttu-id="8f470-121">达到阈值还会触发 SQL Server 代理警报。</span><span class="sxs-lookup"><span data-stu-id="8f470-121">Reaching a threshold can also trigger a SQL Server Agent alert.</span></span> <span data-ttu-id="8f470-122">有关详细信息，请参阅[在复制监视器中设置阈值和警告](monitor/set-thresholds-and-warnings-in-replication-monitor.md)和[以编程方式监视复制](monitoring-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="8f470-122">For more information, see [Set Thresholds and Warnings in Replication Monitor](monitor/set-thresholds-and-warnings-in-replication-monitor.md) and [Programmatically Monitor Replication](monitoring-replication.md).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="8f470-123">用户操作</span><span class="sxs-lookup"><span data-stu-id="8f470-123">User Action</span></span>  
 <span data-ttu-id="8f470-124">如果订阅超过滞后时间阈值，则必须确定是系统发生性能问题还是应当调整阈值。</span><span class="sxs-lookup"><span data-stu-id="8f470-124">If a subscription exceeds a latency threshold, you must determine whether there is a performance issue with the system or whether the threshold should be adjusted.</span></span> <span data-ttu-id="8f470-125">配置复制后，请确立一个性能基准，以便于确定复制在通常用于应用程序和拓扑的常见工作负荷中的行为方式。</span><span class="sxs-lookup"><span data-stu-id="8f470-125">After you configure replication, develop a performance baseline that will let you determine how replication behaves with a workload that is typical for your applications and topology.</span></span> <span data-ttu-id="8f470-126">在此基准中包含滞后时间，以便可以设置适当的阈值。</span><span class="sxs-lookup"><span data-stu-id="8f470-126">Include latency in this baseline so that you can set an appropriate value for the threshold.</span></span>  
  
 <span data-ttu-id="8f470-127">如果阈值适当，但超过了该阈值，则必须确定系统何处存在性能瓶颈。</span><span class="sxs-lookup"><span data-stu-id="8f470-127">If the threshold value is appropriate, but it is being exceeded, you must determine where the performance bottleneck is in the system.</span></span> <span data-ttu-id="8f470-128">有关如何监视复制性能和对其进行故障排除的详细信息，请参阅下列主题：</span><span class="sxs-lookup"><span data-stu-id="8f470-128">For more information about how to monitor and troubleshoot replication performance, see the following topics:</span></span>  
  
-   [<span data-ttu-id="8f470-129">为事务复制测量滞后时间和验证连接</span><span class="sxs-lookup"><span data-stu-id="8f470-129">Measure Latency and Validate Connections for Transactional Replication</span></span>](monitor/measure-latency-and-validate-connections-for-transactional-replication.md)  
  
-   [<span data-ttu-id="8f470-130">用复制监视器监视性能</span><span class="sxs-lookup"><span data-stu-id="8f470-130">Monitor Performance with Replication Monitor</span></span>](monitor/monitor-performance-with-replication-monitor.md)  
  
## <a name="see-also"></a><span data-ttu-id="8f470-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8f470-131">See Also</span></span>  
 [<span data-ttu-id="8f470-132">错误和事件参考（复制）</span><span class="sxs-lookup"><span data-stu-id="8f470-132">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
