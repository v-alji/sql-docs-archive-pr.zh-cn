---
title: MSSQL_ENG014151 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014151 error
ms.assetid: 54b45e70-46b3-4c7a-a5bf-06f6dd028ceb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d2796451f6f681cfb0ce529ed44a946c34135649
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577550"
---
# <a name="mssql_eng014151"></a><span data-ttu-id="49513-102">MSSQL_ENG014151</span><span class="sxs-lookup"><span data-stu-id="49513-102">MSSQL_ENG014151</span></span>
    
## <a name="message-details"></a><span data-ttu-id="49513-103">消息详细信息</span><span class="sxs-lookup"><span data-stu-id="49513-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="49513-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="49513-104">Product Name</span></span>|<span data-ttu-id="49513-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="49513-105">SQL Server</span></span>|  
|<span data-ttu-id="49513-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="49513-106">Event ID</span></span>|<span data-ttu-id="49513-107">14151</span><span class="sxs-lookup"><span data-stu-id="49513-107">14151</span></span>|  
|<span data-ttu-id="49513-108">事件源</span><span class="sxs-lookup"><span data-stu-id="49513-108">Event Source</span></span>|<span data-ttu-id="49513-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="49513-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="49513-110">组件</span><span class="sxs-lookup"><span data-stu-id="49513-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="49513-111">符号名称</span><span class="sxs-lookup"><span data-stu-id="49513-111">Symbolic Name</span></span>||  
|<span data-ttu-id="49513-112">消息正文</span><span class="sxs-lookup"><span data-stu-id="49513-112">Message Text</span></span>|<span data-ttu-id="49513-113">复制 - %s: 代理 %s 失败。</span><span class="sxs-lookup"><span data-stu-id="49513-113">Replication-%s: agent %s failed.</span></span> <span data-ttu-id="49513-114">%s</span><span class="sxs-lookup"><span data-stu-id="49513-114">%s</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="49513-115">说明</span><span class="sxs-lookup"><span data-stu-id="49513-115">Explanation</span></span>  
 <span data-ttu-id="49513-116">此错误可由任何复制代理失败引发。</span><span class="sxs-lookup"><span data-stu-id="49513-116">This error is raised for any replication agent failure.</span></span> <span data-ttu-id="49513-117">消息结尾的文本取决于失败的上下文。</span><span class="sxs-lookup"><span data-stu-id="49513-117">The text at the end of the message depends on the context of the failure.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="49513-118">用户操作</span><span class="sxs-lookup"><span data-stu-id="49513-118">User Action</span></span>  
 <span data-ttu-id="49513-119">此错误可能在多种情况下发生；请根据需要使用下列方法：</span><span class="sxs-lookup"><span data-stu-id="49513-119">This error can occur in a number of situations; use the following approaches as necessary:</span></span>  
  
-   <span data-ttu-id="49513-120">重新启动失败的代理，以查看此代理现在是否能正常运行。</span><span class="sxs-lookup"><span data-stu-id="49513-120">Restart the failed agent to see if it will now run without failures.</span></span> <span data-ttu-id="49513-121">有关详细信息，请参阅[启动和停止复制代理 (SQL Server Management Studio)](agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) 和[复制代理可执行文件概念](concepts/replication-agent-executables-concepts.md)。</span><span class="sxs-lookup"><span data-stu-id="49513-121">For more information, see [Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;](agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) and [Replication Agent Executables Concepts](concepts/replication-agent-executables-concepts.md).</span></span>  
  
-   <span data-ttu-id="49513-122">查看代理历史记录和作业历史记录，寻找同时发生的其他错误。</span><span class="sxs-lookup"><span data-stu-id="49513-122">Check the agent history and job history for other errors that occurred around the same time.</span></span> <span data-ttu-id="49513-123">有关在复制监视器中查看代理状态和错误详细资料的信息，请参阅[使用复制监视器查看信息和执行任务](monitor/view-information-and-perform-tasks-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="49513-123">For information about viewing agent status and error details in Replication Monitor, see [View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
-   <span data-ttu-id="49513-124">验证代理所访问的各计算机之间的基本连接是否正常，然后用实用工具（如 [sqlcmd Utility](../../tools/sqlcmd-utility.md)）连接到每台计算机。</span><span class="sxs-lookup"><span data-stu-id="49513-124">Verify that basic connectivity is working between the computers accessed by the agent, and then connect to each computer with a utility like the [sqlcmd Utility](../../tools/sqlcmd-utility.md).</span></span> <span data-ttu-id="49513-125">连接时，请使用代理建立连接使用的同一帐户。</span><span class="sxs-lookup"><span data-stu-id="49513-125">When connecting, use the same account under which the agent makes connections.</span></span> <span data-ttu-id="49513-126">有关每个代理帐户所需权限的详细信息，请参阅 [Replication Agent Security Model](security/replication-agent-security-model.md)。</span><span class="sxs-lookup"><span data-stu-id="49513-126">For more information about the permissions required by each agent account, see [Replication Agent Security Model](security/replication-agent-security-model.md).</span></span>  
  
-   <span data-ttu-id="49513-127">如果在创建或应用快照发生错误时，请检查快照目录中的文件以查找错误。</span><span class="sxs-lookup"><span data-stu-id="49513-127">If the error occurs while creating or applying a snapshot, check the files in the snapshot directory for errors.</span></span>  
  
-   <span data-ttu-id="49513-128">如果错误继续出现，请增加代理的日志记录并指定日志的输出文件。</span><span class="sxs-lookup"><span data-stu-id="49513-128">If the error continues to occur, increase the logging of the agent and specify an output file for the log.</span></span> <span data-ttu-id="49513-129">此操作可能会提供找到该错误和/或其他错误消息的步骤，具体取决于错误的上下文。</span><span class="sxs-lookup"><span data-stu-id="49513-129">Depending on the context of the error, this could provide the steps leading up to the error and/or additional error messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49513-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="49513-130">See Also</span></span>  
 <span data-ttu-id="49513-131">[复制代理管理](agents/replication-agent-administration.md) </span><span class="sxs-lookup"><span data-stu-id="49513-131">[Replication Agent Administration](agents/replication-agent-administration.md) </span></span>  
 <span data-ttu-id="49513-132">[错误和事件参考（复制）](errors-and-events-reference-replication.md) </span><span class="sxs-lookup"><span data-stu-id="49513-132">[Errors and Events Reference &#40;Replication&#41;](errors-and-events-reference-replication.md) </span></span>  
 <span data-ttu-id="49513-133">[Replication Distribution Agent](agents/replication-distribution-agent.md) </span><span class="sxs-lookup"><span data-stu-id="49513-133">[Replication Distribution Agent](agents/replication-distribution-agent.md) </span></span>  
 <span data-ttu-id="49513-134">[Replication Log Reader Agent](agents/replication-log-reader-agent.md) </span><span class="sxs-lookup"><span data-stu-id="49513-134">[Replication Log Reader Agent](agents/replication-log-reader-agent.md) </span></span>  
 <span data-ttu-id="49513-135">[Replication Merge Agent](agents/replication-merge-agent.md) </span><span class="sxs-lookup"><span data-stu-id="49513-135">[Replication Merge Agent](agents/replication-merge-agent.md) </span></span>  
 <span data-ttu-id="49513-136">[复制队列读取器代理](agents/replication-queue-reader-agent.md) </span><span class="sxs-lookup"><span data-stu-id="49513-136">[Replication Queue Reader Agent](agents/replication-queue-reader-agent.md) </span></span>  
 [<span data-ttu-id="49513-137">Replication Snapshot Agent</span><span class="sxs-lookup"><span data-stu-id="49513-137">Replication Snapshot Agent</span></span>](agents/replication-snapshot-agent.md)  
  
  
