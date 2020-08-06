---
title: SQL Server 复制 "发布服务器信息" 对话框 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publisherinfo.publications.f1
ms.assetid: 0b2e3d4e-03b7-4c31-8f96-48648d750010
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d3797ae4f9fe8f42b4abec715c63bc627c2a62cf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688807"
---
# <a name="sql-server-replication-publisher-information-dialog-box"></a><span data-ttu-id="aaf2f-102">SQL Server 复制 "发布服务器信息" 对话框</span><span class="sxs-lookup"><span data-stu-id="aaf2f-102">SQL Server Replication 'Publisher Information' dialog box</span></span>
  <span data-ttu-id="aaf2f-103">**“发布”** 选项卡提供在左窗格中选择的发布服务器的所有发布的摘要信息。</span><span class="sxs-lookup"><span data-stu-id="aaf2f-103">The **Publications** tab provides summary information for all publications at the Publisher selected in the left pane.</span></span>  
  
## <a name="options"></a><span data-ttu-id="aaf2f-104">选项</span><span class="sxs-lookup"><span data-stu-id="aaf2f-104">Options</span></span>  
 <span data-ttu-id="aaf2f-105">若要更改网格显示数据的方式，请右键单击网格，然后单击以下选项之一：</span><span class="sxs-lookup"><span data-stu-id="aaf2f-105">To change the way that the grid displays data, right-click the grid, and then click one of the following options:</span></span>  
  
-   <span data-ttu-id="aaf2f-106">**排序**：按 **“列排序”** 对话框中的一列或多列排序。</span><span class="sxs-lookup"><span data-stu-id="aaf2f-106">**Sort**: Sort on one or more columns in the **Sort Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="aaf2f-107">**选择要显示的列**：选择要显示哪些列以及要在 **“选择列”** 对话框中以何种顺序显示它们。</span><span class="sxs-lookup"><span data-stu-id="aaf2f-107">**Choose Columns to Show**: Select which columns to display and the order in which to display them in the **Choose Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="aaf2f-108">**筛选器**：根据 **“筛选设置”** 对话框中的列值筛选网格中的行。</span><span class="sxs-lookup"><span data-stu-id="aaf2f-108">**Filter**: Filter rows in the grid based on column values in the **Filter Settings** dialog box.</span></span>  
  
-   <span data-ttu-id="aaf2f-109">**清除筛选器**：清除网格的任何筛选设置。</span><span class="sxs-lookup"><span data-stu-id="aaf2f-109">**Clear Filter**: Clear any filter settings for the grid.</span></span>  
  
 <span data-ttu-id="aaf2f-110">筛选设置是特定于每个网格的。</span><span class="sxs-lookup"><span data-stu-id="aaf2f-110">Filter settings are specific to each grid.</span></span> <span data-ttu-id="aaf2f-111">列的选择和排序应用于同一类型的所有网格，如每个发布服务器的发布网格。</span><span class="sxs-lookup"><span data-stu-id="aaf2f-111">Column selection and sorting are applied to all grids of the same type, such as the publications grid for each Publisher.</span></span>  
  
 <span data-ttu-id="aaf2f-112">**Status**</span><span class="sxs-lookup"><span data-stu-id="aaf2f-112">**Status**</span></span>  
 <span data-ttu-id="aaf2f-113">每个发布的状态，由其订阅的最高优先级状态决定。</span><span class="sxs-lookup"><span data-stu-id="aaf2f-113">The status of each publication, which is determined by the highest priority status of its subscriptions.</span></span> <span data-ttu-id="aaf2f-114">默认情况下，包含发布信息的网格按 **“状态”** 列排序。</span><span class="sxs-lookup"><span data-stu-id="aaf2f-114">By default, the grid containing publication information is sorted by the **Status** column.</span></span> <span data-ttu-id="aaf2f-115">下面的列表显示了可能的状态值以及这些值的排序顺序（例如，错误项始终显示在该网格的顶部）：</span><span class="sxs-lookup"><span data-stu-id="aaf2f-115">The following list shows the possible status values and the sort order for the values (for example, errors are always shown at the top of the grid):</span></span>  
  
-   <span data-ttu-id="aaf2f-116">错误</span><span class="sxs-lookup"><span data-stu-id="aaf2f-116">Error</span></span>  
  
-   <span data-ttu-id="aaf2f-117">“严重”状态下的性能</span><span class="sxs-lookup"><span data-stu-id="aaf2f-117">Performance critical</span></span>  
  
-   <span data-ttu-id="aaf2f-118">正在重试失败的命令</span><span class="sxs-lookup"><span data-stu-id="aaf2f-118">Retrying failed command</span></span>  
  
-   <span data-ttu-id="aaf2f-119">OK</span><span class="sxs-lookup"><span data-stu-id="aaf2f-119">OK</span></span>  
  
 <span data-ttu-id="aaf2f-120">状态值 **“‘严重’状态下的性能”** 与事务订阅和合并订阅相关；只有设置阈值后，才可以显示该值。</span><span class="sxs-lookup"><span data-stu-id="aaf2f-120">The status value **Performance critical** is relevant for transactional subscriptions and merge subscriptions; for transactional subscriptions, it can be displayed only if a threshold is set.</span></span> <span data-ttu-id="aaf2f-121">有关性能度量和设置阈值的信息，请参阅[使用复制监视器监视性能](monitor/monitor-performance-with-replication-monitor.md)和[在复制监视器中设置阈值和警告](monitor/set-thresholds-and-warnings-in-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="aaf2f-121">For information on performance measurements and setting thresholds, see [Monitor Performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md) and [Set Thresholds and Warnings in Replication Monitor](monitor/set-thresholds-and-warnings-in-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="aaf2f-122">**发布**</span><span class="sxs-lookup"><span data-stu-id="aaf2f-122">**Publication**</span></span>  
 <span data-ttu-id="aaf2f-123">每个发布的名称，格式为 *PublicationDatabaseName: PublicationName*。</span><span class="sxs-lookup"><span data-stu-id="aaf2f-123">The name of each publication, in the form *PublicationDatabaseName: PublicationName*.</span></span>  
  
 <span data-ttu-id="aaf2f-124">**订阅**</span><span class="sxs-lookup"><span data-stu-id="aaf2f-124">**Subscriptions**</span></span>  
 <span data-ttu-id="aaf2f-125">每个发布的订阅数量。</span><span class="sxs-lookup"><span data-stu-id="aaf2f-125">The number of subscriptions for each publication.</span></span>  
  
 <span data-ttu-id="aaf2f-126">**正在同步**</span><span class="sxs-lookup"><span data-stu-id="aaf2f-126">**Synchronizing**</span></span>  
 <span data-ttu-id="aaf2f-127">当前正在同步的每个发布的订阅数量：</span><span class="sxs-lookup"><span data-stu-id="aaf2f-127">The number of subscriptions for each publication that are currently synchronizing:</span></span>  
  
-   <span data-ttu-id="aaf2f-128">对于事务复制，“同步”意味着分发代理正在运行，但是无需复制数据。</span><span class="sxs-lookup"><span data-stu-id="aaf2f-128">For transactional replication, "synchronizing" means that the Distribution Agent is running, but data is not necessarily being replicated.</span></span>  
  
-   <span data-ttu-id="aaf2f-129">对于合并复制，“同步”意味着合并代理正在运行，并且正在复制数据。</span><span class="sxs-lookup"><span data-stu-id="aaf2f-129">For merge replication, "synchronizing" means that the Merge Agent is running and that data is currently being replicated.</span></span>  
  
-   <span data-ttu-id="aaf2f-130">对于快照复制，“同步”意味着分发代理正在运行，并且正在复制数据。</span><span class="sxs-lookup"><span data-stu-id="aaf2f-130">For snapshot replication, "synchronizing" means that the Distribution Agent is running and that data is currently being replicated.</span></span>  
  
 <span data-ttu-id="aaf2f-131">**“当前平均性能”** 和 **“当前最差的性能”**</span><span class="sxs-lookup"><span data-stu-id="aaf2f-131">**Current Average Performance** and **Current Worst Performance**</span></span>  
 <span data-ttu-id="aaf2f-132">仅限 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 及更高版本。</span><span class="sxs-lookup"><span data-stu-id="aaf2f-132">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only.</span></span> <span data-ttu-id="aaf2f-133">发布的所有订阅各自的平均性能率和最差性能率。</span><span class="sxs-lookup"><span data-stu-id="aaf2f-133">The average performance rating and the worst performance rating, respectively, for all subscriptions to a publication.</span></span> <span data-ttu-id="aaf2f-134">这些比率是基于复制监视器最近取得的度量值，并不反映某段时间内的订阅性能。</span><span class="sxs-lookup"><span data-stu-id="aaf2f-134">Ratings are based on the most recent measurements taken by Replication Monitor and do not reflect the performance of a subscription over time.</span></span>  
  
 <span data-ttu-id="aaf2f-135">对于事务复制，复制监视器仅为定义了性能阈值的发布显示值。</span><span class="sxs-lookup"><span data-stu-id="aaf2f-135">For transactional replication, Replication Monitor displays a value only for publications that have performance thresholds defined.</span></span> <span data-ttu-id="aaf2f-136">如果没有为发布定义性能阈值，则此列将显示 **“未启用”** 。</span><span class="sxs-lookup"><span data-stu-id="aaf2f-136">If performance thresholds are not defined for a publication, this column displays **Not enabled**.</span></span> <span data-ttu-id="aaf2f-137">对于合并复制，在通过同一类型的连接（拨号或 LAN）进行了五次同步、并且每次同步所做的更改为 50 处或更多处之后，复制监视器将会显示值。</span><span class="sxs-lookup"><span data-stu-id="aaf2f-137">For merge replication, Replication Monitor displays a value after five synchronizations have occurred with 50 or more changes each over the same type of connection (dial-up or LAN).</span></span> <span data-ttu-id="aaf2f-138">如果所做更改为 50 处或更多处的同步次数少于五次，或最近一次同步所做的更改少于 50 处，则此列为空白。</span><span class="sxs-lookup"><span data-stu-id="aaf2f-138">If there have been less than five synchronizations with 50 or more changes or the most recent synchronization has less than 50 changes, this column is blank.</span></span>  
  
 <span data-ttu-id="aaf2f-139">性能等级可以为以下值之一：</span><span class="sxs-lookup"><span data-stu-id="aaf2f-139">The performance rating is one of the following values:</span></span>  
  
-   <span data-ttu-id="aaf2f-140">很好</span><span class="sxs-lookup"><span data-stu-id="aaf2f-140">Excellent</span></span>  
  
-   <span data-ttu-id="aaf2f-141">好</span><span class="sxs-lookup"><span data-stu-id="aaf2f-141">Good</span></span>  
  
-   <span data-ttu-id="aaf2f-142">一般</span><span class="sxs-lookup"><span data-stu-id="aaf2f-142">Fair</span></span>  
  
-   <span data-ttu-id="aaf2f-143">较差</span><span class="sxs-lookup"><span data-stu-id="aaf2f-143">Poor</span></span>  
  
-   <span data-ttu-id="aaf2f-144">严重</span><span class="sxs-lookup"><span data-stu-id="aaf2f-144">Critical</span></span>  
  
 <span data-ttu-id="aaf2f-145">有关如何定义性能等级以及如何设置性能阈值的详细信息，请参阅[使用复制监视器监视性能](monitor/monitor-performance-with-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="aaf2f-145">For more information about how performance ratings are defined and how performance thresholds are set, see [Monitor Performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aaf2f-146">另请参阅</span><span class="sxs-lookup"><span data-stu-id="aaf2f-146">See Also</span></span>  
 <span data-ttu-id="aaf2f-147">[启动复制监视器](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="aaf2f-147">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="aaf2f-148">[使用复制监视器查看信息和执行任务](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="aaf2f-148">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 [<span data-ttu-id="aaf2f-149">监视复制</span><span class="sxs-lookup"><span data-stu-id="aaf2f-149">Monitoring Replication</span></span>](monitoring-replication.md)  
  
  
