---
title: 发布服务器信息，订阅监视列表 (快照发布，SQL Server 2005 及更高版本) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publisherinfo.subscriptionssummary.snapshot.f1
ms.assetid: 2ebeee62-7f54-4c77-9d37-15708bc5cc23
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ea44958c81465570c036ab7dd83247fb55652f1f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689861"
---
# <a name="publisher-information-subscription-watch-list-snapshot-publication-sql-server-2005-and-later"></a><span data-ttu-id="0289e-102">发布服务器信息，订阅监视列表（快照发布，SQL Server 2005 和更高版本）</span><span class="sxs-lookup"><span data-stu-id="0289e-102">Publisher Information, Subscription Watch List (Snapshot Publication, SQL Server 2005 and Later)</span></span>
  <span data-ttu-id="0289e-103">在运行 **及更高版本的分发服务器上，可以使用** “订阅监视列表” [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 选项卡；此选项卡用于显示所选发布服务器上的所有可用发布中的订阅的相关信息。</span><span class="sxs-lookup"><span data-stu-id="0289e-103">The **Subscription Watch List** tab is available for Distributors running [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions; it is intended to display information on subscriptions from all publications available at the selected Publisher.</span></span> <span data-ttu-id="0289e-104">可以筛选订阅列表，以查看有错误的订阅、出现警告的订阅以及所有性能较差的订阅。</span><span class="sxs-lookup"><span data-stu-id="0289e-104">You can filter the list of subscriptions to see errors, warnings, and any poorly performing subscriptions.</span></span> <span data-ttu-id="0289e-105">此选项卡为管理员提供了监视发布服务器上所有复制活动的单一位置：复制监视器根据所选复制类型和在 **“显示”** 下拉列表框中选择的选项，显示所有需要注意的订阅。</span><span class="sxs-lookup"><span data-stu-id="0289e-105">This tab provides a single location for an administrator to monitor all replication activity at a Publisher: Replication Monitor displays all subscriptions that require attention, based on the selected replication type and on the option chosen in the **Show** drop-down list box.</span></span> <span data-ttu-id="0289e-106">由于此选项卡上显示的项基于当前状态和性能，因此只有与 **“显示”** 列表框中的当前选项相匹配的订阅才会显示在此页上。</span><span class="sxs-lookup"><span data-stu-id="0289e-106">Because the items displayed on this tab are based on current status and performance, subscriptions are displayed on this page only if they match the option in the **Show** list box at the current time.</span></span>  
  
## <a name="options"></a><span data-ttu-id="0289e-107">选项</span><span class="sxs-lookup"><span data-stu-id="0289e-107">Options</span></span>  
 <span data-ttu-id="0289e-108">有关订阅的详细信息及相关任务，请右键单击相应订阅所在的行，再单击快捷菜单上的选项。</span><span class="sxs-lookup"><span data-stu-id="0289e-108">For more detailed information and tasks related to a subscription, right-click the row for that subscription, and then click an option on the shortcut menu.</span></span> <span data-ttu-id="0289e-109">若要更改网格显示数据的方式，请右键单击网格，然后单击以下选项之一：</span><span class="sxs-lookup"><span data-stu-id="0289e-109">To change the way that the grid displays data, right-click the grid, and then click one of the following options:</span></span>  
  
-   <span data-ttu-id="0289e-110">**排序**：按 **“列排序”** 对话框中的一列或多列排序。</span><span class="sxs-lookup"><span data-stu-id="0289e-110">**Sort**: Sort on one or more columns in the **Sort Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="0289e-111">**选择要显示的列**：选择要显示哪些列以及要在 **“选择列”** 对话框中以何种顺序显示它们。</span><span class="sxs-lookup"><span data-stu-id="0289e-111">**Choose Columns to Show**: Select which columns to display and the order in which to display them in the **Choose Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="0289e-112">**筛选器**：根据 **“筛选设置”** 对话框中的列值筛选网格中的行。</span><span class="sxs-lookup"><span data-stu-id="0289e-112">**Filter**: Filter rows in the grid based on column values in the **Filter Settings** dialog box.</span></span>  
  
-   <span data-ttu-id="0289e-113">**清除筛选器**：清除网格的任何筛选设置。</span><span class="sxs-lookup"><span data-stu-id="0289e-113">**Clear Filter**: Clear any filter settings for the grid.</span></span>  
  
 <span data-ttu-id="0289e-114">筛选设置是特定于每个网格的。</span><span class="sxs-lookup"><span data-stu-id="0289e-114">Filter settings are specific to each grid.</span></span> <span data-ttu-id="0289e-115">列的选择和排序应用于同一类型的所有网格，如每个发布服务器的发布网格。</span><span class="sxs-lookup"><span data-stu-id="0289e-115">Column selection and sorting are applied to all grids of the same type, such as the publications grid for each Publisher.</span></span>  
  
 <span data-ttu-id="0289e-116">**显示快照订阅**</span><span class="sxs-lookup"><span data-stu-id="0289e-116">**Show Snapshot Subscriptions**</span></span>  
 <span data-ttu-id="0289e-117">为所选发布服务器选择要显示的订阅类型（事务、快照或合并）。</span><span class="sxs-lookup"><span data-stu-id="0289e-117">Select the type of subscriptions (transactional, snapshot, or merge) to display for the selected Publisher.</span></span>  
  
 <span data-ttu-id="0289e-118">**显示**</span><span class="sxs-lookup"><span data-stu-id="0289e-118">**Show**</span></span>  
 <span data-ttu-id="0289e-119">为所选订阅类型选择要显示的订阅状态。</span><span class="sxs-lookup"><span data-stu-id="0289e-119">Select the subscription states to display for the selected subscription type.</span></span> <span data-ttu-id="0289e-120">例如，可以选择仅显示包含错误的订阅。</span><span class="sxs-lookup"><span data-stu-id="0289e-120">For example, you can select to display only those subscriptions that have an error.</span></span>  
  
 <span data-ttu-id="0289e-121">**Status**</span><span class="sxs-lookup"><span data-stu-id="0289e-121">**Status**</span></span>  
 <span data-ttu-id="0289e-122">每一个订阅的状态，该状态由快照代理或分发代理的状态决定（显示优先级较高的状态）。</span><span class="sxs-lookup"><span data-stu-id="0289e-122">The status of each subscription, which is determined by the status of the Snapshot Agent or the Distribution Agent (the higher priority status is displayed).</span></span>  
  
 <span data-ttu-id="0289e-123">默认情况下，包含订阅信息的网格按 **“状态”** 列排序。</span><span class="sxs-lookup"><span data-stu-id="0289e-123">By default, the grid containing subscription information is sorted by the **Status** column.</span></span> <span data-ttu-id="0289e-124">下面的列表显示了可能的状态值以及这些值的排序顺序（例如，错误项始终显示在该网格的顶部）：</span><span class="sxs-lookup"><span data-stu-id="0289e-124">The following list shows the possible status values and the sort order for the values (for example, errors are always shown at the top of the grid).</span></span>  
  
-   <span data-ttu-id="0289e-125">错误</span><span class="sxs-lookup"><span data-stu-id="0289e-125">Error</span></span>  
  
-   <span data-ttu-id="0289e-126">即将过期/已过期</span><span class="sxs-lookup"><span data-stu-id="0289e-126">Expiring soon/Expired</span></span>  
  
-   <span data-ttu-id="0289e-127">未初始化的订阅</span><span class="sxs-lookup"><span data-stu-id="0289e-127">Uninitialized subscription</span></span>  
  
-   <span data-ttu-id="0289e-128">正在重试失败的命令</span><span class="sxs-lookup"><span data-stu-id="0289e-128">Retrying failed command</span></span>  
  
-   <span data-ttu-id="0289e-129">正在同步</span><span class="sxs-lookup"><span data-stu-id="0289e-129">Synchronizing</span></span>  
  
-   <span data-ttu-id="0289e-130">未同步</span><span class="sxs-lookup"><span data-stu-id="0289e-130">Not synchronizing</span></span>  
  
 <span data-ttu-id="0289e-131">如果给定的订阅处于多种状态，该排序顺序还决定将要显示哪个值。</span><span class="sxs-lookup"><span data-stu-id="0289e-131">The sort order also determines which value is displayed if a given subscription is in more than one state.</span></span> <span data-ttu-id="0289e-132">例如，如果某个订阅包含错误并且即将过期， **“状态”** 列将显示 **“错误”**。</span><span class="sxs-lookup"><span data-stu-id="0289e-132">For example, if a subscription has an error and is expiring soon, the **Status** column displays **Error**.</span></span>  
  
 <span data-ttu-id="0289e-133">状态值 **“即将过期/已过期”** 和 **“未初始化的订阅”** 属于警告。</span><span class="sxs-lookup"><span data-stu-id="0289e-133">The status values **Expiring soon/Expired** and **Uninitialized subscription** are warnings.</span></span> <span data-ttu-id="0289e-134">当显示警告时， **“状态”** 列还可显示是否正在运行代理。</span><span class="sxs-lookup"><span data-stu-id="0289e-134">When a warning is displayed, the **Status** column also displays if an agent is running.</span></span> <span data-ttu-id="0289e-135">例如，状态可以为 **“正在运行，即将过期/已过期”**。</span><span class="sxs-lookup"><span data-stu-id="0289e-135">For example, the status could be **Running, Expiring soon/Expired**.</span></span>  
  
 <span data-ttu-id="0289e-136">只有在设置了阈值时，才会显示状态值 **“即将过期/已过期”** 。</span><span class="sxs-lookup"><span data-stu-id="0289e-136">The status value **Expiring soon/Expired** is displayed only if a threshold is set.</span></span> <span data-ttu-id="0289e-137">有关设置阈值的信息，请参阅[在复制监视器中设置阈值和警告](monitor/set-thresholds-and-warnings-in-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="0289e-137">For information on setting thresholds, see [Set Thresholds and Warnings in Replication Monitor](monitor/set-thresholds-and-warnings-in-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="0289e-138">**订阅**</span><span class="sxs-lookup"><span data-stu-id="0289e-138">**Subscription**</span></span>  
 <span data-ttu-id="0289e-139">每个订阅的名称，格式为： *SubscriberName: SubscriptionDatabaseName*。</span><span class="sxs-lookup"><span data-stu-id="0289e-139">The name of each subscription, in the form: *SubscriberName: SubscriptionDatabaseName*.</span></span>  
  
 <span data-ttu-id="0289e-140">**发布**</span><span class="sxs-lookup"><span data-stu-id="0289e-140">**Publication**</span></span>  
 <span data-ttu-id="0289e-141">与订阅同步的发布的名称，格式为： *PublicationDatabaseName: PublicationName*。</span><span class="sxs-lookup"><span data-stu-id="0289e-141">The name of the publication with which a subscription synchronizes, in the form: *PublicationDatabaseName: PublicationName*.</span></span>  
  
 <span data-ttu-id="0289e-142">**上次同步**</span><span class="sxs-lookup"><span data-stu-id="0289e-142">**Last Synchronization**</span></span>  
 <span data-ttu-id="0289e-143">分发代理上次运行的时间。</span><span class="sxs-lookup"><span data-stu-id="0289e-143">The time at which the Distribution Agent last ran.</span></span> <span data-ttu-id="0289e-144">如果正在进行同步，则显示 **“正在进行”** 。</span><span class="sxs-lookup"><span data-stu-id="0289e-144">If synchronization is in progress, **In progress** is displayed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0289e-145">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0289e-145">See Also</span></span>  
 <span data-ttu-id="0289e-146">[启动复制监视器](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="0289e-146">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="0289e-147">[使用复制监视器查看信息和执行任务](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="0289e-147">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 [<span data-ttu-id="0289e-148">监视复制</span><span class="sxs-lookup"><span data-stu-id="0289e-148">Monitoring Replication</span></span>](monitoring-replication.md)  
  
  
