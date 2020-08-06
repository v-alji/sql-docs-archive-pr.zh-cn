---
title: 发布服务器信息，订阅监视列表 (合并发布，SQL Server 2005 及更高版本) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publisherinfo.subscriptionssummary.merge.f1
ms.assetid: 4ec956bf-5cef-4377-a1d1-8c7f0107a6cb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: cd38540533e3e663fa23eee2c651f0beb9463546
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691656"
---
# <a name="publisher-information-subscription-watch-list-merge-publication-sql-server-2005-and-later"></a><span data-ttu-id="e30e2-102">发布服务器信息，订阅监视列表（合并发布，SQL Server 2005 和更高版本）</span><span class="sxs-lookup"><span data-stu-id="e30e2-102">Publisher Information, Subscription Watch List (Merge Publication, SQL Server 2005 and Later)</span></span>
  <span data-ttu-id="e30e2-103">在运行 **及更高版本的分发服务器上，可以使用** “订阅监视列表” [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 选项卡；此选项卡用于显示所选发布服务器上的所有可用发布中的订阅的相关信息。</span><span class="sxs-lookup"><span data-stu-id="e30e2-103">The **Subscription Watch List** tab is available for Distributors running [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions; it is intended to display information on subscriptions from all publications available at the selected Publisher.</span></span> <span data-ttu-id="e30e2-104">可以筛选订阅列表，以查看有错误的订阅、出现警告的订阅以及所有性能较差的订阅。</span><span class="sxs-lookup"><span data-stu-id="e30e2-104">You can filter the list of subscriptions to see errors, warnings, and any poorly performing subscriptions.</span></span> <span data-ttu-id="e30e2-105">此选项卡为管理员提供了监视发布服务器上所有复制活动的单一位置：复制监视器根据所选复制类型和在 **“显示”** 下拉列表框中选择的选项，显示所有需要注意的订阅。</span><span class="sxs-lookup"><span data-stu-id="e30e2-105">This tab provides a single location for an administrator to monitor all replication activity at a Publisher: Replication Monitor displays all subscriptions that require attention, based on the selected replication type and on the option chosen in the **Show** drop-down list box.</span></span> <span data-ttu-id="e30e2-106">由于此选项卡上显示的项基于当前状态和性能，因此只有与 **“显示”** 列表框中的当前选项相匹配的订阅才会显示在此页上。</span><span class="sxs-lookup"><span data-stu-id="e30e2-106">Because the items displayed on this tab are based on current status and performance, subscriptions are displayed on this page only if they match the option in the **Show** list box at the current time.</span></span>  
  
## <a name="options"></a><span data-ttu-id="e30e2-107">选项</span><span class="sxs-lookup"><span data-stu-id="e30e2-107">Options</span></span>  
 <span data-ttu-id="e30e2-108">有关订阅的详细信息及相关任务，请右键单击相应订阅所在的行，再单击快捷菜单上的选项。</span><span class="sxs-lookup"><span data-stu-id="e30e2-108">For more detailed information and tasks related to a subscription, right-click the row for that subscription, and then click an option on the shortcut menu.</span></span> <span data-ttu-id="e30e2-109">若要更改网格显示数据的方式，请右键单击网格，然后单击以下选项之一：</span><span class="sxs-lookup"><span data-stu-id="e30e2-109">To change the way that the grid displays data, right-click the grid, and then click one of the following options:</span></span>  
  
-   <span data-ttu-id="e30e2-110">**排序**：按 **“列排序”** 对话框中的一列或多列排序。</span><span class="sxs-lookup"><span data-stu-id="e30e2-110">**Sort**: Sort on one or more columns in the **Sort Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="e30e2-111">**选择要显示的列**：选择要显示哪些列以及要在 **“选择列”** 对话框中以何种顺序显示它们。</span><span class="sxs-lookup"><span data-stu-id="e30e2-111">**Choose Columns to Show**: Select which columns to display and the order in which to display them in the **Choose Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="e30e2-112">**筛选器**：根据 **“筛选设置”** 对话框中的列值筛选网格中的行。</span><span class="sxs-lookup"><span data-stu-id="e30e2-112">**Filter**: Filter rows in the grid based on column values in the **Filter Settings** dialog box.</span></span>  
  
-   <span data-ttu-id="e30e2-113">**清除筛选器**：清除网格的任何筛选设置。</span><span class="sxs-lookup"><span data-stu-id="e30e2-113">**Clear Filter**: Clear any filter settings for the grid.</span></span>  
  
 <span data-ttu-id="e30e2-114">筛选设置是特定于每个网格的。</span><span class="sxs-lookup"><span data-stu-id="e30e2-114">Filter settings are specific to each grid.</span></span> <span data-ttu-id="e30e2-115">列的选择和排序应用于同一类型的所有网格，如每个发布服务器的发布网格。</span><span class="sxs-lookup"><span data-stu-id="e30e2-115">Column selection and sorting are applied to all grids of the same type, such as the publications grid for each Publisher.</span></span>  
  
 <span data-ttu-id="e30e2-116">**显示合并订阅**</span><span class="sxs-lookup"><span data-stu-id="e30e2-116">**Show Merge Subscriptions**</span></span>  
 <span data-ttu-id="e30e2-117">为所选发布服务器选择要显示的订阅类型（事务、快照或合并）。</span><span class="sxs-lookup"><span data-stu-id="e30e2-117">Select the type of subscriptions (transactional, snapshot, or merge) to display for the selected Publisher.</span></span>  
  
 <span data-ttu-id="e30e2-118">**显示**</span><span class="sxs-lookup"><span data-stu-id="e30e2-118">**Show**</span></span>  
 <span data-ttu-id="e30e2-119">为所选订阅类型选择要显示的订阅状态。</span><span class="sxs-lookup"><span data-stu-id="e30e2-119">Select the subscription states to display for the selected subscription type.</span></span> <span data-ttu-id="e30e2-120">例如，可以选择仅显示包含错误的订阅。</span><span class="sxs-lookup"><span data-stu-id="e30e2-120">For example, you can select to display only those subscriptions that have an error.</span></span>  
  
 <span data-ttu-id="e30e2-121">**Status**</span><span class="sxs-lookup"><span data-stu-id="e30e2-121">**Status**</span></span>  
 <span data-ttu-id="e30e2-122">每个订阅的状态，这取决于合并代理的状态。</span><span class="sxs-lookup"><span data-stu-id="e30e2-122">The status of each subscription, which is determined by the status of the Merge Agent.</span></span>  
  
 <span data-ttu-id="e30e2-123">默认情况下，包含订阅信息的网格按 **“状态”** 列排序（对于具有相同状态的订阅，再按 **“性能”** 列排序）。</span><span class="sxs-lookup"><span data-stu-id="e30e2-123">By default, the grid containing subscription information is sorted by the **Status** column (and then sorted by the **Performance** column for those subscriptions with the same status).</span></span> <span data-ttu-id="e30e2-124">下面的列表显示了可能的状态值以及这些值的排序顺序（例如，错误项始终显示在该网格的顶部）：</span><span class="sxs-lookup"><span data-stu-id="e30e2-124">The following list shows the possible status values and the sort order for the values (for example, errors are always shown at the top of the grid).</span></span>  
  
-   <span data-ttu-id="e30e2-125">错误</span><span class="sxs-lookup"><span data-stu-id="e30e2-125">Error</span></span>  
  
-   <span data-ttu-id="e30e2-126">“严重”状态下的性能</span><span class="sxs-lookup"><span data-stu-id="e30e2-126">Performance critical</span></span>  
  
-   <span data-ttu-id="e30e2-127">长时间运行的合并</span><span class="sxs-lookup"><span data-stu-id="e30e2-127">Long-running merge</span></span>  
  
-   <span data-ttu-id="e30e2-128">即将过期/已过期</span><span class="sxs-lookup"><span data-stu-id="e30e2-128">Expiring soon/Expired</span></span>  
  
-   <span data-ttu-id="e30e2-129">未初始化的订阅</span><span class="sxs-lookup"><span data-stu-id="e30e2-129">Uninitialized subscription</span></span>  
  
-   <span data-ttu-id="e30e2-130">正在重试失败的命令</span><span class="sxs-lookup"><span data-stu-id="e30e2-130">Retrying failed command</span></span>  
  
-   <span data-ttu-id="e30e2-131">正在同步</span><span class="sxs-lookup"><span data-stu-id="e30e2-131">Synchronizing</span></span>  
  
-   <span data-ttu-id="e30e2-132">未同步</span><span class="sxs-lookup"><span data-stu-id="e30e2-132">Not synchronizing</span></span>  
  
 <span data-ttu-id="e30e2-133">如果给定的订阅处于多种状态，该排序顺序还决定将要显示哪个值。</span><span class="sxs-lookup"><span data-stu-id="e30e2-133">The sort order also determines which value is displayed if a given subscription is in more than one state.</span></span> <span data-ttu-id="e30e2-134">例如，如果某个订阅包含错误并且即将过期， **“状态”** 列将显示 **“错误”**。</span><span class="sxs-lookup"><span data-stu-id="e30e2-134">For example, if a subscription has an error and is expiring soon, the **Status** column displays **Error**.</span></span>  
  
 <span data-ttu-id="e30e2-135">状态值 **“‘严重’状态下的性能”**、 **“长时间运行的合并”**、 **“即将过期/已过期”** 和 **“未初始化的订阅”** 都是警告。</span><span class="sxs-lookup"><span data-stu-id="e30e2-135">The status values **Performance critical**, **Long-running merge**, **Expiring soon/Expired**, and **Uninitialized subscription** are warnings.</span></span> <span data-ttu-id="e30e2-136">当显示警告时， **“状态”** 列还可显示是否正在同步代理。</span><span class="sxs-lookup"><span data-stu-id="e30e2-136">When a warning is displayed, the **Status** column also displays if an agent is synchronizing.</span></span> <span data-ttu-id="e30e2-137">例如，状态可能为 **“同步，‘严重’状态下的性能”**。</span><span class="sxs-lookup"><span data-stu-id="e30e2-137">For example, the status could be **Synchronizing, Performance critical**.</span></span>  
  
 <span data-ttu-id="e30e2-138">只有在设置了阈值时，才会显示状态值 **“即将过期/已过期”** 和 **“长时间运行的合并”** 。</span><span class="sxs-lookup"><span data-stu-id="e30e2-138">The status values **Expiring soon/Expired** and **Long-running merge** can be displayed only if thresholds are set.</span></span> <span data-ttu-id="e30e2-139">只有在使用相同的连接类型（拨号或 LAN）对订阅进行五次同步后，才会显示状态值 **“‘严重’状态下的性能”** 。</span><span class="sxs-lookup"><span data-stu-id="e30e2-139">The status value **Performance critical** can be displayed only after five synchronizations of subscriptions with the same connection type (dial-up or LAN).</span></span> <span data-ttu-id="e30e2-140">有关性能度量和设置阈值的信息，请参阅[使用复制监视器监视性能](monitor/monitor-performance-with-replication-monitor.md)和[在复制监视器中设置阈值和警告](monitor/set-thresholds-and-warnings-in-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="e30e2-140">For information on performance measurements and setting thresholds, see [Monitor Performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md) and [Set Thresholds and Warnings in Replication Monitor](monitor/set-thresholds-and-warnings-in-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="e30e2-141">**订阅**</span><span class="sxs-lookup"><span data-stu-id="e30e2-141">**Subscription**</span></span>  
 <span data-ttu-id="e30e2-142">每个订阅的名称，格式为：*SubscriberName: SubscriptionDatabaseName*。</span><span class="sxs-lookup"><span data-stu-id="e30e2-142">The name of each subscription, in the form:*SubscriberName: SubscriptionDatabaseName*.</span></span>  
  
 <span data-ttu-id="e30e2-143">**友好名称**</span><span class="sxs-lookup"><span data-stu-id="e30e2-143">**Friendly Name**</span></span>  
 <span data-ttu-id="e30e2-144">每个订阅的说明。</span><span class="sxs-lookup"><span data-stu-id="e30e2-144">The description of each subscription.</span></span> <span data-ttu-id="e30e2-145">此说明是在 **“订阅属性”** 对话框中输入的，或是用 **@description** 或 [sp_addmergepullsubscription](/sql/relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql) 的 [@description](/sql/relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="e30e2-145">The description is entered in the **Subscription Properties** dialog box or specified with the **@description** parameter of [sp_addmergesubscription](/sql/relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql) or [sp_addmergepullsubscription](/sql/relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql).</span></span> <span data-ttu-id="e30e2-146">用户通常将说明用作订阅的“友好名称”或别名。</span><span class="sxs-lookup"><span data-stu-id="e30e2-146">Users often use the description as a "friendly name" or nickname for the subscription.</span></span>  
  
 <span data-ttu-id="e30e2-147">**发布**</span><span class="sxs-lookup"><span data-stu-id="e30e2-147">**Publication**</span></span>  
 <span data-ttu-id="e30e2-148">与订阅同步的发布的名称，格式为： *PublicationDatabaseName: PublicationName*。</span><span class="sxs-lookup"><span data-stu-id="e30e2-148">The name of the publication with which a subscription synchronizes, in the form: *PublicationDatabaseName: PublicationName*.</span></span>  
  
 <span data-ttu-id="e30e2-149">**性能**</span><span class="sxs-lookup"><span data-stu-id="e30e2-149">**Performance**</span></span>  
 <span data-ttu-id="e30e2-150">每个订阅的性能等级，这是基于复制监视器对传送速率的最新度量值来确定的。</span><span class="sxs-lookup"><span data-stu-id="e30e2-150">The performance rating for each subscription, based on the most recent measurements of delivery rate taken by Replication Monitor.</span></span> <span data-ttu-id="e30e2-151">对于具有相同连接类型（拨号或 LAN）的发布的订阅，通过将单独的订阅性能与其平均历史性能进行比较，可以确定性能等级。</span><span class="sxs-lookup"><span data-stu-id="e30e2-151">The rating is determined by comparing individual subscription performance to the average historical performance of subscriptions to the publication that have the same connection type (dial-up or LAN).</span></span> <span data-ttu-id="e30e2-152">如果通过同一类型的连接进行了五次同步，且每次同步都进行了 50 处或更多的更改，则复制监视器将在此列中显示一个值。</span><span class="sxs-lookup"><span data-stu-id="e30e2-152">Replication Monitor displays a value after five synchronizations have occurred with 50 or more changes each over the same type of connection.</span></span> <span data-ttu-id="e30e2-153">如果所做更改为 50 处或更多处的同步次数少于五次，或最近一次同步所做的更改少于 50 处，则此列为空白。</span><span class="sxs-lookup"><span data-stu-id="e30e2-153">If there have been less than five synchronizations with 50 or more changes or the most recent synchronization has less than 50 changes, this column is blank.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e30e2-154"> 性能是根据 **“连接”** 列中显示的连接类型确定的；因此，对于较低传送速率的订阅来说，如果是通过较慢速度的连接进行同步的，那么该订阅也有可能显示出比其他订阅更高的性能等级。</span><span class="sxs-lookup"><span data-stu-id="e30e2-154">Performance is based on the connection type displayed in the **Connection** column; therefore it is possible for a subscription with a lower delivery rate to display a better performance rating than another subscription if the first subscription is synchronized over a slower connection.</span></span>  
  
 <span data-ttu-id="e30e2-155">性能等级可以为以下值之一：</span><span class="sxs-lookup"><span data-stu-id="e30e2-155">The performance rating is one of the following values:</span></span>  
  
-   <span data-ttu-id="e30e2-156">优秀</span><span class="sxs-lookup"><span data-stu-id="e30e2-156">Excellent</span></span>  
  
-   <span data-ttu-id="e30e2-157">好</span><span class="sxs-lookup"><span data-stu-id="e30e2-157">Good</span></span>  
  
-   <span data-ttu-id="e30e2-158">一般</span><span class="sxs-lookup"><span data-stu-id="e30e2-158">Fair</span></span>  
  
-   <span data-ttu-id="e30e2-159">差</span><span class="sxs-lookup"><span data-stu-id="e30e2-159">Poor</span></span>  
  
 <span data-ttu-id="e30e2-160">有关如何定义性能等级以及如何设置性能阈值的详细信息，请参阅[使用复制监视器监视性能](monitor/monitor-performance-with-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="e30e2-160">For more information about how performance ratings are defined and how performance thresholds are set, see [Monitor Performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="e30e2-161">**传送速率**</span><span class="sxs-lookup"><span data-stu-id="e30e2-161">**Delivery Rate**</span></span>  
 <span data-ttu-id="e30e2-162">合并代理每秒处理的行数。</span><span class="sxs-lookup"><span data-stu-id="e30e2-162">The number of rows per second processed by the Merge Agent.</span></span>  
  
 <span data-ttu-id="e30e2-163">**上次同步**</span><span class="sxs-lookup"><span data-stu-id="e30e2-163">**Last Synchronization**</span></span>  
 <span data-ttu-id="e30e2-164">合并代理上次运行的时间。</span><span class="sxs-lookup"><span data-stu-id="e30e2-164">The time at which the Merge Agent last ran.</span></span> <span data-ttu-id="e30e2-165">在此同步过程中，更改可能已处理，也可能尚未处理。</span><span class="sxs-lookup"><span data-stu-id="e30e2-165">Changes may or may not have been processed during this synchronization.</span></span> <span data-ttu-id="e30e2-166">如果正在进行同步，则会显示完成百分比值。</span><span class="sxs-lookup"><span data-stu-id="e30e2-166">If synchronization is in progress, a percentage complete value is displayed.</span></span>  
  
 <span data-ttu-id="e30e2-167">**持续时间**</span><span class="sxs-lookup"><span data-stu-id="e30e2-167">**Duration**</span></span>  
 <span data-ttu-id="e30e2-168">上次同步过程中合并代理运行所用的时间。</span><span class="sxs-lookup"><span data-stu-id="e30e2-168">The amount of time the Merge Agent has run during the last synchronization.</span></span> <span data-ttu-id="e30e2-169">如果合并代理当前正在同步，该时间表示已运行的时间；如果合并代理之前已经同步，该时间则表示上次同步所用的总时间。</span><span class="sxs-lookup"><span data-stu-id="e30e2-169">The time represents elapsed time if the Merge Agent is currently synchronizing and total time if the Merge Agent has synchronized previously.</span></span>  
  
 <span data-ttu-id="e30e2-170">**Connection**</span><span class="sxs-lookup"><span data-stu-id="e30e2-170">**Connection**</span></span>  
 <span data-ttu-id="e30e2-171">订阅服务器与发布服务器之间的连接类型。</span><span class="sxs-lookup"><span data-stu-id="e30e2-171">The type of connection between the Subscriber and the Publisher.</span></span> <span data-ttu-id="e30e2-172">可能的值包括 **LAN**、 **“拨号”** 和 **Internet**。</span><span class="sxs-lookup"><span data-stu-id="e30e2-172">The possible values are **LAN**, **Dialup**, and **Internet**.</span></span> <span data-ttu-id="e30e2-173">如果订阅使用 Web 同步，则会显示 **Internet** 值。</span><span class="sxs-lookup"><span data-stu-id="e30e2-173">The **Internet** value is displayed if the subscription uses Web synchronization.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e30e2-174">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e30e2-174">See Also</span></span>  
 <span data-ttu-id="e30e2-175">[启动复制监视器](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="e30e2-175">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="e30e2-176">[使用复制监视器查看信息和执行任务](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="e30e2-176">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 <span data-ttu-id="e30e2-177">[监视复制](monitoring-replication.md) </span><span class="sxs-lookup"><span data-stu-id="e30e2-177">[Monitoring Replication](monitoring-replication.md) </span></span>  
 [<span data-ttu-id="e30e2-178">合并复制的 Web 同步</span><span class="sxs-lookup"><span data-stu-id="e30e2-178">Web Synchronization for Merge Replication</span></span>](web-synchronization-for-merge-replication.md)  
  
  
