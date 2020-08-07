---
title: 缓存、刷新和复制监视器性能 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- monitoring performance [SQL Server replication], Replication Monitor
- cache [SQL Server], replication
- Replication Monitor, caching
- refreshing data
- Replication Monitor, refreshing
ms.assetid: a2d8b666-ed41-4f86-b2b8-c8e118416ab7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b04a91e971e65d19c66cc36f142d8c4764b1b05a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580132"
---
# <a name="caching-refresh-and-replication-monitor-performance"></a><span data-ttu-id="3a340-102">缓存、刷新和复制监视器性能</span><span class="sxs-lookup"><span data-stu-id="3a340-102">Caching, Refresh, and Replication Monitor Performance</span></span>
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)]<span data-ttu-id="3a340-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]复制监视器旨在有效地监视生产系统中的大量计算机。</span><span class="sxs-lookup"><span data-stu-id="3a340-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Replication Monitor is designed to efficiently monitor a large number of computers in a production system.</span></span> <span data-ttu-id="3a340-104">系统定期对复制监视器用来执行计算和收集数据的查询进行缓存和刷新。</span><span class="sxs-lookup"><span data-stu-id="3a340-104">The queries that Replication Monitor uses to perform calculations and gather data are cached and refreshed on a periodic basis.</span></span> <span data-ttu-id="3a340-105">缓存可减少在复制监视器中查看不同页时所需的查询和计算次数，并可很好地满足多个用户的监视需要。</span><span class="sxs-lookup"><span data-stu-id="3a340-105">Caching reduces the number of queries and calculations required as you view different pages in Replication Monitor and allows monitoring to scale well for multiple users.</span></span>  
  
 <span data-ttu-id="3a340-106">缓存刷新由 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 代理作业“用于分发的复制监视刷新器” \*\*\*\* 进行处理。</span><span class="sxs-lookup"><span data-stu-id="3a340-106">Cache refresh is handled by a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent job, the **Replication monitoring refresher for distribution**.</span></span> <span data-ttu-id="3a340-107">作业是连续运行的，但缓存刷新计划取决于上次刷新后等待的特定时间：</span><span class="sxs-lookup"><span data-stu-id="3a340-107">The job runs continuously, but the cache refresh schedule is based on waiting a certain amount time after the previous refresh:</span></span>  
  
-   <span data-ttu-id="3a340-108">如果上次创建缓存后，代理历史记录有更改，则等待时间是以下时间中的最小值：4 秒或创建上一个缓存所用的时间。</span><span class="sxs-lookup"><span data-stu-id="3a340-108">If there were agent history changes since the cache was last created, the wait time is the minimum of: 4 seconds; or the amount of time taken to create the previous cache.</span></span>  
  
-   <span data-ttu-id="3a340-109">如果上次创建缓存后，代理历史记录没有更改（可能有其他更改），则等待时间是以下时间中的最大值：30 秒或创建上一个缓存所用的时间。</span><span class="sxs-lookup"><span data-stu-id="3a340-109">If there were no agent history changes since the cache was last created (there could have been other changes), the wait time is the maximum of: 30 seconds; or the amount of time taken to create the previous cache.</span></span>  
  
## <a name="refreshing-the-replication-monitor-user-interface"></a><span data-ttu-id="3a340-110">刷新复制监视器用户界面</span><span class="sxs-lookup"><span data-stu-id="3a340-110">Refreshing the Replication Monitor User Interface</span></span>  
 <span data-ttu-id="3a340-111">可以通过下列方式刷新复制监视器用户界面：</span><span class="sxs-lookup"><span data-stu-id="3a340-111">The Replication Monitor user interface can be refreshed in the following ways:</span></span>  
  
-   <span data-ttu-id="3a340-112">复制监视器主窗口（包括所有选项卡），默认每 5 秒钟自动刷新一次。</span><span class="sxs-lookup"><span data-stu-id="3a340-112">The main Replication Monitor window (including all tabs), automatically refreshes by default every five seconds.</span></span> <span data-ttu-id="3a340-113">自动刷新不强制刷新缓存；用户界面显示缓存中最新的数据。</span><span class="sxs-lookup"><span data-stu-id="3a340-113">Automatic refreshes do not force a refresh of the cache; the user interface displays the most recent version of the data from the cache.</span></span> <span data-ttu-id="3a340-114">可以通过编辑发布服务器设置为发布服务器的所有关联窗口自定义刷新速率。</span><span class="sxs-lookup"><span data-stu-id="3a340-114">You can customize the refresh rate used for all windows associated with a Publisher by editing the Publisher settings.</span></span> <span data-ttu-id="3a340-115">也可以禁用发布服务器的自动刷新。</span><span class="sxs-lookup"><span data-stu-id="3a340-115">You can also disable automatic refreshes for a Publisher.</span></span>  
  
-   <span data-ttu-id="3a340-116">默认情况下，从复制监视器启动的详细信息窗口不自动刷新，但与正在同步的合并订阅相关的窗口除外。</span><span class="sxs-lookup"><span data-stu-id="3a340-116">The detail windows that are launched from Replication Monitor are not automatically refreshed by default, with the exception of windows related to merge subscriptions that are synchronizing.</span></span> <span data-ttu-id="3a340-117">如果指定详细信息窗口自动刷新，则它们的刷新速率与复制监视器主窗口相同。</span><span class="sxs-lookup"><span data-stu-id="3a340-117">If you specify that detail windows should automatically refresh, they refresh on the same schedule as the main Replication Monitor window.</span></span>  
  
-   <span data-ttu-id="3a340-118">所有窗口都可以手动刷新，方法是按 F5 或右键单击复制监视器树中的节点，再单击 **“刷新”**。</span><span class="sxs-lookup"><span data-stu-id="3a340-118">All windows can be manually refreshed by pressing F5 or by right-clicking a node in the Replication Monitor tree and clicking **Refresh**.</span></span> <span data-ttu-id="3a340-119">手动刷新会强制刷新缓存。</span><span class="sxs-lookup"><span data-stu-id="3a340-119">Manual refreshes force a refresh of the cache.</span></span>  
  
 <span data-ttu-id="3a340-120">有关详细信息，请参阅[刷新复制监视器中的数据](refresh-data-in-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="3a340-120">For more information, see [Refresh Data in Replication Monitor](refresh-data-in-replication-monitor.md).</span></span>  
  
## <a name="performance-considerations"></a><span data-ttu-id="3a340-121">性能注意事项</span><span class="sxs-lookup"><span data-stu-id="3a340-121">Performance Considerations</span></span>  
 <span data-ttu-id="3a340-122">尽管复制监视器旨在高效运行，但请注意以下事项：</span><span class="sxs-lookup"><span data-stu-id="3a340-122">Although Replication Monitor is designed to run efficiently, be aware of the following:</span></span>  
  
-   <span data-ttu-id="3a340-123">如果有大量的发布或订阅，请为用户界面设置一个频率较低的自动刷新计划。</span><span class="sxs-lookup"><span data-stu-id="3a340-123">If you have a large number of publications or subscriptions, consider setting a less frequent automatic refresh schedule for the user interface.</span></span>  
  
-   <span data-ttu-id="3a340-124">避免并发运行多个复制监视器实例。</span><span class="sxs-lookup"><span data-stu-id="3a340-124">Avoid concurrently running multiple instances of Replication Monitor.</span></span>  
  
-   <span data-ttu-id="3a340-125">避免注册大量分发服务器，并避免设置复制监视器自动连接到所有分发服务器上。</span><span class="sxs-lookup"><span data-stu-id="3a340-125">Avoid registering a large number of Distributors and setting Replication Monitor to automatically connect to all of them.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a340-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3a340-126">See Also</span></span>  
 <span data-ttu-id="3a340-127">[运行复制维护作业 (SQL Server Management Studio)](../../../ssms/sql-server-management-studio-ssms.md) </span><span class="sxs-lookup"><span data-stu-id="3a340-127">[Run Replication Maintenance Jobs &#40;SQL Server Management Studio&#41;](../../../ssms/sql-server-management-studio-ssms.md) </span></span>  
 [<span data-ttu-id="3a340-128">监视复制</span><span class="sxs-lookup"><span data-stu-id="3a340-128">Monitoring Replication</span></span>](../monitoring-replication.md)  
  
  
