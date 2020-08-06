---
title: 发布信息，所有订阅（事务发布）| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publicationinfo.allsubscriptions.tran.f1
ms.assetid: 7073350c-f667-4f70-88e9-152c9a1b08dd
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ccc34bbe0933f4558478bd1d8276898219016e24
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578820"
---
# <a name="publication-information-all-subscriptions-transactional-publication"></a><span data-ttu-id="2c57d-102">发布信息，所有订阅（事务发布）</span><span class="sxs-lookup"><span data-stu-id="2c57d-102">Publication Information, All Subscriptions (Transactional Publication)</span></span>
  <span data-ttu-id="2c57d-103">“所有订阅”\*\*\*\* 选项卡显示所选事务发布的所有订阅的相关信息。</span><span class="sxs-lookup"><span data-stu-id="2c57d-103">The **All Subscriptions** tab displays information on all subscriptions to the selected transactional publication.</span></span>  
  
## <a name="options"></a><span data-ttu-id="2c57d-104">选项</span><span class="sxs-lookup"><span data-stu-id="2c57d-104">Options</span></span>  
 <span data-ttu-id="2c57d-105">有关订阅的详细信息及相关任务，请右键单击相应订阅所在的行，再单击快捷菜单上的选项。</span><span class="sxs-lookup"><span data-stu-id="2c57d-105">For more detailed information and tasks related to a subscription, right-click the row for that subscription, and then click an option on the shortcut menu.</span></span> <span data-ttu-id="2c57d-106">若要更改网格显示数据的方式，请右键单击网格，然后单击以下选项之一：</span><span class="sxs-lookup"><span data-stu-id="2c57d-106">To change the way that the grid displays data, right-click the grid, and then click one of the following options:</span></span>  
  
-   <span data-ttu-id="2c57d-107">**排序**：按 **“列排序”** 对话框中的一列或多列排序。</span><span class="sxs-lookup"><span data-stu-id="2c57d-107">**Sort**: Sort on one or more columns in the **Sort Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="2c57d-108">**选择要显示的列**：选择要显示哪些列以及要在 **“选择列”** 对话框中以何种顺序显示它们。</span><span class="sxs-lookup"><span data-stu-id="2c57d-108">**Choose Columns to Show**: Select which columns to display and the order in which to display them in the **Choose Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="2c57d-109">**筛选器**：根据 **“筛选设置”** 对话框中的列值筛选网格中的行。</span><span class="sxs-lookup"><span data-stu-id="2c57d-109">**Filter**: Filter rows in the grid based on column values in the **Filter Settings** dialog box.</span></span>  
  
-   <span data-ttu-id="2c57d-110">**清除筛选器**：清除网格的任何筛选设置。</span><span class="sxs-lookup"><span data-stu-id="2c57d-110">**Clear Filter**: Clear any filter settings for the grid.</span></span>  
  
 <span data-ttu-id="2c57d-111">筛选设置是特定于每个网格的。</span><span class="sxs-lookup"><span data-stu-id="2c57d-111">Filter settings are specific to each grid.</span></span> <span data-ttu-id="2c57d-112">列的选择和排序应用于同一类型的所有网格，如每个发布服务器的发布网格。</span><span class="sxs-lookup"><span data-stu-id="2c57d-112">Column selection and sorting are applied to all grids of the same type, such as the publications grid for each Publisher.</span></span>  
  
 <span data-ttu-id="2c57d-113">**显示**</span><span class="sxs-lookup"><span data-stu-id="2c57d-113">**Show**</span></span>  
 <span data-ttu-id="2c57d-114">仅限 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 及更高版本。</span><span class="sxs-lookup"><span data-stu-id="2c57d-114">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only.</span></span> <span data-ttu-id="2c57d-115">为所选订阅类型选择要显示的订阅状态。</span><span class="sxs-lookup"><span data-stu-id="2c57d-115">Select the subscription states to display for the selected subscription type.</span></span> <span data-ttu-id="2c57d-116">例如，可以选择仅显示包含错误的订阅。</span><span class="sxs-lookup"><span data-stu-id="2c57d-116">For example, you can select to display only those subscriptions that have an error.</span></span>  
  
 <span data-ttu-id="2c57d-117">**Status**</span><span class="sxs-lookup"><span data-stu-id="2c57d-117">**Status**</span></span>  
 <span data-ttu-id="2c57d-118">每个订阅的状态，由分发代理或日志读取器代理的状态决定（显示优先级较高的状态；如果使用排队更新订阅，则状态还可以由队列读取器代理决定）。</span><span class="sxs-lookup"><span data-stu-id="2c57d-118">The status of each subscription, which is determined by the status of the Distribution Agent or the Log Reader Agent (the higher priority status is displayed; the status can also be determined by the Queue Reader Agent if queued updating subscriptions are used).</span></span>  
  
 <span data-ttu-id="2c57d-119">默认情况下，包含订阅信息的网格按 **“状态”** 列排序（对于具有相同状态的订阅，再按 **“性能”** 列排序）。</span><span class="sxs-lookup"><span data-stu-id="2c57d-119">By default, the grid containing subscription information is sorted by the **Status** column (and then sorted by the **Performance** column for those subscriptions with the same status).</span></span> <span data-ttu-id="2c57d-120">下面的列表显示了可能的状态值以及这些值的排序顺序（例如，错误项始终显示在该网格的顶部）：</span><span class="sxs-lookup"><span data-stu-id="2c57d-120">The following list shows the possible status values and the sort order for the values (for example, errors are always shown at the top of the grid).</span></span>  
  
-   <span data-ttu-id="2c57d-121">错误</span><span class="sxs-lookup"><span data-stu-id="2c57d-121">Error</span></span>  
  
-   <span data-ttu-id="2c57d-122">“严重”状态下的性能（仅限[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 和更高版本）</span><span class="sxs-lookup"><span data-stu-id="2c57d-122">Performance critical ([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only)</span></span>  
  
-   <span data-ttu-id="2c57d-123">即将过期/已过期（仅限[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 和更高版本）</span><span class="sxs-lookup"><span data-stu-id="2c57d-123">Expiring soon/Expired ([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only)</span></span>  
  
-   <span data-ttu-id="2c57d-124">未初始化的订阅（仅限[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 和更高版本）</span><span class="sxs-lookup"><span data-stu-id="2c57d-124">Uninitialized subscription ([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only)</span></span>  
  
-   <span data-ttu-id="2c57d-125">正在重试失败的命令</span><span class="sxs-lookup"><span data-stu-id="2c57d-125">Retrying failed command</span></span>  
  
-   <span data-ttu-id="2c57d-126">未运行</span><span class="sxs-lookup"><span data-stu-id="2c57d-126">Not Running</span></span>  
  
-   <span data-ttu-id="2c57d-127">正在运行</span><span class="sxs-lookup"><span data-stu-id="2c57d-127">Running</span></span>  
  
 <span data-ttu-id="2c57d-128">如果给定的订阅处于多种状态，该排序顺序还决定将要显示哪个值。</span><span class="sxs-lookup"><span data-stu-id="2c57d-128">The sort order also determines which value is displayed if a given subscription is in more than one state.</span></span> <span data-ttu-id="2c57d-129">例如，如果某个订阅包含错误并且即将过期， **“状态”** 列将显示 **“错误”**。</span><span class="sxs-lookup"><span data-stu-id="2c57d-129">For example, if a subscription has an error and is expiring soon, the **Status** column displays **Error**.</span></span>  
  
 <span data-ttu-id="2c57d-130">状态值 **“‘严重’状态下的性能”**、 **“即将过期/已过期”** 和 **“未初始化的订阅”** 都是警告。</span><span class="sxs-lookup"><span data-stu-id="2c57d-130">The status values **Performance critical**, **Expiring soon/Expired**, and **Uninitialized subscription** are warnings.</span></span> <span data-ttu-id="2c57d-131">当显示警告时， **“状态”** 列还可显示是否正在运行代理。</span><span class="sxs-lookup"><span data-stu-id="2c57d-131">When a warning is displayed, the **Status** column also displays if an agent is running.</span></span> <span data-ttu-id="2c57d-132">例如，状态可能为 **“正在运行，‘严重’状态下的性能”**。</span><span class="sxs-lookup"><span data-stu-id="2c57d-132">For example, the status could be **Running, Performance critical**.</span></span>  
  
 <span data-ttu-id="2c57d-133">只有在设置了阈值时，才会显示状态值 **“‘严重’状态下的性能”** 和 **“即将过期/已过期”** 。</span><span class="sxs-lookup"><span data-stu-id="2c57d-133">The status values **Performance critical** and **Expiring soon/Expired** are displayed only if thresholds are set.</span></span> <span data-ttu-id="2c57d-134">有关性能度量和设置阈值的信息，请参阅[使用复制监视器监视性能](monitor/monitor-performance-with-replication-monitor.md)和[在复制监视器中设置阈值和警告](monitor/set-thresholds-and-warnings-in-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="2c57d-134">For information on performance measurements and setting thresholds, see [Monitor Performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md) and [Set Thresholds and Warnings in Replication Monitor](monitor/set-thresholds-and-warnings-in-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="2c57d-135">**订阅**</span><span class="sxs-lookup"><span data-stu-id="2c57d-135">**Subscription**</span></span>  
 <span data-ttu-id="2c57d-136">每个订阅的名称，格式为： *SubscriberName: SubscriptionDatabaseName*。</span><span class="sxs-lookup"><span data-stu-id="2c57d-136">The name of each subscription, in the form: *SubscriberName: SubscriptionDatabaseName*.</span></span>  
  
 <span data-ttu-id="2c57d-137">**性能**</span><span class="sxs-lookup"><span data-stu-id="2c57d-137">**Performance**</span></span>  
 <span data-ttu-id="2c57d-138">仅限[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 和更高版本。</span><span class="sxs-lookup"><span data-stu-id="2c57d-138">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only.</span></span> <span data-ttu-id="2c57d-139">每个订阅的性能等级都是基于复制监视器的最新度量值，并不反映历史性能。</span><span class="sxs-lookup"><span data-stu-id="2c57d-139">The performance rating for each subscription is based on the most recent measurements taken by Replication Monitor and does not reflect historical performance.</span></span> <span data-ttu-id="2c57d-140">对于为发布定义了性能阈值的订阅，均会度量其性能；如果没有为发布定义性能阈值，此列将显示 **“未启用”**。</span><span class="sxs-lookup"><span data-stu-id="2c57d-140">Performance is measured for subscriptions to publications that have performance thresholds defined; if performance thresholds are not defined for a publication, this column displays **Not enabled**.</span></span> <span data-ttu-id="2c57d-141">性能等级可以为以下值之一：</span><span class="sxs-lookup"><span data-stu-id="2c57d-141">The performance rating is one of the following values:</span></span>  
  
-   <span data-ttu-id="2c57d-142">优秀</span><span class="sxs-lookup"><span data-stu-id="2c57d-142">Excellent</span></span>  
  
-   <span data-ttu-id="2c57d-143">好</span><span class="sxs-lookup"><span data-stu-id="2c57d-143">Good</span></span>  
  
-   <span data-ttu-id="2c57d-144">一般</span><span class="sxs-lookup"><span data-stu-id="2c57d-144">Fair</span></span>  
  
-   <span data-ttu-id="2c57d-145">差</span><span class="sxs-lookup"><span data-stu-id="2c57d-145">Poor</span></span>  
  
-   <span data-ttu-id="2c57d-146">严重</span><span class="sxs-lookup"><span data-stu-id="2c57d-146">Critical</span></span>  
  
 <span data-ttu-id="2c57d-147">如果性能状态为“严重”，则 **“状态”** 列中将显示 **“‘严重’状态下的性能”** 。</span><span class="sxs-lookup"><span data-stu-id="2c57d-147">If performance is critical, **Performance Critical** is displayed in the **Status** column.</span></span> <span data-ttu-id="2c57d-148">有关如何定义性能等级以及如何设置性能阈值的详细信息，请参阅[使用复制监视器监视性能](monitor/monitor-performance-with-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="2c57d-148">For more information on how performance ratings are defined and how performance thresholds are set, see [Monitor Performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="2c57d-149">**延迟**</span><span class="sxs-lookup"><span data-stu-id="2c57d-149">**Latency**</span></span>  
 <span data-ttu-id="2c57d-150">仅限[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 和更高版本。</span><span class="sxs-lookup"><span data-stu-id="2c57d-150">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only.</span></span> <span data-ttu-id="2c57d-151">事务在发布服务器上提交和相应的事务在订阅服务器上提交之间间隔的平均时间。</span><span class="sxs-lookup"><span data-stu-id="2c57d-151">The average amount of time that elapses between a transaction being committed at the Publisher and the corresponding transaction being committed at the Subscriber.</span></span> <span data-ttu-id="2c57d-152">所显示的滞后时间基于复制监视器的最新度量值。</span><span class="sxs-lookup"><span data-stu-id="2c57d-152">The latency displayed is based on the most recent measurements taken by Replication Monitor.</span></span> <span data-ttu-id="2c57d-153">有关测量滞后时间的详细信息，请参阅[为事务复制测量滞后时间和验证连接](monitor/measure-latency-and-validate-connections-for-transactional-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="2c57d-153">For more information about measuring latency, see [Measure Latency and Validate Connections for Transactional Replication](monitor/measure-latency-and-validate-connections-for-transactional-replication.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c57d-154">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2c57d-154">See Also</span></span>  
 <span data-ttu-id="2c57d-155">[启动复制监视器](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="2c57d-155">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="2c57d-156">[使用复制监视器查看信息和执行任务](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="2c57d-156">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 [<span data-ttu-id="2c57d-157">监视复制</span><span class="sxs-lookup"><span data-stu-id="2c57d-157">Monitoring Replication</span></span>](monitoring-replication.md)  
  
  
