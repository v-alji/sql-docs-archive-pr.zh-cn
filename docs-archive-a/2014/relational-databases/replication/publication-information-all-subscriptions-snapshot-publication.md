---
title: 发布信息，所有订阅（快照发布）| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publicationinfo.allsubscriptions.snapshot.f1
ms.assetid: 7ce656c2-6e60-4625-8955-1daff641070c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 75eb85adae46481ddd4360f095c00060af5677fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587353"
---
# <a name="publication-information-all-subscriptions-snapshot-publication"></a><span data-ttu-id="41015-102">发布信息，所有订阅（快照发布）</span><span class="sxs-lookup"><span data-stu-id="41015-102">Publication Information, All Subscriptions (Snapshot Publication)</span></span>
  <span data-ttu-id="41015-103">**“所有订阅”** 选项卡显示针对所选快照发布的所有订阅的相关信息。</span><span class="sxs-lookup"><span data-stu-id="41015-103">The **All Subscriptions** tab displays information on all subscriptions to the selected snapshot publication.</span></span>  
  
## <a name="options"></a><span data-ttu-id="41015-104">选项</span><span class="sxs-lookup"><span data-stu-id="41015-104">Options</span></span>  
 <span data-ttu-id="41015-105">有关订阅的详细信息及相关任务，请右键单击相应订阅所在的行，再单击快捷菜单上的选项。</span><span class="sxs-lookup"><span data-stu-id="41015-105">For more detailed information and tasks related to a subscription, right-click the row for that subscription, and then click an option on the shortcut menu.</span></span> <span data-ttu-id="41015-106">若要更改网格显示数据的方式，请右键单击网格，然后单击以下选项之一：</span><span class="sxs-lookup"><span data-stu-id="41015-106">To change the way that the grid displays data, right-click the grid, and then click one of the following options:</span></span>  
  
-   <span data-ttu-id="41015-107">**排序**：按 **“列排序”** 对话框中的一列或多列排序。</span><span class="sxs-lookup"><span data-stu-id="41015-107">**Sort**: Sort on one or more columns in the **Sort Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="41015-108">**选择要显示的列**：选择要显示哪些列以及要在 **“选择列”** 对话框中以何种顺序显示它们。</span><span class="sxs-lookup"><span data-stu-id="41015-108">**Choose Columns to Show**: Select which columns to display and the order in which to display them in the **Choose Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="41015-109">**筛选器**：根据 **“筛选设置”** 对话框中的列值筛选网格中的行。</span><span class="sxs-lookup"><span data-stu-id="41015-109">**Filter**: Filter rows in the grid based on column values in the **Filter Settings** dialog box.</span></span>  
  
-   <span data-ttu-id="41015-110">**清除筛选器**：清除网格的任何筛选设置。</span><span class="sxs-lookup"><span data-stu-id="41015-110">**Clear Filter**: Clear any filter settings for the grid.</span></span>  
  
 <span data-ttu-id="41015-111">筛选设置是特定于每个网格的。</span><span class="sxs-lookup"><span data-stu-id="41015-111">Filter settings are specific to each grid.</span></span> <span data-ttu-id="41015-112">列的选择和排序应用于同一类型的所有网格，如每个发布服务器的发布网格。</span><span class="sxs-lookup"><span data-stu-id="41015-112">Column selection and sorting are applied to all grids of the same type, such as the publications grid for each Publisher.</span></span>  
  
 <span data-ttu-id="41015-113">**显示**</span><span class="sxs-lookup"><span data-stu-id="41015-113">**Show**</span></span>  
 <span data-ttu-id="41015-114">仅限 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 及更高版本。</span><span class="sxs-lookup"><span data-stu-id="41015-114">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only.</span></span> <span data-ttu-id="41015-115">为所选订阅类型选择要显示的订阅状态。</span><span class="sxs-lookup"><span data-stu-id="41015-115">Select the subscription states to display for the selected subscription type.</span></span> <span data-ttu-id="41015-116">例如，可以选择仅显示包含错误的订阅。</span><span class="sxs-lookup"><span data-stu-id="41015-116">For example, you can select to display only those subscriptions that have an error.</span></span>  
  
 <span data-ttu-id="41015-117">**Status**</span><span class="sxs-lookup"><span data-stu-id="41015-117">**Status**</span></span>  
 <span data-ttu-id="41015-118">每一个订阅的状态，该状态由快照代理或分发代理的状态决定（显示优先级较高的状态）。</span><span class="sxs-lookup"><span data-stu-id="41015-118">The status of each subscription, which is determined by the status of the Snapshot Agent or the Distribution Agent (the higher priority status is displayed).</span></span>  
  
 <span data-ttu-id="41015-119">默认情况下，包含订阅信息的网格按 **“状态”** 列排序。</span><span class="sxs-lookup"><span data-stu-id="41015-119">By default, the grid containing subscription information is sorted by the **Status** column.</span></span> <span data-ttu-id="41015-120">下面的列表显示了可能的状态值以及这些值的排序顺序（例如，错误项始终显示在该网格的顶部）：</span><span class="sxs-lookup"><span data-stu-id="41015-120">The following list shows the possible status values and the sort order for the values (for example, errors are always shown at the top of the grid).</span></span>  
  
-   <span data-ttu-id="41015-121">错误</span><span class="sxs-lookup"><span data-stu-id="41015-121">Error</span></span>  
  
-   <span data-ttu-id="41015-122">即将过期/已过期（仅限[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 和更高版本）</span><span class="sxs-lookup"><span data-stu-id="41015-122">Expiring soon/Expired ([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only)</span></span>  
  
-   <span data-ttu-id="41015-123">未初始化的订阅（仅限[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 和更高版本）</span><span class="sxs-lookup"><span data-stu-id="41015-123">Uninitialized subscription ([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only)</span></span>  
  
-   <span data-ttu-id="41015-124">正在重试失败的命令</span><span class="sxs-lookup"><span data-stu-id="41015-124">Retrying failed command</span></span>  
  
-   <span data-ttu-id="41015-125">正在同步</span><span class="sxs-lookup"><span data-stu-id="41015-125">Synchronizing</span></span>  
  
-   <span data-ttu-id="41015-126">未同步</span><span class="sxs-lookup"><span data-stu-id="41015-126">Not synchronizing</span></span>  
  
 <span data-ttu-id="41015-127">如果给定的订阅处于多种状态，该排序顺序还决定将要显示哪个值。</span><span class="sxs-lookup"><span data-stu-id="41015-127">The sort order also determines which value is displayed if a given subscription is in more than one state.</span></span> <span data-ttu-id="41015-128">例如，如果某个订阅包含错误并且即将过期， **“状态”** 列将显示 **“错误”**。</span><span class="sxs-lookup"><span data-stu-id="41015-128">For example, if a subscription has an error and is expiring soon, the **Status** column displays **Error**.</span></span>  
  
 <span data-ttu-id="41015-129">状态值 **“即将过期/已过期”** 和 **“未初始化的订阅”** 属于警告。</span><span class="sxs-lookup"><span data-stu-id="41015-129">The status values **Expiring soon/Expired** and **Uninitialized subscription** are warnings.</span></span> <span data-ttu-id="41015-130">当显示警告时， **“状态”** 列还可显示是否正在运行代理。</span><span class="sxs-lookup"><span data-stu-id="41015-130">When a warning is displayed, the **Status** column also displays if an agent is running.</span></span> <span data-ttu-id="41015-131">例如，状态可以为 **“正在运行，即将过期/已过期”**。</span><span class="sxs-lookup"><span data-stu-id="41015-131">For example, the status could be **Running, Expiring soon/Expired**.</span></span>  
  
 <span data-ttu-id="41015-132">只有在设置了阈值时，才会显示状态值 **“即将过期/已过期”** 。</span><span class="sxs-lookup"><span data-stu-id="41015-132">The status value **Expiring soon/Expired** is displayed only if a threshold is set.</span></span> <span data-ttu-id="41015-133">有关设置阈值的信息，请参阅[在复制监视器中设置阈值和警告](monitor/set-thresholds-and-warnings-in-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="41015-133">For information on setting thresholds, see [Set Thresholds and Warnings in Replication Monitor](monitor/set-thresholds-and-warnings-in-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="41015-134">**订阅**</span><span class="sxs-lookup"><span data-stu-id="41015-134">**Subscription**</span></span>  
 <span data-ttu-id="41015-135">每个订阅的名称，格式为： *SubscriberName: SubscriptionDatabaseName*。</span><span class="sxs-lookup"><span data-stu-id="41015-135">The name of each subscription, in the form: *SubscriberName: SubscriptionDatabaseName*.</span></span>  
  
 <span data-ttu-id="41015-136">**上次同步**</span><span class="sxs-lookup"><span data-stu-id="41015-136">**Last Synchronization**</span></span>  
 <span data-ttu-id="41015-137">分发代理上次运行的时间。</span><span class="sxs-lookup"><span data-stu-id="41015-137">The time at which the Distribution Agent last ran.</span></span> <span data-ttu-id="41015-138">如果正在进行同步，则显示 **“正在进行”** 。</span><span class="sxs-lookup"><span data-stu-id="41015-138">If synchronization is in progress, **In progress** is displayed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41015-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="41015-139">See Also</span></span>  
 <span data-ttu-id="41015-140">[启动复制监视器](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="41015-140">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="41015-141">[使用复制监视器查看信息和执行任务](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="41015-141">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 [<span data-ttu-id="41015-142">监视复制</span><span class="sxs-lookup"><span data-stu-id="41015-142">Monitoring Replication</span></span>](monitoring-replication.md)  
  
  
