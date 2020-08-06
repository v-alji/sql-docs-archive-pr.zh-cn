---
title: 复制监视器界面概述 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Replication Monitor
- Replication Monitor, about Replication Monitor
ms.assetid: 078f0e34-7153-45c4-8725-778b5bef88da
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4d9b7edbd76153f23168ec9bcf4a286d5f7cbe9b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580126"
---
# <a name="overview-of-the-replication-monitor-interface"></a><span data-ttu-id="9548d-102">复制监视器界面概述</span><span class="sxs-lookup"><span data-stu-id="9548d-102">Overview of the Replication Monitor Interface</span></span>
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="9548d-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 复制监视器提供一个以发布服务器为主的视图或一个以分发服务器为主的视图，以两个窗格的形式显示所有复制活动。</span><span class="sxs-lookup"><span data-stu-id="9548d-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Replication Monitor presents a Publisher-focused view or Distributor-focused view of all replication activity in a two pane format.</span></span> <span data-ttu-id="9548d-104">在监视器的左窗格中添加发布服务器后，监视器的右窗格中即显示发布服务器、其发布、对这些发布的订阅和各种复制代理的相关信息。</span><span class="sxs-lookup"><span data-stu-id="9548d-104">You add a Publisher to the monitor in the left pane, and in the right pane the monitor displays information on the Publisher, its publications, the subscriptions to those publications, and the various replication agents.</span></span> <span data-ttu-id="9548d-105">除了显示有关复制拓扑的信息以外，复制监视器还可用于执行多种任务，如启动和停止代理以及验证数据。</span><span class="sxs-lookup"><span data-stu-id="9548d-105">In addition to presenting information for the replication topology, Replication Monitor allows you to perform a number of tasks, such as starting and stopping agents, and validating data.</span></span>  
  
## <a name="viewing-information-for-the-entire-topology"></a><span data-ttu-id="9548d-106">查看整个拓扑的信息</span><span class="sxs-lookup"><span data-stu-id="9548d-106">Viewing Information for the Entire Topology</span></span>  
 <span data-ttu-id="9548d-107">复制监视器的左窗格显示</span><span class="sxs-lookup"><span data-stu-id="9548d-107">The left pane of Replication Monitor displays</span></span>  
  
-   <span data-ttu-id="9548d-108">发布服务器组、发布服务器和发布内容。</span><span class="sxs-lookup"><span data-stu-id="9548d-108">Publisher groups, Publishers, and publications.</span></span>  
  
-   <span data-ttu-id="9548d-109">分发服务器、发布服务器和发布内容。</span><span class="sxs-lookup"><span data-stu-id="9548d-109">Distributors, Publishers, and publications.</span></span>  
  
 <span data-ttu-id="9548d-110">若要在复制监视器中查看任何信息，必须首先添加发布服务器。</span><span class="sxs-lookup"><span data-stu-id="9548d-110">To view any information in Replication Monitor, you must first add a Publisher.</span></span> <span data-ttu-id="9548d-111">有关详细信息，请参阅 [从复制监视器中添加和删除发布服务器](add-and-remove-publishers-from-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="9548d-111">For more information, see [Add and Remove Publishers from Replication Monitor](add-and-remove-publishers-from-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="9548d-112">左窗格有助于解答下列问题：</span><span class="sxs-lookup"><span data-stu-id="9548d-112">The left pane helps answer the following questions:</span></span>  
  
-   <span data-ttu-id="9548d-113">我的复制系统是否正常？</span><span class="sxs-lookup"><span data-stu-id="9548d-113">Is my replication system healthy?</span></span>  
  
     <span data-ttu-id="9548d-114">如果左窗格中的节点上无错误图标，则复制系统比较正常。</span><span class="sxs-lookup"><span data-stu-id="9548d-114">The replication system is relatively healthy if there are no error icons on nodes in the left pane.</span></span> <span data-ttu-id="9548d-115">若要详细了解系统运行状况，请查看 **“订阅监视列表”** 选项卡，该选项卡显示了可能需要注意的订阅的相关信息。</span><span class="sxs-lookup"><span data-stu-id="9548d-115">To get a more complete view of system health, you should also check the **Subscription Watch List** tab, which displays information on subscriptions that might require attention.</span></span>  
  
-   <span data-ttu-id="9548d-116">为什么代理不运行？</span><span class="sxs-lookup"><span data-stu-id="9548d-116">Why is an agent not running?</span></span>  
  
     <span data-ttu-id="9548d-117">代理未在特定时间运行的原因包括：未安排其运行或出现错误。</span><span class="sxs-lookup"><span data-stu-id="9548d-117">An agent is not running at a particular time either because it is not scheduled to run or because an error has occurred.</span></span> <span data-ttu-id="9548d-118">如果出现错误，左窗格中的相应节点上将显示错误图标。</span><span class="sxs-lookup"><span data-stu-id="9548d-118">If an error has occurred, an error icon is displayed on the appropriate nodes in the left pane.</span></span> <span data-ttu-id="9548d-119">例如，如果发布的快照代理因出错而停止，发布服务器组、发布服务器和发布节点上将显示错误图标。</span><span class="sxs-lookup"><span data-stu-id="9548d-119">For example, if the Snapshot Agent for a publication stopped because of an error, an error icon is displayed on the Publisher group, Publisher, and publication nodes.</span></span> <span data-ttu-id="9548d-120">快照代理的摘要信息显示在该发布的 **“代理”** 选项卡中；双击此选项卡上的快照代理可查看详细的错误信息。</span><span class="sxs-lookup"><span data-stu-id="9548d-120">Summary information for the Snapshot Agent is displayed on the **Agents** tab for the publication; double click the Snapshot Agent on this tab for detailed error information.</span></span>  
  
## <a name="viewing-information-and-performing-tasks-related-to-distributors"></a><span data-ttu-id="9548d-121">查看与分发服务器相关的信息并执行与其相关的任务</span><span class="sxs-lookup"><span data-stu-id="9548d-121">Viewing Information and Performing Tasks Related to Distributors</span></span>  
 <span data-ttu-id="9548d-122">复制监视器在三个选项卡上显示分发服务器的相关信息：</span><span class="sxs-lookup"><span data-stu-id="9548d-122">Replication Monitor displays information about Distributors on three tabs:</span></span>  
  
-   <span data-ttu-id="9548d-123">**“发布”** 选项卡</span><span class="sxs-lookup"><span data-stu-id="9548d-123">**Publications** tab</span></span>  
  
     <span data-ttu-id="9548d-124">此选项卡提供分发服务器上所有发布的摘要信息。</span><span class="sxs-lookup"><span data-stu-id="9548d-124">This tab provides summary information for all publications of a Distributor.</span></span>  
  
-   <span data-ttu-id="9548d-125">**“订阅监视列表”** 选项卡</span><span class="sxs-lookup"><span data-stu-id="9548d-125">**Subscription Watch List** tab</span></span>  
  
     <span data-ttu-id="9548d-126">此选项卡提供有关所选分发服务器的订阅的信息。</span><span class="sxs-lookup"><span data-stu-id="9548d-126">This tab provides information about subscriptions for the selected Distributor.</span></span> <span data-ttu-id="9548d-127">可以筛选订阅列表，以查看有错误的订阅、出现警告的订阅以及所有性能较差的订阅。</span><span class="sxs-lookup"><span data-stu-id="9548d-127">You can filter the list of subscriptions to see errors, warnings, and any poorly performing subscriptions.</span></span> <span data-ttu-id="9548d-128">使用该选项卡还可以执行以下任务：访问订阅属性、访问与订阅关联的代理的详细信息、重新初始化订阅以及验证订阅。</span><span class="sxs-lookup"><span data-stu-id="9548d-128">The tab also lets you to perform the following tasks: access subscription properties, access detailed information about the agent or agents associated with a subscription, reinitialize subscriptions, and validate subscriptions.</span></span>  
  
     <span data-ttu-id="9548d-129">**“订阅监视列表”** 选项卡可以帮助解答下列问题：</span><span class="sxs-lookup"><span data-stu-id="9548d-129">The **Subscription Watch List** tab helps answer the following questions:</span></span>  
  
    -   <span data-ttu-id="9548d-130">哪些订阅比较慢？</span><span class="sxs-lookup"><span data-stu-id="9548d-130">Which subscriptions are slow?</span></span>  
  
         <span data-ttu-id="9548d-131">设置此选项卡上的选项，使网格按订阅的相对性能顺序显示订阅。</span><span class="sxs-lookup"><span data-stu-id="9548d-131">Set options on this tab so that the grid displays subscriptions in order by their relative performance.</span></span>  
  
    -   <span data-ttu-id="9548d-132">我的复制系统是否正常？</span><span class="sxs-lookup"><span data-stu-id="9548d-132">Is my replication system healthy?</span></span>  
  
         <span data-ttu-id="9548d-133">对于任何需要注意的订阅，此选项卡上的网格都将显示错误图标和警告图标。</span><span class="sxs-lookup"><span data-stu-id="9548d-133">The grid on this tab displays error and warning icons for any subscriptions that require your attention.</span></span>  
  
     <span data-ttu-id="9548d-134">此选项卡对于运行 [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] 或更低版本的分发服务器不可用。</span><span class="sxs-lookup"><span data-stu-id="9548d-134">This tab is not available for Distributors that are running versions of [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] or earlier.</span></span>  
  
-   <span data-ttu-id="9548d-135">**“代理”** 选项卡</span><span class="sxs-lookup"><span data-stu-id="9548d-135">**Agents** tab</span></span>  
  
     <span data-ttu-id="9548d-136">此选项卡显示所有类型的复制所使用的代理和作业的详细信息。</span><span class="sxs-lookup"><span data-stu-id="9548d-136">This tab displays detailed information about the agents and jobs that are used by all types of replication.</span></span> <span data-ttu-id="9548d-137">使用此选项卡，还可以启动和停止每个代理和作业。</span><span class="sxs-lookup"><span data-stu-id="9548d-137">The tab also let you start and stop each agent and job.</span></span>  
  
 <span data-ttu-id="9548d-138">复制监视器还为分发服务器节点提供了上下文菜单。</span><span class="sxs-lookup"><span data-stu-id="9548d-138">Replication Monitor also provides a context menu for the Distributor node.</span></span> <span data-ttu-id="9548d-139">右键单击左窗格中的分发服务器，可以执行以下任务：</span><span class="sxs-lookup"><span data-stu-id="9548d-139">Right-click a Distributor in the left pane to perform the following tasks:</span></span>  
  
-   <span data-ttu-id="9548d-140">向复制监视器添加发布服务器。</span><span class="sxs-lookup"><span data-stu-id="9548d-140">Add a Publisher to Replication Monitor.</span></span>  
  
-   <span data-ttu-id="9548d-141">编辑分发服务器的复制监视器设置。</span><span class="sxs-lookup"><span data-stu-id="9548d-141">Edit Replication Monitor settings for the Distributor.</span></span>  
  
-   <span data-ttu-id="9548d-142">切换到“发布服务器组”视图。</span><span class="sxs-lookup"><span data-stu-id="9548d-142">Switch to the Publisher Group view.</span></span>  
  
## <a name="viewing-information-and-performing-tasks-related-to-publishers"></a><span data-ttu-id="9548d-143">查看与发布服务器相关的信息并执行与其相关的任务</span><span class="sxs-lookup"><span data-stu-id="9548d-143">Viewing Information and Performing Tasks Related to Publishers</span></span>  
 <span data-ttu-id="9548d-144">复制监视器在三个选项卡上显示发布服务器的相关信息：</span><span class="sxs-lookup"><span data-stu-id="9548d-144">Replication Monitor displays information about Publishers on three tabs:</span></span>  
  
-   <span data-ttu-id="9548d-145">**“发布”** 选项卡</span><span class="sxs-lookup"><span data-stu-id="9548d-145">**Publications** tab</span></span>  
  
     <span data-ttu-id="9548d-146">此选项卡提供发布服务器上所有发布的摘要信息。</span><span class="sxs-lookup"><span data-stu-id="9548d-146">This tab provides summary information for all publications at a Publisher.</span></span>  
  
-   <span data-ttu-id="9548d-147">**“订阅监视列表”** 选项卡</span><span class="sxs-lookup"><span data-stu-id="9548d-147">**Subscription Watch List** tab</span></span>  
  
     <span data-ttu-id="9548d-148">此选项卡用于显示所选发布服务器上所有可用发布的订阅的信息。</span><span class="sxs-lookup"><span data-stu-id="9548d-148">This tab is intended to display information on subscriptions from all publications available at the selected Publisher.</span></span> <span data-ttu-id="9548d-149">可以筛选订阅列表，以查看有错误的订阅、出现警告的订阅以及所有性能较差的订阅。</span><span class="sxs-lookup"><span data-stu-id="9548d-149">You can filter the list of subscriptions to see errors, warnings, and any poorly performing subscriptions.</span></span> <span data-ttu-id="9548d-150">使用该选项卡可以：访问订阅属性、访问与订阅关联的代理的详细信息、重新初始化订阅以及验证订阅。</span><span class="sxs-lookup"><span data-stu-id="9548d-150">The tab also allows you to: access subscription properties; access detailed information about the agent or agents associated with a subscription; reinitialize subscriptions; and validate subscriptions.</span></span>  
  
     <span data-ttu-id="9548d-151">**“订阅监视列表”** 选项卡可以帮助解答下列问题：</span><span class="sxs-lookup"><span data-stu-id="9548d-151">The **Subscription Watch List** tab helps answer the following questions:</span></span>  
  
    -   <span data-ttu-id="9548d-152">哪些订阅比较慢？</span><span class="sxs-lookup"><span data-stu-id="9548d-152">Which subscriptions are slow?</span></span>  
  
         <span data-ttu-id="9548d-153">设置此选项卡上的选项，使网格按订阅的相对性能顺序显示订阅。</span><span class="sxs-lookup"><span data-stu-id="9548d-153">Set options on this tab so that the grid displays subscriptions in order by their relative performance.</span></span>  
  
    -   <span data-ttu-id="9548d-154">我的复制系统是否正常？</span><span class="sxs-lookup"><span data-stu-id="9548d-154">Is my replication system healthy?</span></span>  
  
         <span data-ttu-id="9548d-155">对于任何需要注意的订阅，此选项卡上的网格都将显示错误图标和警告图标。</span><span class="sxs-lookup"><span data-stu-id="9548d-155">The grid on this tab displays error and warning icons for any subscriptions that require your attention.</span></span>  
  
     <span data-ttu-id="9548d-156">对于运行 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]之前版本的分发服务器，将不显示此选项卡。</span><span class="sxs-lookup"><span data-stu-id="9548d-156">This tab is not displayed for Distributors running versions prior to [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].</span></span>  
  
-   <span data-ttu-id="9548d-157">**“代理”** 选项卡</span><span class="sxs-lookup"><span data-stu-id="9548d-157">**Agents** tab</span></span>  
  
     <span data-ttu-id="9548d-158">此选项卡显示所有类型的复制所用代理和作业的详细信息。</span><span class="sxs-lookup"><span data-stu-id="9548d-158">This tab displays detailed information about the agents and jobs used by all types of replication.</span></span> <span data-ttu-id="9548d-159">使用该选项卡，还可以启动和停止每个代理和作业。</span><span class="sxs-lookup"><span data-stu-id="9548d-159">The tab also allows you to start and stop each agent and job.</span></span>  
  
 <span data-ttu-id="9548d-160">有关详细信息，请参阅[使用复制监视器查看信息和执行任务](view-information-and-perform-tasks-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="9548d-160">For more information, see [View Information and Perform Tasks using Replication Monitor](view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="9548d-161">复制监视器还为发布服务器节点提供了上下文菜单。</span><span class="sxs-lookup"><span data-stu-id="9548d-161">Replication Monitor also provides a context menu for the Publisher node.</span></span> <span data-ttu-id="9548d-162">右键单击左窗格中的发布服务器，可以执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="9548d-162">Right-click a Publisher in the left pane to:</span></span>  
  
-   <span data-ttu-id="9548d-163">编辑发布服务器的复制监视器设置</span><span class="sxs-lookup"><span data-stu-id="9548d-163">Edit Replication Monitor settings for the Publisher</span></span>  
  
-   <span data-ttu-id="9548d-164">从复制监视器中删除发布服务器</span><span class="sxs-lookup"><span data-stu-id="9548d-164">Remove the Publisher from Replication Monitor</span></span>  
  
-   <span data-ttu-id="9548d-165">查看和编辑代理配置文件</span><span class="sxs-lookup"><span data-stu-id="9548d-165">View and edit agent profiles</span></span>  
  
-   <span data-ttu-id="9548d-166">与存储发布服务器信息的分发服务器连接或断开连接</span><span class="sxs-lookup"><span data-stu-id="9548d-166">Connect to or disconnect from the Distributor that stores information about the Publisher</span></span>  
  
## <a name="viewing-information-and-performing-tasks-related-to-publications"></a><span data-ttu-id="9548d-167">查看与发布相关的信息并执行与其相关的任务</span><span class="sxs-lookup"><span data-stu-id="9548d-167">Viewing Information and Performing Tasks Related to Publications</span></span>  
 <span data-ttu-id="9548d-168">复制监视器在三个选项卡和多个详细信息窗口中显示发布的相关信息：</span><span class="sxs-lookup"><span data-stu-id="9548d-168">Replication Monitor displays information about publications on three tabs and a number of detail windows:</span></span>  
  
-   <span data-ttu-id="9548d-169">**“所有订阅”** 选项卡</span><span class="sxs-lookup"><span data-stu-id="9548d-169">**All Subscriptions** tab</span></span>  
  
     <span data-ttu-id="9548d-170">此选项卡显示有关所选发布的所有订阅的信息。</span><span class="sxs-lookup"><span data-stu-id="9548d-170">This tab displays information about all subscriptions to the selected publication.</span></span> <span data-ttu-id="9548d-171">默认情况下，此选项卡按优先级顺序排序：先是有错误的订阅，接着是有警告的订阅，然后是按性能升序排列的订阅，最后，执行不当的订阅位于顶部。</span><span class="sxs-lookup"><span data-stu-id="9548d-171">By default, this tab is sorted in priority order: errors, then warnings, then in increasing order of performance, with any poorly performing subscriptions at the top.</span></span>  
  
     <span data-ttu-id="9548d-172">**“所有订阅”** 选项卡可以帮助解答下列问题：</span><span class="sxs-lookup"><span data-stu-id="9548d-172">The **All Subscriptions** tab helps answer the following questions:</span></span>  
  
    -   <span data-ttu-id="9548d-173">哪些订阅比较慢？</span><span class="sxs-lookup"><span data-stu-id="9548d-173">Which subscriptions are slow?</span></span>  
  
         <span data-ttu-id="9548d-174">设置此选项卡上的选项，使网格按订阅的相对性能顺序显示订阅。</span><span class="sxs-lookup"><span data-stu-id="9548d-174">Set options on this tab so that the grid displays subscriptions in order by their relative performance.</span></span>  
  
    -   <span data-ttu-id="9548d-175">我的复制系统是否正常？</span><span class="sxs-lookup"><span data-stu-id="9548d-175">Is my replication system healthy?</span></span>  
  
         <span data-ttu-id="9548d-176">对于任何需要注意的订阅，此选项卡上的网格都将显示错误图标和警告图标。</span><span class="sxs-lookup"><span data-stu-id="9548d-176">The grid on this tab displays error and warning icons for any subscriptions that require your attention.</span></span>  
  
-   <span data-ttu-id="9548d-177">**“代理”** 选项卡</span><span class="sxs-lookup"><span data-stu-id="9548d-177">**Agents** tab</span></span>  
  
     <span data-ttu-id="9548d-178">此选项卡显示复制所用代理的相关信息。</span><span class="sxs-lookup"><span data-stu-id="9548d-178">This tab displays information about the agents that are used by replication.</span></span> <span data-ttu-id="9548d-179">此选项卡显示有关下列代理的信息：</span><span class="sxs-lookup"><span data-stu-id="9548d-179">This tab displays information about the following agents:</span></span>  
  
    -   <span data-ttu-id="9548d-180">快照代理，用于所有发布。</span><span class="sxs-lookup"><span data-stu-id="9548d-180">The Snapshot Agent, which is used by all publications.</span></span>  
  
    -   <span data-ttu-id="9548d-181">日志读取器代理，用于所有事务发布。</span><span class="sxs-lookup"><span data-stu-id="9548d-181">The Log Reader Agent, which is used by all transactional publications.</span></span>  
  
    -   <span data-ttu-id="9548d-182">队列读取器代理，用于为排队更新订阅启用的事务发布。</span><span class="sxs-lookup"><span data-stu-id="9548d-182">The Queue Reader Agent, which is used by transactional publications enabled for queued updating subscriptions.</span></span>  
  
     <span data-ttu-id="9548d-183">使用该选项卡，还可以执行以下任务：访问每个代理的详细信息，以及启动和停止每个代理。</span><span class="sxs-lookup"><span data-stu-id="9548d-183">The tab also allows for you to perform the following tasks: access detailed information about each agent, and start and stop each agent.</span></span> <span data-ttu-id="9548d-184">有关与订阅关联的代理（分发代理和合并代理）的信息，请参阅本主题中的“查看与订阅相关的信息并执行与订阅相关的任务”部分。</span><span class="sxs-lookup"><span data-stu-id="9548d-184">For information about agents that are associated with subscriptions (the Distribution Agent and Merge Agent), see the section "Viewing Information and Performing Tasks Related to Subscriptions" in this topic.</span></span>  
  
-   <span data-ttu-id="9548d-185">**“警告”** 选项卡</span><span class="sxs-lookup"><span data-stu-id="9548d-185">**Warnings** tab</span></span>  
  
     <span data-ttu-id="9548d-186">使用此选项卡可以为代理指定警告和警报。</span><span class="sxs-lookup"><span data-stu-id="9548d-186">This tab enables you to specify warnings and alerts for agents.</span></span> <span data-ttu-id="9548d-187">有关详细信息，请参阅 [Set Thresholds and Warnings in Replication Monitor](set-thresholds-and-warnings-in-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="9548d-187">For more information, see [Set Thresholds and Warnings in Replication Monitor](set-thresholds-and-warnings-in-replication-monitor.md).</span></span>  
  
-   <span data-ttu-id="9548d-188">**“跟踪令牌”** 选项卡（仅事务复制）</span><span class="sxs-lookup"><span data-stu-id="9548d-188">**Tracer Tokens** tab (transactional replication only)</span></span>  
  
     <span data-ttu-id="9548d-189">可以使用此选项卡衡量滞后时间，滞后时间是指从事务在发布服务器上提交到相应的事务在订阅服务器上提交之间间隔的时间。</span><span class="sxs-lookup"><span data-stu-id="9548d-189">This tab allows you to measure latency, the amount of time that elapses between a transaction being committed at the Publisher and the corresponding transaction being committed at the Subscriber.</span></span>  
  
     <span data-ttu-id="9548d-190">此选项卡可以帮助解答下面的问题：</span><span class="sxs-lookup"><span data-stu-id="9548d-190">This tab helps answers the following question:</span></span>  
  
    -   <span data-ttu-id="9548d-191">在事务复制中，现在提交的事务要过多久才能到达订阅服务器？</span><span class="sxs-lookup"><span data-stu-id="9548d-191">How long will it take a transaction committed now to reach a Subscriber in transactional replication?</span></span>  
  
         <span data-ttu-id="9548d-192">查看事务通过系统的总时间并将其与先前所用时间进行比较。</span><span class="sxs-lookup"><span data-stu-id="9548d-192">View the total time for a transaction to travel through the system and also compare it to previous times.</span></span>  
  
     <span data-ttu-id="9548d-193">对于运行 [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] 或更低版本的分发服务器，将不显示此选项卡。</span><span class="sxs-lookup"><span data-stu-id="9548d-193">This tab is not displayed for Distributors running [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] or earlier.</span></span> <span data-ttu-id="9548d-194">有关跟踪令牌的详细信息，请参阅[为事务复制测量滞后时间和验证连接](measure-latency-and-validate-connections-for-transactional-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="9548d-194">For more information on tracer tokens, see [Measure Latency and Validate Connections for Transactional Replication](measure-latency-and-validate-connections-for-transactional-replication.md).</span></span>  
  
-   <span data-ttu-id="9548d-195">与发布关联的代理的详细信息窗口。</span><span class="sxs-lookup"><span data-stu-id="9548d-195">Detail windows for the agents associated with a publication.</span></span> <span data-ttu-id="9548d-196">下列代理与发布相关联：</span><span class="sxs-lookup"><span data-stu-id="9548d-196">The following agents are associated with publications:</span></span>  
  
    -   <span data-ttu-id="9548d-197">快照代理，用于所有发布。</span><span class="sxs-lookup"><span data-stu-id="9548d-197">The Snapshot Agent, which is used by all publications.</span></span>  
  
    -   <span data-ttu-id="9548d-198">日志读取器代理，用于所有事务发布。</span><span class="sxs-lookup"><span data-stu-id="9548d-198">The Log Reader Agent, which is used by all transactional publications.</span></span>  
  
    -   <span data-ttu-id="9548d-199">队列读取器代理，用于为排队更新订阅启用的事务发布。</span><span class="sxs-lookup"><span data-stu-id="9548d-199">The Queue Reader Agent, which is used by transactional publications enabled for queued updating subscriptions.</span></span>  
  
     <span data-ttu-id="9548d-200">双击复制监视器中的代理，可以访问详细信息窗口中的信息。</span><span class="sxs-lookup"><span data-stu-id="9548d-200">Double-click an agent in Replication Monitor to access information in a detail window.</span></span> <span data-ttu-id="9548d-201">除了上面列出的代理之外，与订阅关联的代理还包括：快照和事务发布的订阅的分发代理，以及合并发布的订阅的合并代理。</span><span class="sxs-lookup"><span data-stu-id="9548d-201">In addition to the agents listed above, there are agents associated with subscriptions: the Distribution Agent for subscriptions to snapshot and transactional publications; and the Merge Agent for subscriptions to merge publications.</span></span> <span data-ttu-id="9548d-202">有关详细信息，请参阅本主题中的“查看与订阅相关的信息并执行与订阅相关的任务”部分。</span><span class="sxs-lookup"><span data-stu-id="9548d-202">For more information, see the section "Viewing Information and Performing Tasks Related to Subscriptions" in this topic.</span></span>  
  
     <span data-ttu-id="9548d-203">代理详细信息窗口提供有关代理会话的信息，包括开始时间、结束时间、持续时间和会话中执行的操作。</span><span class="sxs-lookup"><span data-stu-id="9548d-203">The agent detail windows provide information about agent sessions, including start time, end time, duration, and the actions performed in a session.</span></span> <span data-ttu-id="9548d-204">这些窗口可以帮助解答下面的问题：</span><span class="sxs-lookup"><span data-stu-id="9548d-204">They help to answer the following question:</span></span>  
  
    -   <span data-ttu-id="9548d-205">为什么代理不运行？</span><span class="sxs-lookup"><span data-stu-id="9548d-205">Why is an agent not running?</span></span>  
  
         <span data-ttu-id="9548d-206">可用的错误消息提供代理不运行的详细原因，并为解决与发布关联的代理的问题提供一个起点。</span><span class="sxs-lookup"><span data-stu-id="9548d-206">The error messages available provide detailed information on why an agent is not running and provide a starting point for troubleshooting issues with the agents associated with a publication.</span></span>  
  
 <span data-ttu-id="9548d-207">有关详细信息，请参阅[使用复制监视器查看信息和执行任务](view-information-and-perform-tasks-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="9548d-207">For more information, see [View Information and Perform Tasks using Replication Monitor](view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="9548d-208">复制监视器还为发布节点提供了上下文菜单。</span><span class="sxs-lookup"><span data-stu-id="9548d-208">Replication Monitor also provides a context menu for the publications node.</span></span> <span data-ttu-id="9548d-209">右键单击左窗格中的发布，可以执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="9548d-209">Right-click a publication in the left pane to:</span></span>  
  
-   <span data-ttu-id="9548d-210">重新初始化发布的所有订阅</span><span class="sxs-lookup"><span data-stu-id="9548d-210">Reinitialize all subscriptions to a publication</span></span>  
  
-   <span data-ttu-id="9548d-211">验证发布的所有订阅</span><span class="sxs-lookup"><span data-stu-id="9548d-211">Validate all subscriptions to a publication</span></span>  
  
-   <span data-ttu-id="9548d-212">为发布生成快照</span><span class="sxs-lookup"><span data-stu-id="9548d-212">Generate a snapshot for a publication</span></span>  
  
-   <span data-ttu-id="9548d-213">查看和编辑发布属性</span><span class="sxs-lookup"><span data-stu-id="9548d-213">View and edit publication properties</span></span>  
  
## <a name="viewing-information-and-performing-tasks-related-to-subscriptions"></a><span data-ttu-id="9548d-214">查看与订阅相关的信息并执行与订阅相关的任务</span><span class="sxs-lookup"><span data-stu-id="9548d-214">Viewing Information and Performing Tasks Related to Subscriptions</span></span>  
 <span data-ttu-id="9548d-215">复制监视器在多个不同的选项卡上显示订阅的相关信息。</span><span class="sxs-lookup"><span data-stu-id="9548d-215">Replication Monitor displays information about subscriptions on a number of different tabs.</span></span> <span data-ttu-id="9548d-216">双击复制监视器中的订阅，可以访问详细信息窗口中的这些选项卡。</span><span class="sxs-lookup"><span data-stu-id="9548d-216">Double-click a subscription in Replication Monitor to access these tabs in a detail window.</span></span> <span data-ttu-id="9548d-217">对于解答“为什么代理不运行”这个问题，所有选项卡都很有用。</span><span class="sxs-lookup"><span data-stu-id="9548d-217">All of the tabs are useful in answering the question "Why is an agent not running?"</span></span> <span data-ttu-id="9548d-218">可用的错误消息提供代理不运行的详细原因，并为解决与订阅关联的代理的问题提供一个起点。</span><span class="sxs-lookup"><span data-stu-id="9548d-218">The error messages available provide detailed information on why an agent is not running and provide a starting point for troubleshooting issues with the agents associated with a subscription.</span></span>  
  
-   <span data-ttu-id="9548d-219">**“所有订阅”** 和 **“订阅监视列表”**</span><span class="sxs-lookup"><span data-stu-id="9548d-219">**All Subscriptions tab** and **Subscription Watch List tab.**</span></span>  
  
     <span data-ttu-id="9548d-220">本主题的前面已对这两个选项卡进行了说明。</span><span class="sxs-lookup"><span data-stu-id="9548d-220">These tabs are described earlier in this topic.</span></span>  
  
-   <span data-ttu-id="9548d-221">**“发布服务器到分发服务器的历史记录”** 选项卡（仅事务复制）</span><span class="sxs-lookup"><span data-stu-id="9548d-221">**Publisher to Distributor History** tab (transactional replication only)</span></span>  
  
     <span data-ttu-id="9548d-222">此选项卡显示发布的日志读取器代理的信息（该选项卡与日志读取器代理详细信息窗口的作用相同）。</span><span class="sxs-lookup"><span data-stu-id="9548d-222">This tab displays information on the Log Reader Agent for a publication (the tab is identical to the Log Reader Agent details window).</span></span>  
  
-   <span data-ttu-id="9548d-223">**“分发服务器到订阅服务器的历史记录”** 选项卡（快照复制和事务复制）</span><span class="sxs-lookup"><span data-stu-id="9548d-223">**Distributor to Subscriber History** tab (snapshot replication and transactional replication)</span></span>  
  
     <span data-ttu-id="9548d-224">此选项卡显示订阅的分发代理的信息。</span><span class="sxs-lookup"><span data-stu-id="9548d-224">This tab displays information on the Distribution Agent for a subscription.</span></span>  
  
-   <span data-ttu-id="9548d-225">**“未分发的命令”** 选项卡（仅事务复制）</span><span class="sxs-lookup"><span data-stu-id="9548d-225">**Undistributed Commands** tab (transactional replication only)</span></span>  
  
     <span data-ttu-id="9548d-226">此选项卡显示分发数据库中未传递到所选订阅服务器的命令数以及传递那些命令的估计时间。</span><span class="sxs-lookup"><span data-stu-id="9548d-226">This tab displays information about the number of commands in the distribution database that have not been delivered to the selected Subscriber, and the estimated time to deliver those commands.</span></span> <span data-ttu-id="9548d-227">该选项卡可以帮助解答问题“我的订阅滞后多久？”</span><span class="sxs-lookup"><span data-stu-id="9548d-227">The tab helps answer the question, "How far behind is my subscription?"</span></span> <span data-ttu-id="9548d-228">对于运行 SQL Server 2005 之前版本的分发服务器，将不显示此选项卡。</span><span class="sxs-lookup"><span data-stu-id="9548d-228">This tab is not displayed for Distributors running versions prior to SQL Server 2005.</span></span>  
  
-   <span data-ttu-id="9548d-229">**“同步历史记录”** 选项卡（仅合并复制）</span><span class="sxs-lookup"><span data-stu-id="9548d-229">**Synchronization History** tab (merge replication only)</span></span>  
  
     <span data-ttu-id="9548d-230">此选项卡显示订阅的合并代理的信息。</span><span class="sxs-lookup"><span data-stu-id="9548d-230">This tab displays information on the Merge Agent for a subscription.</span></span> <span data-ttu-id="9548d-231">此选项卡可以帮助解答下面的问题：</span><span class="sxs-lookup"><span data-stu-id="9548d-231">This tab helps answer the following question:</span></span>  
  
    -   <span data-ttu-id="9548d-232">为什么我的合并订阅比较慢？</span><span class="sxs-lookup"><span data-stu-id="9548d-232">Why is my merge subscription slow?</span></span>  
  
         <span data-ttu-id="9548d-233">此选项卡提供同步过程中处理的每个项目的详细统计信息，包括每个处理阶段（上载更改、下载更改等）所用的时间。</span><span class="sxs-lookup"><span data-stu-id="9548d-233">This tab provides detailed statistics for each article processed during synchronization, including the amount of time spent in each processing phase (uploading changes, downloading changes, and so on).</span></span> <span data-ttu-id="9548d-234">该选项卡可以帮助准确定位导致减速的特定表，并且是解决合并订阅的性能问题的最佳位置。</span><span class="sxs-lookup"><span data-stu-id="9548d-234">It can help pinpoint specific tables that are causing slowdowns and is the best place to troubleshoot performance issues with merge subscriptions.</span></span>  
  
 <span data-ttu-id="9548d-235">有关详细信息，请参阅[使用复制监视器查看信息和执行任务](view-information-and-perform-tasks-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="9548d-235">For more information, see [View Information and Perform Tasks using Replication Monitor](view-information-and-perform-tasks-replication-monitor.md).</span></span>
  
## <a name="viewing-information-and-performing-tasks-related-to-agent-profiles"></a><span data-ttu-id="9548d-236">查看与代理配置文件相关的信息并执行与其相关的任务</span><span class="sxs-lookup"><span data-stu-id="9548d-236">Viewing Information and Performing Tasks Related to Agent Profiles</span></span>  
 <span data-ttu-id="9548d-237">复制监视器中包含多个管理代理配置文件的对话框。</span><span class="sxs-lookup"><span data-stu-id="9548d-237">Replication Monitor includes a number of dialog boxes for managing agent profiles.</span></span> <span data-ttu-id="9548d-238">代理配置文件是代理的参数集，用于确定代理的行为。</span><span class="sxs-lookup"><span data-stu-id="9548d-238">Agent profiles are sets of parameters for an agent that determine agent behavior.</span></span> <span data-ttu-id="9548d-239">有关详细信息，请参阅 [Replication Agent Profiles](../agents/replication-agent-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="9548d-239">For more information, see [Replication Agent Profiles](../agents/replication-agent-profiles.md).</span></span> <span data-ttu-id="9548d-240">这些对话框包括：</span><span class="sxs-lookup"><span data-stu-id="9548d-240">The dialog boxes are:</span></span>  
  
-   <span data-ttu-id="9548d-241">**代理配置文件**</span><span class="sxs-lookup"><span data-stu-id="9548d-241">**Agent Profiles**</span></span>  
  
     <span data-ttu-id="9548d-242">使用此对话框可以：更改配置文件的属性、创建和删除配置文件、指定默认配置文件，以及指定某特定类型的所有代理（如快照代理）应使用给定配置文件。</span><span class="sxs-lookup"><span data-stu-id="9548d-242">This dialog box allows you to: change the properties of profiles; create and delete profiles; specify a default profile; and specify that all agents of a specific type (such as Snapshot Agents) should use a given profile.</span></span>  
  
-   <span data-ttu-id="9548d-243">**\<AgentProfileName> 属性**</span><span class="sxs-lookup"><span data-stu-id="9548d-243">**\<AgentProfileName> Properties**</span></span>  
  
     <span data-ttu-id="9548d-244">使用此对话框可以查看和编辑配置文件中的参数设置。</span><span class="sxs-lookup"><span data-stu-id="9548d-244">This dialog box allows you to view and edit the parameter settings in a profile.</span></span>  
  
-   <span data-ttu-id="9548d-245">**新建代理配置文件**</span><span class="sxs-lookup"><span data-stu-id="9548d-245">**New Agent Profile**</span></span>  
  
     <span data-ttu-id="9548d-246">使用此对话框可以创建新的配置文件，可以选择包括现有配置文件的值。</span><span class="sxs-lookup"><span data-stu-id="9548d-246">This dialog box allows you to create a new profile, optionally including the values from an existing profile.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9548d-247">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9548d-247">See Also</span></span>  
 [<span data-ttu-id="9548d-248">监视复制</span><span class="sxs-lookup"><span data-stu-id="9548d-248">Monitoring Replication</span></span>](../monitoring-replication.md)  
  
  
