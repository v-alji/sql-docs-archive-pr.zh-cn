---
title: 发布信息，警告 (合并发布，SQL Server 2005 及更高版本) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publicationinfo.warningsandagents.merge.f1
ms.assetid: 9bef3565-5f13-42ac-8723-ebe55b0c11e6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 75f58a4cd9bd84791acf7fd9d28147ef3bbd6232
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587354"
---
# <a name="publication-information-warnings-merge-publication-sql-server-2005-and-later"></a><span data-ttu-id="5a564-102">发布信息，警告（合并发布，SQL Server 2005 及更高版本）</span><span class="sxs-lookup"><span data-stu-id="5a564-102">Publication Information, Warnings (Merge Publication, SQL Server 2005 and Later)</span></span>
  <span data-ttu-id="5a564-103">**“警告”** 选项卡适用于运行 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 和更高版本的分发服务器。</span><span class="sxs-lookup"><span data-stu-id="5a564-103">The **Warnings** tab is available for Distributors that are running [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions.</span></span> <span data-ttu-id="5a564-104">使用 **“警告”** 选项卡可以为所选发布执行下列任务：</span><span class="sxs-lookup"><span data-stu-id="5a564-104">The **Warnings** tab allows you to perform the following tasks for the selected publication:</span></span>  
  
-   <span data-ttu-id="5a564-105">启用警告。</span><span class="sxs-lookup"><span data-stu-id="5a564-105">Enable warnings.</span></span>  
  
-   <span data-ttu-id="5a564-106">指定与警告关联的阈值。</span><span class="sxs-lookup"><span data-stu-id="5a564-106">Specify thresholds associated with warnings.</span></span>  
  
-   <span data-ttu-id="5a564-107">定义与警告关联的警报。</span><span class="sxs-lookup"><span data-stu-id="5a564-107">Define alerts associated with warnings.</span></span>  
  
## <a name="warnings-thresholds-and-alerts"></a><span data-ttu-id="5a564-108">警告、阈值和警报</span><span class="sxs-lookup"><span data-stu-id="5a564-108">Warnings, Thresholds, and Alerts</span></span>  
 <span data-ttu-id="5a564-109">默认情况下，复制监视器会为未初始化的订阅显示警告：在包含订阅信息的页的 **“状态”** 列中，显示 **“未初始化的订阅”** 状态作为警告。</span><span class="sxs-lookup"><span data-stu-id="5a564-109">By default, Replication Monitor displays warnings for uninitialized subscriptions: a status of **Uninitialized subscription** is displayed as a warning in the **Status** column of pages that include subscription information.</span></span> <span data-ttu-id="5a564-110">对于合并发布，可以指定以下附加条件是否导致警告：</span><span class="sxs-lookup"><span data-stu-id="5a564-110">For merge publications, you can specify whether these additional conditions result in warnings:</span></span>  
  
-   <span data-ttu-id="5a564-111">订阅即将过期。</span><span class="sxs-lookup"><span data-stu-id="5a564-111">Imminent subscription expiration.</span></span>  
  
     <span data-ttu-id="5a564-112">它对应于选项 **“如果订阅将在阈值内过期，则发出警告”**。</span><span class="sxs-lookup"><span data-stu-id="5a564-112">This corresponds to the option **Warn if a subscription will expire within the threshold**.</span></span> <span data-ttu-id="5a564-113">如果达到或超过指定的阈值，订阅状态将显示为 **“即将过期/已过期”** （除非需要显示更高优先级的问题）。</span><span class="sxs-lookup"><span data-stu-id="5a564-113">If the specified threshold is met or exceeded, the subscription status is displayed as **Expiring soon/Expired** (unless an issue with a higher priority needs to be displayed).</span></span>  
  
-   <span data-ttu-id="5a564-114">超出了指定的同步时间。</span><span class="sxs-lookup"><span data-stu-id="5a564-114">Exceeding the specified synchronization time.</span></span>  
  
     <span data-ttu-id="5a564-115">它对应于选项 **“如果拨号连接的合并长度超出阈值，则发出警告”** 和 **“如果 LAN 连接的合并长度超出阈值，则发出警告”**。</span><span class="sxs-lookup"><span data-stu-id="5a564-115">This corresponds to the options **Warn if a merge length for dialup connections exceeds the threshold** and **Warn if a merge length for LAN connections exceeds the threshold**.</span></span> <span data-ttu-id="5a564-116">可以设置这两个阈值，但在给定的同步过程中仅使用其中的一个。</span><span class="sxs-lookup"><span data-stu-id="5a564-116">Both of these thresholds can be set, but only one is used during a given synchronization.</span></span> <span data-ttu-id="5a564-117">合并代理将根据连接类型来应用相应的阈值。</span><span class="sxs-lookup"><span data-stu-id="5a564-117">The Merge Agent applies the appropriate threshold based on the connection type.</span></span>  
  
     <span data-ttu-id="5a564-118">如果达到或超过指定的阈值，则订阅状态将显示为 **“长时间运行的合并”** （除非需要显示更高优先级的问题）。</span><span class="sxs-lookup"><span data-stu-id="5a564-118">If the specified threshold is met or exceeded, the subscription status is displayed as **Long-running merge** (unless an issue with a higher priority needs to be displayed).</span></span>  
  
-   <span data-ttu-id="5a564-119">在给定时间内未处理完指定的行数。</span><span class="sxs-lookup"><span data-stu-id="5a564-119">Falling short of processing the specified number of rows in a given amount of time.</span></span>  
  
     <span data-ttu-id="5a564-120">它对应于选项 **“如果拨号连接每秒合并的行数小于阈值，则发出警告”** 和 **“如果 LAN 连接的合并长度超出阈值，则发出警告”**。</span><span class="sxs-lookup"><span data-stu-id="5a564-120">This corresponds to the options **Warn if rows merged per second for dialup connections is less than the threshold** and **Warn if a merge length for LAN connections exceeds the threshold**.</span></span> <span data-ttu-id="5a564-121">可以设置这两个阈值，但在给定的同步过程中仅使用其中的一个。</span><span class="sxs-lookup"><span data-stu-id="5a564-121">Both of these thresholds can be set, but only one is used during a given synchronization.</span></span> <span data-ttu-id="5a564-122">合并代理将根据连接类型来应用相应的阈值。</span><span class="sxs-lookup"><span data-stu-id="5a564-122">The Merge Agent applies the appropriate threshold based on the connection type.</span></span>  
  
     <span data-ttu-id="5a564-123">如果达到或超过指定的阈值，订阅状态将显示为 **“‘严重’状态下的性能”** （除非需要显示更高优先级的问题）。</span><span class="sxs-lookup"><span data-stu-id="5a564-123">If the specified threshold is met or exceeded, the subscription status is displayed as **Performance critical** (unless an issue with a higher priority needs to be displayed).</span></span>  
  
 <span data-ttu-id="5a564-124">启用警告时，还需要设置阈值。</span><span class="sxs-lookup"><span data-stu-id="5a564-124">When you enable a warning, you also set a threshold.</span></span> <span data-ttu-id="5a564-125">例如，如果启用警告 **“如果 LAN 连接的合并长度超出阈值，则发出警告”**，请设置合并同步允许的最大时间长度。</span><span class="sxs-lookup"><span data-stu-id="5a564-125">For example, if you enable the warning **Warn if a merge length for LAN connections exceeds the threshold**, set the maximum allowable length of time for a merge synchronization.</span></span>  
  
 <span data-ttu-id="5a564-126">除了在复制监视器中显示警告之外，达到阈值也可以触发警报。</span><span class="sxs-lookup"><span data-stu-id="5a564-126">In addition to displaying a warning in Replication Monitor, reaching a threshold can also trigger an alert.</span></span> <span data-ttu-id="5a564-127">通过单击 **“配置警报”** 并在 **“配置复制警报”** 对话框中提供信息，可以定义警报。</span><span class="sxs-lookup"><span data-stu-id="5a564-127">Alerts are defined by clicking **Configure Alerts** and providing information in the **Configure Replication Alerts** dialog box.</span></span>  
  
## <a name="options"></a><span data-ttu-id="5a564-128">选项</span><span class="sxs-lookup"><span data-stu-id="5a564-128">Options</span></span>  
 <span data-ttu-id="5a564-129">**已启用**</span><span class="sxs-lookup"><span data-stu-id="5a564-129">**Enabled**</span></span>  
 <span data-ttu-id="5a564-130">选择此项可以启用警告并指定阈值。</span><span class="sxs-lookup"><span data-stu-id="5a564-130">Select to enable a warning and specify a threshold.</span></span>  
  
 <span data-ttu-id="5a564-131">**Alert**</span><span class="sxs-lookup"><span data-stu-id="5a564-131">**Alert**</span></span>  
 <span data-ttu-id="5a564-132">选择可启用给定复制警报的警报设置。</span><span class="sxs-lookup"><span data-stu-id="5a564-132">Select to enable the alert setting for a given replication warning.</span></span>  
  
 <span data-ttu-id="5a564-133">**警告**</span><span class="sxs-lookup"><span data-stu-id="5a564-133">**Warning**</span></span>  
 <span data-ttu-id="5a564-134">与阈值关联的警告的说明。</span><span class="sxs-lookup"><span data-stu-id="5a564-134">A description of the warning associated with a threshold.</span></span>  
  
 <span data-ttu-id="5a564-135">**阈值**</span><span class="sxs-lookup"><span data-stu-id="5a564-135">**Threshold**</span></span>  
 <span data-ttu-id="5a564-136">指定阈值的值。</span><span class="sxs-lookup"><span data-stu-id="5a564-136">Specify a value for the threshold.</span></span>  
  
 <span data-ttu-id="5a564-137">**配置警报**</span><span class="sxs-lookup"><span data-stu-id="5a564-137">**Configure Alerts**</span></span>  
 <span data-ttu-id="5a564-138">从 **“警告”** 网格中选择行，再单击 **“配置警报”** 可启动 **“配置复制警报”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="5a564-138">Select a row in the **Warnings** grid, and click **Configure Alerts** to launch the **Configure Replication Alerts** dialog box.</span></span> <span data-ttu-id="5a564-139">使用该对话框，可以定义与所选阈值和警告关联的警报。</span><span class="sxs-lookup"><span data-stu-id="5a564-139">The dialog box allows you to define an alert, which is associated with the selected threshold and warning.</span></span>  
  
 <span data-ttu-id="5a564-140">**放弃更改**</span><span class="sxs-lookup"><span data-stu-id="5a564-140">**Discard Changes**</span></span>  
 <span data-ttu-id="5a564-141">单击此项可放弃对警告和阈值所做的任何更改。</span><span class="sxs-lookup"><span data-stu-id="5a564-141">Click to discard any changes to warnings and thresholds.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5a564-142">单击 **“放弃更改”** 不会影响在 **“配置复制警报”** 对话框中定义的警报。</span><span class="sxs-lookup"><span data-stu-id="5a564-142">Clicking **Discard Changes** does not affect alerts defined in the **Configure Replication Alerts** dialog box.</span></span>  
  
 <span data-ttu-id="5a564-143">**保存更改**</span><span class="sxs-lookup"><span data-stu-id="5a564-143">**Save Changes**</span></span>  
 <span data-ttu-id="5a564-144">单击此项可保存对警告和阈值所做的任何更改。</span><span class="sxs-lookup"><span data-stu-id="5a564-144">Click to save any changes to warnings and thresholds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a564-145">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5a564-145">See Also</span></span>  
 <span data-ttu-id="5a564-146">[启动复制监视器](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="5a564-146">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="5a564-147">[使用复制监视器查看信息和执行任务](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="5a564-147">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 <span data-ttu-id="5a564-148">[用复制监视器监视性能](monitor/monitor-performance-with-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="5a564-148">[Monitor Performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md) </span></span>  
 <span data-ttu-id="5a564-149">[监视复制](monitoring-replication.md) </span><span class="sxs-lookup"><span data-stu-id="5a564-149">[Monitoring Replication](monitoring-replication.md) </span></span>  
 [<span data-ttu-id="5a564-150">在复制监视器中设置阈值和警告</span><span class="sxs-lookup"><span data-stu-id="5a564-150">Set Thresholds and Warnings in Replication Monitor</span></span>](monitor/set-thresholds-and-warnings-in-replication-monitor.md)  
  
  
