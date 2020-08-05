---
title: MSSQL_ENG014152 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014152 error
ms.assetid: 4215e2b1-cd30-441f-9671-9afc742adf6e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 615b9cf2996653d86c44d6e43a83e01e8287b110
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580693"
---
# <a name="mssql_eng014152"></a><span data-ttu-id="a5553-102">MSSQL_ENG014152</span><span class="sxs-lookup"><span data-stu-id="a5553-102">MSSQL_ENG014152</span></span>
    
## <a name="message-details"></a><span data-ttu-id="a5553-103">消息详细信息</span><span class="sxs-lookup"><span data-stu-id="a5553-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a5553-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="a5553-104">Product Name</span></span>|<span data-ttu-id="a5553-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="a5553-105">SQL Server</span></span>|  
|<span data-ttu-id="a5553-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="a5553-106">Event ID</span></span>|<span data-ttu-id="a5553-107">14152</span><span class="sxs-lookup"><span data-stu-id="a5553-107">14152</span></span>|  
|<span data-ttu-id="a5553-108">事件源</span><span class="sxs-lookup"><span data-stu-id="a5553-108">Event Source</span></span>|<span data-ttu-id="a5553-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="a5553-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="a5553-110">组件</span><span class="sxs-lookup"><span data-stu-id="a5553-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="a5553-111">符号名称</span><span class="sxs-lookup"><span data-stu-id="a5553-111">Symbolic Name</span></span>||  
|<span data-ttu-id="a5553-112">消息正文</span><span class="sxs-lookup"><span data-stu-id="a5553-112">Message Text</span></span>|<span data-ttu-id="a5553-113">复制 - %s：代理 %s 计划重试。</span><span class="sxs-lookup"><span data-stu-id="a5553-113">Replication-%s: agent %s scheduled for retry.</span></span> <span data-ttu-id="a5553-114">%s</span><span class="sxs-lookup"><span data-stu-id="a5553-114">%s</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a5553-115">说明</span><span class="sxs-lookup"><span data-stu-id="a5553-115">Explanation</span></span>  
 <span data-ttu-id="a5553-116">指定的复制代理已计划重试请求的操作。</span><span class="sxs-lookup"><span data-stu-id="a5553-116">The specified replication agent has been scheduled to retry the requested operation.</span></span> <span data-ttu-id="a5553-117">进程继续重试，直到达到配置的最大作业步骤重试次数。</span><span class="sxs-lookup"><span data-stu-id="a5553-117">The process continues to retry until it reaches the configured maximum number of retry attempts for the job step.</span></span>  
  
 <span data-ttu-id="a5553-118">通常由于下列原因之一发生重试：</span><span class="sxs-lookup"><span data-stu-id="a5553-118">A retry typically occurs because of one of the following reasons:</span></span>  
  
-   <span data-ttu-id="a5553-119">超过了 **QueryTimeout** 值。</span><span class="sxs-lookup"><span data-stu-id="a5553-119">The **QueryTimeout** value is exceeded.</span></span>  
  
-   <span data-ttu-id="a5553-120">超过了 **LoginTimeout** 值。</span><span class="sxs-lookup"><span data-stu-id="a5553-120">The **LoginTimeout** value is exceeded.</span></span>  
  
-   <span data-ttu-id="a5553-121">将复制进程选为了死锁牺牲品。</span><span class="sxs-lookup"><span data-stu-id="a5553-121">The replication process was chosen as a deadlock victim.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a5553-122">用户操作</span><span class="sxs-lookup"><span data-stu-id="a5553-122">User Action</span></span>  
 <span data-ttu-id="a5553-123">如果重试消息很少出现，则不需要用户操作。</span><span class="sxs-lookup"><span data-stu-id="a5553-123">If the retry message is infrequent, no user action is required.</span></span>  
  
 <span data-ttu-id="a5553-124">使用 [sp_help_jobstep](/sql/relational-databases/system-stored-procedures/sp-help-jobstep-transact-sql) 查看指定复制代理将要重试的“运行代理”  步骤的当前最大尝试次数设置。</span><span class="sxs-lookup"><span data-stu-id="a5553-124">Use [sp_help_jobstep](/sql/relational-databases/system-stored-procedures/sp-help-jobstep-transact-sql) to view the current setting for the maximum number of times the **Run agent** step for the specified replication agent will retry.</span></span> <span data-ttu-id="a5553-125">您可以使用 **@retry_attempts** [sp_update_jobstep](/sql/relational-databases/system-stored-procedures/sp-update-jobstep-transact-sql)存储过程的参数来调整作业步骤重试的次数。</span><span class="sxs-lookup"><span data-stu-id="a5553-125">You can use the **@retry_attempts** parameter of the [sp_update_jobstep](/sql/relational-databases/system-stored-procedures/sp-update-jobstep-transact-sql) stored procedure to adjust the number of times a job step retries.</span></span>  
  
 <span data-ttu-id="a5553-126">如果重试消息频繁重复出现，则应根据错误消息排除导致重试的问题。</span><span class="sxs-lookup"><span data-stu-id="a5553-126">If the retry message recurs frequently, troubleshoot the issue based on the message that is causing the retry.</span></span> <span data-ttu-id="a5553-127">对于指示为何必须计划重试的消息，检查代理的历史记录。</span><span class="sxs-lookup"><span data-stu-id="a5553-127">Check the agent's history for messages that indicate why the retry had to be scheduled.</span></span> <span data-ttu-id="a5553-128">某些情况下，您可能需要对复制代理启用更详细的日志记录。</span><span class="sxs-lookup"><span data-stu-id="a5553-128">In some cases you may have to enable more detailed logging for your replication agent.</span></span> <span data-ttu-id="a5553-129">有关如何配置复制日志记录的详细信息，请参阅 Microsoft 知识库文章 [312292](https://support.microsoft.com/kb/312292)。</span><span class="sxs-lookup"><span data-stu-id="a5553-129">For more information about how to configure logging for replication, see the Microsoft Knowledge Base article [312292](https://support.microsoft.com/kb/312292).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5553-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a5553-130">See Also</span></span>  
 [<span data-ttu-id="a5553-131">错误和事件参考（复制）</span><span class="sxs-lookup"><span data-stu-id="a5553-131">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
