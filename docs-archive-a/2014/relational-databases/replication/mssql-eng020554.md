---
title: MSSQL_ENG020554 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG020554 error
ms.assetid: ef1a1b88-b2ab-43e8-99cd-163a973262d6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b48714f19fdec520c7bd20e4d8598d491f6e1908
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690548"
---
# <a name="mssql_eng020554"></a><span data-ttu-id="9d9a1-102">MSSQL_ENG020554</span><span class="sxs-lookup"><span data-stu-id="9d9a1-102">MSSQL_ENG020554</span></span>
    
## <a name="message-details"></a><span data-ttu-id="9d9a1-103">消息详细信息</span><span class="sxs-lookup"><span data-stu-id="9d9a1-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9d9a1-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="9d9a1-104">Product Name</span></span>|<span data-ttu-id="9d9a1-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="9d9a1-105">SQL Server</span></span>|  
|<span data-ttu-id="9d9a1-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="9d9a1-106">Event ID</span></span>|<span data-ttu-id="9d9a1-107">20554</span><span class="sxs-lookup"><span data-stu-id="9d9a1-107">20554</span></span>|  
|<span data-ttu-id="9d9a1-108">事件源</span><span class="sxs-lookup"><span data-stu-id="9d9a1-108">Event Source</span></span>|<span data-ttu-id="9d9a1-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="9d9a1-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="9d9a1-110">组件</span><span class="sxs-lookup"><span data-stu-id="9d9a1-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="9d9a1-111">符号名称</span><span class="sxs-lookup"><span data-stu-id="9d9a1-111">Symbolic Name</span></span>||  
|<span data-ttu-id="9d9a1-112">消息正文</span><span class="sxs-lookup"><span data-stu-id="9d9a1-112">Message Text</span></span>|<span data-ttu-id="9d9a1-113">复制代理在 %ld 分钟内没有记录任何进度消息。</span><span class="sxs-lookup"><span data-stu-id="9d9a1-113">The replication agent has not logged a progress message in %ld minutes.</span></span> <span data-ttu-id="9d9a1-114">这表明代理已停止响应或系统活动过多。</span><span class="sxs-lookup"><span data-stu-id="9d9a1-114">This might indicate an unresponsive agent or high system activity.</span></span> <span data-ttu-id="9d9a1-115">请确保正在将记录复制到目标，并且与订阅服务器、发布服务器和分发服务器的连接仍然是活动的。</span><span class="sxs-lookup"><span data-stu-id="9d9a1-115">Verify that records are being replicated to the destination and that connections to the Subscriber, Publisher, and Distributor are still active.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="9d9a1-116">说明</span><span class="sxs-lookup"><span data-stu-id="9d9a1-116">Explanation</span></span>  
 <span data-ttu-id="9d9a1-117">复制代理检查  作业以指定的时间间隔运行（默认为 10 分钟），检查每个复制代理的状态。</span><span class="sxs-lookup"><span data-stu-id="9d9a1-117">The **Replication agents checkup** job runs at a specified interval (10 minutes by default) to check on the status of each replication agent.</span></span> <span data-ttu-id="9d9a1-118">如果自上次代理检查作业运行后，代理未记录任何进度消息，将引发错误 MSSQL_ENG020554。</span><span class="sxs-lookup"><span data-stu-id="9d9a1-118">If an agent has not logged any progress messages since the last time the agent checkup job ran, error MSSQL_ENG020554 can be raised.</span></span> <span data-ttu-id="9d9a1-119">即使未发生其他复制活动，代理至少应该记录历史记录消息。</span><span class="sxs-lookup"><span data-stu-id="9d9a1-119">The agent is expected at least to log history messages even if no other replication activity is occurring.</span></span> <span data-ttu-id="9d9a1-120">虽然复制代理未按预期响应，但其未必已停止或失败（如果代理失败，将引发错误 MSSQL_ENG020536）。</span><span class="sxs-lookup"><span data-stu-id="9d9a1-120">Although the replication agent is not responding as expected, it has not necessarily stopped or failed (if an agent has failed, error MSSQL_ENG020536 should be raised).</span></span>  
  
 <span data-ttu-id="9d9a1-121">下列问题可导致引发错误 MSSQL_ENG020554：</span><span class="sxs-lookup"><span data-stu-id="9d9a1-121">The following issues can cause error MSSQL_ENG020554 to be raised:</span></span>  
  
-   <span data-ttu-id="9d9a1-122">代理正忙。</span><span class="sxs-lookup"><span data-stu-id="9d9a1-122">The agent is busy.</span></span>  
  
     <span data-ttu-id="9d9a1-123">当代理检查作业轮询时，如果代理因为过于繁忙而无法响应，则代理检查作业无法报告复制代理运行是否正常。</span><span class="sxs-lookup"><span data-stu-id="9d9a1-123">If the agent is too busy to respond when polled by the agent checkup job, the agent checkup job cannot report whether the replication agent is functioning properly.</span></span> <span data-ttu-id="9d9a1-124">有很多原因可导致复制代理忙：可能有大量数据正在复制，或者由于应用程序设计或配置问题而导致进程长时间运行。</span><span class="sxs-lookup"><span data-stu-id="9d9a1-124">There are a number of reasons why the replication agent could be busy: there might be a lot of data being replicated, or there might be application design or configuration issues that result in processes that run for a long time.</span></span>  
  
-   <span data-ttu-id="9d9a1-125">代理无法登录到拓扑中的某台计算机。</span><span class="sxs-lookup"><span data-stu-id="9d9a1-125">The agent cannot log in to one of the computers in the topology.</span></span>  
  
     <span data-ttu-id="9d9a1-126">所有代理都有参数 **-LoginTimeOut** （默认设置为 15 秒），此参数管理代理尝试登录到复制节点的所用时间，如合并代理登录到发布服务器。</span><span class="sxs-lookup"><span data-stu-id="9d9a1-126">All agents have a parameter **-LoginTimeOut** (set to 15 seconds by default), which governs how long an agent attempts to log in to a replication node, such as a Merge Agent logging in to the Publisher.</span></span> <span data-ttu-id="9d9a1-127">如果将 **-LoginTimeOut** 值设置为高于复制代理检查作业运行的时间间隔，则登录问题可能是导致该错误的根本原因：错误 MSSQL_ENG020554 引发后，该代理才会引发更具体的错误。</span><span class="sxs-lookup"><span data-stu-id="9d9a1-127">If the **-LoginTimeOut** value is set higher than the interval at which the replication agent checkup job runs, a login problem could be the root cause of the error: error MSSQL_ENG020554 is raised before the agent is able to raise a more specific error.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="9d9a1-128">用户操作</span><span class="sxs-lookup"><span data-stu-id="9d9a1-128">User Action</span></span>  
 <span data-ttu-id="9d9a1-129">所需操作取决于错误的原因：</span><span class="sxs-lookup"><span data-stu-id="9d9a1-129">The action required depends on the cause of the error:</span></span>  
  
-   <span data-ttu-id="9d9a1-130">对于引发此错误的所有情况：</span><span class="sxs-lookup"><span data-stu-id="9d9a1-130">For all cases in which this error is raised:</span></span>  
  
     <span data-ttu-id="9d9a1-131">检查复制监视器中的错误详细信息，如果代理已停止，请重新启动它。</span><span class="sxs-lookup"><span data-stu-id="9d9a1-131">Check the error details in Replication Monitor, and then restart the agent if it has stopped.</span></span> <span data-ttu-id="9d9a1-132">错误详细信息可能提供关于代理为何无法正常运行的附加信息。</span><span class="sxs-lookup"><span data-stu-id="9d9a1-132">The error details might provide additional information on why the agent was not running properly.</span></span> <span data-ttu-id="9d9a1-133">如果代理正在运行，请不要停止和重新启动代理，因为这样会使问题恶化。</span><span class="sxs-lookup"><span data-stu-id="9d9a1-133">If the agent is running, do not stop and restart the agent, because that can exacerbate the problem.</span></span> <span data-ttu-id="9d9a1-134">有关在复制监视器中查看代理状态和错误详细资料的信息，请参阅以下主题：</span><span class="sxs-lookup"><span data-stu-id="9d9a1-134">For information about viewing agent status and error details in Replication Monitor, see the following topics:</span></span>  
  
    -   <span data-ttu-id="9d9a1-135">有关快照代理、日志读取器代理和队列读取器代理，请参阅[使用复制监视器查看信息和执行任务](monitor/view-information-and-perform-tasks-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="9d9a1-135">For the Snapshot Agent, Log Reader Agent, and Queue Reader Agent, see [View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
    -   <span data-ttu-id="9d9a1-136">有关分发代理和合并代理，请参阅[使用复制监视器查看信息和执行任务](monitor/view-information-and-perform-tasks-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="9d9a1-136">For the Distribution Agent and Merge Agent, see [View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
-   <span data-ttu-id="9d9a1-137">如果由于代理忙而频频引发此错误：</span><span class="sxs-lookup"><span data-stu-id="9d9a1-137">If this error is raised frequently because the agent is busy:</span></span>  
  
     <span data-ttu-id="9d9a1-138">可能需要重新设计应用程序，以便减少代理进行处理所花费的时间。</span><span class="sxs-lookup"><span data-stu-id="9d9a1-138">You might need to redesign your application so that the agent spends less time processing.</span></span>  
  
     <span data-ttu-id="9d9a1-139">可以通过 **“作业属性”** 对话框来加大检查代理状态的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="9d9a1-139">You can increase the interval at which agent status is checked using the **Job Properties** dialog box.</span></span> <span data-ttu-id="9d9a1-140">有关访问此对话框以获取复制作业的信息，请参阅[使用复制监视器查看信息和执行任务](monitor/view-information-and-perform-tasks-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="9d9a1-140">For information about accessing this dialog box for replication jobs, see [View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
-   <span data-ttu-id="9d9a1-141">如果代理无法登录到拓扑中的某台计算机：</span><span class="sxs-lookup"><span data-stu-id="9d9a1-141">If an agent cannot log in to one of the computers in the topology:</span></span>  
  
     <span data-ttu-id="9d9a1-142">建议将 **-LoginTimeOut** 的值设置为低于复制代理检查作业运行的时间间隔值。</span><span class="sxs-lookup"><span data-stu-id="9d9a1-142">We recommend that the **-LoginTimeOut** value be set lower than the interval at which the replication agent checkup job runs.</span></span> <span data-ttu-id="9d9a1-143">在某些情况下，由于导致登录超时的网络问题，需要将 **-LoginTimeOut** 的值设置得更高。如果将 **-LoginTimeOut** 设置得较低，复制会报告更为具体的错误，使你可以解决可能因权限、网络问题或其他问题而导致的登录问题。</span><span class="sxs-lookup"><span data-stu-id="9d9a1-143">In some cases, the value for **-LoginTimeOut** is set higher because of network issues that cause logins to time out. If the **-LoginTimeOut** is set lower, replication can report more specific errors, allowing you to troubleshoot login problems that could be caused by permissions, network problems, or other issues.</span></span> <span data-ttu-id="9d9a1-144">代理参数可以在代理配置文件和命令行中指定。</span><span class="sxs-lookup"><span data-stu-id="9d9a1-144">Agent parameters can be specified in agent profiles and on the command line.</span></span> <span data-ttu-id="9d9a1-145">有关详细信息，请参阅：</span><span class="sxs-lookup"><span data-stu-id="9d9a1-145">For more information, see:</span></span>  
  
    -   [<span data-ttu-id="9d9a1-146">处理复制代理配置文件</span><span class="sxs-lookup"><span data-stu-id="9d9a1-146">Work with Replication Agent Profiles</span></span>](agents/replication-agent-profiles.md)  
  
    -   [<span data-ttu-id="9d9a1-147">查看和修改复制代理命令提示符参数 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="9d9a1-147">View and Modify Replication Agent Command Prompt Parameters &#40;SQL Server Management Studio&#41;</span></span>](agents/view-and-modify-replication-agent-command-prompt-parameters.md)  
  
    -   <span data-ttu-id="9d9a1-148">[Replication Agent Executables Concepts](concepts/replication-agent-executables-concepts.md)的最小和最大内存量。</span><span class="sxs-lookup"><span data-stu-id="9d9a1-148">[Replication Agent Executables Concepts](concepts/replication-agent-executables-concepts.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d9a1-149">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9d9a1-149">See Also</span></span>  
 <span data-ttu-id="9d9a1-150">[复制代理管理](agents/replication-agent-administration.md) </span><span class="sxs-lookup"><span data-stu-id="9d9a1-150">[Replication Agent Administration](agents/replication-agent-administration.md) </span></span>  
 <span data-ttu-id="9d9a1-151">[错误和事件参考（复制）](errors-and-events-reference-replication.md) </span><span class="sxs-lookup"><span data-stu-id="9d9a1-151">[Errors and Events Reference &#40;Replication&#41;](errors-and-events-reference-replication.md) </span></span>  
 <span data-ttu-id="9d9a1-152">[Replication Distribution Agent](agents/replication-distribution-agent.md) </span><span class="sxs-lookup"><span data-stu-id="9d9a1-152">[Replication Distribution Agent](agents/replication-distribution-agent.md) </span></span>  
 <span data-ttu-id="9d9a1-153">[Replication Log Reader Agent](agents/replication-log-reader-agent.md) </span><span class="sxs-lookup"><span data-stu-id="9d9a1-153">[Replication Log Reader Agent](agents/replication-log-reader-agent.md) </span></span>  
 <span data-ttu-id="9d9a1-154">[Replication Merge Agent](agents/replication-merge-agent.md) </span><span class="sxs-lookup"><span data-stu-id="9d9a1-154">[Replication Merge Agent](agents/replication-merge-agent.md) </span></span>  
 <span data-ttu-id="9d9a1-155">[复制队列读取器代理](agents/replication-queue-reader-agent.md) </span><span class="sxs-lookup"><span data-stu-id="9d9a1-155">[Replication Queue Reader Agent](agents/replication-queue-reader-agent.md) </span></span>  
 [<span data-ttu-id="9d9a1-156">Replication Snapshot Agent</span><span class="sxs-lookup"><span data-stu-id="9d9a1-156">Replication Snapshot Agent</span></span>](agents/replication-snapshot-agent.md)  
  
  
