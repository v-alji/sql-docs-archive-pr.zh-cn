---
title: 查看和修改复制代理命令提示符参数 (SQL Server Management Studio) |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- agents [SQL Server replication], command prompt parameters
ms.assetid: 45f2e781-c21d-4b44-8992-89f60fb3d022
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 752f674c21bb66c7b64e399e30e4917512431195
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578141"
---
# <a name="view-and-modify-replication-agent-command-prompt-parameters-sql-server-management-studio"></a><span data-ttu-id="bc1ec-102">查看和修改复制代理命令提示符参数 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="bc1ec-102">View and Modify Replication Agent Command Prompt Parameters (SQL Server Management Studio)</span></span>
  <span data-ttu-id="bc1ec-103">复制代理是接受命令行参数的可执行文件。</span><span class="sxs-lookup"><span data-stu-id="bc1ec-103">Replication agents are executables that accept command line parameters.</span></span> <span data-ttu-id="bc1ec-104">默认情况下，代理在 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 代理作业步骤下运行，因此，可以使用“作业属性 - \<Job>”对话框来查看和修改这些参数。</span><span class="sxs-lookup"><span data-stu-id="bc1ec-104">By default, agents run under [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent job steps, so these parameters can be viewed and modified using the **Job Properties - \<Job>** dialog box.</span></span> <span data-ttu-id="bc1ec-105">此对话框可通过 **的** “作业” [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 文件夹和复制监视器中的 **“代理”** 选项卡打开。</span><span class="sxs-lookup"><span data-stu-id="bc1ec-105">This dialog box is available from the **Jobs** folder in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] and from the **Agents** tab in Replication Monitor.</span></span> <span data-ttu-id="bc1ec-106">有关启动复制监视器的信息，请参阅[启动复制监视器](../monitor/start-the-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="bc1ec-106">For information about starting Replication Monitor, see [Start the Replication Monitor](../monitor/start-the-replication-monitor.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bc1ec-107">对代理参数所做的更改在下次启动代理时生效。</span><span class="sxs-lookup"><span data-stu-id="bc1ec-107">Agent parameter changes take effect the next time the agent is started.</span></span> <span data-ttu-id="bc1ec-108">如果代理连续运行，则必须停止该代理，然后重新启动。</span><span class="sxs-lookup"><span data-stu-id="bc1ec-108">If the agent runs continuously, you must stop and restart the agent.</span></span>  
  
 <span data-ttu-id="bc1ec-109">虽然可以直接修改这些参数，但通常的做法还是通过代理配置文件来修改它们。</span><span class="sxs-lookup"><span data-stu-id="bc1ec-109">Although parameters can be modified directly, it is more common to modify them through an agent profile.</span></span> <span data-ttu-id="bc1ec-110">有关详细信息，请参阅 [Replication Agent Profiles](replication-agent-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="bc1ec-110">For more information, see [Replication Agent Profiles](replication-agent-profiles.md).</span></span>  
  
 <span data-ttu-id="bc1ec-111">如果从 **“作业”** 文件夹访问代理作业，则请使用下表来确定代理作业名称和每个代理可用的参数。</span><span class="sxs-lookup"><span data-stu-id="bc1ec-111">If you access agent jobs from the **Jobs** folder, use the following table to determine the agent job name and the parameters available for each agent.</span></span>  
  
|<span data-ttu-id="bc1ec-112">代理</span><span class="sxs-lookup"><span data-stu-id="bc1ec-112">Agent</span></span>|<span data-ttu-id="bc1ec-113">作业名称</span><span class="sxs-lookup"><span data-stu-id="bc1ec-113">Job name</span></span>|<span data-ttu-id="bc1ec-114">有关参数列表，请参阅...</span><span class="sxs-lookup"><span data-stu-id="bc1ec-114">For a list of parameters, see...</span></span>|  
|-----------|--------------|------------------------------------|  
|<span data-ttu-id="bc1ec-115">快照代理</span><span class="sxs-lookup"><span data-stu-id="bc1ec-115">Snapshot Agent</span></span>|**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<integer>**|[<span data-ttu-id="bc1ec-116">Replication Snapshot Agent</span><span class="sxs-lookup"><span data-stu-id="bc1ec-116">Replication Snapshot Agent</span></span>](replication-snapshot-agent.md)|  
|<span data-ttu-id="bc1ec-117">合并发布分区的快照代理</span><span class="sxs-lookup"><span data-stu-id="bc1ec-117">Snapshot Agent for a merge publication partition</span></span>|<span data-ttu-id="bc1ec-118">Dyn_\<Publisher>-\<PublicationDatabase>-\<Publication>-\<GUID></span><span class="sxs-lookup"><span data-stu-id="bc1ec-118">**Dyn_\<Publisher>-\<PublicationDatabase>-\<Publication>-\<GUID>**</span></span>|[<span data-ttu-id="bc1ec-119">Replication Snapshot Agent</span><span class="sxs-lookup"><span data-stu-id="bc1ec-119">Replication Snapshot Agent</span></span>](replication-snapshot-agent.md)|  
|<span data-ttu-id="bc1ec-120">日志读取器代理</span><span class="sxs-lookup"><span data-stu-id="bc1ec-120">Log Reader Agent</span></span>|**\<Publisher>-\<PublicationDatabase>-\<integer>**|[<span data-ttu-id="bc1ec-121">复制日志读取器代理</span><span class="sxs-lookup"><span data-stu-id="bc1ec-121">Replication Log Reader Agent</span></span>](replication-log-reader-agent.md)|  
|<span data-ttu-id="bc1ec-122">请求订阅的合并代理</span><span class="sxs-lookup"><span data-stu-id="bc1ec-122">Merge Agent for pull subscriptions</span></span>|**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<SubscriptionDatabase>-\<integer>**|[<span data-ttu-id="bc1ec-123">Replication Merge Agent</span><span class="sxs-lookup"><span data-stu-id="bc1ec-123">Replication Merge Agent</span></span>](replication-merge-agent.md)|  
|<span data-ttu-id="bc1ec-124">推送订阅的合并代理</span><span class="sxs-lookup"><span data-stu-id="bc1ec-124">Merge Agent for push subscriptions</span></span>|**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<integer>**|[<span data-ttu-id="bc1ec-125">Replication Merge Agent</span><span class="sxs-lookup"><span data-stu-id="bc1ec-125">Replication Merge Agent</span></span>](replication-merge-agent.md)|  
|<span data-ttu-id="bc1ec-126">推送订阅的分发代理</span><span class="sxs-lookup"><span data-stu-id="bc1ec-126">Distribution Agent for push subscriptions</span></span>|<span data-ttu-id="bc1ec-127">**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<integer>** <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="bc1ec-127">**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<integer>** <sup>1</sup></span></span>|[<span data-ttu-id="bc1ec-128">Replication Distribution Agent</span><span class="sxs-lookup"><span data-stu-id="bc1ec-128">Replication Distribution Agent</span></span>](replication-distribution-agent.md)|  
|<span data-ttu-id="bc1ec-129">请求订阅的分发代理</span><span class="sxs-lookup"><span data-stu-id="bc1ec-129">Distribution Agent for pull subscriptions</span></span>|<span data-ttu-id="bc1ec-130">**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<SubscriptionDatabase>-\<GUID>** <sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="bc1ec-130">**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<SubscriptionDatabase>-\<GUID>** <sup>2</sup></span></span>|[<span data-ttu-id="bc1ec-131">Replication Distribution Agent</span><span class="sxs-lookup"><span data-stu-id="bc1ec-131">Replication Distribution Agent</span></span>](replication-distribution-agent.md)|  
|<span data-ttu-id="bc1ec-132">非 SQL Server 订阅服务器的推送订阅的分发代理</span><span class="sxs-lookup"><span data-stu-id="bc1ec-132">Distribution Agent for push subscriptions to non-SQL Server Subscribers</span></span>|**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<integer>**|[<span data-ttu-id="bc1ec-133">Replication Distribution Agent</span><span class="sxs-lookup"><span data-stu-id="bc1ec-133">Replication Distribution Agent</span></span>](replication-distribution-agent.md)|  
|<span data-ttu-id="bc1ec-134">队列读取器代理</span><span class="sxs-lookup"><span data-stu-id="bc1ec-134">Queue Reader Agent</span></span>|<span data-ttu-id="bc1ec-135">**[\<Distributor>].\<integer>**</span><span class="sxs-lookup"><span data-stu-id="bc1ec-135">**[\<Distributor>].\<integer>**</span></span>|[<span data-ttu-id="bc1ec-136">复制队列读取器代理</span><span class="sxs-lookup"><span data-stu-id="bc1ec-136">Replication Queue Reader Agent</span></span>](replication-queue-reader-agent.md)|  
  
 <span data-ttu-id="bc1ec-137"><sup>1</sup> 对于 Oracle 发布的推送订阅，它是 \*\*\<Publisher>-\<Publisher**>，而不是 \<Publisher>-\<PublicationDatabase></span><span class="sxs-lookup"><span data-stu-id="bc1ec-137"><sup>1</sup> For push subscriptions to Oracle publications, it is \*\*\<Publisher>-\<Publisher**> rather than **\<Publisher>-\<PublicationDatabase>**</span></span>  
  
 <span data-ttu-id="bc1ec-138"><sup>2</sup> 对于 Oracle 发布的请求订阅，它是 \*\*\<Publisher>-\<DistributionDatabase**>，而不是 \<Publisher>-\<PublicationDatabase></span><span class="sxs-lookup"><span data-stu-id="bc1ec-138"><sup>2</sup> For pull subscriptions to Oracle publications, it is \*\*\<Publisher>-\<DistributionDatabase**> rather than **\<Publisher>-\<PublicationDatabase>**</span></span>  
  
### <a name="to-view-and-modify-replication-agent-command-line-parameters-from-management-studio"></a><span data-ttu-id="bc1ec-139">从 Management Studio 中查看和修改复制代理命令行参数</span><span class="sxs-lookup"><span data-stu-id="bc1ec-139">To view and modify replication agent command line parameters from Management Studio</span></span>  
  
1.  <span data-ttu-id="bc1ec-140">在 [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]中连接到相应的计算机，然后展开服务器节点：</span><span class="sxs-lookup"><span data-stu-id="bc1ec-140">Connect to the appropriate computer in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], and then expand the server node:</span></span>  
  
    -   <span data-ttu-id="bc1ec-141">对于请求订阅的分发代理和合并代理，连接到订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="bc1ec-141">For the Distribution Agent and Merge Agent for pull subscriptions, connect to the Subscriber.</span></span>  
  
    -   <span data-ttu-id="bc1ec-142">对于所有其他代理，连接到分发服务器。</span><span class="sxs-lookup"><span data-stu-id="bc1ec-142">For all other agents, connect to the Distributor.</span></span>  
  
2.  <span data-ttu-id="bc1ec-143">展开 **“SQL Server 代理”** 文件夹，再展开 **“作业”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="bc1ec-143">Expand the **SQL Server Agent** folder, and then expand the **Jobs** folder.</span></span>  
  
3.  <span data-ttu-id="bc1ec-144">右键单击一个作业，然后单击 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="bc1ec-144">Right-click a job, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="bc1ec-145">在“作业属性 - \<Job>”对话框的“步骤”页上，选择步骤“运行代理”，然后单击“编辑”   。</span><span class="sxs-lookup"><span data-stu-id="bc1ec-145">On the **Steps** page of the **Job Properties - \<Job>** dialog box, select the step **Run agent**, and then click **Edit**.</span></span>  
  
5.  <span data-ttu-id="bc1ec-146">在 **“作业步骤属性 - 运行代理”** 对话框中，编辑 **“命令”** 字段。</span><span class="sxs-lookup"><span data-stu-id="bc1ec-146">In the **Job Step Properties - Run agent** dialog box, edit the **Command** field.</span></span>  
  
6.  <span data-ttu-id="bc1ec-147">在这两个对话框上单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="bc1ec-147">Click **OK** on both dialog boxes.</span></span>  
  
### <a name="to-view-and-modify-distribution-agent-and-merge-agent-command-line-parameters-from-replication-monitor"></a><span data-ttu-id="bc1ec-148">从复制监视器中查看和修改分发代理和合并代理的命令行参数</span><span class="sxs-lookup"><span data-stu-id="bc1ec-148">To view and modify Distribution Agent and Merge Agent command line parameters from Replication Monitor</span></span>  
  
1.  <span data-ttu-id="bc1ec-149">在复制监视器的左窗格中依次展开发布服务器组、发布服务器，然后单击某个发布。</span><span class="sxs-lookup"><span data-stu-id="bc1ec-149">Expand a Publisher group in the left pane of Replication Monitor, expand a Publisher, and then click a publication.</span></span>  
  
2.  <span data-ttu-id="bc1ec-150">单击 **“所有订阅”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="bc1ec-150">Click the **All Subscriptions** tab.</span></span>  
  
3.  <span data-ttu-id="bc1ec-151">右键单击订阅，然后单击 **“查看详细信息”** 。</span><span class="sxs-lookup"><span data-stu-id="bc1ec-151">Right-click a subscription, and then click **View Details**.</span></span>  
  
4.  <span data-ttu-id="bc1ec-152">在 "**订阅 \< SubscriptionName> \*\* " 窗口中，单击 "**操作**"，然后单击 " \*\* \<AgentName> 作业属性**"。</span><span class="sxs-lookup"><span data-stu-id="bc1ec-152">In the **Subscription \< SubscriptionName>** window, click **Action**, and then click **\<AgentName> Job Properties**.</span></span>  
  
5.  <span data-ttu-id="bc1ec-153">在“作业属性 - \<Job>”对话框的“步骤”页上，选择步骤“运行代理”，然后单击“编辑”   。</span><span class="sxs-lookup"><span data-stu-id="bc1ec-153">On the **Steps** page of the **Job Properties - \<Job>** dialog box, select the step **Run agent**, and then click **Edit**.</span></span>  
  
6.  <span data-ttu-id="bc1ec-154">在 **“作业步骤属性 - 运行代理”** 对话框中，编辑 **“命令”** 字段。</span><span class="sxs-lookup"><span data-stu-id="bc1ec-154">In the **Job Step Properties - Run agent** dialog box, edit the **Command** field.</span></span>  
  
7.  <span data-ttu-id="bc1ec-155">在这两个对话框上单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="bc1ec-155">Click **OK** on both dialog boxes.</span></span>  
  
### <a name="to-view-and-modify-snapshot-agent-log-reader-agent-and-queue-reader-agent-command-line-parameters-from-replication-monitor"></a><span data-ttu-id="bc1ec-156">从复制监视器中查看和修改快照代理、日志读取器代理和队列读取器代理命令行参数</span><span class="sxs-lookup"><span data-stu-id="bc1ec-156">To view and modify Snapshot Agent, Log Reader Agent, and Queue Reader Agent command line parameters from Replication Monitor</span></span>  
  
1.  <span data-ttu-id="bc1ec-157">在复制监视器的左窗格中依次展开发布服务器组、发布服务器，然后单击某个发布。</span><span class="sxs-lookup"><span data-stu-id="bc1ec-157">Expand a Publisher group in the left pane of Replication Monitor, expand a Publisher, and then click a publication.</span></span>  
  
2.  <span data-ttu-id="bc1ec-158">单击 **“代理”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="bc1ec-158">Click the **Agents** tab.</span></span>  
  
3.  <span data-ttu-id="bc1ec-159">右键单击网格中的代理，然后单击 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="bc1ec-159">Right-click an agent in the grid, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="bc1ec-160">在“作业属性 - \<Job>”对话框的“步骤”页上，选择步骤“运行代理”，然后单击“编辑”   。</span><span class="sxs-lookup"><span data-stu-id="bc1ec-160">On the **Steps** page of the **Job Properties - \<Job>** dialog box, select the step **Run agent**, and then click **Edit**.</span></span>  
  
5.  <span data-ttu-id="bc1ec-161">在 **“作业步骤属性 - 运行代理”** 对话框中，编辑 **“命令”** 字段。</span><span class="sxs-lookup"><span data-stu-id="bc1ec-161">In the **Job Step Properties - Run agent** dialog box, edit the **Command** field.</span></span>  
  
6.  <span data-ttu-id="bc1ec-162">在这两个对话框上单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="bc1ec-162">Click **OK** on both dialog boxes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc1ec-163">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bc1ec-163">See Also</span></span>  
 <span data-ttu-id="bc1ec-164">[复制代理管理](replication-agent-administration.md) </span><span class="sxs-lookup"><span data-stu-id="bc1ec-164">[Replication Agent Administration](replication-agent-administration.md) </span></span>  
 <span data-ttu-id="bc1ec-165">[复制代理可执行文件概念](../concepts/replication-agent-executables-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="bc1ec-165">[Replication Agent Executables Concepts](../concepts/replication-agent-executables-concepts.md) </span></span>  
 [<span data-ttu-id="bc1ec-166">复制代理概述</span><span class="sxs-lookup"><span data-stu-id="bc1ec-166">Replication Agents Overview</span></span>](replication-agents-overview.md)  
  
  
