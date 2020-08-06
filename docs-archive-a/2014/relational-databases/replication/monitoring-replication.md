---
title: 监视复制 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- monitoring performance [SQL Server replication], about monitoring replication
- transactional replication, monitoring
- monitoring [SQL Server replication]
- merge replication monitoring [SQL Server replication]
- snapshot replication [SQL Server], monitoring
- replication [SQL Server], monitoring
- administering replication, monitoring
ms.assetid: f182f43a-6af8-45bc-a708-08d5f7a6984a
author: rothja
ms.author: jroth
ms.openlocfilehash: df2760e4ce04c95f38ceb9dfe9fa9f79c4c467f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690563"
---
# <a name="monitoring-replication"></a><span data-ttu-id="32c1e-102">监视（复制）</span><span class="sxs-lookup"><span data-stu-id="32c1e-102">Monitoring (Replication)</span></span>
  <span data-ttu-id="32c1e-103">监视复制拓扑是部署复制的一个重要方面。</span><span class="sxs-lookup"><span data-stu-id="32c1e-103">Monitoring a replication topology is an important aspect of deploying replication.</span></span> <span data-ttu-id="32c1e-104">因为复制活动是分布式的，所以跟踪复制过程中涉及的所有计算机的活动和状态非常有必要。</span><span class="sxs-lookup"><span data-stu-id="32c1e-104">Because replication activity is distributed, it is essential to track activity and status across all computers involved in replication.</span></span> <span data-ttu-id="32c1e-105">以下工具可用于监视复制：</span><span class="sxs-lookup"><span data-stu-id="32c1e-105">The following tools can be used to monitor replication:</span></span>  
  
-   [!INCLUDE[msCoName](../../includes/msCoName-md.md)]<span data-ttu-id="32c1e-106">[!INCLUDE[ssNoVersion](../../includes/ssNoVersion-md.md)]复制监视器</span><span class="sxs-lookup"><span data-stu-id="32c1e-106">[!INCLUDE[ssNoVersion](../../includes/ssNoVersion-md.md)] Replication Monitor</span></span>  
  
     <span data-ttu-id="32c1e-107">复制监视器是监视复制最重要的工具，它可以显示以发布服务器为中心的所有复制活动视图。</span><span class="sxs-lookup"><span data-stu-id="32c1e-107">Replication Monitor is the most important tool for monitoring replication, presenting a Publisher-focused view of all replication activity.</span></span> <span data-ttu-id="32c1e-108">有关详细信息，请参阅[通过复制监视器监视性能](monitor/monitor-performance-with-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="32c1e-108">For more information, see [Monitor performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md).</span></span>  
  
-   [!INCLUDE[msCoName](../../includes/msCoName-md.md)] <span data-ttu-id="32c1e-109">[!INCLUDE[ssManStudioFull](../../includes/ssManStudioFull-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32c1e-109">[!INCLUDE[ssManStudioFull](../../includes/ssManStudioFull-md.md)]</span></span>  
  
     [!INCLUDE[ssManStudio](../../includes/ssManStudio-md.md)] <span data-ttu-id="32c1e-110">提供对复制监视器的访问。</span><span class="sxs-lookup"><span data-stu-id="32c1e-110">provides access to Replication Monitor.</span></span> <span data-ttu-id="32c1e-111">它还允许你查看当前状态以及由下列代理记录的最后一条消息，还允许你启动和停止每个代理：日志读取器代理、快照代理、合并代理和分发代理。</span><span class="sxs-lookup"><span data-stu-id="32c1e-111">It also allows you to view the current status and last message logged by the following agents and allows you start and stop each agent: Log Reader Agent, Snapshot Agent, Merge Agent, and Distribution Agent.</span></span> <span data-ttu-id="32c1e-112">有关详细信息，请参阅 [Monitor Replication Agents](monitor/monitor-replication-agents.md)。</span><span class="sxs-lookup"><span data-stu-id="32c1e-112">For more information, see [Monitor Replication Agents](monitor/monitor-replication-agents.md).</span></span>  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="32c1e-113">和复制管理对象 (RMO)</span><span class="sxs-lookup"><span data-stu-id="32c1e-113">and Replication Management Objects (RMO)</span></span>  
  
     <span data-ttu-id="32c1e-114">两个界面都可用于监视分发服务器上的所有复制类型。</span><span class="sxs-lookup"><span data-stu-id="32c1e-114">Both interfaces allow you to monitor all types of replication from the Distributor.</span></span> <span data-ttu-id="32c1e-115">合并复制还提供从发布服务器监视复制的功能。</span><span class="sxs-lookup"><span data-stu-id="32c1e-115">Merge replication also provides the ability to monitor replication from the Subscriber.</span></span>  
  
-   <span data-ttu-id="32c1e-116">复制代理事件的警报</span><span class="sxs-lookup"><span data-stu-id="32c1e-116">Alerts for replication agent events</span></span>  
  
     <span data-ttu-id="32c1e-117">复制提供了许多复制代理事件的预定义警报，如果有必要，您还可以创建其他警报。</span><span class="sxs-lookup"><span data-stu-id="32c1e-117">Replication provides a number of predefined alerts for replication agent events, and you can create additional alerts if necessary.</span></span> <span data-ttu-id="32c1e-118">警报用于触发对某个事件的自动响应和/或用于通知管理员。</span><span class="sxs-lookup"><span data-stu-id="32c1e-118">Alerts can be used to trigger an automated response to an event and/or notify an administrator.</span></span> <span data-ttu-id="32c1e-119">有关详细信息，请参阅[对复制代理事件使用警报](agents/use-alerts-for-replication-agent-events.md)。</span><span class="sxs-lookup"><span data-stu-id="32c1e-119">For more information, see [Use Alerts for Replication Agent Events](agents/use-alerts-for-replication-agent-events.md).</span></span>  
  
-   <span data-ttu-id="32c1e-120">系统监视器</span><span class="sxs-lookup"><span data-stu-id="32c1e-120">System Monitor</span></span>  
  
     <span data-ttu-id="32c1e-121">系统监视器对性能监视很有用，它可为复制提供多个计数器。</span><span class="sxs-lookup"><span data-stu-id="32c1e-121">System Monitor can be useful for monitoring performance, providing a number of counters for replication.</span></span> <span data-ttu-id="32c1e-122">有关详细信息，请参阅 [Monitoring Replication with System Monitor](monitor/monitoring-replication-with-system-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="32c1e-122">For more information, see [Monitoring Replication with System Monitor](monitor/monitoring-replication-with-system-monitor.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32c1e-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="32c1e-123">See Also</span></span>  
 <span data-ttu-id="32c1e-124">[复制管理常见问题解答](administration/frequently-asked-questions-for-replication-administrators.md) </span><span class="sxs-lookup"><span data-stu-id="32c1e-124">[Replication Administration FAQ](administration/frequently-asked-questions-for-replication-administrators.md) </span></span>  
 [<span data-ttu-id="32c1e-125">Best Practices for Replication Administration</span><span class="sxs-lookup"><span data-stu-id="32c1e-125">Best Practices for Replication Administration</span></span>](administration/best-practices-for-replication-administration.md)   

  
  
