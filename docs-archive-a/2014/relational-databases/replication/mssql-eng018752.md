---
title: MSSQL_ENG018752 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG018752 error
ms.assetid: 405b2655-acb4-4e15-bcc6-b8f86bb22b37
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: fe62d540ea8e988cd4249112f196f75493a8f623
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693251"
---
# <a name="mssql_eng018752"></a><span data-ttu-id="89e24-102">MSSQL_ENG018752</span><span class="sxs-lookup"><span data-stu-id="89e24-102">MSSQL_ENG018752</span></span>
    
## <a name="message-details"></a><span data-ttu-id="89e24-103">消息详细信息</span><span class="sxs-lookup"><span data-stu-id="89e24-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="89e24-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="89e24-104">Product Name</span></span>|<span data-ttu-id="89e24-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="89e24-105">SQL Server</span></span>|  
|<span data-ttu-id="89e24-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="89e24-106">Event ID</span></span>|<span data-ttu-id="89e24-107">18752</span><span class="sxs-lookup"><span data-stu-id="89e24-107">18752</span></span>|  
|<span data-ttu-id="89e24-108">事件源</span><span class="sxs-lookup"><span data-stu-id="89e24-108">Event Source</span></span>|<span data-ttu-id="89e24-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="89e24-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="89e24-110">组件</span><span class="sxs-lookup"><span data-stu-id="89e24-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="89e24-111">符号名称</span><span class="sxs-lookup"><span data-stu-id="89e24-111">Symbolic Name</span></span>||  
|<span data-ttu-id="89e24-112">消息正文</span><span class="sxs-lookup"><span data-stu-id="89e24-112">Message Text</span></span>|<span data-ttu-id="89e24-113">一次只能有一个日志读取器代理或日志相关过程(sp_repldone、sp_replcmds 和 sp_replshowcmds)连接到某个数据库。</span><span class="sxs-lookup"><span data-stu-id="89e24-113">Only one Log Reader Agent or log-related procedure (sp_repldone, sp_replcmds, and sp_replshowcmds) can connect to a database at a time.</span></span> <span data-ttu-id="89e24-114">如果执行了一个日志相关过程，那么在启动日志读取器代理或者执行另一个日志相关过程之前，请删除执行第一个过程时所用的连接，或者在该连接上执行 sp_replflush。</span><span class="sxs-lookup"><span data-stu-id="89e24-114">If you executed a log-related procedure, drop the connection over which the procedure was executed or execute sp_replflush over that connection before starting the Log Reader Agent or executing another log-related procedure.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="89e24-115">说明</span><span class="sxs-lookup"><span data-stu-id="89e24-115">Explanation</span></span>  
 <span data-ttu-id="89e24-116">有多个当前连接正在尝试执行以下任一日志相关过程: **sp_repldone**、 **sp_replcmds**或 **sp_replshowcmds**。</span><span class="sxs-lookup"><span data-stu-id="89e24-116">More than one current connection is trying to execute any of the following: **sp_repldone**, **sp_replcmds**, or **sp_replshowcmds**.</span></span> <span data-ttu-id="89e24-117">存储过程 [sp_repldone &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-repldone-transact-sql) 和 [sp_replcmds &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replcmds-transact-sql) 是日志读取器代理用来在已发布数据库中查找和更新已复制事务的相关信息的存储过程。</span><span class="sxs-lookup"><span data-stu-id="89e24-117">The stored procedures [sp_repldone &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-repldone-transact-sql) and [sp_replcmds &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replcmds-transact-sql) are stored procedures used by the Log Reader Agent to locate and update information about replicated transactions in a published database.</span></span> <span data-ttu-id="89e24-118">存储过程 [sp_replshowcmds &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replshowcmds-transact-sql) 用于解决事务性复制发生的某些类型的问题。</span><span class="sxs-lookup"><span data-stu-id="89e24-118">The stored procedure [sp_replshowcmds &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replshowcmds-transact-sql) is used to troubleshoot certain types of issues with transactional replication.</span></span>  
  
 <span data-ttu-id="89e24-119">在以下情形下将引发此错误：</span><span class="sxs-lookup"><span data-stu-id="89e24-119">This error is raised in the following circumstances:</span></span>  
  
-   <span data-ttu-id="89e24-120">如果某个已发布数据库的日志读取器代理正在运行，而另一个日志读取器代理试图在同一个数据库上运行，则对第二个代理引发此错误，并且此错误将出现在代理历史记录中。</span><span class="sxs-lookup"><span data-stu-id="89e24-120">If the Log Reader Agent for a published database is running and a second Log Reader Agent attempts to run against the same database, the error is raised for the second agent and appears in the agent history.</span></span>  
  
     <span data-ttu-id="89e24-121">有时看起来像是有多个代理，则可能其中一个代理是执行孤立进程的结果。</span><span class="sxs-lookup"><span data-stu-id="89e24-121">In a situation where it appears there are multiple agents, it is possible that one of them is the result of an orphaned process.</span></span>  
  
-   <span data-ttu-id="89e24-122">如果启动了已发布数据库的日志读取器代理，而用户在同一个数据库上执行 **sp_repldone**、 **sp_replcmds**或 **sp_replshowcmds** ，则在执行存储过程的应用程序（如 **sqlcmd**）中将引发此错误。</span><span class="sxs-lookup"><span data-stu-id="89e24-122">If the Log Reader Agent for a published database is started and a user executes **sp_repldone**, **sp_replcmds**, or **sp_replshowcmds** against the same database, the error is raised in the application where the stored procedure was executed (such as **sqlcmd**).</span></span>  
  
-   <span data-ttu-id="89e24-123">如果已发布数据库的日志读取器代理不在运行状态，而用户在执行 **sp_repldone**、 **sp_replcmds**或 **sp_replshowcmds** 后没有关闭用于执行此过程的连接，则当日志读取器代理尝试连接到数据库时将引发此错误。</span><span class="sxs-lookup"><span data-stu-id="89e24-123">If no Log Reader Agent is running for a published database and a user executes **sp_repldone**, **sp_replcmds**, or **sp_replshowcmds** and then does not close the connection over which the procedure was executed, the error is raised when the Log Reader Agent attempts to connect to the database.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="89e24-124">用户操作</span><span class="sxs-lookup"><span data-stu-id="89e24-124">User Action</span></span>  
 <span data-ttu-id="89e24-125">以下步骤可以帮助您解决这个问题。</span><span class="sxs-lookup"><span data-stu-id="89e24-125">The following steps can help you to troubleshoot the problem.</span></span> <span data-ttu-id="89e24-126">如果任何一个步骤能正确启动日志读取器代理，则没有必要完成剩余的步骤。</span><span class="sxs-lookup"><span data-stu-id="89e24-126">If any step allows the Log Reader Agent to start without errors, there is no need to complete the remaining steps.</span></span>  
  
-   <span data-ttu-id="89e24-127">检查日志读取器代理的历史记录，查找可能导致此错误的其他任何错误。</span><span class="sxs-lookup"><span data-stu-id="89e24-127">Check the history of the Log Reader agent for any other errors that could be contributing to this error.</span></span> <span data-ttu-id="89e24-128">有关在复制监视器中查看代理状态和错误详细资料的信息，请参阅[使用复制监视器查看信息和执行任务](monitor/view-information-and-perform-tasks-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="89e24-128">For information about viewing agent status and error details in Replication Monitor, see [View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
-   <span data-ttu-id="89e24-129">检查 [sp_who &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-who-transact-sql) 的输出，查找连接到已发布数据库的具体进程标识号(SPID)。</span><span class="sxs-lookup"><span data-stu-id="89e24-129">Check the output of [sp_who &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-who-transact-sql) for specific process identification numbers (SPIDs) that are connected to the published database.</span></span> <span data-ttu-id="89e24-130">关闭所有可能运行 **sp_repldone**、 **sp_replcmds**或 **sp_replshowcmds**的连接。</span><span class="sxs-lookup"><span data-stu-id="89e24-130">Close any connections that might have run **sp_repldone**, **sp_replcmds**, or **sp_replshowcmds**.</span></span>  
  
-   <span data-ttu-id="89e24-131">重新启动日志读取器代理。</span><span class="sxs-lookup"><span data-stu-id="89e24-131">Restart the Log Reader Agent.</span></span> <span data-ttu-id="89e24-132">有关详细信息，请参阅[启动和停止复制代理 (SQL Server Management Studio)](agents/start-and-stop-a-replication-agent-sql-server-management-studio.md).</span><span class="sxs-lookup"><span data-stu-id="89e24-132">For more information, see [Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;](agents/start-and-stop-a-replication-agent-sql-server-management-studio.md).</span></span>  
  
-   <span data-ttu-id="89e24-133">在分发服务器上重新启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理服务（使之在群集中脱机或联机）。</span><span class="sxs-lookup"><span data-stu-id="89e24-133">Restart the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service (bring it offline or online in a cluster) on the Distributor.</span></span> <span data-ttu-id="89e24-134">如果计划的作业有可能在任何其他 **实例中执行了**sp_repldone **、** sp_replcmds **或** sp_replshowcmds [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，则也要为那些实例重新启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理。</span><span class="sxs-lookup"><span data-stu-id="89e24-134">If there is possibility that a scheduled job could have executed **sp_repldone**, **sp_replcmds**, or **sp_replshowcmds** from any other [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance, restart the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent for those instances as well.</span></span> <span data-ttu-id="89e24-135">有关详细信息，请参阅[启动、停止或暂停 SQL Server 代理服务](../../ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md)。</span><span class="sxs-lookup"><span data-stu-id="89e24-135">For more information, see [Start, Stop, or Pause the SQL Server Agent Service](../../ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md).</span></span>  
  
-   <span data-ttu-id="89e24-136">对发布服务器上的发布数据库执行 [sp_replflush &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replflush-transact-sql)，然后重新启动日志读取器代理。</span><span class="sxs-lookup"><span data-stu-id="89e24-136">Execute [sp_replflush &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replflush-transact-sql) at the Publisher on the publication database, and then restart the Log Reader Agent.</span></span>  
  
-   <span data-ttu-id="89e24-137">如果错误继续出现，请增加代理的日志记录并指定日志的输出文件。</span><span class="sxs-lookup"><span data-stu-id="89e24-137">If the error continues to occur, increase the logging of the agent and specify an output file for the log.</span></span> <span data-ttu-id="89e24-138">此操作可能会提供找到该错误和/或其他错误消息的步骤，具体取决于错误的上下文。</span><span class="sxs-lookup"><span data-stu-id="89e24-138">Depending on the context of the error, this could provide the steps leading up to the error and/or additional error messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89e24-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="89e24-139">See Also</span></span>  
 <span data-ttu-id="89e24-140">[错误和事件参考（复制）](errors-and-events-reference-replication.md) </span><span class="sxs-lookup"><span data-stu-id="89e24-140">[Errors and Events Reference &#40;Replication&#41;](errors-and-events-reference-replication.md) </span></span>  
 [<span data-ttu-id="89e24-141">复制日志读取器代理</span><span class="sxs-lookup"><span data-stu-id="89e24-141">Replication Log Reader Agent</span></span>](agents/replication-log-reader-agent.md)  
  
  
