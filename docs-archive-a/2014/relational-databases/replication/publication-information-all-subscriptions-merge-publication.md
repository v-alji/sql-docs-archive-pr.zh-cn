---
title: 发布信息，所有订阅（合并发布）| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publicationinfo.allsubscriptions.merge.f1
ms.assetid: 0f4fa946-a0d9-4d3b-b90b-53503c40fba2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 251e4c6e2e2adc60c838c7875d5d7d99aee64b54
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693249"
---
# <a name="publication-information-all-subscriptions-merge-publication"></a><span data-ttu-id="e91ac-102">发布信息，所有订阅（合并发布）</span><span class="sxs-lookup"><span data-stu-id="e91ac-102">Publication Information, All Subscriptions (Merge Publication)</span></span>
  <span data-ttu-id="e91ac-103">“所有订阅”\*\*\*\* 选项卡显示所选合并发布的所有订阅的相关信息。</span><span class="sxs-lookup"><span data-stu-id="e91ac-103">The **All Subscriptions** tab displays information on all subscriptions to the selected merge publication.</span></span>  
  
## <a name="options"></a><span data-ttu-id="e91ac-104">选项</span><span class="sxs-lookup"><span data-stu-id="e91ac-104">Options</span></span>  
 <span data-ttu-id="e91ac-105">有关订阅的详细信息及相关任务，请右键单击相应订阅所在的行，再单击快捷菜单上的选项。</span><span class="sxs-lookup"><span data-stu-id="e91ac-105">For more detailed information and tasks related to a subscription, right-click the row for that subscription, and then click an option on the shortcut menu.</span></span> <span data-ttu-id="e91ac-106">若要更改网格显示数据的方式，请右键单击网格，然后单击以下选项之一：</span><span class="sxs-lookup"><span data-stu-id="e91ac-106">To change the way that the grid displays data, right-click the grid, and then click one of the following options:</span></span>  
  
-   <span data-ttu-id="e91ac-107">**排序**：按 **“列排序”** 对话框中的一列或多列排序。</span><span class="sxs-lookup"><span data-stu-id="e91ac-107">**Sort**: Sort on one or more columns in the **Sort Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="e91ac-108">**选择要显示的列**：选择要显示哪些列以及要在 **“选择列”** 对话框中以何种顺序显示它们。</span><span class="sxs-lookup"><span data-stu-id="e91ac-108">**Choose Columns to Show**: Select which columns to display and the order in which to display them in the **Choose Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="e91ac-109">**筛选器**：根据 **“筛选设置”** 对话框中的列值筛选网格中的行。</span><span class="sxs-lookup"><span data-stu-id="e91ac-109">**Filter**: Filter rows in the grid based on column values in the **Filter Settings** dialog box.</span></span>  
  
-   <span data-ttu-id="e91ac-110">**清除筛选器**：清除网格的任何筛选设置。</span><span class="sxs-lookup"><span data-stu-id="e91ac-110">**Clear Filter**: Clear any filter settings for the grid.</span></span>  
  
 <span data-ttu-id="e91ac-111">筛选设置是特定于每个网格的。</span><span class="sxs-lookup"><span data-stu-id="e91ac-111">Filter settings are specific to each grid.</span></span> <span data-ttu-id="e91ac-112">列的选择和排序应用于同一类型的所有网格，如每个发布服务器的发布网格。</span><span class="sxs-lookup"><span data-stu-id="e91ac-112">Column selection and sorting are applied to all grids of the same type, such as the publications grid for each Publisher.</span></span>  
  
 <span data-ttu-id="e91ac-113">**显示**</span><span class="sxs-lookup"><span data-stu-id="e91ac-113">**Show**</span></span>  
 <span data-ttu-id="e91ac-114">仅限 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 及更高版本。</span><span class="sxs-lookup"><span data-stu-id="e91ac-114">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only.</span></span> <span data-ttu-id="e91ac-115">为所选订阅类型选择要显示的订阅状态。</span><span class="sxs-lookup"><span data-stu-id="e91ac-115">Select the subscription states to display for the selected subscription type.</span></span> <span data-ttu-id="e91ac-116">例如，可以选择仅显示包含错误的订阅。</span><span class="sxs-lookup"><span data-stu-id="e91ac-116">For example, you can select to display only those subscriptions that have an error.</span></span>  
  
 <span data-ttu-id="e91ac-117">**Status**</span><span class="sxs-lookup"><span data-stu-id="e91ac-117">**Status**</span></span>  
 <span data-ttu-id="e91ac-118">每个订阅的状态，这取决于合并代理的状态。</span><span class="sxs-lookup"><span data-stu-id="e91ac-118">The status of each subscription, which is determined by the status of the Merge Agent.</span></span>  
  
 <span data-ttu-id="e91ac-119">默认情况下，包含订阅信息的网格按 **“状态”** 列排序（对于具有相同状态的订阅，再按 **“性能”** 列排序）。</span><span class="sxs-lookup"><span data-stu-id="e91ac-119">By default, the grid containing subscription information is sorted by the **Status** column (and then sorted by the **Performance** column for those subscriptions with the same status).</span></span> <span data-ttu-id="e91ac-120">下面的列表显示了可能的状态值以及这些值的排序顺序（例如，错误项始终显示在该网格的顶部）：</span><span class="sxs-lookup"><span data-stu-id="e91ac-120">The following list shows the possible status values and the sort order for the values (for example, errors are always shown at the top of the grid).</span></span>  
  
-   <span data-ttu-id="e91ac-121">错误</span><span class="sxs-lookup"><span data-stu-id="e91ac-121">Error</span></span>  
  
-   <span data-ttu-id="e91ac-122">“严重”状态下的性能（仅限[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 和更高版本）</span><span class="sxs-lookup"><span data-stu-id="e91ac-122">Performance critical ([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only)</span></span>  
  
-   <span data-ttu-id="e91ac-123">长时间运行的合并（仅限[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 和更高版本）</span><span class="sxs-lookup"><span data-stu-id="e91ac-123">Long-running merge ([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only)</span></span>  
  
-   <span data-ttu-id="e91ac-124">即将过期/已过期（仅限[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 和更高版本）</span><span class="sxs-lookup"><span data-stu-id="e91ac-124">Expiring soon/Expired ([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only)</span></span>  
  
-   <span data-ttu-id="e91ac-125">未初始化的订阅（仅限[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 和更高版本）</span><span class="sxs-lookup"><span data-stu-id="e91ac-125">Uninitialized subscription ([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only)</span></span>  
  
-   <span data-ttu-id="e91ac-126">正在重试失败的命令</span><span class="sxs-lookup"><span data-stu-id="e91ac-126">Retrying failed command</span></span>  
  
-   <span data-ttu-id="e91ac-127">正在同步</span><span class="sxs-lookup"><span data-stu-id="e91ac-127">Synchronizing</span></span>  
  
-   <span data-ttu-id="e91ac-128">未同步</span><span class="sxs-lookup"><span data-stu-id="e91ac-128">Not synchronizing</span></span>  
  
 <span data-ttu-id="e91ac-129">如果给定的订阅处于多种状态，该排序顺序还决定将要显示哪个值。</span><span class="sxs-lookup"><span data-stu-id="e91ac-129">The sort order also determines which value is displayed if a given subscription is in more than one state.</span></span> <span data-ttu-id="e91ac-130">例如，如果某个订阅包含错误并且即将过期， **“状态”** 列将显示 **“错误”**。</span><span class="sxs-lookup"><span data-stu-id="e91ac-130">For example, if a subscription has an error and is expiring soon, the **Status** column displays **Error**.</span></span>  
  
 <span data-ttu-id="e91ac-131">状态值 **“‘严重’状态下的性能”**、 **“长时间运行的合并”**、 **“即将过期/已过期”** 和 **“未初始化的订阅”** 都是警告。</span><span class="sxs-lookup"><span data-stu-id="e91ac-131">The status values **Performance critical**, **Long-running merge**, **Expiring soon/Expired**, and **Uninitialized subscription** are warnings.</span></span> <span data-ttu-id="e91ac-132">当显示警告时， **“状态”** 列还可显示是否正在同步代理。</span><span class="sxs-lookup"><span data-stu-id="e91ac-132">When a warning is displayed, the **Status** column also displays if an agent is synchronizing.</span></span> <span data-ttu-id="e91ac-133">例如，状态可能为 **“同步，‘严重’状态下的性能”**。</span><span class="sxs-lookup"><span data-stu-id="e91ac-133">For example, the status could be **Synchronizing, Performance critical**.</span></span>  
  
 <span data-ttu-id="e91ac-134">只有在设置了阈值时，才会显示状态值 **“即将过期/已过期”** 和 **“长时间运行的合并”** 。</span><span class="sxs-lookup"><span data-stu-id="e91ac-134">The status values **Expiring soon/Expired** and **Long-running merge** can be displayed only if thresholds are set.</span></span> <span data-ttu-id="e91ac-135">只有在使用相同的连接类型（拨号或 LAN）对订阅进行五次同步后，才会显示状态值 **“‘严重’状态下的性能”** 。</span><span class="sxs-lookup"><span data-stu-id="e91ac-135">The status value **Performance critical** can be displayed only after five synchronizations of subscriptions with the same connection type (dial-up or LAN).</span></span> <span data-ttu-id="e91ac-136">有关性能度量和设置阈值的信息，请参阅[使用复制监视器监视性能](monitor/monitor-performance-with-replication-monitor.md)和[在复制监视器中设置阈值和警告](monitor/set-thresholds-and-warnings-in-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="e91ac-136">For information about performance measurements and setting thresholds, see [Monitor Performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md) and [Set Thresholds and Warnings in Replication Monitor](monitor/set-thresholds-and-warnings-in-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="e91ac-137">**订阅**</span><span class="sxs-lookup"><span data-stu-id="e91ac-137">**Subscription**</span></span>  
 <span data-ttu-id="e91ac-138">每个订阅的名称，格式为：*SubscriberName: SubscriptionDatabaseName*。</span><span class="sxs-lookup"><span data-stu-id="e91ac-138">The name of each subscription, in the form:*SubscriberName: SubscriptionDatabaseName*.</span></span>  
  
 <span data-ttu-id="e91ac-139">**友好名称**</span><span class="sxs-lookup"><span data-stu-id="e91ac-139">**Friendly Name**</span></span>  
 <span data-ttu-id="e91ac-140">仅限[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 和更高版本。</span><span class="sxs-lookup"><span data-stu-id="e91ac-140">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only.</span></span> <span data-ttu-id="e91ac-141">每个订阅的说明。</span><span class="sxs-lookup"><span data-stu-id="e91ac-141">The description of each subscription.</span></span> <span data-ttu-id="e91ac-142">此说明是在 **“订阅属性”** 对话框中输入的，或是用 **@description** 或 [sp_addmergepullsubscription](/sql/relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql) 的 [@description](/sql/relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="e91ac-142">The description is entered in the **Subscription Properties** dialog box or specified with the **@description** parameter of [sp_addmergesubscription](/sql/relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql) or [sp_addmergepullsubscription](/sql/relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql).</span></span> <span data-ttu-id="e91ac-143">用户通常将说明用作订阅的“友好名称”或别名。</span><span class="sxs-lookup"><span data-stu-id="e91ac-143">Users often use the description as a "friendly name" or nickname for the subscription.</span></span>  
  
 <span data-ttu-id="e91ac-144">**性能**</span><span class="sxs-lookup"><span data-stu-id="e91ac-144">**Performance**</span></span>  
 <span data-ttu-id="e91ac-145">仅限[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 和更高版本。</span><span class="sxs-lookup"><span data-stu-id="e91ac-145">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only.</span></span> <span data-ttu-id="e91ac-146">每个订阅的性能等级，这是基于复制监视器对传送速率的最新度量值来确定的。</span><span class="sxs-lookup"><span data-stu-id="e91ac-146">The performance rating for each subscription, based on the most recent measurements of delivery rate taken by Replication Monitor.</span></span> <span data-ttu-id="e91ac-147">对于具有相同连接类型（拨号或 LAN）的发布的订阅，通过将单独的订阅性能与其平均历史性能进行比较，可以确定性能等级。</span><span class="sxs-lookup"><span data-stu-id="e91ac-147">The rating is determined by comparing individual subscription performance to the average historical performance of subscriptions to the publication that have the same connection type (dial-up or LAN).</span></span> <span data-ttu-id="e91ac-148">如果通过同一类型的连接进行了五次同步，且每次同步都进行了 50 处或更多的更改，则复制监视器将在此列中显示一个值。</span><span class="sxs-lookup"><span data-stu-id="e91ac-148">Replication Monitor displays a value after five synchronizations have occurred with 50 or more changes each over the same type of connection.</span></span> <span data-ttu-id="e91ac-149">如果所做更改为 50 处或更多处的同步次数少于五次，或最近一次同步所做的更改少于 50 处，则此列为空白。</span><span class="sxs-lookup"><span data-stu-id="e91ac-149">If there have been less than five synchronizations with 50 or more changes or the most recent synchronization has less than 50 changes, this column is blank.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e91ac-150"> 性能是根据 **“连接”** 列中显示的连接类型确定的；因此，对于较低传送速率的订阅来说，如果是通过较慢速度的连接进行同步的，那么该订阅也有可能显示出比其他订阅更高的性能等级。</span><span class="sxs-lookup"><span data-stu-id="e91ac-150">Performance is based on the connection type displayed in the **Connection** column; therefore it is possible for a subscription with a lower delivery rate to display a better performance rating than another subscription if the first subscription is synchronized over a slower connection.</span></span>  
  
 <span data-ttu-id="e91ac-151">性能等级可以为以下值之一：</span><span class="sxs-lookup"><span data-stu-id="e91ac-151">The performance rating is one of the following values:</span></span>  
  
-   <span data-ttu-id="e91ac-152">优秀</span><span class="sxs-lookup"><span data-stu-id="e91ac-152">Excellent</span></span>  
  
-   <span data-ttu-id="e91ac-153">好</span><span class="sxs-lookup"><span data-stu-id="e91ac-153">Good</span></span>  
  
-   <span data-ttu-id="e91ac-154">一般</span><span class="sxs-lookup"><span data-stu-id="e91ac-154">Fair</span></span>  
  
-   <span data-ttu-id="e91ac-155">差</span><span class="sxs-lookup"><span data-stu-id="e91ac-155">Poor</span></span>  
  
 <span data-ttu-id="e91ac-156">有关如何定义性能等级以及如何设置性能阈值的详细信息，请参阅[使用复制监视器监视性能](monitor/monitor-performance-with-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="e91ac-156">For more information on how performance ratings are defined and how performance thresholds are set, see [Monitor Performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="e91ac-157">**传送速率**</span><span class="sxs-lookup"><span data-stu-id="e91ac-157">**Delivery Rate**</span></span>  
 <span data-ttu-id="e91ac-158">合并代理每秒处理的行数。</span><span class="sxs-lookup"><span data-stu-id="e91ac-158">The number of rows per second processed by the Merge Agent.</span></span>  
  
 <span data-ttu-id="e91ac-159">**上次同步**</span><span class="sxs-lookup"><span data-stu-id="e91ac-159">**Last Synchronization**</span></span>  
 <span data-ttu-id="e91ac-160">合并代理上次运行的时间。</span><span class="sxs-lookup"><span data-stu-id="e91ac-160">The time at which the Merge Agent last ran.</span></span> <span data-ttu-id="e91ac-161">在此同步过程中，更改可能已处理，也可能尚未处理。</span><span class="sxs-lookup"><span data-stu-id="e91ac-161">Changes may or may not have been processed during this synchronization.</span></span> <span data-ttu-id="e91ac-162">如果正在进行同步，则会显示完成百分比值。</span><span class="sxs-lookup"><span data-stu-id="e91ac-162">If synchronization is in progress, a percentage complete value is displayed.</span></span>  
  
 <span data-ttu-id="e91ac-163">**持续时间**</span><span class="sxs-lookup"><span data-stu-id="e91ac-163">**Duration**</span></span>  
 <span data-ttu-id="e91ac-164">上次同步过程中合并代理运行所用的时间。</span><span class="sxs-lookup"><span data-stu-id="e91ac-164">The amount of time the Merge Agent has run during the last synchronization.</span></span> <span data-ttu-id="e91ac-165">如果合并代理当前正在同步，该时间表示已运行的时间；如果合并代理之前已经同步，该时间则表示上次同步所用的总时间。</span><span class="sxs-lookup"><span data-stu-id="e91ac-165">The time represents elapsed time if the Merge Agent is currently synchronizing and total time if the Merge Agent has synchronized previously.</span></span>  
  
 <span data-ttu-id="e91ac-166">**Connection**</span><span class="sxs-lookup"><span data-stu-id="e91ac-166">**Connection**</span></span>  
 <span data-ttu-id="e91ac-167">仅限[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 和更高版本。</span><span class="sxs-lookup"><span data-stu-id="e91ac-167">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only.</span></span> <span data-ttu-id="e91ac-168">订阅服务器与发布服务器之间的连接类型。</span><span class="sxs-lookup"><span data-stu-id="e91ac-168">The type of connection between the Subscriber and the Publisher.</span></span> <span data-ttu-id="e91ac-169">可能的值包括 **LAN**、 **“拨号”** 和 **Internet**。</span><span class="sxs-lookup"><span data-stu-id="e91ac-169">The possible values are **LAN**, **Dialup**, and **Internet**.</span></span> <span data-ttu-id="e91ac-170">如果订阅使用 Web 同步，则会显示 **Internet** 值。</span><span class="sxs-lookup"><span data-stu-id="e91ac-170">The **Internet** value is displayed if the subscription uses Web synchronization.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e91ac-171">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e91ac-171">See Also</span></span>  
 <span data-ttu-id="e91ac-172">[启动复制监视器](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="e91ac-172">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="e91ac-173">[使用复制监视器查看信息和执行任务](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="e91ac-173">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 <span data-ttu-id="e91ac-174">[监视复制](monitoring-replication.md) </span><span class="sxs-lookup"><span data-stu-id="e91ac-174">[Monitoring Replication](monitoring-replication.md) </span></span>  
 [<span data-ttu-id="e91ac-175">合并复制的 Web 同步</span><span class="sxs-lookup"><span data-stu-id="e91ac-175">Web Synchronization for Merge Replication</span></span>](web-synchronization-for-merge-replication.md)  
  
  
