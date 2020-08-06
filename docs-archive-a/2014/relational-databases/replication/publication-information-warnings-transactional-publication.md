---
title: 发布信息，警告 (事务发布，SQL Server 2005 及更高版本) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publicationinfo.warningsandagents.tran.f1
ms.assetid: 4d4baf1d-d0a1-4d09-bec7-137811f43f09
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: cac7ab0f712fe69d3736985921d70b0ce200d474
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690509"
---
# <a name="publication-information-warnings-transactional-publication-sql-server-2005-and-later"></a><span data-ttu-id="1573e-102">发布信息，警告（事务发布，SQL Server 2005 及更高版本）</span><span class="sxs-lookup"><span data-stu-id="1573e-102">Publication Information, Warnings (Transactional Publication, SQL Server 2005 and Later)</span></span>
  <span data-ttu-id="1573e-103">**“警告”** 选项卡适用于运行 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 和更高版本的分发服务器。</span><span class="sxs-lookup"><span data-stu-id="1573e-103">The **Warnings** tab is available for Distributors that are running [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions.</span></span> <span data-ttu-id="1573e-104">使用 **“警告”** 选项卡可以为所选发布执行下列任务：</span><span class="sxs-lookup"><span data-stu-id="1573e-104">The **Warnings** tab allows you to perform the following tasks for the selected publication:</span></span>  
  
-   <span data-ttu-id="1573e-105">在复制监视器中显示警告。</span><span class="sxs-lookup"><span data-stu-id="1573e-105">Enable warnings to be displayed in Replication Monitor.</span></span>  
  
-   <span data-ttu-id="1573e-106">指定与警告关联的阈值。</span><span class="sxs-lookup"><span data-stu-id="1573e-106">Specify thresholds associated with warnings.</span></span>  
  
-   <span data-ttu-id="1573e-107">定义与警告关联的警报。</span><span class="sxs-lookup"><span data-stu-id="1573e-107">Define alerts associated with warnings.</span></span>  
  
## <a name="warnings-thresholds-and-alerts"></a><span data-ttu-id="1573e-108">警告、阈值和警报</span><span class="sxs-lookup"><span data-stu-id="1573e-108">Warnings, Thresholds, and Alerts</span></span>  
 <span data-ttu-id="1573e-109">默认情况下，复制监视器会为未初始化的订阅显示警告：在包含订阅信息的页的 **“状态”** 列中，显示 **“未初始化的订阅”** 状态作为警告。</span><span class="sxs-lookup"><span data-stu-id="1573e-109">By default, Replication Monitor displays warnings for uninitialized subscriptions: a status of **Uninitialized subscription** is displayed as a warning in the **Status** column of pages that include subscription information.</span></span> <span data-ttu-id="1573e-110">对于事务发布，您可以指定下列这些附加条件是否会导致警告：</span><span class="sxs-lookup"><span data-stu-id="1573e-110">For transactional publications, you can specify whether these additional conditions result in warnings:</span></span>  
  
-   <span data-ttu-id="1573e-111">订阅即将过期。</span><span class="sxs-lookup"><span data-stu-id="1573e-111">Imminent subscription expiration.</span></span>  
  
     <span data-ttu-id="1573e-112">它对应于选项 **“如果订阅将在阈值内过期，则发出警告”**。</span><span class="sxs-lookup"><span data-stu-id="1573e-112">This corresponds to the option **Warn if a subscription will expire within the threshold**.</span></span> <span data-ttu-id="1573e-113">如果达到或超过指定的阈值，订阅状态将显示为 **“即将过期/已过期”** （除非需要显示更高优先级的问题）。</span><span class="sxs-lookup"><span data-stu-id="1573e-113">If the specified threshold is met or exceeded, the subscription status is displayed as **Expiring soon/Expired** (unless an issue with a higher priority needs to be displayed).</span></span>  
  
-   <span data-ttu-id="1573e-114">超出指定的滞后时间。</span><span class="sxs-lookup"><span data-stu-id="1573e-114">Exceeding the specified latency.</span></span> <span data-ttu-id="1573e-115">这是从在发布服务器提交事务到在订阅服务器提交对应的事务所经过的时间。</span><span class="sxs-lookup"><span data-stu-id="1573e-115">This is the amount of time that elapses between a transaction being committed at the Publisher and the corresponding transaction being committed at the Subscriber.</span></span>  
  
     <span data-ttu-id="1573e-116">它对应于选项 **“如果滞后时间超出阈值，则发出警告”**。</span><span class="sxs-lookup"><span data-stu-id="1573e-116">This corresponds to the option **Warn if latency exceeds the threshold**.</span></span> <span data-ttu-id="1573e-117">如果达到或超过指定的阈值，订阅状态将显示为 **“‘严重’状态下的性能”** （除非需要显示更高优先级的问题）。</span><span class="sxs-lookup"><span data-stu-id="1573e-117">If the specified threshold is met or exceeded, the subscription status is displayed as **Performance critical** (unless an issue with a higher priority needs to be displayed).</span></span> <span data-ttu-id="1573e-118">该阈值还可用于确定性能等级，等级信息显示在包含订阅信息的页上的 **“性能”** 列中。</span><span class="sxs-lookup"><span data-stu-id="1573e-118">The threshold is also used to provide a performance rating, which is displayed in the **Performance** column of pages that include subscription information.</span></span> <span data-ttu-id="1573e-119">性能等级可以为以下值之一：</span><span class="sxs-lookup"><span data-stu-id="1573e-119">The performance rating is one of the following values:</span></span>  
  
    -   <span data-ttu-id="1573e-120">优秀</span><span class="sxs-lookup"><span data-stu-id="1573e-120">Excellent</span></span>  
  
    -   <span data-ttu-id="1573e-121">好</span><span class="sxs-lookup"><span data-stu-id="1573e-121">Good</span></span>  
  
    -   <span data-ttu-id="1573e-122">一般</span><span class="sxs-lookup"><span data-stu-id="1573e-122">Fair</span></span>  
  
    -   <span data-ttu-id="1573e-123">差</span><span class="sxs-lookup"><span data-stu-id="1573e-123">Poor</span></span>  
  
    -   <span data-ttu-id="1573e-124">严重</span><span class="sxs-lookup"><span data-stu-id="1573e-124">Critical</span></span>  
  
 <span data-ttu-id="1573e-125">启用警告时，还需要设置阈值。</span><span class="sxs-lookup"><span data-stu-id="1573e-125">When you enable a warning, you also set a threshold.</span></span> <span data-ttu-id="1573e-126">例如，如果启用警告 **“如果滞后时间超出阈值，则发出警告”**，请选择在发布服务器上提交事务与在订阅服务器上提交事务之间允许的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="1573e-126">For example, if you enable the warning **Warn if latency exceeds the threshold**, select the amount of time allowable between a transaction being committed at the Publisher and the transaction being committed at the Subscriber.</span></span>  
  
 <span data-ttu-id="1573e-127">除了在复制监视器中显示警告之外，达到阈值也可以触发警报。</span><span class="sxs-lookup"><span data-stu-id="1573e-127">In addition to displaying a warning in Replication Monitor, reaching a threshold can also trigger an alert.</span></span> <span data-ttu-id="1573e-128">通过单击 **“配置警报”** 并在 **“配置复制警报”** 对话框中提供信息，可以定义警报。</span><span class="sxs-lookup"><span data-stu-id="1573e-128">Alerts are defined by clicking **Configure Alerts** and providing information in the **Configure Replication Alerts** dialog box.</span></span>  
  
## <a name="options"></a><span data-ttu-id="1573e-129">选项</span><span class="sxs-lookup"><span data-stu-id="1573e-129">Options</span></span>  
 <span data-ttu-id="1573e-130">**已启用**</span><span class="sxs-lookup"><span data-stu-id="1573e-130">**Enabled**</span></span>  
 <span data-ttu-id="1573e-131">选择此项可以启用警告并指定阈值。</span><span class="sxs-lookup"><span data-stu-id="1573e-131">Select to enable a warning and specify a threshold.</span></span>  
  
 <span data-ttu-id="1573e-132">**警告**</span><span class="sxs-lookup"><span data-stu-id="1573e-132">**Warning**</span></span>  
 <span data-ttu-id="1573e-133">与阈值关联的警告的说明。</span><span class="sxs-lookup"><span data-stu-id="1573e-133">A description of the warning associated with a threshold.</span></span>  
  
 <span data-ttu-id="1573e-134">**阈值**</span><span class="sxs-lookup"><span data-stu-id="1573e-134">**Threshold**</span></span>  
 <span data-ttu-id="1573e-135">指定阈值的值。</span><span class="sxs-lookup"><span data-stu-id="1573e-135">Specify a value for the threshold.</span></span>  
  
 <span data-ttu-id="1573e-136">**配置警报**</span><span class="sxs-lookup"><span data-stu-id="1573e-136">**Configure Alerts**</span></span>  
 <span data-ttu-id="1573e-137">从 **“警告”** 网格中选择行，再单击 **“配置警报”** 可启动 **“配置复制警报”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="1573e-137">Select a row in the **Warnings** grid, and click **Configure Alerts** to launch the **Configure Replication Alerts** dialog box.</span></span> <span data-ttu-id="1573e-138">使用该对话框，可以定义与所选阈值和警告关联的警报。</span><span class="sxs-lookup"><span data-stu-id="1573e-138">The dialog box allows you to define an alert, which is associated with the selected threshold and warning.</span></span>  
  
 <span data-ttu-id="1573e-139">**放弃更改**</span><span class="sxs-lookup"><span data-stu-id="1573e-139">**Discard Changes**</span></span>  
 <span data-ttu-id="1573e-140">单击此项可放弃对警告和阈值所做的任何更改。</span><span class="sxs-lookup"><span data-stu-id="1573e-140">Click to discard any changes to warnings and thresholds.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1573e-141">单击 **“放弃更改”** 不会影响在 **“配置复制警报”** 对话框中定义的警报。</span><span class="sxs-lookup"><span data-stu-id="1573e-141">Clicking **Discard Changes** does not affect alerts defined in the **Configure Replication Alerts** dialog box.</span></span>  
  
 <span data-ttu-id="1573e-142">**保存更改**</span><span class="sxs-lookup"><span data-stu-id="1573e-142">**Save Changes**</span></span>  
 <span data-ttu-id="1573e-143">单击此项可保存对警告和阈值所做的任何更改。</span><span class="sxs-lookup"><span data-stu-id="1573e-143">Click to save any changes to warnings and thresholds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1573e-144">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1573e-144">See Also</span></span>  
 <span data-ttu-id="1573e-145">[启动复制监视器](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="1573e-145">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="1573e-146">[使用复制监视器查看信息和执行任务](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="1573e-146">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 <span data-ttu-id="1573e-147">[用复制监视器监视性能](monitor/monitor-performance-with-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="1573e-147">[Monitor Performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md) </span></span>  
 <span data-ttu-id="1573e-148">[监视复制](monitoring-replication.md) </span><span class="sxs-lookup"><span data-stu-id="1573e-148">[Monitoring Replication](monitoring-replication.md) </span></span>  
 [<span data-ttu-id="1573e-149">在复制监视器中设置阈值和警告</span><span class="sxs-lookup"><span data-stu-id="1573e-149">Set Thresholds and Warnings in Replication Monitor</span></span>](monitor/set-thresholds-and-warnings-in-replication-monitor.md)  
  
  
