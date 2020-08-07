---
title: 发布服务器信息，订阅监视列表 (事务发布，SQL Server 2005 及更高版本) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publisherinfo.subscriptionssummary.tran.f1
ms.assetid: 6bc64ddb-5c86-4681-a391-77fc1d3c4e6e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: bf6d151b75bca1dbfd2e5ad8f7601fb1002e84be
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576634"
---
# <a name="publisher-information-subscription-watch-list-transactional-publication-sql-server-2005-and-later"></a><span data-ttu-id="d293a-102">发布服务器信息，订阅监视列表（事务发布，SQL Server 2005 和更高版本）</span><span class="sxs-lookup"><span data-stu-id="d293a-102">Publisher Information, Subscription Watch List (Transactional Publication, SQL Server 2005 and Later)</span></span>
  <span data-ttu-id="d293a-103">**“订阅监视列表”** 选项卡可用于运行 SQL Server 2005 及更高版本的分发服务器；用来显示所选发布服务器上所有可用发布中的订阅的有关信息。</span><span class="sxs-lookup"><span data-stu-id="d293a-103">The **Subscription Watch List** tab is available for Distributors running SQL Server 2005 and later versions; it is intended to display information on subscriptions from all publications available at the selected Publisher.</span></span> <span data-ttu-id="d293a-104">可以筛选订阅列表，以查看有错误的订阅、出现警告的订阅以及所有性能较差的订阅。</span><span class="sxs-lookup"><span data-stu-id="d293a-104">You can filter the list of subscriptions to see errors, warnings, and any poorly performing subscriptions.</span></span> <span data-ttu-id="d293a-105">此选项卡为管理员提供了监视发布服务器上所有复制活动的单一位置：复制监视器根据所选复制类型和在 **“显示”** 下拉列表框中选择的选项，显示所有需要注意的订阅。</span><span class="sxs-lookup"><span data-stu-id="d293a-105">This tab provides a single location for an administrator to monitor all replication activity at a Publisher: Replication Monitor displays all subscriptions that require attention, based on the selected replication type and on the option chosen in the **Show** drop-down list box.</span></span> <span data-ttu-id="d293a-106">由于此选项卡上显示的项基于当前状态和性能，因此只有与 **“显示”** 列表框中的当前选项相匹配的订阅才会显示在此页上。</span><span class="sxs-lookup"><span data-stu-id="d293a-106">Because the items displayed on this tab are based on current status and performance, subscriptions are displayed on this page only if they match the option in the **Show** list box at the current time.</span></span>  
  
## <a name="options"></a><span data-ttu-id="d293a-107">选项</span><span class="sxs-lookup"><span data-stu-id="d293a-107">Options</span></span>  
 <span data-ttu-id="d293a-108">有关订阅的详细信息及相关任务，请右键单击相应订阅所在的行，再单击快捷菜单上的选项。</span><span class="sxs-lookup"><span data-stu-id="d293a-108">For more detailed information and tasks related to a subscription, right-click the row for that subscription, and then click an option on the shortcut menu.</span></span> <span data-ttu-id="d293a-109">若要更改网格显示数据的方式，请右键单击网格，然后单击以下选项之一：</span><span class="sxs-lookup"><span data-stu-id="d293a-109">To change the way that the grid displays data, right-click the grid, and then click one of the following options:</span></span>  
  
-   <span data-ttu-id="d293a-110">**排序**：按 **“列排序”** 对话框中的一列或多列排序。</span><span class="sxs-lookup"><span data-stu-id="d293a-110">**Sort**: Sort on one or more columns in the **Sort Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="d293a-111">**选择要显示的列**：选择要显示哪些列以及要在 **“选择列”** 对话框中以何种顺序显示它们。</span><span class="sxs-lookup"><span data-stu-id="d293a-111">**Choose Columns to Show**: Select which columns to display and the order in which to display them in the **Choose Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="d293a-112">**筛选器**：根据 **“筛选设置”** 对话框中的列值筛选网格中的行。</span><span class="sxs-lookup"><span data-stu-id="d293a-112">**Filter**: Filter rows in the grid based on column values in the **Filter Settings** dialog box.</span></span>  
  
-   <span data-ttu-id="d293a-113">**清除筛选器**：清除网格的任何筛选设置。</span><span class="sxs-lookup"><span data-stu-id="d293a-113">**Clear Filter**: Clear any filter settings for the grid.</span></span>  
  
 <span data-ttu-id="d293a-114">筛选设置是特定于每个网格的。</span><span class="sxs-lookup"><span data-stu-id="d293a-114">Filter settings are specific to each grid.</span></span> <span data-ttu-id="d293a-115">列的选择和排序应用于同一类型的所有网格，如每个发布服务器的发布网格。</span><span class="sxs-lookup"><span data-stu-id="d293a-115">Column selection and sorting are applied to all grids of the same type, such as the publications grid for each Publisher.</span></span>  
  
 <span data-ttu-id="d293a-116">**显示事务订阅**</span><span class="sxs-lookup"><span data-stu-id="d293a-116">**Show Transactional Subscriptions**</span></span>  
 <span data-ttu-id="d293a-117">为所选发布服务器选择要显示的订阅类型（事务、快照或合并）。</span><span class="sxs-lookup"><span data-stu-id="d293a-117">Select the type of subscriptions (transactional, snapshot, or merge) to display for the selected Publisher.</span></span>  
  
 <span data-ttu-id="d293a-118">**显示**</span><span class="sxs-lookup"><span data-stu-id="d293a-118">**Show**</span></span>  
 <span data-ttu-id="d293a-119">为所选订阅类型选择要显示的订阅状态。</span><span class="sxs-lookup"><span data-stu-id="d293a-119">Select the subscription states to display for the selected subscription type.</span></span> <span data-ttu-id="d293a-120">例如，可以选择仅显示包含错误的订阅。</span><span class="sxs-lookup"><span data-stu-id="d293a-120">For example, you can select to display only those subscriptions that have an error.</span></span>  
  
 <span data-ttu-id="d293a-121">**Status**</span><span class="sxs-lookup"><span data-stu-id="d293a-121">**Status**</span></span>  
 <span data-ttu-id="d293a-122">每个订阅的状态，由分发代理或日志读取器代理的状态决定（显示优先级较高的状态；如果使用排队更新订阅，则状态还可以由队列读取器代理决定）。</span><span class="sxs-lookup"><span data-stu-id="d293a-122">The status of each subscription, which is determined by the status of the Distribution Agent or the Log Reader Agent (the higher priority status is displayed; the status can also be determined by the Queue Reader Agent if queued updating subscriptions are used).</span></span>  
  
 <span data-ttu-id="d293a-123">默认情况下，包含订阅信息的网格按 **“状态”** 列排序（对于具有相同状态的订阅，再按 **“性能”** 列排序）。</span><span class="sxs-lookup"><span data-stu-id="d293a-123">By default, the grid containing subscription information is sorted by the **Status** column (and then sorted by the **Performance** column for those subscriptions with the same status).</span></span> <span data-ttu-id="d293a-124">下面的列表显示了可能的状态值以及这些值的排序顺序（例如，错误项始终显示在该网格的顶部）：</span><span class="sxs-lookup"><span data-stu-id="d293a-124">The following list shows the possible status values and the sort order for the values (for example, errors are always shown at the top of the grid).</span></span>  
  
-   <span data-ttu-id="d293a-125">错误</span><span class="sxs-lookup"><span data-stu-id="d293a-125">Error</span></span>  
  
-   <span data-ttu-id="d293a-126">“严重”状态下的性能</span><span class="sxs-lookup"><span data-stu-id="d293a-126">Performance critical</span></span>  
  
-   <span data-ttu-id="d293a-127">即将过期/已过期</span><span class="sxs-lookup"><span data-stu-id="d293a-127">Expiring soon/Expired</span></span>  
  
-   <span data-ttu-id="d293a-128">未初始化的订阅</span><span class="sxs-lookup"><span data-stu-id="d293a-128">Uninitialized subscription</span></span>  
  
-   <span data-ttu-id="d293a-129">正在重试失败的命令</span><span class="sxs-lookup"><span data-stu-id="d293a-129">Retrying failed command</span></span>  
  
-   <span data-ttu-id="d293a-130">未运行</span><span class="sxs-lookup"><span data-stu-id="d293a-130">Not Running</span></span>  
  
-   <span data-ttu-id="d293a-131">正在运行</span><span class="sxs-lookup"><span data-stu-id="d293a-131">Running</span></span>  
  
 <span data-ttu-id="d293a-132">如果给定的订阅处于多种状态，该排序顺序还决定将要显示哪个值。</span><span class="sxs-lookup"><span data-stu-id="d293a-132">The sort order also determines which value is displayed if a given subscription is in more than one state.</span></span> <span data-ttu-id="d293a-133">例如，如果某个订阅包含错误并且即将过期， **“状态”** 列将显示 **“错误”** 。</span><span class="sxs-lookup"><span data-stu-id="d293a-133">For example, if a subscription has an error and is expiring soon, the **Status** column displays **Error**.</span></span>  
  
 <span data-ttu-id="d293a-134">状态值 **“‘严重’状态下的性能”** 、 **“即将过期/已过期”** 和 **“未初始化的订阅”** 都是警告。</span><span class="sxs-lookup"><span data-stu-id="d293a-134">The status values **Performance critical**, **Expiring soon/Expired**, and **Uninitialized subscription** are warnings.</span></span> <span data-ttu-id="d293a-135">当显示警告时， **“状态”** 列还可显示是否正在运行代理。</span><span class="sxs-lookup"><span data-stu-id="d293a-135">When a warning is displayed, the **Status** column also displays if an agent is running.</span></span> <span data-ttu-id="d293a-136">例如，状态可能为 **“正在运行，‘严重’状态下的性能”** 。</span><span class="sxs-lookup"><span data-stu-id="d293a-136">For example, the status could be **Running, Performance critical**.</span></span>  
  
 <span data-ttu-id="d293a-137">只有在设置了阈值时，才会显示状态值 **“‘严重’状态下的性能”** 和 **“即将过期/已过期”** 。</span><span class="sxs-lookup"><span data-stu-id="d293a-137">The status values **Performance critical** and **Expiring soon/Expired** are displayed only if thresholds are set.</span></span> <span data-ttu-id="d293a-138">有关性能度量和设置阈值的信息，请参阅[使用复制监视器监视性能](monitor/monitor-performance-with-replication-monitor.md)和[在复制监视器中设置阈值和警告](monitor/set-thresholds-and-warnings-in-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="d293a-138">For information about performance measurements and setting thresholds, see [Monitor Performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md) and [Set Thresholds and Warnings in Replication Monitor](monitor/set-thresholds-and-warnings-in-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="d293a-139">**订阅**</span><span class="sxs-lookup"><span data-stu-id="d293a-139">**Subscription**</span></span>  
 <span data-ttu-id="d293a-140">每个订阅的名称，格式为： *SubscriberName: SubscriptionDatabaseName*。</span><span class="sxs-lookup"><span data-stu-id="d293a-140">The name of each subscription, in the form: *SubscriberName: SubscriptionDatabaseName*.</span></span>  
  
 <span data-ttu-id="d293a-141">**发布**</span><span class="sxs-lookup"><span data-stu-id="d293a-141">**Publication**</span></span>  
 <span data-ttu-id="d293a-142">与订阅同步的发布的名称，格式为： *PublicationDatabaseName: PublicationName*。</span><span class="sxs-lookup"><span data-stu-id="d293a-142">The name of the publication with which a subscription synchronizes, in the form: *PublicationDatabaseName: PublicationName*.</span></span>  
  
 <span data-ttu-id="d293a-143">**“性能”**</span><span class="sxs-lookup"><span data-stu-id="d293a-143">**Performance**</span></span>  
 <span data-ttu-id="d293a-144">每个订阅的性能等级都是基于复制监视器的最新度量值，并不反映历史性能。</span><span class="sxs-lookup"><span data-stu-id="d293a-144">The performance rating for each subscription is based on the most recent measurements taken by Replication Monitor and does not reflect historical performance.</span></span> <span data-ttu-id="d293a-145">对于为发布定义了性能阈值的订阅，均会度量其性能；如果没有为发布定义性能阈值，此列将显示 **“未启用”** 。</span><span class="sxs-lookup"><span data-stu-id="d293a-145">Performance is measured for subscriptions to publications that have performance thresholds defined; if performance thresholds are not defined for a publication, this column displays **Not enabled**.</span></span> <span data-ttu-id="d293a-146">性能等级可以为以下值之一：</span><span class="sxs-lookup"><span data-stu-id="d293a-146">The performance rating is one of the following values:</span></span>  
  
-   <span data-ttu-id="d293a-147">很好</span><span class="sxs-lookup"><span data-stu-id="d293a-147">Excellent</span></span>  
  
-   <span data-ttu-id="d293a-148">好</span><span class="sxs-lookup"><span data-stu-id="d293a-148">Good</span></span>  
  
-   <span data-ttu-id="d293a-149">一般</span><span class="sxs-lookup"><span data-stu-id="d293a-149">Fair</span></span>  
  
-   <span data-ttu-id="d293a-150">较差</span><span class="sxs-lookup"><span data-stu-id="d293a-150">Poor</span></span>  
  
-   <span data-ttu-id="d293a-151">严重</span><span class="sxs-lookup"><span data-stu-id="d293a-151">Critical</span></span>  
  
 <span data-ttu-id="d293a-152">如果性能状态为“严重”，则 **“状态”** 列中将显示 **“‘严重’状态下的性能”** 。</span><span class="sxs-lookup"><span data-stu-id="d293a-152">If performance is critical, **Performance Critical** is displayed in the **Status** column.</span></span> <span data-ttu-id="d293a-153">有关如何定义性能等级以及如何设置性能阈值的详细信息，请参阅[使用复制监视器监视性能](monitor/monitor-performance-with-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="d293a-153">For more information about how performance ratings are defined and how performance thresholds are set, see [Monitor Performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="d293a-154">**滞后时间**</span><span class="sxs-lookup"><span data-stu-id="d293a-154">**Latency**</span></span>  
 <span data-ttu-id="d293a-155">事务在发布服务器上提交和相应的事务在订阅服务器上提交之间间隔的平均时间。</span><span class="sxs-lookup"><span data-stu-id="d293a-155">The average amount of time that elapses between a transaction being committed at the Publisher and the corresponding transaction being committed at the Subscriber.</span></span> <span data-ttu-id="d293a-156">所显示的滞后时间基于复制监视器的最新度量值。</span><span class="sxs-lookup"><span data-stu-id="d293a-156">The latency displayed is based on the most recent measurements taken by Replication Monitor.</span></span> <span data-ttu-id="d293a-157">有关测量滞后时间的详细信息，请参阅[为事务复制测量滞后时间和验证连接](monitor/measure-latency-and-validate-connections-for-transactional-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="d293a-157">For more information about measuring latency, see [Measure Latency and Validate Connections for Transactional Replication](monitor/measure-latency-and-validate-connections-for-transactional-replication.md).</span></span>  
  
 <span data-ttu-id="d293a-158">**上次同步**</span><span class="sxs-lookup"><span data-stu-id="d293a-158">**Last Synchronization**</span></span>  
 <span data-ttu-id="d293a-159">分发代理上次运行的时间。</span><span class="sxs-lookup"><span data-stu-id="d293a-159">The time when the Distribution Agent last ran.</span></span> <span data-ttu-id="d293a-160">如果正在进行同步，则显示 **“正在进行”** 。</span><span class="sxs-lookup"><span data-stu-id="d293a-160">If synchronization is in progress, **In progress** is displayed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d293a-161">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d293a-161">See Also</span></span>  
 <span data-ttu-id="d293a-162">[启动复制监视器](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="d293a-162">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="d293a-163">[使用复制监视器查看信息和执行任务](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="d293a-163">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 [<span data-ttu-id="d293a-164">监视复制</span><span class="sxs-lookup"><span data-stu-id="d293a-164">Monitoring Replication</span></span>](monitoring-replication.md)  
  
  
