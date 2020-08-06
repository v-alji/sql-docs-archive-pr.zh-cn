---
title: SQL Server 复制 "分发服务器信息" 对话框 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.Distributor.Publications.f1
- sql12.rep.monitor.Distributor.commonjobs..f1
- sql12.rep.monitor.Distributor.SubscriptionSummary.merge.f1
- sql12.rep.monitor.Distributor.SubscriptionSummary.snapshot.f1
- sql12.rep.monitor.Distributor.SubscriptionSummary.tran.f1
ms.assetid: 1f499277-7f12-42ba-8cf4-52b683434944
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8ca0717a63c9660c225ec238e1e4d2423f7d01ba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578115"
---
# <a name="distributor-information-dialog-box"></a><span data-ttu-id="3f0ac-102">"分发服务器信息" 对话框</span><span class="sxs-lookup"><span data-stu-id="3f0ac-102">Distributor Information Dialog Box</span></span> 
<span data-ttu-id="3f0ac-103">本主题提供有关 "**分发服务器**" 对话框的信息</span><span class="sxs-lookup"><span data-stu-id="3f0ac-103">This topic provides information on the **Distributor** dialog box</span></span> 

## <a name="publications"></a><span data-ttu-id="3f0ac-104">发布</span><span class="sxs-lookup"><span data-stu-id="3f0ac-104">Publications</span></span>

  <span data-ttu-id="3f0ac-105">**“发布”** 选项卡提供左窗格中所选分发服务器的所有发布的摘要信息。</span><span class="sxs-lookup"><span data-stu-id="3f0ac-105">The **Publications** tab provides summary information for all publications at the Distributor that is selected in the left pane.</span></span>  
  
### <a name="options"></a><span data-ttu-id="3f0ac-106">选项</span><span class="sxs-lookup"><span data-stu-id="3f0ac-106">Options</span></span>  
 <span data-ttu-id="3f0ac-107">显示的有关分发服务器支持的发布信息包括一个列，该列包含发布服务器的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="3f0ac-107">The information that is displayed about the publications supported by the Distributor includes a column that contains the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance of the Publisher.</span></span> <span data-ttu-id="3f0ac-108">否则，发布信息与您在复制监视器的发布服务器视图中查看发布时提供的发布信息相同。</span><span class="sxs-lookup"><span data-stu-id="3f0ac-108">Otherwise, the publication information is the same as the publication information that is provided when you view publications in the Publisher view of Replication Monitor.</span></span> <span data-ttu-id="3f0ac-109">有关 **“发布”** 选项卡中的列的详细信息，请参阅 [Publisher Information, Publications](publisher-information-publications.md)。</span><span class="sxs-lookup"><span data-stu-id="3f0ac-109">For more information about the columns in the **Publications** tab, see [Publisher Information, Publications](publisher-information-publications.md).</span></span>  

## <a name="subscription-watch-list"></a><span data-ttu-id="3f0ac-110">订阅监视列表</span><span class="sxs-lookup"><span data-stu-id="3f0ac-110">Subscription watch list</span></span>

### <a name="transactional-replication"></a><span data-ttu-id="3f0ac-111">事务复制</span><span class="sxs-lookup"><span data-stu-id="3f0ac-111">Transactional replication</span></span> 
  <span data-ttu-id="3f0ac-112">用于事务订阅的信息包括发布服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="3f0ac-112">Information for transactional subscriptions includes the name of the Publisher.</span></span> <span data-ttu-id="3f0ac-113">否则，在此对话框中提供的功能和信息与发布服务器视图中的功能和信息相同。</span><span class="sxs-lookup"><span data-stu-id="3f0ac-113">Otherwise, the functionality and the information that is provided in this dialog box is the same as in the Publisher view.</span></span> <span data-ttu-id="3f0ac-114">有关如何使用此对话框的详细信息，请参阅[发布服务器信息，订阅监视列表（事务发布，SQL Server 2005 和更高版本）](publisher-information-subscription-watch-list-transactional.md)。</span><span class="sxs-lookup"><span data-stu-id="3f0ac-114">For more information about how to use this dialog box, see [Publisher Information, Subscription Watch List &#40;Transactional Publication, SQL Server 2005 and Later&#41;](publisher-information-subscription-watch-list-transactional.md).</span></span>  

### <a name="merge-replication"></a><span data-ttu-id="3f0ac-115">合并复制</span><span class="sxs-lookup"><span data-stu-id="3f0ac-115">Merge replication</span></span>
  <span data-ttu-id="3f0ac-116">用于合并发布订阅的信息包括发布服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="3f0ac-116">Information for merge publication subscriptions includes the name of the Publisher.</span></span> <span data-ttu-id="3f0ac-117">否则，在此对话框中提供的功能和信息与发布服务器视图中的功能和信息相同。</span><span class="sxs-lookup"><span data-stu-id="3f0ac-117">Otherwise, the functionality and the information that is provided in this dialog box is the same as in the Publisher view.</span></span> <span data-ttu-id="3f0ac-118">有关如何使用此对话框的详细信息，请参阅[发布服务器信息，订阅监视列表（合并发布，SQL Server 2005 和更高版本）](publisher-information-subscription-watch-list-merge-publication.md)。</span><span class="sxs-lookup"><span data-stu-id="3f0ac-118">For more information about how to use this dialog box, see [Publisher Information, Subscription Watch List &#40;Merge Publication, SQL Server 2005 and Later&#41;](publisher-information-subscription-watch-list-merge-publication.md).</span></span> 

### <a name="snapshot-replication"></a><span data-ttu-id="3f0ac-119">快照复制</span><span class="sxs-lookup"><span data-stu-id="3f0ac-119">Snapshot replication</span></span>
  <span data-ttu-id="3f0ac-120">用于快照发布订阅的信息包括发布服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="3f0ac-120">Information for snapshot publication subscriptions includes the name of the Publisher.</span></span> <span data-ttu-id="3f0ac-121">否则，在此对话框中提供的功能和信息与发布服务器视图中的功能和信息相同。</span><span class="sxs-lookup"><span data-stu-id="3f0ac-121">Otherwise, the functionality and the information that is provided in this dialog box is the same as in the Publisher view.</span></span> <span data-ttu-id="3f0ac-122">有关如何使用此对话框的详细信息，请参阅[发布服务器信息，订阅监视列表（快照发布，SQL Server 2005 和更高版本）](publisher-information-subscription-watch-list-snapshot.md)。</span><span class="sxs-lookup"><span data-stu-id="3f0ac-122">For more information about how to use this dialog box, see [Publisher Information, Subscription Watch List &#40;Snapshot Publication, SQL Server 2005 and Later&#41;](publisher-information-subscription-watch-list-snapshot.md).</span></span>  

## <a name="agents"></a><span data-ttu-id="3f0ac-123">代理</span><span class="sxs-lookup"><span data-stu-id="3f0ac-123">Agents</span></span>
  <span data-ttu-id="3f0ac-124">“代理”\*\*\*\* 选项卡显示与发布服务器和订阅服务器关联的代理和维护作业的相关信息。</span><span class="sxs-lookup"><span data-stu-id="3f0ac-124">The **Agents** tab displays information about the agents and maintenance jobs that are associated with the Publisher and Subscriber.</span></span>  
  
 <span data-ttu-id="3f0ac-125">在分发服务器视图中分发服务器的 **“代理”** 选项卡中可用的代理包括在发布服务器的 **“代理”** 选项卡中可用的所有代理。</span><span class="sxs-lookup"><span data-stu-id="3f0ac-125">The agents that are available in the **Agents** tab for a Distributor in Distributor view include all the agents that are available in the **Agents** tab for a Publisher.</span></span> <span data-ttu-id="3f0ac-126">不过，分发服务器视图中分发服务器的 **“代理”** 选项卡还包括一个分发服务器代理和一个合并代理。</span><span class="sxs-lookup"><span data-stu-id="3f0ac-126">However, the **Agents** tab for a Distributor in Distributor view also includes a Distributor Agent and a Merge Agent.</span></span>  
  
 <span data-ttu-id="3f0ac-127">有关快照代理、日志读取器代理和队列读取器代理的详细信息，请参阅 [Publisher Information, Agents](publisher-information-agents.md)。</span><span class="sxs-lookup"><span data-stu-id="3f0ac-127">For more information about the Snapshot, Log Reader, and Queue Reader agents, and maintenance jobs, see [Publisher Information, Agents](publisher-information-agents.md).</span></span> <span data-ttu-id="3f0ac-128">请注意，当您查看分发服务器的 **“代理”** 选项卡上的代理信息时，将提供快照代理和日志读取器代理的发布服务器信息。</span><span class="sxs-lookup"><span data-stu-id="3f0ac-128">Notice that when you are viewing agent information on the **Agents** tab for a Distributor, Publisher information is present for the Snapshot and Log Reader agents.</span></span> <span data-ttu-id="3f0ac-129">不过，在分发服务器视图中分发服务器的 **“代理”** 选项卡中，您还可以选择 **“分发服务器代理”** 和 **“合并代理”**。</span><span class="sxs-lookup"><span data-stu-id="3f0ac-129">However, in the **Agents** tab for a Distributor in Distributor view, you can also select **Distributor Agent** and **Merge Agent**.</span></span>  
  
### <a name="options"></a><span data-ttu-id="3f0ac-130">选项</span><span class="sxs-lookup"><span data-stu-id="3f0ac-130">Options</span></span>  
 <span data-ttu-id="3f0ac-131">以下各节说明了此选项卡上为分发服务器代理和合并代理显示的数据。</span><span class="sxs-lookup"><span data-stu-id="3f0ac-131">The following sections describe the data that is displayed on this tab for the Distributor Agent and Merge Agent.</span></span>  
  
### <a name="distributor-agent"></a><span data-ttu-id="3f0ac-132">“分发服务器代理”</span><span class="sxs-lookup"><span data-stu-id="3f0ac-132">Distributor Agent</span></span>  
 <span data-ttu-id="3f0ac-133">**Status**</span><span class="sxs-lookup"><span data-stu-id="3f0ac-133">**Status**</span></span>  
 <span data-ttu-id="3f0ac-134">此代理的状态。</span><span class="sxs-lookup"><span data-stu-id="3f0ac-134">The status of the agent.</span></span> <span data-ttu-id="3f0ac-135">下面列出了可能的状态值：</span><span class="sxs-lookup"><span data-stu-id="3f0ac-135">The following list shows the possible status values:</span></span>  
  
-   <span data-ttu-id="3f0ac-136">错误</span><span class="sxs-lookup"><span data-stu-id="3f0ac-136">Error</span></span>    
-   <span data-ttu-id="3f0ac-137">重试</span><span class="sxs-lookup"><span data-stu-id="3f0ac-137">Retry</span></span>    
-   <span data-ttu-id="3f0ac-138">正在运行</span><span class="sxs-lookup"><span data-stu-id="3f0ac-138">Running</span></span>    
-   <span data-ttu-id="3f0ac-139">未运行</span><span class="sxs-lookup"><span data-stu-id="3f0ac-139">Not Running</span></span>    
-   <span data-ttu-id="3f0ac-140">从未启动</span><span class="sxs-lookup"><span data-stu-id="3f0ac-140">Never started</span></span>  
  
 <span data-ttu-id="3f0ac-141">**发布者**</span><span class="sxs-lookup"><span data-stu-id="3f0ac-141">**Publisher**</span></span>  
 <span data-ttu-id="3f0ac-142">发布服务器的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="3f0ac-142">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance of the Publisher.</span></span>  
  
 <span data-ttu-id="3f0ac-143">**发布**</span><span class="sxs-lookup"><span data-stu-id="3f0ac-143">**Publication**</span></span>  
 <span data-ttu-id="3f0ac-144">与此代理关联的发布的名称。</span><span class="sxs-lookup"><span data-stu-id="3f0ac-144">The name of the publication with which the agent is associated.</span></span>  
  
 <span data-ttu-id="3f0ac-145">**订阅**</span><span class="sxs-lookup"><span data-stu-id="3f0ac-145">**Subscription**</span></span>  
 <span data-ttu-id="3f0ac-146">订阅的名称，格式为：[*SubscriberName*].[*Database*]。</span><span class="sxs-lookup"><span data-stu-id="3f0ac-146">The name of the subscription, in the form: [*SubscriberName*].[*Database*].</span></span>  
  
 <span data-ttu-id="3f0ac-147">**Type**</span><span class="sxs-lookup"><span data-stu-id="3f0ac-147">**Type**</span></span>  
 <span data-ttu-id="3f0ac-148">复制的类型：推送、请求或匿名。</span><span class="sxs-lookup"><span data-stu-id="3f0ac-148">Type of replication: push, pull, or Anonymous.</span></span>  
  
 <span data-ttu-id="3f0ac-149">**上次启动时间**</span><span class="sxs-lookup"><span data-stu-id="3f0ac-149">**Last Start Time**</span></span>  
 <span data-ttu-id="3f0ac-150">上次启动此代理的时间。</span><span class="sxs-lookup"><span data-stu-id="3f0ac-150">The last time at which the agent started.</span></span>  
  
 <span data-ttu-id="3f0ac-151">**持续时间**</span><span class="sxs-lookup"><span data-stu-id="3f0ac-151">**Duration**</span></span>  
 <span data-ttu-id="3f0ac-152">此代理已经运行的时间长度。</span><span class="sxs-lookup"><span data-stu-id="3f0ac-152">The length of time that the agent has run.</span></span> <span data-ttu-id="3f0ac-153">如果此代理当前正在运行，该时间表示已运行的时间；如果此代理之前已运行完毕，则该时间表示总时间。</span><span class="sxs-lookup"><span data-stu-id="3f0ac-153">The time represents elapsed time if the agent is currently running, and total time if the agent has run previously.</span></span>  
  
 <span data-ttu-id="3f0ac-154">**上一操作**</span><span class="sxs-lookup"><span data-stu-id="3f0ac-154">**Last Action**</span></span>  
 <span data-ttu-id="3f0ac-155">在此代理最近一次运行的过程中最后执行的操作。</span><span class="sxs-lookup"><span data-stu-id="3f0ac-155">The last action that was performed during the most recent run of the agent.</span></span>  
  
 <span data-ttu-id="3f0ac-156">**传送速率**</span><span class="sxs-lookup"><span data-stu-id="3f0ac-156">**Delivery Rate**</span></span>  
 <span data-ttu-id="3f0ac-157">在此代理最近一次运行期间分发数据库中提交初始化命令的速率，以每秒的命令数表示。</span><span class="sxs-lookup"><span data-stu-id="3f0ac-157">The rate, in commands per second, at which initialization commands are committed in the distribution database during the most recent run of the agent.</span></span>  
  
 <span data-ttu-id="3f0ac-158">**延迟**</span><span class="sxs-lookup"><span data-stu-id="3f0ac-158">**Latency**</span></span>  
 <span data-ttu-id="3f0ac-159">从在发布数据库中提交最近的更改到在分发数据库中提交对应的命令经过的时间，以秒为单位。</span><span class="sxs-lookup"><span data-stu-id="3f0ac-159">The time, in seconds, that has elapsed between the most recent change being committed in the publication database, and the corresponding command being committed in the distribution database.</span></span>  
  
 <span data-ttu-id="3f0ac-160">**事务数**</span><span class="sxs-lookup"><span data-stu-id="3f0ac-160">**#Trans**</span></span>  
 <span data-ttu-id="3f0ac-161">在此代理最近一次运行期间分发数据库中提交的事务数。</span><span class="sxs-lookup"><span data-stu-id="3f0ac-161">The number of transactions committed in the distribution database during the most recent run of the agent.</span></span>  
  
 <span data-ttu-id="3f0ac-162">**命令数**</span><span class="sxs-lookup"><span data-stu-id="3f0ac-162">**#Cmds**</span></span>  
 <span data-ttu-id="3f0ac-163">在此代理最近一次运行期间分发数据库中提交的命令数。</span><span class="sxs-lookup"><span data-stu-id="3f0ac-163">The number of commands committed in the distribution database during the most recent run of the agent.</span></span> <span data-ttu-id="3f0ac-164">一个命令与一次数据更改（如一次更新）相同。</span><span class="sxs-lookup"><span data-stu-id="3f0ac-164">A command is the same as a data change, such as an update.</span></span>  
  
 <span data-ttu-id="3f0ac-165">**平均命令数**</span><span class="sxs-lookup"><span data-stu-id="3f0ac-165">**Avg. #Cmds**</span></span>  
 <span data-ttu-id="3f0ac-166">在此代理最近一次运行期间平均每个事务的命令数。</span><span class="sxs-lookup"><span data-stu-id="3f0ac-166">The average number of commands per transaction during the most recent run of the agent.</span></span>  
  
### <a name="merge-agent"></a><span data-ttu-id="3f0ac-167">合并代理</span><span class="sxs-lookup"><span data-stu-id="3f0ac-167">Merge Agent</span></span>  
 <span data-ttu-id="3f0ac-168">**Status**</span><span class="sxs-lookup"><span data-stu-id="3f0ac-168">**Status**</span></span>  
 <span data-ttu-id="3f0ac-169">此代理的状态。</span><span class="sxs-lookup"><span data-stu-id="3f0ac-169">The status of the agent.</span></span> <span data-ttu-id="3f0ac-170">下面列出了可能的状态值：</span><span class="sxs-lookup"><span data-stu-id="3f0ac-170">The following list shows the possible status values:</span></span>  
  
-   <span data-ttu-id="3f0ac-171">错误</span><span class="sxs-lookup"><span data-stu-id="3f0ac-171">Error</span></span>    
-   <span data-ttu-id="3f0ac-172">重试</span><span class="sxs-lookup"><span data-stu-id="3f0ac-172">Retry</span></span>    
-   <span data-ttu-id="3f0ac-173">正在运行</span><span class="sxs-lookup"><span data-stu-id="3f0ac-173">Running</span></span>    
-   <span data-ttu-id="3f0ac-174">未运行</span><span class="sxs-lookup"><span data-stu-id="3f0ac-174">Not Running</span></span>    
-   <span data-ttu-id="3f0ac-175">从未启动</span><span class="sxs-lookup"><span data-stu-id="3f0ac-175">Never started</span></span>  
  
 <span data-ttu-id="3f0ac-176">**发布者**</span><span class="sxs-lookup"><span data-stu-id="3f0ac-176">**Publisher**</span></span>  
 <span data-ttu-id="3f0ac-177">发布服务器的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="3f0ac-177">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance of the Publisher.</span></span>  
  
 <span data-ttu-id="3f0ac-178">**发布**</span><span class="sxs-lookup"><span data-stu-id="3f0ac-178">**Publication**</span></span>  
 <span data-ttu-id="3f0ac-179">与此代理关联的发布的名称。</span><span class="sxs-lookup"><span data-stu-id="3f0ac-179">The name of the publication with which the agent is associated.</span></span>  
  
 <span data-ttu-id="3f0ac-180">**订阅**</span><span class="sxs-lookup"><span data-stu-id="3f0ac-180">**Subscription**</span></span>  
 <span data-ttu-id="3f0ac-181">订阅的名称，格式为：[*SubscriberName*].[*Database*]。</span><span class="sxs-lookup"><span data-stu-id="3f0ac-181">The name of the subscription, in the form: [*SubscriberName*].[*Database*].</span></span>  
  
 <span data-ttu-id="3f0ac-182">**Type**</span><span class="sxs-lookup"><span data-stu-id="3f0ac-182">**Type**</span></span>  
 <span data-ttu-id="3f0ac-183">复制的类型：推送、请求或匿名。</span><span class="sxs-lookup"><span data-stu-id="3f0ac-183">Type of replication: push, pull, or Anonymous.</span></span>  
  
 <span data-ttu-id="3f0ac-184">**上次启动时间**</span><span class="sxs-lookup"><span data-stu-id="3f0ac-184">**Last Start Time**</span></span>  
 <span data-ttu-id="3f0ac-185">上次启动此代理的时间。</span><span class="sxs-lookup"><span data-stu-id="3f0ac-185">The last time at which the agent started.</span></span>  
  
 <span data-ttu-id="3f0ac-186">**持续时间**</span><span class="sxs-lookup"><span data-stu-id="3f0ac-186">**Duration**</span></span>  
 <span data-ttu-id="3f0ac-187">此代理已经运行的时间长度。</span><span class="sxs-lookup"><span data-stu-id="3f0ac-187">The length of time that the agent has run.</span></span> <span data-ttu-id="3f0ac-188">如果此代理当前正在运行，该时间表示已运行的时间；如果此代理之前已运行完毕，则该时间表示总时间。</span><span class="sxs-lookup"><span data-stu-id="3f0ac-188">The time represents elapsed time if the agent is currently running, and total time if the agent has run previously.</span></span>  
  
 <span data-ttu-id="3f0ac-189">**上一操作**</span><span class="sxs-lookup"><span data-stu-id="3f0ac-189">**Last Action**</span></span>  
 <span data-ttu-id="3f0ac-190">在此代理最近一次运行的过程中最后执行的操作。</span><span class="sxs-lookup"><span data-stu-id="3f0ac-190">The last action that was performed during the most recent run of the agent.</span></span>  
  
 <span data-ttu-id="3f0ac-191">**传送速率**</span><span class="sxs-lookup"><span data-stu-id="3f0ac-191">**Delivery Rate**</span></span>  
 <span data-ttu-id="3f0ac-192">在分发数据库中提交更改的速率，以每秒的命令数为单位。</span><span class="sxs-lookup"><span data-stu-id="3f0ac-192">The rate, in commands per second, at which changes are committed in the distribution database.</span></span>  
  
 <span data-ttu-id="3f0ac-193">**发布服务器插入**</span><span class="sxs-lookup"><span data-stu-id="3f0ac-193">**Publisher Inserts**</span></span>  
 <span data-ttu-id="3f0ac-194">发布服务器上应用的 INSERT 命令数。</span><span class="sxs-lookup"><span data-stu-id="3f0ac-194">Number of INSERT commands applied at the Publisher.</span></span>  
  
 <span data-ttu-id="3f0ac-195">**发布服务器更新**</span><span class="sxs-lookup"><span data-stu-id="3f0ac-195">**Publisher Updates**</span></span>  
 <span data-ttu-id="3f0ac-196">发布服务器上应用的 UPDATE 命令数。</span><span class="sxs-lookup"><span data-stu-id="3f0ac-196">Number of UPDATE commands applied at the Publisher.</span></span>  
  
 <span data-ttu-id="3f0ac-197">**发布服务器删除**</span><span class="sxs-lookup"><span data-stu-id="3f0ac-197">**Publisher Deletes**</span></span>  
 <span data-ttu-id="3f0ac-198">发布服务器上应用的 DELETE 命令数。</span><span class="sxs-lookup"><span data-stu-id="3f0ac-198">Number of DELETE commands applied at the Publisher.</span></span>  
  
 <span data-ttu-id="3f0ac-199">**发布服务器冲突**</span><span class="sxs-lookup"><span data-stu-id="3f0ac-199">**Publisher Conflicts**</span></span>  
 <span data-ttu-id="3f0ac-200">合并过程中发布服务器上发生的冲突数。</span><span class="sxs-lookup"><span data-stu-id="3f0ac-200">The number of conflicts occurring at the Publisher during the merge process.</span></span>  
  
 <span data-ttu-id="3f0ac-201">**订阅服务器插入**</span><span class="sxs-lookup"><span data-stu-id="3f0ac-201">**Subscriber Inserts**</span></span>  
 <span data-ttu-id="3f0ac-202">订阅服务器上应用的 INSERT 命令数。</span><span class="sxs-lookup"><span data-stu-id="3f0ac-202">Number of INSERT commands applied at the Subscriber.</span></span>  
  
 <span data-ttu-id="3f0ac-203">**订阅服务器更新**</span><span class="sxs-lookup"><span data-stu-id="3f0ac-203">**Subscriber Updates**</span></span>  
 <span data-ttu-id="3f0ac-204">订阅服务器上应用的 UPDATE 命令数。</span><span class="sxs-lookup"><span data-stu-id="3f0ac-204">Number of UPDATE commands applied at the Subscriber.</span></span>  
  
 <span data-ttu-id="3f0ac-205">**订阅服务器删除**</span><span class="sxs-lookup"><span data-stu-id="3f0ac-205">**Subscriber Deletes**</span></span>  
 <span data-ttu-id="3f0ac-206">订阅服务器上应用的 DELETE 命令数。</span><span class="sxs-lookup"><span data-stu-id="3f0ac-206">Number of DELETE commands applied at the Subscriber.</span></span>  
  
 <span data-ttu-id="3f0ac-207">**订阅服务器冲突**</span><span class="sxs-lookup"><span data-stu-id="3f0ac-207">**Subscriber Conflicts**</span></span>  
 <span data-ttu-id="3f0ac-208">合并过程中订阅服务器上发生的冲突数。</span><span class="sxs-lookup"><span data-stu-id="3f0ac-208">The number of conflicts occurring at the Subscriber during the merge process.</span></span>  
  
 
## <a name="see-also"></a><span data-ttu-id="3f0ac-209">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3f0ac-209">See Also</span></span>  
 <span data-ttu-id="3f0ac-210">[启动复制监视器](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="3f0ac-210">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 [<span data-ttu-id="3f0ac-211">监视复制</span><span class="sxs-lookup"><span data-stu-id="3f0ac-211">Monitoring Replication</span></span>](monitoring-replication.md)  
  
  
