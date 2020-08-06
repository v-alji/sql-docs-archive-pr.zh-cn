---
title: 订阅，分发服务器到订阅服务器的历史记录（快照订阅）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.subscription.pubtodist.snapshot.f1
ms.assetid: d3575964-f287-4bcf-8d2e-f81a33141b25
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: fe894e23e7ad7fef9c328334740eff73164130a6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693236"
---
# <a name="subscription-distributor-to-subscriber-history-snapshot-subscription"></a><span data-ttu-id="3e118-102">订阅，分发服务器到订阅服务器的历史记录（快照订阅）</span><span class="sxs-lookup"><span data-stu-id="3e118-102">Subscription, Distributor to Subscriber History (Snapshot Subscription)</span></span>
  <span data-ttu-id="3e118-103">**“分发服务器到订阅服务器的历史记录”** 选项卡显示有关分发代理的详细信息，包括状态、历史记录、信息性消息和所有错误消息。</span><span class="sxs-lookup"><span data-stu-id="3e118-103">The **Distributor to Subscriber History** tab displays detailed information on the Distribution Agent, including status, history, informational messages, and any error messages.</span></span>  
  
## <a name="options"></a><span data-ttu-id="3e118-104">选项</span><span class="sxs-lookup"><span data-stu-id="3e118-104">Options</span></span>  
 <span data-ttu-id="3e118-105">从 **“视图”** 菜单中选择要查看哪些分发代理会话，然后在标记为 **“分发代理的会话”** 的网格中选择特定的会话。</span><span class="sxs-lookup"><span data-stu-id="3e118-105">Select which Distribution Agent sessions to view from the **View** menu, and then select a specific session in the grid labeled **Sessions of the Distribution Agent**.</span></span> <span data-ttu-id="3e118-106">有关此会话的详细信息显示在标记为 **“所选会话中的操作”** 的网格中。</span><span class="sxs-lookup"><span data-stu-id="3e118-106">Detailed information on this session is displayed in the grid labeled **Actions in the selected session**.</span></span> <span data-ttu-id="3e118-107">如果所选会话由于出错而结束，则还将显示一个标记为 **“所选会话的错误详细信息或消息”** 的文本区域。</span><span class="sxs-lookup"><span data-stu-id="3e118-107">If the selected session ended in an error, the text area labeled **Error details or message of the selected session** is also displayed.</span></span>  
  
 <span data-ttu-id="3e118-108">**视图**</span><span class="sxs-lookup"><span data-stu-id="3e118-108">**View**</span></span>  
 <span data-ttu-id="3e118-109">选择要查看哪些分发代理会话。</span><span class="sxs-lookup"><span data-stu-id="3e118-109">Select which Distribution Agent sessions to view.</span></span>  
  
 <span data-ttu-id="3e118-110">**Status**</span><span class="sxs-lookup"><span data-stu-id="3e118-110">**Status**</span></span>  
 <span data-ttu-id="3e118-111">分发代理的状态。</span><span class="sxs-lookup"><span data-stu-id="3e118-111">The status of the Distribution Agent.</span></span> <span data-ttu-id="3e118-112">下面列出了可能的状态值：</span><span class="sxs-lookup"><span data-stu-id="3e118-112">The following list shows the possible status values:</span></span>  
  
-   <span data-ttu-id="3e118-113">错误</span><span class="sxs-lookup"><span data-stu-id="3e118-113">Error</span></span>  
  
-   <span data-ttu-id="3e118-114">已完成</span><span class="sxs-lookup"><span data-stu-id="3e118-114">Completed</span></span>  
  
-   <span data-ttu-id="3e118-115">正在重试</span><span class="sxs-lookup"><span data-stu-id="3e118-115">Retrying</span></span>  
  
-   <span data-ttu-id="3e118-116">正在运行</span><span class="sxs-lookup"><span data-stu-id="3e118-116">Running</span></span>  
  
 <span data-ttu-id="3e118-117">**开始时间**</span><span class="sxs-lookup"><span data-stu-id="3e118-117">**Start Time**</span></span>  
 <span data-ttu-id="3e118-118">会话的开始时间。</span><span class="sxs-lookup"><span data-stu-id="3e118-118">The start time of the session.</span></span>  
  
 <span data-ttu-id="3e118-119">**结束时间**</span><span class="sxs-lookup"><span data-stu-id="3e118-119">**End Time**</span></span>  
 <span data-ttu-id="3e118-120">会话的结束时间。</span><span class="sxs-lookup"><span data-stu-id="3e118-120">The end time of the session.</span></span> <span data-ttu-id="3e118-121">如果代理尚未停止，此字段为空。</span><span class="sxs-lookup"><span data-stu-id="3e118-121">If the agent has not stopped, this field is empty.</span></span>  
  
 <span data-ttu-id="3e118-122">**持续时间**</span><span class="sxs-lookup"><span data-stu-id="3e118-122">**Duration**</span></span>  
 <span data-ttu-id="3e118-123">分发代理已在此会话中运行的时间。</span><span class="sxs-lookup"><span data-stu-id="3e118-123">The amount of time the Distribution Agent has run in this session.</span></span> <span data-ttu-id="3e118-124">如果代理当前正在运行，该时间表示已用时间；如果代理会话已经结束，则该时间表示会话的总时间。</span><span class="sxs-lookup"><span data-stu-id="3e118-124">The time represents elapsed time if the agent is currently running and the total time of the session if the agent session had ended.</span></span>  
  
 <span data-ttu-id="3e118-125">**错误消息**</span><span class="sxs-lookup"><span data-stu-id="3e118-125">**Error Message**</span></span>  
 <span data-ttu-id="3e118-126">如果会话由于出错而结束，此字段将显示分发代理记录的上一条错误消息。</span><span class="sxs-lookup"><span data-stu-id="3e118-126">If a session ended in an error, this field displays the last error message logged by the Distribution Agent.</span></span> <span data-ttu-id="3e118-127">如果某会话未因出错而结束，此字段为空白。</span><span class="sxs-lookup"><span data-stu-id="3e118-127">If a session did not end in an error, this field is blank.</span></span>  
  
 <span data-ttu-id="3e118-128">**操作消息**</span><span class="sxs-lookup"><span data-stu-id="3e118-128">**Action Message**</span></span>  
 <span data-ttu-id="3e118-129">分发代理在所选会话过程中记录的所有信息性消息和错误消息。</span><span class="sxs-lookup"><span data-stu-id="3e118-129">All informational messages and error messages that the Distribution Agent has logged during the selected session.</span></span>  
  
 <span data-ttu-id="3e118-130">**操作时间**</span><span class="sxs-lookup"><span data-stu-id="3e118-130">**Action Time**</span></span>  
 <span data-ttu-id="3e118-131">执行 **“操作消息”** 列中所述操作的时间。</span><span class="sxs-lookup"><span data-stu-id="3e118-131">The time at which the action described in the **Action Message** column was performed.</span></span>  
  
 <span data-ttu-id="3e118-132">**“所选会话的错误详细信息或消息”**</span><span class="sxs-lookup"><span data-stu-id="3e118-132">**Error details or message of the selected session**</span></span>  
 <span data-ttu-id="3e118-133">只有当所选会话在 **“状态”** 列中显示 **“错误”** 值时，才会显示此项。</span><span class="sxs-lookup"><span data-stu-id="3e118-133">Displayed only if the selected session displays a value of **Error** in the **Status** column.</span></span> <span data-ttu-id="3e118-134">此文本区域显示详细错误信息以及出错时尝试执行的命令。</span><span class="sxs-lookup"><span data-stu-id="3e118-134">This text area displays detailed error information and the command that was attempted at the time of the error.</span></span> <span data-ttu-id="3e118-135">另外，还包括指向与该错误相关的其他内容的链接。</span><span class="sxs-lookup"><span data-stu-id="3e118-135">It also includes links to additional content related to the error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e118-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3e118-136">See Also</span></span>  
 <span data-ttu-id="3e118-137">[启动复制监视器](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="3e118-137">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="3e118-138">[使用复制监视器查看信息和执行任务](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="3e118-138">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 <span data-ttu-id="3e118-139">[监视复制](monitoring-replication.md) </span><span class="sxs-lookup"><span data-stu-id="3e118-139">[Monitoring Replication](monitoring-replication.md) </span></span>  
 [<span data-ttu-id="3e118-140">复制代理概述</span><span class="sxs-lookup"><span data-stu-id="3e118-140">Replication Agents Overview</span></span>](agents/replication-agents-overview.md)  
  
  
