---
title: MSSQL_ENG020557 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG020557 error
ms.assetid: c43c6952-5b60-4347-b881-11a0004dce24
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 45c24d453eb95abaa967ae65ceb5934b7dee969e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591291"
---
# <a name="mssql_eng020557"></a><span data-ttu-id="b2501-102">MSSQL_ENG020557</span><span class="sxs-lookup"><span data-stu-id="b2501-102">MSSQL_ENG020557</span></span>
    
## <a name="message-details"></a><span data-ttu-id="b2501-103">消息详细信息</span><span class="sxs-lookup"><span data-stu-id="b2501-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b2501-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="b2501-104">Product Name</span></span>|<span data-ttu-id="b2501-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="b2501-105">SQL Server</span></span>|  
|<span data-ttu-id="b2501-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="b2501-106">Event ID</span></span>|<span data-ttu-id="b2501-107">20557</span><span class="sxs-lookup"><span data-stu-id="b2501-107">20557</span></span>|  
|<span data-ttu-id="b2501-108">事件源</span><span class="sxs-lookup"><span data-stu-id="b2501-108">Event Source</span></span>|<span data-ttu-id="b2501-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="b2501-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="b2501-110">组件</span><span class="sxs-lookup"><span data-stu-id="b2501-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="b2501-111">符号名称</span><span class="sxs-lookup"><span data-stu-id="b2501-111">Symbolic Name</span></span>||  
|<span data-ttu-id="b2501-112">消息正文</span><span class="sxs-lookup"><span data-stu-id="b2501-112">Message Text</span></span>|<span data-ttu-id="b2501-113">代理关闭。</span><span class="sxs-lookup"><span data-stu-id="b2501-113">Agent shutdown.</span></span> <span data-ttu-id="b2501-114">有关详细信息，请参阅作业 '%s' 的 SQL Server 代理作业历史记录。</span><span class="sxs-lookup"><span data-stu-id="b2501-114">For more information, see the SQL Server Agent job history for job '%s'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="b2501-115">说明</span><span class="sxs-lookup"><span data-stu-id="b2501-115">Explanation</span></span>  
 <span data-ttu-id="b2501-116">复制代理在没有将原因写入相应的历史记录表的情况下关闭，或代理在某个过程中关闭。</span><span class="sxs-lookup"><span data-stu-id="b2501-116">A replication agent has shut down without writing a reason to the appropriate history table, or the agent was shut down while in the middle of a process.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b2501-117">用户操作</span><span class="sxs-lookup"><span data-stu-id="b2501-117">User Action</span></span>  
  
-   <span data-ttu-id="b2501-118">重新启动代理，以查看此代理现在是否能正常运行。</span><span class="sxs-lookup"><span data-stu-id="b2501-118">Restart the agent to see whether it will now run without failures.</span></span> <span data-ttu-id="b2501-119">有关详细信息，请参阅[启动和停止复制代理 (SQL Server Management Studio)](agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) 和[复制代理可执行文件概念](concepts/replication-agent-executables-concepts.md)。</span><span class="sxs-lookup"><span data-stu-id="b2501-119">For more information, see [Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;](agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) and [Replication Agent Executables Concepts](concepts/replication-agent-executables-concepts.md).</span></span>  
  
-   <span data-ttu-id="b2501-120">查看代理历史记录和作业历史记录，寻找同时发生的其他错误。</span><span class="sxs-lookup"><span data-stu-id="b2501-120">Check the agent history and job history for other errors that occurred around the same time.</span></span> <span data-ttu-id="b2501-121">有关在如何在复制监视器中查看代理状态和错误详细资料的信息，请参阅[使用复制监视器查看信息和执行任务](monitor/view-information-and-perform-tasks-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="b2501-121">For information about how to view agent status and error details in Replication Monitor, see [View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md).</span></span>
-   <span data-ttu-id="b2501-122">验证代理所访问的各计算机之间的基本连接是否正常，然后用实用工具（如 **sqlcmd** ）连接到每台计算机。</span><span class="sxs-lookup"><span data-stu-id="b2501-122">Verify that basic connectivity is working between the computers that are accessed by the agent, and then connect to each computer by using a utility, such as the **sqlcmd** utility.</span></span> <span data-ttu-id="b2501-123">连接时，请使用代理建立连接使用的同一帐户。</span><span class="sxs-lookup"><span data-stu-id="b2501-123">When you connect, use the same account under which the agent makes connections.</span></span> <span data-ttu-id="b2501-124">有关每个代理帐户所需权限的详细信息，请参阅 [Replication Agent Security Model](security/replication-agent-security-model.md)。</span><span class="sxs-lookup"><span data-stu-id="b2501-124">For more information about the permissions that are required by each agent account, see [Replication Agent Security Model](security/replication-agent-security-model.md).</span></span>  
  
-   <span data-ttu-id="b2501-125">如果在创建或应用快照发生错误，请检查快照目录中的文件以查找错误。</span><span class="sxs-lookup"><span data-stu-id="b2501-125">If the error occurs while you are creating or applying a snapshot, check the files in the snapshot directory for errors.</span></span>  
  
-   <span data-ttu-id="b2501-126">如果错误继续出现，请增加代理的日志记录并指定日志的输出文件。</span><span class="sxs-lookup"><span data-stu-id="b2501-126">If the error continues to occur, increase the logging of the agent and specify an output file for the log.</span></span> <span data-ttu-id="b2501-127">根据错误的上下文，这可能提供导致该错误和其他错误消息的步骤。</span><span class="sxs-lookup"><span data-stu-id="b2501-127">Depending on the context of the error, this could provide the steps leading up to the error and additional error messages.</span></span> <span data-ttu-id="b2501-128">有关如何配置复制日志记录的详细信息，请参阅 Microsoft 知识库文章 [312292](https://support.microsoft.com/kb/312292)。</span><span class="sxs-lookup"><span data-stu-id="b2501-128">For more information about how to configure logging for replication, see the Microsoft Knowledge Base article [312292](https://support.microsoft.com/kb/312292).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2501-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b2501-129">See Also</span></span>  
 [<span data-ttu-id="b2501-130">错误和事件参考（复制）</span><span class="sxs-lookup"><span data-stu-id="b2501-130">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
