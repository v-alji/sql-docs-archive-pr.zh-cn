---
title: 启动和停止复制代理 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- agents [SQL Server replication], stopping
- agents [SQL Server replication], starting
ms.assetid: 97977c4a-8c7c-4a22-9480-69aa812bd1e5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b40e329e0f04e8a54a2d5a40c30aff418da2cd65
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578142"
---
# <a name="start-and-stop-a-replication-agent-sql-server-management-studio"></a><span data-ttu-id="7d089-102">启动和停止复制代理 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="7d089-102">Start and Stop a Replication Agent (SQL Server Management Studio)</span></span>
  <span data-ttu-id="7d089-103">可以从 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 中的“作业”和“复制”文件夹以及复制监视器启动和停止代理 。</span><span class="sxs-lookup"><span data-stu-id="7d089-103">Start and stop agents from the **Jobs** folder and the **Replication** folder in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] and from Replication Monitor.</span></span> <span data-ttu-id="7d089-104">可启动和停止以下代理和作业：</span><span class="sxs-lookup"><span data-stu-id="7d089-104">Start and stop the following agents and jobs:</span></span>  
  
-   <span data-ttu-id="7d089-105">快照代理，用于所有发布。</span><span class="sxs-lookup"><span data-stu-id="7d089-105">The Snapshot Agent, which is used by all publications.</span></span>  
  
-   <span data-ttu-id="7d089-106">日志读取器代理，用于所有事务发布。</span><span class="sxs-lookup"><span data-stu-id="7d089-106">The Log Reader Agent, which is used by all transactional publications.</span></span>  
  
-   <span data-ttu-id="7d089-107">队列读取器代理，用于为排队更新订阅启用的事务发布。</span><span class="sxs-lookup"><span data-stu-id="7d089-107">The Queue Reader Agent, which is used by transactional publications enabled for queued updating subscriptions.</span></span>  
  
-   <span data-ttu-id="7d089-108">分发代理，用于同步对事务发布和快照发布的订阅。</span><span class="sxs-lookup"><span data-stu-id="7d089-108">The Distribution Agent, which synchronizes subscriptions to transactional and snapshot publications.</span></span>  
  
-   <span data-ttu-id="7d089-109">合并代理，用于同步对合并发布的订阅。</span><span class="sxs-lookup"><span data-stu-id="7d089-109">The Merge Agent, which synchronizes subscriptions to merge publications.</span></span>  
  
-   <span data-ttu-id="7d089-110">复制维护作业。</span><span class="sxs-lookup"><span data-stu-id="7d089-110">Replication maintenance jobs.</span></span>  
  
 <span data-ttu-id="7d089-111">有关启动合并代理和分发代理的详细信息，请参阅[同步推送订阅](../synchronize-a-push-subscription.md)和[同步请求订阅](../synchronize-a-pull-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="7d089-111">For more information about starting the Merge Agent and the Distribution Agent, see [Synchronize a Push Subscription](../synchronize-a-push-subscription.md) and [Synchronize a Pull Subscription](../synchronize-a-pull-subscription.md).</span></span> <span data-ttu-id="7d089-112">有关维护作业的详细信息，请参阅[运行复制维护作业 (SQL Server Management Studio)](../../../ssms/sql-server-management-studio-ssms.md)。</span><span class="sxs-lookup"><span data-stu-id="7d089-112">For more information about maintenance jobs, see [Run Replication Maintenance Jobs &#40;SQL Server Management Studio&#41;](../../../ssms/sql-server-management-studio-ssms.md).</span></span>  
  
 <span data-ttu-id="7d089-113">有关启动复制监视器的信息，请参阅[启动复制监视器](../monitor/start-the-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="7d089-113">For information about starting Replication Monitor, see [Start the Replication Monitor](../monitor/start-the-replication-monitor.md).</span></span>  
  
### <a name="to-start-and-stop-a-snapshot-agent-or-log-reader-agent-from-management-studio"></a><span data-ttu-id="7d089-114">从 Management Studio 启动和停止快照代理或日志读取器代理</span><span class="sxs-lookup"><span data-stu-id="7d089-114">To start and stop a Snapshot Agent or Log Reader Agent from Management Studio</span></span>  
  
1.  <span data-ttu-id="7d089-115">在 [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]中连接到发布服务器，然后展开服务器节点和 **“复制”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="7d089-115">Connect to the Publisher in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], and then expand the server node and the **Replication** folder.</span></span>  
  
2.  <span data-ttu-id="7d089-116">展开 **“本地发布”** 文件夹，然后右键单击发布。</span><span class="sxs-lookup"><span data-stu-id="7d089-116">Expand the **Local Publications** folder, and then right-click a publication.</span></span>  
  
3.  <span data-ttu-id="7d089-117">单击 **“查看快照代理状态”** 或 **“查看日志读取器代理状态”** 。</span><span class="sxs-lookup"><span data-stu-id="7d089-117">Click **View Snapshot Agent Status** or **View Log Reader Agent Status**.</span></span>  
  
4.  <span data-ttu-id="7d089-118">单击 **“启动”** 或 **“停止”** 。</span><span class="sxs-lookup"><span data-stu-id="7d089-118">Click **Start** or **Stop**.</span></span>  
  
### <a name="to-start-and-stop-a-queue-reader-agent-from-management-studio"></a><span data-ttu-id="7d089-119">从 Management Studio 启动和停止队列读取器代理</span><span class="sxs-lookup"><span data-stu-id="7d089-119">To start and stop a Queue Reader Agent from Management Studio</span></span>  
  
1.  <span data-ttu-id="7d089-120">在 [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]中连接到分发服务器，然后展开服务器节点。</span><span class="sxs-lookup"><span data-stu-id="7d089-120">Connect to the Distributor in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="7d089-121">展开 **“SQL Server 代理”** 文件夹，再展开 **“作业”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="7d089-121">Expand the **SQL Server Agent** folder, and then expand the **Jobs** folder.</span></span>  
  
3.  <span data-ttu-id="7d089-122">右键单击代理的作业，再单击 **“启动作业”** 或 **“停止作业”** 。</span><span class="sxs-lookup"><span data-stu-id="7d089-122">Right-click the job for the agent, and then click **Start Job** or **Stop Job**.</span></span> <span data-ttu-id="7d089-123">队列读取器代理的作业名称的格式为 [\<Distributor>].\<integer>。</span><span class="sxs-lookup"><span data-stu-id="7d089-123">The name of the job for the Queue Reader Agent is in the form **[\<Distributor>].\<integer>**.</span></span>  
  
### <a name="to-start-and-stop-a-snapshot-agent-log-reader-agent-or-queue-reader-agent-from-replication-monitor"></a><span data-ttu-id="7d089-124">从复制监视器启动和停止快照代理、日志读取器代理或队列读取器代理</span><span class="sxs-lookup"><span data-stu-id="7d089-124">To start and stop a Snapshot Agent, Log Reader Agent, or Queue Reader Agent from Replication Monitor</span></span>  
  
1.  <span data-ttu-id="7d089-125">在左窗格中展开发布服务器组，再展开其中的一个发布服务器，然后单击其中的一个发布。</span><span class="sxs-lookup"><span data-stu-id="7d089-125">Expand a Publisher group in the left pane, expand a Publisher, and then click a publication.</span></span>  
  
2.  <span data-ttu-id="7d089-126">单击 **“代理”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="7d089-126">Click the **Agents** tab.</span></span>  
  
3.  <span data-ttu-id="7d089-127">右键单击代理，再单击 **“启动代理”** 或 **“停止代理”** 。</span><span class="sxs-lookup"><span data-stu-id="7d089-127">Right-click an agent, and then click **Start Agent** or **Stop Agent**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d089-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7d089-128">See Also</span></span>  
 <span data-ttu-id="7d089-129">[监视复制](../monitoring-replication.md) </span><span class="sxs-lookup"><span data-stu-id="7d089-129">[Monitoring Replication](../monitoring-replication.md) </span></span>  
 <span data-ttu-id="7d089-130">[复制代理可执行文件概念](../concepts/replication-agent-executables-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="7d089-130">[Replication Agent Executables Concepts](../concepts/replication-agent-executables-concepts.md) </span></span>  
 [<span data-ttu-id="7d089-131">复制代理概述</span><span class="sxs-lookup"><span data-stu-id="7d089-131">Replication Agents Overview</span></span>](replication-agents-overview.md)  
  
  
