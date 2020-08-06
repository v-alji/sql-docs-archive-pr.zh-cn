---
title: MSSQL_ENG021076 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG021076 error
ms.assetid: 612e5c59-ba3e-49c3-a3df-56bac3d850a2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4161428767ce78726436c0cf794f5250140d35b5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688826"
---
# <a name="mssql_eng021076"></a><span data-ttu-id="da5dd-102">MSSQL_ENG021076</span><span class="sxs-lookup"><span data-stu-id="da5dd-102">MSSQL_ENG021076</span></span>
    
## <a name="message-details"></a><span data-ttu-id="da5dd-103">消息详细信息</span><span class="sxs-lookup"><span data-stu-id="da5dd-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="da5dd-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="da5dd-104">Product Name</span></span>|<span data-ttu-id="da5dd-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="da5dd-105">SQL Server</span></span>|  
|<span data-ttu-id="da5dd-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="da5dd-106">Event ID</span></span>|<span data-ttu-id="da5dd-107">21076</span><span class="sxs-lookup"><span data-stu-id="da5dd-107">21076</span></span>|  
|<span data-ttu-id="da5dd-108">事件源</span><span class="sxs-lookup"><span data-stu-id="da5dd-108">Event Source</span></span>|<span data-ttu-id="da5dd-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="da5dd-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="da5dd-110">组件</span><span class="sxs-lookup"><span data-stu-id="da5dd-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="da5dd-111">符号名称</span><span class="sxs-lookup"><span data-stu-id="da5dd-111">Symbolic Name</span></span>||  
|<span data-ttu-id="da5dd-112">消息正文</span><span class="sxs-lookup"><span data-stu-id="da5dd-112">Message Text</span></span>|<span data-ttu-id="da5dd-113">项目 '%s' 的初始快照尚不可用。</span><span class="sxs-lookup"><span data-stu-id="da5dd-113">The initial snapshot for article '%s' is not yet available.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="da5dd-114">说明</span><span class="sxs-lookup"><span data-stu-id="da5dd-114">Explanation</span></span>  
 <span data-ttu-id="da5dd-115">如果分发代理在快照代理生成完快照之前启动，则会引发错误 MSSQL_ENG021076。</span><span class="sxs-lookup"><span data-stu-id="da5dd-115">Error MSSQL_ENG021076 can be raised if the Distribution Agent is started before the Snapshot Agent has finished generating the snapshot.</span></span> <span data-ttu-id="da5dd-116">仅当发布包含单个项目时才会引发此错误。</span><span class="sxs-lookup"><span data-stu-id="da5dd-116">This error is raised only if the publication contains a single article.</span></span> <span data-ttu-id="da5dd-117">如果发布包含多个项目，将引发 MSSQL_ENG021075。</span><span class="sxs-lookup"><span data-stu-id="da5dd-117">If the publication contains more than one article, MSSQL_ENG021075 is raised instead.</span></span> <span data-ttu-id="da5dd-118">有关详细信息，请参阅 [MSSQL_ENG021075](mssql-eng021075.md)。</span><span class="sxs-lookup"><span data-stu-id="da5dd-118">For more information, see [MSSQL_ENG021075](mssql-eng021075.md).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="da5dd-119">用户操作</span><span class="sxs-lookup"><span data-stu-id="da5dd-119">User Action</span></span>  
 <span data-ttu-id="da5dd-120">如果发布的快照代理自订阅创建以来一直未启动，或者自上次您选择重新初始化订阅以来一直未启动，则启动快照代理并让它在启动分发代理之前完成。</span><span class="sxs-lookup"><span data-stu-id="da5dd-120">If the Snapshot Agent for the publication has not been started since the subscription was created, or if it has not been started since the last time you chose to reinitialize the subscription, start the Snapshot Agent and let it complete before starting the Distribution Agent.</span></span> <span data-ttu-id="da5dd-121">有关详细信息，请参阅[创建并应用快照](create-and-apply-the-snapshot.md)。</span><span class="sxs-lookup"><span data-stu-id="da5dd-121">For more information, see [Create and Apply the Snapshot](create-and-apply-the-snapshot.md).</span></span>  
  
 <span data-ttu-id="da5dd-122">如果快照代理没有完成，请检查快照代理历史记录以查找错误并将其消除。</span><span class="sxs-lookup"><span data-stu-id="da5dd-122">If the Snapshot Agent does not complete, check the Snapshot Agent history for errors and address them.</span></span> <span data-ttu-id="da5dd-123">有关在复制监视器中查看代理状态和错误详细资料的信息，请参阅[使用复制监视器查看信息和执行任务](monitor/view-information-and-perform-tasks-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="da5dd-123">For information about viewing agent status and error details in Replication Monitor, see [View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="da5dd-124">如果错误继续出现，请增加代理的日志记录并指定日志的输出文件。</span><span class="sxs-lookup"><span data-stu-id="da5dd-124">If the error continues to occur, increase the logging of the agent and specify an output file for the log.</span></span> <span data-ttu-id="da5dd-125">此操作可能会提供找到该错误和/或其他错误消息的步骤，具体取决于错误的上下文。</span><span class="sxs-lookup"><span data-stu-id="da5dd-125">Depending on the context of the error, this could provide the steps leading up to the error and/or additional error messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da5dd-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="da5dd-126">See Also</span></span>  
 [<span data-ttu-id="da5dd-127">错误和事件参考（复制）</span><span class="sxs-lookup"><span data-stu-id="da5dd-127">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
