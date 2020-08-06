---
title: 在复制监视器中设置阈值和警告 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- alerts [SQL Server replication]
- Merge Agent, thresholds and warnings
- Distribution Agent, thresholds and warnings
- thresholds [SQL Server replication]
- Replication Monitor, thresholds and warnings
- monitoring performance [SQL Server replication], thresholds and warnings
ms.assetid: 3a409c2c-b77e-4001-b81a-1dcd918618ec
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f34878a6398df34e55e6dd3783f2da736bee0959
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693752"
---
# <a name="set-thresholds-and-warnings-in-replication-monitor"></a><span data-ttu-id="3fea3-102">在复制监视器中设置阈值和警告</span><span class="sxs-lookup"><span data-stu-id="3fea3-102">Set Thresholds and Warnings in Replication Monitor</span></span>
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)]<span data-ttu-id="3fea3-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]复制监视器显示发布和订阅的状态信息。</span><span class="sxs-lookup"><span data-stu-id="3fea3-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Replication Monitor displays status information for publications and subscriptions.</span></span> <span data-ttu-id="3fea3-104">默认情况下，复制监视器只为未初始化的订阅显示警告，但是，您可以为其他情况启用警告。</span><span class="sxs-lookup"><span data-stu-id="3fea3-104">By default, Replication Monitor displays warnings only for uninitialized subscriptions, but you can enable warnings for other conditions.</span></span> <span data-ttu-id="3fea3-105">建议您对拓扑启用警告，以便及时获悉有关状态和性能的信息。</span><span class="sxs-lookup"><span data-stu-id="3fea3-105">It is recommended that you enable warnings for your topology, so that you are informed about status and performance in a timely manner.</span></span>  
  
 <span data-ttu-id="3fea3-106">启用警告时，需要指定阈值。</span><span class="sxs-lookup"><span data-stu-id="3fea3-106">When you enable a warning, you specify a threshold.</span></span> <span data-ttu-id="3fea3-107">达到或超过该阈值时，将显示警告（除非需要显示更高优先级的问题）。</span><span class="sxs-lookup"><span data-stu-id="3fea3-107">When that threshold is met or exceeded, a warning is displayed (unless an issue with a higher priority needs to be displayed).</span></span> <span data-ttu-id="3fea3-108">除了在复制监视器中显示警告之外，达到阈值也可以触发警报。</span><span class="sxs-lookup"><span data-stu-id="3fea3-108">In addition to displaying a warning in Replication Monitor, reaching a threshold can also trigger an alert.</span></span> <span data-ttu-id="3fea3-109">您可以为下列情况启用警告：</span><span class="sxs-lookup"><span data-stu-id="3fea3-109">You can enable warnings for the following conditions:</span></span>  
  
-   <span data-ttu-id="3fea3-110">订阅即将过期</span><span class="sxs-lookup"><span data-stu-id="3fea3-110">Imminent subscription expiration</span></span>  
  
     <span data-ttu-id="3fea3-111">这种情况适用于所有类型的复制。</span><span class="sxs-lookup"><span data-stu-id="3fea3-111">This applies to all types of replication.</span></span> <span data-ttu-id="3fea3-112">如果达到或超过指定的阈值，订阅状态会显示为 **“即将过期/已过期”**。</span><span class="sxs-lookup"><span data-stu-id="3fea3-112">If the specified threshold is met or exceeded, the subscription status is displayed as **Expiring soon/Expired**.</span></span>  
  
-   <span data-ttu-id="3fea3-113">超过指定的滞后时间（从事务在发布服务器上提交到相应的事务在订阅服务器上提交之间间隔的时间）。</span><span class="sxs-lookup"><span data-stu-id="3fea3-113">Exceeding the specified latency (the amount of time that elapses between a transaction being committed at the Publisher and the corresponding transaction being committed at the Subscriber).</span></span>  
  
     <span data-ttu-id="3fea3-114">这适用于事务复制。</span><span class="sxs-lookup"><span data-stu-id="3fea3-114">This applies to transactional replication.</span></span> <span data-ttu-id="3fea3-115">如果达到或超过指定的阈值，订阅状态便会显示为 **“‘严重’状态下的性能”**。</span><span class="sxs-lookup"><span data-stu-id="3fea3-115">If the specified threshold is met or exceeded, the subscription status is displayed as **Performance critical**.</span></span>  
  
-   <span data-ttu-id="3fea3-116">超出了指定的同步时间。</span><span class="sxs-lookup"><span data-stu-id="3fea3-116">Exceeding the specified synchronization time.</span></span>  
  
     <span data-ttu-id="3fea3-117">这适用于合并复制。</span><span class="sxs-lookup"><span data-stu-id="3fea3-117">This applies to merge replication.</span></span> <span data-ttu-id="3fea3-118">如果达到或超过指定的阈值，状态将显示为 **“长时间运行的合并”**。</span><span class="sxs-lookup"><span data-stu-id="3fea3-118">If the specified threshold is met or exceeded, the status is displayed as **Long-running merge**.</span></span> <span data-ttu-id="3fea3-119">您可以为拨号连接和局域网 (LAN) 连接指定不同的阈值。</span><span class="sxs-lookup"><span data-stu-id="3fea3-119">You can specify different thresholds for dialup and Local Area Network (LAN) connections.</span></span>  
  
-   <span data-ttu-id="3fea3-120">在给定时间内未处理完指定的行数。</span><span class="sxs-lookup"><span data-stu-id="3fea3-120">Falling short of processing the specified number of rows in a given amount of time.</span></span>  
  
     <span data-ttu-id="3fea3-121">这适用于合并复制。</span><span class="sxs-lookup"><span data-stu-id="3fea3-121">This applies to merge replication.</span></span> <span data-ttu-id="3fea3-122">如果达到或超过指定的阈值，状态将显示为 **“‘严重’状态下的性能”**。</span><span class="sxs-lookup"><span data-stu-id="3fea3-122">If the specified threshold is met or exceeded, the status is displayed as **Performance critical**.</span></span> <span data-ttu-id="3fea3-123">可以为拨号连接和 LAN 连接指定不同的阈值。</span><span class="sxs-lookup"><span data-stu-id="3fea3-123">You can specify different thresholds for dialup and LAN connections.</span></span>  
  
 <span data-ttu-id="3fea3-124">有关“‘严重’状态下的性能”和“长时间运行的合并”\*\*\*\*\*\*\*\* 警告的详细信息，请参阅[使用复制监视器监视性能](monitor-performance-with-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="3fea3-124">For more information on the warnings **Performance critical** and **Long-running merge**, see [Monitor Performance with Replication Monitor](monitor-performance-with-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="3fea3-125">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="3fea3-125">**In This Topic**</span></span>  
  
-   [<span data-ttu-id="3fea3-126">为事务发布设置阈值和警告</span><span class="sxs-lookup"><span data-stu-id="3fea3-126">Set thresholds and warnings for a transactional publication</span></span>](#Transactional)  
  
-   [<span data-ttu-id="3fea3-127">为合并发布设置阈值和警告</span><span class="sxs-lookup"><span data-stu-id="3fea3-127">Set thresholds and warnings for a merge publication</span></span>](#Merge)  
  
-   [<span data-ttu-id="3fea3-128">为快照发布设置阈值和警告</span><span class="sxs-lookup"><span data-stu-id="3fea3-128">Set thresholds and warnings for a snapshot publication</span></span>](#Snapshot)  
  
##  <a name="to-set-thresholds-and-warnings-for-a-transactional-publication"></a><a name="Transactional"></a><span data-ttu-id="3fea3-129">为事务发布设置阈值和警告</span><span class="sxs-lookup"><span data-stu-id="3fea3-129">To set thresholds and warnings for a transactional publication</span></span>  
  
1.  <span data-ttu-id="3fea3-130">在左窗格中展开发布服务器组，再展开其中的一个发布服务器，然后单击其中的一个发布。</span><span class="sxs-lookup"><span data-stu-id="3fea3-130">Expand a Publisher group in the left pane, expand a Publisher, and then click a publication.</span></span>  
  
2.  <span data-ttu-id="3fea3-131">单击 "**警告**" 选项卡。若要查看有关此选项卡上选项的详细信息，请单击菜单栏上的 "**帮助**"。</span><span class="sxs-lookup"><span data-stu-id="3fea3-131">Click the **Warnings** tab. To view more information about the options on this tab click **Help** on the menu bar.</span></span>  
  
3.  <span data-ttu-id="3fea3-132">通过选中相应的复选框来启用警告： **“如果订阅将在阈值内过期，则发出警告”** 或 **“如果滞后时间超出阈值，则发出警告”**。</span><span class="sxs-lookup"><span data-stu-id="3fea3-132">Enable a warning by selecting the appropriate check box: **Warn if a subscription will expire within the threshold** or **Warn if latency exceeds the threshold**.</span></span>  
  
4.  <span data-ttu-id="3fea3-133">在 **“阈值”** 列中，为警告设置阈值。</span><span class="sxs-lookup"><span data-stu-id="3fea3-133">Set a threshold for the warnings in the **Threshold** column.</span></span> <span data-ttu-id="3fea3-134">例如，如果在步骤 3 中选中了 **“如果滞后时间超出阈值，则发出警告”** ，就可以在 **“阈值”** 列中，选择滞后时间 **“60 秒”** 。</span><span class="sxs-lookup"><span data-stu-id="3fea3-134">For example, if you selected **Warn if latency exceeds the threshold** in step 3, you could select a latency of **60 seconds** in the **Threshold** column.</span></span>  
  
5.  <span data-ttu-id="3fea3-135">单击 **“保存更改”** 。</span><span class="sxs-lookup"><span data-stu-id="3fea3-135">Click **Save Changes**.</span></span>  
  
#### <a name="to-configure-an-alert-for-a-threshold"></a><span data-ttu-id="3fea3-136">为阈值配置警报</span><span class="sxs-lookup"><span data-stu-id="3fea3-136">To configure an alert for a threshold</span></span>  
  
1.  <span data-ttu-id="3fea3-137">单击 **“配置警报”**。</span><span class="sxs-lookup"><span data-stu-id="3fea3-137">Click **Configure Alerts**.</span></span>  
  
2.  <span data-ttu-id="3fea3-138">在 **“配置复制警报”** 对话框中，选择一个警报，然后单击 **“配置”** 。</span><span class="sxs-lookup"><span data-stu-id="3fea3-138">In the **Configure Replication Alerts** dialog box, select an alert, and then click **Configure**.</span></span>  
  
     <span data-ttu-id="3fea3-139">此对话框将显示所有发布类型的警报，包括与监视阈值无关的警报。</span><span class="sxs-lookup"><span data-stu-id="3fea3-139">This dialog box displays alerts for all publication types, including alerts that are not related to monitoring thresholds.</span></span> <span data-ttu-id="3fea3-140">有关详细信息，请参阅[对复制代理事件使用警报](../agents/use-alerts-for-replication-agent-events.md)。</span><span class="sxs-lookup"><span data-stu-id="3fea3-140">For more information, see [Use Alerts for Replication Agent Events](../agents/use-alerts-for-replication-agent-events.md).</span></span>  
  
3.  <span data-ttu-id="3fea3-141">在“\<AlertName> 警报属性”对话框中设置选项：</span><span class="sxs-lookup"><span data-stu-id="3fea3-141">Set options in the **\<AlertName> alert properties** dialog box:</span></span>  
  
    -   <span data-ttu-id="3fea3-142">在 **“常规”** 页上，单击 **“启用”** ，指定应用此警报的数据库。</span><span class="sxs-lookup"><span data-stu-id="3fea3-142">On the **General** page, click **Enable**; specify which database the alert should apply to.</span></span>  
  
    -   <span data-ttu-id="3fea3-143">在 **“响应”** 页上，指定是否应发送电子邮件和/或是否应执行作业。</span><span class="sxs-lookup"><span data-stu-id="3fea3-143">On the **Response** page, specify whether an e-mail should be sent and/or a job should be executed.</span></span>  
  
    -   <span data-ttu-id="3fea3-144">在 **“选项”** 页上，自定义响应文本。</span><span class="sxs-lookup"><span data-stu-id="3fea3-144">On the **Options** page, customize the text of the response.</span></span>  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  <span data-ttu-id="3fea3-145">单击“关闭”。</span><span class="sxs-lookup"><span data-stu-id="3fea3-145">Click **Close**.</span></span>  
  
##  <a name="set-thresholds-and-warnings-for-a-merge-publication"></a><a name="Merge"></a><span data-ttu-id="3fea3-146">为合并发布设置阈值和警告</span><span class="sxs-lookup"><span data-stu-id="3fea3-146">Set thresholds and warnings for a merge publication</span></span>  
  
1.  <span data-ttu-id="3fea3-147">在左窗格中展开发布服务器组，再展开其中的一个发布服务器，然后单击其中的一个发布。</span><span class="sxs-lookup"><span data-stu-id="3fea3-147">Expand a Publisher group in the left pane, expand a Publisher, and then click a publication.</span></span>  
  
2.  <span data-ttu-id="3fea3-148">单击 "**警告**" 选项卡。若要查看有关此选项卡上选项的详细信息，请单击菜单栏上的 "**帮助**"。</span><span class="sxs-lookup"><span data-stu-id="3fea3-148">Click the **Warnings** tab. To view more information about the options on this tab, click **Help** on the menu bar.</span></span>  
  
3.  <span data-ttu-id="3fea3-149">通过选中相应的复选框来启用警告：</span><span class="sxs-lookup"><span data-stu-id="3fea3-149">Enable a warning by selecting the appropriate check box:</span></span>  
  
    -   <span data-ttu-id="3fea3-150">**“如果订阅将在阈值内过期，则发出警告”**</span><span class="sxs-lookup"><span data-stu-id="3fea3-150">**Warn if a subscription will expire within the threshold**</span></span>  
  
    -   <span data-ttu-id="3fea3-151">**如果拨号连接的合并长度超出阈值，则发出警告**</span><span class="sxs-lookup"><span data-stu-id="3fea3-151">**Warn if a merge length for dialup connections exceeds the threshold**</span></span>  
  
    -   <span data-ttu-id="3fea3-152">**如果 LAN 连接的合并长度超出阈值，则发出警告**</span><span class="sxs-lookup"><span data-stu-id="3fea3-152">**Warn if a merge length for LAN connections exceeds the threshold**</span></span>  
  
    -   <span data-ttu-id="3fea3-153">**如果 LAN 连接每秒合并的行数小于阈值，则发出警告**</span><span class="sxs-lookup"><span data-stu-id="3fea3-153">**Warn if rows merged per second for LAN connections is less than the threshold**</span></span>  
  
    -   <span data-ttu-id="3fea3-154">**如果拨号连接每秒合并的行数小于阈值，则发出警告**</span><span class="sxs-lookup"><span data-stu-id="3fea3-154">**Warn if rows merged per second for dialup connections is less than the threshold**</span></span>  
  
4.  <span data-ttu-id="3fea3-155">在 **“阈值”** 列中设置警告阈值。</span><span class="sxs-lookup"><span data-stu-id="3fea3-155">Set thresholds for the warnings in the **Threshold** column.</span></span> <span data-ttu-id="3fea3-156">例如，如果在步骤 3 中选择了 **“如果拨号连接的合并长度超出阈值，则发出警告”** ，则可以在 **“阈值”** 列中选择时间 **“10 分钟”** 。</span><span class="sxs-lookup"><span data-stu-id="3fea3-156">For example, if you selected **Warn if a merge length for dialup connections exceeds the threshold** in step 3, you could select a time of **10 minutes** in the **Threshold** column.</span></span>  
  
5.  <span data-ttu-id="3fea3-157">单击 **“保存更改”** 。</span><span class="sxs-lookup"><span data-stu-id="3fea3-157">Click **Save Changes**.</span></span>  
  
#### <a name="to-configure-an-alert-for-a-threshold"></a><span data-ttu-id="3fea3-158">为阈值配置警报</span><span class="sxs-lookup"><span data-stu-id="3fea3-158">To configure an alert for a threshold</span></span>  
  
1.  <span data-ttu-id="3fea3-159">单击 **“配置警报”**。</span><span class="sxs-lookup"><span data-stu-id="3fea3-159">Click **Configure Alerts**.</span></span>  
  
2.  <span data-ttu-id="3fea3-160">在 **“配置复制警报”** 对话框中，选择一个警报，然后单击 **“配置”** 。</span><span class="sxs-lookup"><span data-stu-id="3fea3-160">In the **Configure Replication Alerts** dialog box, select an alert, and then click **Configure**.</span></span>  
  
     <span data-ttu-id="3fea3-161">此对话框将显示所有发布类型的警报，包括与监视阈值无关的警报。</span><span class="sxs-lookup"><span data-stu-id="3fea3-161">This dialog box displays alerts for all publication types, including alerts that are not related to monitoring thresholds.</span></span>  
  
3.  <span data-ttu-id="3fea3-162">在“\<AlertName> 警报属性”对话框中设置选项：</span><span class="sxs-lookup"><span data-stu-id="3fea3-162">Set options in the **\<AlertName> alert properties** dialog box:</span></span>  
  
    -   <span data-ttu-id="3fea3-163">在 **“常规”** 页上，单击 **“启用”** ，指定应用此警报的数据库。</span><span class="sxs-lookup"><span data-stu-id="3fea3-163">On the **General** page, click **Enable**; specify which database the alert should apply to.</span></span>  
  
    -   <span data-ttu-id="3fea3-164">在 **“响应”** 页上，指定是否应发送电子邮件和/或是否应执行作业。</span><span class="sxs-lookup"><span data-stu-id="3fea3-164">On the **Response** page, specify whether an e-mail should be sent and/or a job should be executed.</span></span>  
  
    -   <span data-ttu-id="3fea3-165">在 **“选项”** 页上，自定义响应文本。</span><span class="sxs-lookup"><span data-stu-id="3fea3-165">On the **Options** page, customize the text of the response.</span></span>  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  <span data-ttu-id="3fea3-166">单击“关闭”。</span><span class="sxs-lookup"><span data-stu-id="3fea3-166">Click **Close**.</span></span>  
  
##  <a name="set-thresholds-and-warnings-for-a-snapshot-publication"></a><a name="Snapshot"></a> <span data-ttu-id="3fea3-167">为快照发布设置阈值和警告</span><span class="sxs-lookup"><span data-stu-id="3fea3-167">Set thresholds and warnings for a snapshot publication</span></span>  
  
1.  <span data-ttu-id="3fea3-168">在左窗格中展开发布服务器组，再展开其中的一个发布服务器，然后单击其中的一个发布。</span><span class="sxs-lookup"><span data-stu-id="3fea3-168">Expand a Publisher group in the left pane, expand a Publisher, and then click a publication.</span></span>  
  
2.  <span data-ttu-id="3fea3-169">单击 "**警告**" 选项卡。若要查看有关此选项卡上选项的详细信息，请单击顶部菜单中的 "**帮助**"。</span><span class="sxs-lookup"><span data-stu-id="3fea3-169">Click the **Warnings** tab. To view more information about the options on this tab click **Help** on the top menu.</span></span>  
  
3.  <span data-ttu-id="3fea3-170">通过选中 **“如果订阅将在阈值内过期，则发出警告”** 复选框来启用警告。</span><span class="sxs-lookup"><span data-stu-id="3fea3-170">Enable a warning by selecting the check box **Warn if a subscription will expire within the threshold**.</span></span>  
  
4.  <span data-ttu-id="3fea3-171">在 **“阈值”** 列中，为警告设置阈值。</span><span class="sxs-lookup"><span data-stu-id="3fea3-171">Set a threshold for the warning in the **Threshold** column.</span></span> <span data-ttu-id="3fea3-172">例如，可以在 **“阈值”** 列中选择值 **70%** 。</span><span class="sxs-lookup"><span data-stu-id="3fea3-172">For example, you could select a value of **70%** in the **Threshold** column.</span></span>  
  
5.  <span data-ttu-id="3fea3-173">单击 **“保存更改”** 。</span><span class="sxs-lookup"><span data-stu-id="3fea3-173">Click **Save Changes**.</span></span>  
  
#### <a name="to-configure-an-alert-for-a-threshold"></a><span data-ttu-id="3fea3-174">为阈值配置警报</span><span class="sxs-lookup"><span data-stu-id="3fea3-174">To configure an alert for a threshold</span></span>  
  
1.  <span data-ttu-id="3fea3-175">单击 **“配置警报”**。</span><span class="sxs-lookup"><span data-stu-id="3fea3-175">Click **Configure Alerts**.</span></span>  
  
2.  <span data-ttu-id="3fea3-176">在 **“配置复制警报”** 对话框中，选择一个警报，然后单击 **“配置”** 。</span><span class="sxs-lookup"><span data-stu-id="3fea3-176">In the **Configure Replication Alerts** dialog box, select an alert, and then click **Configure**.</span></span>  
  
     <span data-ttu-id="3fea3-177">此对话框将显示所有发布类型的警报，包括与监视阈值无关的警报。</span><span class="sxs-lookup"><span data-stu-id="3fea3-177">This dialog box displays alerts for all publication types, including alerts that are not related to monitoring thresholds.</span></span> <span data-ttu-id="3fea3-178">有关详细信息，请参阅[对复制代理事件使用警报](../agents/use-alerts-for-replication-agent-events.md)。</span><span class="sxs-lookup"><span data-stu-id="3fea3-178">For more information, see [Use Alerts for Replication Agent Events](../agents/use-alerts-for-replication-agent-events.md).</span></span>  
  
3.  <span data-ttu-id="3fea3-179">在“\<AlertName> 警报属性”对话框中设置选项：</span><span class="sxs-lookup"><span data-stu-id="3fea3-179">Set options in the **\<AlertName> alert properties** dialog box:</span></span>  
  
    -   <span data-ttu-id="3fea3-180">在 **“常规”** 页上，单击 **“启用”** ，指定应用此警报的数据库。</span><span class="sxs-lookup"><span data-stu-id="3fea3-180">On the **General** page, click **Enable**; specify which database the alert should apply to.</span></span>  
  
    -   <span data-ttu-id="3fea3-181">在 **“响应”** 页上，指定是否应发送电子邮件和/或是否应执行作业。</span><span class="sxs-lookup"><span data-stu-id="3fea3-181">On the **Response** page, specify whether an e-mail should be sent and/or a job should be executed.</span></span>  
  
    -   <span data-ttu-id="3fea3-182">在 **“选项”** 页上，自定义响应文本。</span><span class="sxs-lookup"><span data-stu-id="3fea3-182">On the **Options** page, customize the text of the response.</span></span>  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  <span data-ttu-id="3fea3-183">单击“关闭”。</span><span class="sxs-lookup"><span data-stu-id="3fea3-183">Click **Close**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fea3-184">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3fea3-184">See Also</span></span>  
 [<span data-ttu-id="3fea3-185">监视复制</span><span class="sxs-lookup"><span data-stu-id="3fea3-185">Monitoring Replication</span></span>](../monitoring-replication.md)  
  
  
