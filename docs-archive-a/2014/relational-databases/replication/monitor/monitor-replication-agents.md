---
title: 监视复制代理 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- monitoring performance [SQL Server replication], agents
- Log Reader Agent, monitoring
- Replication Monitor, agents
- Merge Agent, monitoring
- Queue Reader Agent, monitoring
- Snapshot Agent, monitoring
- agents [SQL Server replication], monitoring
- Distribution Agent, monitoring
ms.assetid: d06ed24f-82d7-4b9e-9e40-cc9780476a71
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: baa22ef9e9f7c4621f76838e82c309d17f1e12a6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580131"
---
# <a name="monitor-replication-agents"></a><span data-ttu-id="9b402-102">监视复制代理</span><span class="sxs-lookup"><span data-stu-id="9b402-102">Monitor Replication Agents</span></span>
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="9b402-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 复制监视器提供复制活动的系统视图，并且还可以直观地查找有关特定代理的信息。</span><span class="sxs-lookup"><span data-stu-id="9b402-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Replication Monitor provides a systemic view of replication activity, but also makes it straightforward to find information on a specific agent.</span></span> <span data-ttu-id="9b402-104">以下列表列出了每个代理、可以在其中找到代理的选项卡（位于复制监视器中）以及指向说明如何访问这些选项卡的主题的链接：</span><span class="sxs-lookup"><span data-stu-id="9b402-104">The following list includes each agent, the tabs in the Replication Monitor on which it can be found, and a link to a topic that explains how to access these tabs:</span></span>  
  
-   <span data-ttu-id="9b402-105">以下代理与复制监视器中的发布相关联：</span><span class="sxs-lookup"><span data-stu-id="9b402-105">The following agents are associated with publications in Replication Monitor:</span></span>  
  
    -   <span data-ttu-id="9b402-106">快照代理</span><span class="sxs-lookup"><span data-stu-id="9b402-106">Snapshot Agent</span></span>  
  
    -   <span data-ttu-id="9b402-107">日志读取器代理</span><span class="sxs-lookup"><span data-stu-id="9b402-107">Log Reader Agent</span></span>  
  
    -   <span data-ttu-id="9b402-108">队列读取器代理</span><span class="sxs-lookup"><span data-stu-id="9b402-108">Queue Reader Agent</span></span>  
  
     <span data-ttu-id="9b402-109">通过以下选项卡访问与这些代理相关联的信息和任务：“代理”（可用于每个发布服务器和发布）和“警告”（可用于每个发布） 。</span><span class="sxs-lookup"><span data-stu-id="9b402-109">Access information and tasks associated with these agents through the following tabs: **Agents** (available for each Publisher and publication) and **Warnings** (available for each publication).</span></span> <span data-ttu-id="9b402-110">有关详细信息，请参阅[使用复制监视器查看信息和执行任务](view-information-and-perform-tasks-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="9b402-110">For more information, see [View Information and Perform Tasks using Replication Monitor](view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
-   <span data-ttu-id="9b402-111">以下代理与复制监视器中的订阅相关联：</span><span class="sxs-lookup"><span data-stu-id="9b402-111">The following agents are associated with subscriptions in Replication Monitor:</span></span>  
  
    -   <span data-ttu-id="9b402-112">分发代理</span><span class="sxs-lookup"><span data-stu-id="9b402-112">Distribution Agent</span></span>  
  
    -   <span data-ttu-id="9b402-113">合并代理</span><span class="sxs-lookup"><span data-stu-id="9b402-113">Merge Agent</span></span>  
  
     <span data-ttu-id="9b402-114">通过以下选项卡访问与这些代理相关联的信息和任务：“订阅监视列表”（所有发布服务器都提供）或“所有订阅”选项卡（所有发布都提供） 。</span><span class="sxs-lookup"><span data-stu-id="9b402-114">Access information and tasks associated with these agents through the following tabs: **Subscription Watch List** (available for each Publisher) or the **All Subscriptions** tab (available for each publication).</span></span> <span data-ttu-id="9b402-115">有关详细信息，请参阅[使用复制监视器查看信息和执行任务](view-information-and-perform-tasks-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="9b402-115">For more information, see [View Information and Perform Tasks using Replication Monitor](view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
## <a name="using-sql-server-management-studio-to-monitor-replication-agents"></a><span data-ttu-id="9b402-116">使用 SQL Server Management Studio 监视复制代理</span><span class="sxs-lookup"><span data-stu-id="9b402-116">Using SQL Server Management Studio to Monitor Replication Agents</span></span>  
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="9b402-117">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 为监视复制代理提供下列对话框：</span><span class="sxs-lookup"><span data-stu-id="9b402-117">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] provides the following dialog boxes for monitoring replication agents:</span></span>  
  
-   <span data-ttu-id="9b402-118">**“查看快照代理状态”** （针对所有发布）</span><span class="sxs-lookup"><span data-stu-id="9b402-118">**View Snapshot Agent Status** (for all publications)</span></span>  
  
-   <span data-ttu-id="9b402-119">**“查看日志读取器代理状态”** （针对所有事务发布）</span><span class="sxs-lookup"><span data-stu-id="9b402-119">**View Log Reader Agent Status** (for all transactional publications)</span></span>  
  
-   <span data-ttu-id="9b402-120">**“查看同步状态”** （针对所有订阅；使用此对话框可以访问分发代理和合并代理）</span><span class="sxs-lookup"><span data-stu-id="9b402-120">**View Synchronization Status** (for all subscriptions; this dialog box allows access to the Distribution Agent and the Merge Agent)</span></span>  
  
 <span data-ttu-id="9b402-121">复制监视器提供有关每个代理的补充信息，并且如果使用了队列读取器代理，它还会对其进行监视。</span><span class="sxs-lookup"><span data-stu-id="9b402-121">Replication Monitor provides additional information about each agent and provides monitoring for the Queue Reader Agent, if it is used.</span></span> <span data-ttu-id="9b402-122">有关详细信息，请参阅[使用复制监视器查看信息和执行任务](view-information-and-perform-tasks-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="9b402-122">For more information, see [View Information and Perform Tasks using Replication Monitor](view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
#### <a name="to-monitor-the-snapshot-agent-and-log-reader-agent"></a><span data-ttu-id="9b402-123">监视快照代理和日志读取器代理</span><span class="sxs-lookup"><span data-stu-id="9b402-123">To monitor the Snapshot Agent and Log Reader Agent</span></span>  
  
1.  <span data-ttu-id="9b402-124">在 [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]中连接到发布服务器，然后展开服务器节点。</span><span class="sxs-lookup"><span data-stu-id="9b402-124">Connect to the Publisher in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="9b402-125">展开 **“复制”** 文件夹，再展开 **“本地发布”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="9b402-125">Expand the **Replication** folder, and then expand the **Local Publications** folder.</span></span>  
  
3.  <span data-ttu-id="9b402-126">右键单击发布，再单击 **“查看日志读取器代理状态”** 或 **“查看快照代理状态”** 。</span><span class="sxs-lookup"><span data-stu-id="9b402-126">Right-click a publication, and then click **View Log Reader Agent Status** or **View Snapshot Agent Status**.</span></span>  
  
4.  <span data-ttu-id="9b402-127">在 **“查看日志读取器代理状态”** 或 **“查看快照代理状态”** 对话框中：</span><span class="sxs-lookup"><span data-stu-id="9b402-127">In the **View Log Reader Agent Status** or **View Snapshot Agent Status** dialog box:</span></span>  
  
    -   <span data-ttu-id="9b402-128">查看代理状态。</span><span class="sxs-lookup"><span data-stu-id="9b402-128">View agent status.</span></span>  
  
    -   <span data-ttu-id="9b402-129">必要时启动或停止代理。</span><span class="sxs-lookup"><span data-stu-id="9b402-129">Start or stop the agent if necessary.</span></span>  
  
    -   <span data-ttu-id="9b402-130">单击 **“监视器”** 启动 **复制监视器**。</span><span class="sxs-lookup"><span data-stu-id="9b402-130">Click **Monitor** to launch **Replication Monitor**.</span></span>  
  
5.  <span data-ttu-id="9b402-131">单击“关闭”。</span><span class="sxs-lookup"><span data-stu-id="9b402-131">Click **Close**.</span></span>  
  
#### <a name="to-monitor-the-distribution-agent-and-merge-agent-from-the-publisher"></a><span data-ttu-id="9b402-132">监视分发代理和合并代理（从发布服务器）</span><span class="sxs-lookup"><span data-stu-id="9b402-132">To monitor the Distribution Agent and Merge Agent (from the Publisher)</span></span>  
  
1.  <span data-ttu-id="9b402-133">在 [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]中连接到发布服务器，然后展开服务器节点。</span><span class="sxs-lookup"><span data-stu-id="9b402-133">Connect to the Publisher in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="9b402-134">展开 **“复制”** 文件夹，再展开 **“本地发布”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="9b402-134">Expand the **Replication** folder, and then expand the **Local Publications** folder.</span></span>  
  
3.  <span data-ttu-id="9b402-135">展开要监视的订阅的发布。</span><span class="sxs-lookup"><span data-stu-id="9b402-135">Expand the publication for the subscription you want to monitor.</span></span>  
  
4.  <span data-ttu-id="9b402-136">右键单击此订阅，再单击 **“查看同步状态”** 。</span><span class="sxs-lookup"><span data-stu-id="9b402-136">Right-click the subscription, and then click **View Synchronization Status**.</span></span>  
  
5.  <span data-ttu-id="9b402-137">在 **“查看同步状态”** 对话框中：</span><span class="sxs-lookup"><span data-stu-id="9b402-137">In the **View Synchronization Status** dialog box:</span></span>  
  
    -   <span data-ttu-id="9b402-138">查看代理状态。</span><span class="sxs-lookup"><span data-stu-id="9b402-138">View agent status.</span></span>  
  
    -   <span data-ttu-id="9b402-139">必要时启动或停止代理。</span><span class="sxs-lookup"><span data-stu-id="9b402-139">Start or stop the agent if necessary.</span></span>  
  
    -   <span data-ttu-id="9b402-140">对于推送订阅，单击 **“监视器”** 启动 **复制监视器**。</span><span class="sxs-lookup"><span data-stu-id="9b402-140">For push subscriptions, click **Monitor** to launch **Replication Monitor**.</span></span>  
  
    -   <span data-ttu-id="9b402-141">对于请求订阅，单击 **“查看作业历史记录”** 启动 **日志文件查看器**，此查看器可以显示代理日志的输出。</span><span class="sxs-lookup"><span data-stu-id="9b402-141">For pull subscriptions, click **View Job History** to launch the **Log File Viewer**, which displays output from the agent log.</span></span>  
  
6.  <span data-ttu-id="9b402-142">单击“关闭”。</span><span class="sxs-lookup"><span data-stu-id="9b402-142">Click **Close**.</span></span>  
  
#### <a name="to-monitor-the-distribution-agent-and-merge-agent-from-the-subscriber"></a><span data-ttu-id="9b402-143">监视分发代理和合并代理（从订阅服务器）</span><span class="sxs-lookup"><span data-stu-id="9b402-143">To monitor the Distribution Agent and Merge Agent (from the Subscriber)</span></span>  
  
1.  <span data-ttu-id="9b402-144">在 [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]中连接到订阅服务器，然后展开服务器节点。</span><span class="sxs-lookup"><span data-stu-id="9b402-144">Connect to the Subscriber in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="9b402-145">展开 **“复制”** 文件夹，再展开 **“本地订阅”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="9b402-145">Expand the **Replication** folder, and then expand the **Local Subscriptions** folder.</span></span>  
  
3.  <span data-ttu-id="9b402-146">右键单击要监视的订阅，再单击 **“查看同步状态”** 。</span><span class="sxs-lookup"><span data-stu-id="9b402-146">Right-click the subscription you want to monitor, and then click **View Synchronization Status**.</span></span>  
  
4.  <span data-ttu-id="9b402-147">在 **“查看同步状态”** 对话框中：</span><span class="sxs-lookup"><span data-stu-id="9b402-147">In the **View Synchronization Status** dialog box:</span></span>  
  
    -   <span data-ttu-id="9b402-148">查看代理状态。</span><span class="sxs-lookup"><span data-stu-id="9b402-148">View agent status.</span></span>  
  
    -   <span data-ttu-id="9b402-149">必要时启动或停止代理。</span><span class="sxs-lookup"><span data-stu-id="9b402-149">Start or stop the agent if necessary.</span></span>  
  
    -   <span data-ttu-id="9b402-150">单击 **“查看作业历史记录”** 启动 **日志文件查看器**，此查看器可以显示代理日志的输出。</span><span class="sxs-lookup"><span data-stu-id="9b402-150">Click **View Job History** to launch the **Log File Viewer**, which displays output from the agent log.</span></span>  
  
5.  <span data-ttu-id="9b402-151">单击“关闭”。</span><span class="sxs-lookup"><span data-stu-id="9b402-151">Click **Close**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b402-152">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9b402-152">See Also</span></span>  
 <span data-ttu-id="9b402-153">[监视复制](../monitoring-replication.md) </span><span class="sxs-lookup"><span data-stu-id="9b402-153">[Monitoring Replication](../monitoring-replication.md) </span></span>  
 [<span data-ttu-id="9b402-154">复制代理概述</span><span class="sxs-lookup"><span data-stu-id="9b402-154">Replication Agents Overview</span></span>](../agents/replication-agents-overview.md)  
  
  
