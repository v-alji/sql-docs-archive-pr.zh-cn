---
title: 订阅，同步历史记录 (合并订阅，SQL Server 2005 及更高版本) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.subscription.synchhistory.f1
- sql12.rep.monitor.subscription.downlevelsynchhistory.f1
ms.assetid: 85f666f6-14ee-4f19-b385-e5cc508aabe4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 49fe19f22976116813ac2454b2d08fc1fe47d8de
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589512"
---
# <a name="subscription-synchronization-history-merge-subscription-sql-server-2005-and-later"></a><span data-ttu-id="29458-102">订阅，同步历史记录（合并订阅，SQL Server 2005 和更高版本）</span><span class="sxs-lookup"><span data-stu-id="29458-102">Subscription, Synchronization History (Merge Subscription, SQL Server 2005 and Later)</span></span>
  <span data-ttu-id="29458-103">**“同步历史记录”** 选项卡显示有关合并代理的详细信息，包括状态、项目统计信息、历史记录、信息性消息和所有错误信息。</span><span class="sxs-lookup"><span data-stu-id="29458-103">The **Synchronization History** tab displays detailed information on the Merge Agent, including status, article statistics, history, informational messages, and any error messages.</span></span>  
  
## <a name="options"></a><span data-ttu-id="29458-104">选项</span><span class="sxs-lookup"><span data-stu-id="29458-104">Options</span></span>  
 <span data-ttu-id="29458-105">从 **“视图”** 菜单中选择要查看的合并代理会话，然后在标记为 **“合并代理的会话”** 的网格中选择特定的会话。</span><span class="sxs-lookup"><span data-stu-id="29458-105">Select which Merge Agent sessions to view from the **View** menu, and then select a specific session in the grid labeled **Sessions of the Merge Agent**.</span></span> <span data-ttu-id="29458-106">有关此会话的详细信息显示在标记为 **“所选会话中已处理的项目”** 的网格中。</span><span class="sxs-lookup"><span data-stu-id="29458-106">Detailed information on this session is displayed in the grid labeled **Articles processed in the selected session**.</span></span>  
  
 <span data-ttu-id="29458-107">**视图**</span><span class="sxs-lookup"><span data-stu-id="29458-107">**View**</span></span>  
 <span data-ttu-id="29458-108">选择要查看的合并代理会话。</span><span class="sxs-lookup"><span data-stu-id="29458-108">Select which Merge Agent sessions to view.</span></span>  
  
 <span data-ttu-id="29458-109">**Status**</span><span class="sxs-lookup"><span data-stu-id="29458-109">**Status**</span></span>  
 <span data-ttu-id="29458-110">会话结束时合并代理的状态。</span><span class="sxs-lookup"><span data-stu-id="29458-110">The status of the Merge Agent at the end of the session.</span></span> <span data-ttu-id="29458-111">下面列出了可能的状态值：</span><span class="sxs-lookup"><span data-stu-id="29458-111">The following list shows the possible status values:</span></span>  
  
-   <span data-ttu-id="29458-112">错误</span><span class="sxs-lookup"><span data-stu-id="29458-112">Error</span></span>  
  
-   <span data-ttu-id="29458-113">已完成</span><span class="sxs-lookup"><span data-stu-id="29458-113">Completed</span></span>  
  
-   <span data-ttu-id="29458-114">正在重试</span><span class="sxs-lookup"><span data-stu-id="29458-114">Retrying</span></span>  
  
-   <span data-ttu-id="29458-115">正在运行</span><span class="sxs-lookup"><span data-stu-id="29458-115">Running</span></span>  
  
 <span data-ttu-id="29458-116">**Start Time**</span><span class="sxs-lookup"><span data-stu-id="29458-116">**Start Time**</span></span>  
 <span data-ttu-id="29458-117">会话的开始时间。</span><span class="sxs-lookup"><span data-stu-id="29458-117">The start time of the session.</span></span>  
  
 <span data-ttu-id="29458-118">**结束时间**</span><span class="sxs-lookup"><span data-stu-id="29458-118">**End Time**</span></span>  
 <span data-ttu-id="29458-119">会话的结束时间。</span><span class="sxs-lookup"><span data-stu-id="29458-119">The end time of the session.</span></span> <span data-ttu-id="29458-120">如果代理尚未停止，此字段为空。</span><span class="sxs-lookup"><span data-stu-id="29458-120">If the agent has not stopped, this field is empty.</span></span>  
  
 <span data-ttu-id="29458-121">**Duration**</span><span class="sxs-lookup"><span data-stu-id="29458-121">**Duration**</span></span>  
 <span data-ttu-id="29458-122">合并代理已在会话中运行的时间。</span><span class="sxs-lookup"><span data-stu-id="29458-122">The amount of time the Merge Agent has run in a session.</span></span> <span data-ttu-id="29458-123">如果代理当前正在运行，该时间表示已用时间；如果代理已在之前运行完毕，则该时间表示总时间。</span><span class="sxs-lookup"><span data-stu-id="29458-123">The time represents elapsed time if the agent is currently running and total time if the agent has run previously.</span></span>  
  
 <span data-ttu-id="29458-124">**已上载的命令**</span><span class="sxs-lookup"><span data-stu-id="29458-124">**Uploaded Commands**</span></span>  
 <span data-ttu-id="29458-125">合并代理会话过程中上载的行数。</span><span class="sxs-lookup"><span data-stu-id="29458-125">The number of rows uploaded during the Merge Agent session.</span></span>  
  
 <span data-ttu-id="29458-126">**已下载的命令**</span><span class="sxs-lookup"><span data-stu-id="29458-126">**Downloaded Commands**</span></span>  
 <span data-ttu-id="29458-127">合并代理会话过程中下载的行数。</span><span class="sxs-lookup"><span data-stu-id="29458-127">The number of rows downloaded during the Merge Agent session.</span></span>  
  
 <span data-ttu-id="29458-128">**错误消息**</span><span class="sxs-lookup"><span data-stu-id="29458-128">**Error Message**</span></span>  
 <span data-ttu-id="29458-129">如果某会话由于出错而结束，此字段将会显示合并代理记录的上一条错误消息。</span><span class="sxs-lookup"><span data-stu-id="29458-129">If a session ended in an error, this field displays the last error message logged by the Merge Agent.</span></span> <span data-ttu-id="29458-130">如果某会话未因出错而结束，此字段为空白。</span><span class="sxs-lookup"><span data-stu-id="29458-130">If a session did not end in an error, this field is blank.</span></span>  
  
 <span data-ttu-id="29458-131">**文章**</span><span class="sxs-lookup"><span data-stu-id="29458-131">**Article**</span></span>  
 <span data-ttu-id="29458-132">发布中各个项目的名称以及在整个发布中所处的处理阶段：</span><span class="sxs-lookup"><span data-stu-id="29458-132">The name of each article in the publication, and the following processing phases for the entire publication:</span></span>  
  
-   <span data-ttu-id="29458-133">**初始化**。</span><span class="sxs-lookup"><span data-stu-id="29458-133">**Initialization**.</span></span> <span data-ttu-id="29458-134">这是指启动合并代理；其过程不同于初始化订阅，后者涉及应用快照。</span><span class="sxs-lookup"><span data-stu-id="29458-134">This refers to starting the Merge Agent; this is not synonymous with initializing a subscription, which involves applying a snapshot.</span></span>  
  
-   <span data-ttu-id="29458-135">**架构更改和大容量插入**。</span><span class="sxs-lookup"><span data-stu-id="29458-135">**Schema changes and bulk inserts**.</span></span>  
  
-   <span data-ttu-id="29458-136">**上载对发布服务器的更改**。</span><span class="sxs-lookup"><span data-stu-id="29458-136">**Upload changes to Publisher**.</span></span>  
  
-   <span data-ttu-id="29458-137">**下载对订阅服务器的更改**。</span><span class="sxs-lookup"><span data-stu-id="29458-137">**Download changes to Subscriber**.</span></span>  
  
 <span data-ttu-id="29458-138">包含这些阶段后，网格就可以显示各个阶段在所选会话中所占用的时间以及占总时间的百分比。</span><span class="sxs-lookup"><span data-stu-id="29458-138">The phases are included so that the grid can display the amount of time and percentage of total time that each phase accounts for in the selected session.</span></span>  
  
 <span data-ttu-id="29458-139">**占总时间的百分比**</span><span class="sxs-lookup"><span data-stu-id="29458-139">**% of total**</span></span>  
 <span data-ttu-id="29458-140">在所选的会话中每个阶段占总处理时间的百分比。</span><span class="sxs-lookup"><span data-stu-id="29458-140">The percentage of total processing time that each phase accounts for in the selected session.</span></span>  
  
 <span data-ttu-id="29458-141">**Duration**</span><span class="sxs-lookup"><span data-stu-id="29458-141">**Duration**</span></span>  
 <span data-ttu-id="29458-142">每个处理阶段所用的时间。</span><span class="sxs-lookup"><span data-stu-id="29458-142">The amount of time spent in each processing phase.</span></span> <span data-ttu-id="29458-143">如果合并代理当前正在为会话运行，该时间表示已用时间；如果合并代理之前已经运行完毕，该时间则表示运行所用的总时间。</span><span class="sxs-lookup"><span data-stu-id="29458-143">The time represents elapsed time if the Merge Agent is currently running for the session and total time if the Merge Agent has run previously.</span></span>  
  
 <span data-ttu-id="29458-144">**Inserts**</span><span class="sxs-lookup"><span data-stu-id="29458-144">**Inserts**</span></span>  
 <span data-ttu-id="29458-145">在所选会话的此阶段中插入的行数。</span><span class="sxs-lookup"><span data-stu-id="29458-145">The number of rows inserted in this phase of the selected session.</span></span>  
  
 <span data-ttu-id="29458-146">**更新**</span><span class="sxs-lookup"><span data-stu-id="29458-146">**Updates**</span></span>  
 <span data-ttu-id="29458-147">在所选会话的此阶段中更新的行数。</span><span class="sxs-lookup"><span data-stu-id="29458-147">The number of rows updated in this phase of the selected session.</span></span>  
  
 <span data-ttu-id="29458-148">**Deletes**</span><span class="sxs-lookup"><span data-stu-id="29458-148">**Deletes**</span></span>  
 <span data-ttu-id="29458-149">在所选会话的此阶段中删除的行数。</span><span class="sxs-lookup"><span data-stu-id="29458-149">The number of rows deleted in this phase of the selected session.</span></span>  
  
 <span data-ttu-id="29458-150">**冲突**</span><span class="sxs-lookup"><span data-stu-id="29458-150">**Conflicts**</span></span>  
 <span data-ttu-id="29458-151">所选会话中的冲突数。</span><span class="sxs-lookup"><span data-stu-id="29458-151">The number of conflicts in the selected session.</span></span>  
  
 <span data-ttu-id="29458-152">**架构更改**</span><span class="sxs-lookup"><span data-stu-id="29458-152">**Schema Changes**</span></span>  
 <span data-ttu-id="29458-153">所选会话中的架构更改数。</span><span class="sxs-lookup"><span data-stu-id="29458-153">The number of schema changes in the selected session.</span></span> <span data-ttu-id="29458-154">架构更改可能由于以下原因而发生：从发布数据库中复制架构更改；添加或删除项目；更改项目或发布属性。</span><span class="sxs-lookup"><span data-stu-id="29458-154">Schema changes can result from: schema changes being replicated from the publication database; adding or dropping articles; and changes to article or publication properties.</span></span>  
  
 <span data-ttu-id="29458-155">**所选会话的上一条消息**</span><span class="sxs-lookup"><span data-stu-id="29458-155">**Last message of the selected session**</span></span>  
 <span data-ttu-id="29458-156">此文本区显示所选会话中的最后消息。</span><span class="sxs-lookup"><span data-stu-id="29458-156">This text area displays the last message in the selected session.</span></span> <span data-ttu-id="29458-157">如果发生错误，该区域会显示详细的错误信息以及出错时所尝试的命令。</span><span class="sxs-lookup"><span data-stu-id="29458-157">If an error has occurred, it displays detailed error information and the command that was attempted at the time of the error.</span></span> <span data-ttu-id="29458-158">另外，还包括指向与该错误相关的其他内容的链接。</span><span class="sxs-lookup"><span data-stu-id="29458-158">It also includes links to additional content related to the error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29458-159">另请参阅</span><span class="sxs-lookup"><span data-stu-id="29458-159">See Also</span></span>  
 <span data-ttu-id="29458-160">[启动复制监视器](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="29458-160">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="29458-161">[使用复制监视器查看信息和执行任务](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="29458-161">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 <span data-ttu-id="29458-162">[监视复制](monitoring-replication.md) </span><span class="sxs-lookup"><span data-stu-id="29458-162">[Monitoring Replication](monitoring-replication.md) </span></span>  
 [<span data-ttu-id="29458-163">复制代理概述</span><span class="sxs-lookup"><span data-stu-id="29458-163">Replication Agents Overview</span></span>](agents/replication-agents-overview.md)  
  
  
