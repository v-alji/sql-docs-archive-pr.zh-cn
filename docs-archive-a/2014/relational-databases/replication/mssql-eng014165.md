---
title: MSSQL_ENG014165 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014165 error
ms.assetid: 7bb07672-310c-4f51-ae76-c55e7c8d51ea
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8ac0d9c0bad79b13676296e4a041f0141d134c75
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690565"
---
# <a name="mssql_eng014165"></a><span data-ttu-id="8b764-102">MSSQL_ENG014165</span><span class="sxs-lookup"><span data-stu-id="8b764-102">MSSQL_ENG014165</span></span>
    
## <a name="message-details"></a><span data-ttu-id="8b764-103">消息详细信息</span><span class="sxs-lookup"><span data-stu-id="8b764-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8b764-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="8b764-104">Product Name</span></span>|<span data-ttu-id="8b764-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="8b764-105">SQL Server</span></span>|  
|<span data-ttu-id="8b764-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="8b764-106">Event ID</span></span>|<span data-ttu-id="8b764-107">14165</span><span class="sxs-lookup"><span data-stu-id="8b764-107">14165</span></span>|  
|<span data-ttu-id="8b764-108">事件源</span><span class="sxs-lookup"><span data-stu-id="8b764-108">Event Source</span></span>|<span data-ttu-id="8b764-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="8b764-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="8b764-110">组件</span><span class="sxs-lookup"><span data-stu-id="8b764-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="8b764-111">符号名称</span><span class="sxs-lookup"><span data-stu-id="8b764-111">Symbolic Name</span></span>||  
|<span data-ttu-id="8b764-112">消息正文</span><span class="sxs-lookup"><span data-stu-id="8b764-112">Message Text</span></span>|<span data-ttu-id="8b764-113">已设置发布 [%s] 的阈值 [%s:%s]。</span><span class="sxs-lookup"><span data-stu-id="8b764-113">The threshold [%s:%s] for the publication [%s] has been set.</span></span> <span data-ttu-id="8b764-114">请确保合并代理正在运行且符合要求。</span><span class="sxs-lookup"><span data-stu-id="8b764-114">Please make sure that the merge agent is running and can match the expected requirement.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="8b764-115">说明</span><span class="sxs-lookup"><span data-stu-id="8b764-115">Explanation</span></span>  
 <span data-ttu-id="8b764-116">使用复制可以对一些情况启用警告。</span><span class="sxs-lookup"><span data-stu-id="8b764-116">Replication lets you enable warnings for several conditions.</span></span> <span data-ttu-id="8b764-117">这包括在合并发布服务器和订阅服务器之间同步更改时处理大量行失败的情况。</span><span class="sxs-lookup"><span data-stu-id="8b764-117">This includes failure to process a sufficient number of rows when synchronizing changes between a merge Publisher and Subscriber.</span></span> <span data-ttu-id="8b764-118">可以为 LAN 连接和拨号连接指定不同的连接次数。</span><span class="sxs-lookup"><span data-stu-id="8b764-118">Different times can be specified for LAN connections and dial-up connections.</span></span>  
  
 <span data-ttu-id="8b764-119">使用复制监视器或 [sp_replmonitorchangepublicationthreshold](/sql/relational-databases/system-stored-procedures/sp-replmonitorchangepublicationthreshold-transact-sql)启用警告时，请指定阈值以确定何时触发警告。</span><span class="sxs-lookup"><span data-stu-id="8b764-119">When you enable a warning by using Replication Monitor or [sp_replmonitorchangepublicationthreshold](/sql/relational-databases/system-stored-procedures/sp-replmonitorchangepublicationthreshold-transact-sql), you specify a threshold that determines when a warning is triggered.</span></span> <span data-ttu-id="8b764-120">达到或超过该阈值时，复制监视器中将显示警告，并且将一个事件写入 Windows 事件日志。</span><span class="sxs-lookup"><span data-stu-id="8b764-120">When that threshold is met or exceeded, a warning is displayed in Replication Monitor, and an event is written to the Windows event log.</span></span> <span data-ttu-id="8b764-121">达到阈值还会触发 SQL Server 代理警报。</span><span class="sxs-lookup"><span data-stu-id="8b764-121">Reaching a threshold can also trigger a SQL Server Agent alert.</span></span> <span data-ttu-id="8b764-122">有关详细信息，请参阅[在复制监视器中设置阈值和警告](monitor/set-thresholds-and-warnings-in-replication-monitor.md)和[以编程方式监视复制](monitoring-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="8b764-122">For more information, see [Set Thresholds and Warnings in Replication Monitor](monitor/set-thresholds-and-warnings-in-replication-monitor.md) and [Programmatically Monitor Replication](monitoring-replication.md).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="8b764-123">用户操作</span><span class="sxs-lookup"><span data-stu-id="8b764-123">User Action</span></span>  
 <span data-ttu-id="8b764-124">如果订阅未达到行处理阈值，则必须确定是系统发生性能问题还是应当调整阈值。</span><span class="sxs-lookup"><span data-stu-id="8b764-124">If a subscription is not meeting a row processing threshold, you must determine whether there is a performance issue with the system or whether the threshold should be adjusted.</span></span> <span data-ttu-id="8b764-125">配置复制后，请确立一个性能基准，以便于确定复制在通常用于应用程序和拓扑的常见工作负荷中的行为方式。</span><span class="sxs-lookup"><span data-stu-id="8b764-125">After you configure replication, develop a performance baseline that will let you determine how replication behaves with a workload that is typical for your applications and topology.</span></span> <span data-ttu-id="8b764-126">将已处理行的数目包括在该基准中，以便可以为阈值设置合适的值。</span><span class="sxs-lookup"><span data-stu-id="8b764-126">Include number of rows processed in this baseline so that you can set an appropriate value for the threshold.</span></span>  
  
 <span data-ttu-id="8b764-127">如果阈值适当，但超过了该阈值，则必须确定系统何处存在性能瓶颈。</span><span class="sxs-lookup"><span data-stu-id="8b764-127">If the threshold value is appropriate, but it is being exceeded, you must determine where the performance bottleneck is in the system.</span></span> <span data-ttu-id="8b764-128">有关如何监视复制性能和对其进行故障排除的详细信息，请参阅下列主题：</span><span class="sxs-lookup"><span data-stu-id="8b764-128">For more information about how to monitor and troubleshoot replication performance, see the following topics:</span></span>  
  
-   <span data-ttu-id="8b764-129">[用复制监视器监视性能](monitor/monitor-performance-with-replication-monitor.md)（特别是“查看合并复制的详细同步性能”一节）</span><span class="sxs-lookup"><span data-stu-id="8b764-129">[Monitor Performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md) (especially the section "Viewing Detailed Synchronization Performance for Merge Replication")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b764-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8b764-130">See Also</span></span>  
 [<span data-ttu-id="8b764-131">错误和事件参考（复制）</span><span class="sxs-lookup"><span data-stu-id="8b764-131">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  